# Student Admission Management System

## Local installation (Windows, XAMPP on D drive)
1. Extract the ZIP. Copy `student_admission_system` into `D:\xampp\htdocs\`.
2. Start **Apache** and **MySQL** in XAMPP Control Panel.
3. Open `http://localhost/phpmyadmin/`, choose **Import**, select `database.sql`, click **Go**. The SQL creates `student_admission_db` and tables.
4. If your MySQL user is not root with an empty password, edit `config/db.php` defaults (or set `DB_HOST`, `DB_NAME`, `DB_USER`, `DB_PASS` environment variables).
5. Open `http://localhost/student_admission_system/`.
6. Test `admission.php` and `inquiry.php`; verify rows in phpMyAdmin under admissions and inquiries.
7. Visit `http://localhost/student_admission_system/admin/setup.php`, create a unique admin name and strong password (12+ characters).
8. **Immediately delete `admin/setup.php`** after creating the first admin. Sign in at `admin/login.php`, check dashboard and logout.

## Live deployment
Use a PHP 8 + MySQL hosting provider (cPanel shared hosting is usually easiest). Upload the project contents to the public web root (e.g. `public_html/`) using File Manager. Create a MySQL database and user in the hosting panel, grant access, and import `database.sql` via phpMyAdmin. Some hosts prohibit CREATE DATABASE: remove the first two SQL lines and select your already-created database before importing. Configure the production database name/user/password in `config/db.php` or environment variables. Enable HTTPS and test the public URL, form submissions, and admin login. Create the admin once and delete `admin/setup.php` from the public server. Never upload a local admin account database dump to public hosting.

## Notes
- Uses PHP PDO prepared statements, CSRF tokens, password hashing, session authentication, escaped HTML output, and redirect-after-post.
- Bootstrap loads from a CDN (internet required for full styling).
- The demo has no email sending, no file uploads, and no payment system.
- Protect production database credentials, use HTTPS, keep backups, and add rate limiting and stronger access controls before handling real student personal information.
- The dashboard displays the latest 200 admissions and inquiries; the total counters cover all records.
