# Library Management System (Python + MySQL)

## Overview

This project is a console-based Library Management System built with Python and MySQL. It provides role-based access for administrators, librarians, and members to manage users, books, and borrowing activities through a text menu interface.[1][2]

## Features

- Secure login system with role-based dashboards for admin, librarian, and member.[2]
- User management: add, view, update, and suspend users with role and status control.[1]
- Book management: add, view, update, and remove books with inventory tracking of total and available copies.[1]
- Loan management: check out books, process returns, enforce borrowing limits, and track due dates.[3][4]
- Reporting: view summary reports for books by genre, users by role, and loans by status.[2]
- Member self-service: view currently issued books, remaining days, and search catalog by title, author, or genre.[3]
- Tabular console output using the `tabulate` library for readable grids in the terminal.[5][6]

## Technologies and Tools Used

- Python 3 for application logic and command-line interface.[3]
- MySQL as the relational database for users, books, and loans.[7][8]
- `mysql-connector-python` as the MySQL driver for Python, compliant with the Python DB API 2.0.[9][10][11]
- `tabulate` for pretty-printing query results and reports as formatted tables in the console.[12][6][5]
- Standard libraries: `getpass` (secure password input), `hashlib` (password hashing), `datetime` (date and due date handling), `sys` (process exit control).[13][3]

## Installation and Setup

1. **Prerequisites**

   - Install Python 3 on your system.[3]
   - Install MySQL Server and ensure you can log in with the root or another MySQL user.[4][7]

2. **Clone or download the project**

   - Place the main script file (for example `library_system.py`) in a project directory of your choice.[1]

3. **Install required Python packages**

   Run the following commands in your terminal or command prompt:

   ```bash
   pip install mysql-connector-python
   pip install tabulate
   ```

   These commands install the MySQL driver and the table-formatting library used by the project.[5][9]

4. **Configure MySQL access**

   - Ensure the MySQL service is running.[13]
   - Make sure you have the MySQL password for the user `root` (or adapt the code later if you use a different user).[4]

5. **Database initialization**

   - On first run, the script will:
     - Connect to MySQL using the credentials you provide at the prompt.[13]
     - Create a database named `library_management` if it does not already exist.[1]
     - Create the tables `users`, `books`, and `loans`.[8][7]
     - Insert a default admin account if no users exist:
       - Username: `admin`  
       - Password: `admin123`  

## How to Run the Project

1. Open a terminal or command prompt in the project directory.[1]
2. Run the script:

   ```bash
   python library_system.py
   ```

   Adjust the file name if your main file has a different name.[1]

3. When prompted, enter the MySQL password for the configured user (by default `root` in the code).[13]
4. After successful connection and initialization, the main menu will appear:

   - `1. Login`  
   - `2. Exit`  

5. Log in using the default admin credentials on first run:

   - Username: `admin`  
   - Password: `admin123`  

6. After login, the system will show the dashboard according to your role (admin, librarian, or member).[2]

## Usage Instructions

### Admin role

Admin users can:

- Manage users:
  - Add new users (admin, librarian, member) with secure hashed passwords.[7]
  - View all users with IDs, usernames, roles, and status.[1]
  - Update user full name, role, or status.  
  - Suspend users only if they have no active loans.[8]
- Manage books:
  - Add new books with title, author, ISBN, genre, and copy counts.[7]
  - View books with current available and total copies.  
  - Update book information and adjust total copies with automatic update of available copies.  
  - Remove books only when all copies are available (none checked out).  
- View reports:
  - Books grouped by genre with title and copy counts.  
  - Users grouped by role.  
  - Loans grouped by status.[2]
- Change own password securely.[3]

### Librarian role

Librarian users can:

- Check out books to members:
  - Validate book existence and available copies.  
  - Validate member status (active, role `member`).  
  - Enforce a maximum of 5 active loans per member.[8]
  - Create loan records with 14-day due dates and reduce available copies.[7]
- Process returns:
  - Locate active loans for the given book and member.  
  - Mark loans as returned or overdue depending on the return date.  
  - Increment available copies of the book.[3]
- View active loans ordered by due date.  
- View overdue books with days overdue.  
- Change own password.  

### Member role

Member users can:

- View current checked-out books with checkout date, due date, and days remaining.[3]
- Search books by title, author, or genre and see availability.[8]
- Change own password.  

## Instructions for Testing

1. **Initial admin login**

   - Start the application, connect to MySQL, and log in using the default admin credentials.  
   - Verify you can access the admin dashboard and see menu options for users, books, and reports.[2]

2. **User management tests**

   - Add a librarian and member user.  
   - Use the “View Users” option to confirm the new records appear with correct roles and active status.[1]
   - Update a user’s role or status and verify the change.  
   - Attempt to suspend a user with and without active loans to confirm validation.[8]

3. **Book management tests**

   - Add several books with different genres and copy counts.[7]
   - Verify listing through “View Books” and confirm available vs total copies.  
   - Update total copies and check that available copies adjust correctly.  
   - Try to remove a book that has checked-out copies and confirm the system prevents this.[8]

4. **Loan and return tests (librarian)**

   - Log in as librarian.  
   - Check out a book to a member and confirm:
     - A loan is created.  
     - The book’s available copies decrease by one.[3]
   - Use “View Active Loans” to confirm the record.  
   - Process a return and ensure:
     - The loan status changes to returned or overdue as appropriate.  
     - Available copies increase.  

5. **Member tests**

   - Log in as a member.  
   - Use “View My Books” to confirm current loans and remaining days.  
   - Use “Search Books” with different keywords to validate search across title, author, and genre.[8]

6. **Report verification**

   - As admin, use “View Reports” to confirm:
     - Books by genre display correct counts.  
     - Users by role match actual users created.  
     - Loans by status reflect active, returned, and overdue loans.[2]

7. **Password change tests**

   - For each role (admin, librarian, member), change the password.  
   - Log out and log back in with the new password to verify that authentication uses the updated hash.[3]
## Git commit history is mentioned in the project report
#### Below are the References used to make the Project
[1](https://github.com/PavanAnanthSharma/Library-Management-Using-Python-and-MySQL)
[2](https://open.openclass.ai/resource/lesson-66956fb1c61552c43c77965f/share?code=i96uVzSAf0kVag)
[3](https://data-flair.training/blogs/library-management-system-python-project/)
[4](https://pyseek.com/2022/04/library-management-system-project-in-python/)
[5](https://pypi.org/project/tabulate/)
[6](https://www.datacamp.com/tutorial/python-tabulate)
[7](https://www.scribd.com/document/606463210/Library-Management-System-Project)
[8](https://www.geeksforgeeks.org/software-engineering/library-management-system/)
[9](https://pypi.org/project/mysql-connector-python/)
[10](https://www.geeksforgeeks.org/python/mysql-connector-python-module-in-python/)
[11](https://dev.mysql.com/doc/connectors/en/connector-python-introduction.html)
[12](https://www.geeksforgeeks.org/python/introduction-to-python-tabulate-library/)
[13](https://dev.mysql.com/doc/connector-python/en/connector-python-example-connecting.html)
[14](https://pythongeeks.org/python-library-management-system-project/)
[15](https://www.youtube.com/watch?v=BeGP5H24xtM)
[16](https://stackoverflow.com/questions/67548514/how-to-display-pretty-tables-in-terminal-with-tabulate-python-package)
[17](https://github.com/mysql/mysql-connector-python)
[18](https://github.com/vikasgola/Library-Management-System)
[19](https://www.linkedin.com/pulse/effortless-data-tabulation-python-tabulate-library-360-digitmg)
[20](https://360digitmg.com/blog/python-tabulate)
