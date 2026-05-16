# 🚀 AI Job Portal

A polished recruitment portal built with PHP, MySQL, HTML, CSS, and JavaScript.

This app delivers a role-based hiring experience with separate dashboards for admins, employers, and job seekers.

---

# 🌟 What this project delivers

- **Admin dashboard** for managing users, jobs, categories, and analytics.
- **Employer portal** for posting jobs, editing listings, and reviewing applications.
- **Job seeker experience** for searching jobs, applying with resume uploads, and tracking application status.
- **Modern responsive UI** designed for desktop and mobile.
- **Clean PHP structure** with reusable includes and role-based access control.

---

# 🧩 Project structure

```
ai_job_portal/
├── admin/            # Admin pages and dashboard
├── employer/         # Employer dashboard and job management
├── jobseeker/        # Job seeker interface and applications
├── includes/         # Shared auth, database, header/footer files
├── assets/           # CSS and JavaScript
│   ├── css/
│   └── js/
├── uploads/          # Uploaded resumes
├── index.php         # Home page
├── login.php         # Login page
├── register.php      # Registration page
└── README.md         # Project documentation
```

---

# 🚀 Key features

## Admin
- Manage users
- Manage jobs
- Manage categories
- View summary statistics

## Employer
- Create and update job posts
- Manage active job listings
- View candidate applications

## Job Seeker
- Search and filter job listings
- Apply with resume upload
- Track submitted applications

---

# 🛠 Tech stack

- PHP (Core PHP)
- MySQL
- HTML5
- CSS3
- JavaScript
- XAMPP

---

# 📝 Setup guide

1. Copy the project folder into `xampp/htdocs/ai_job_portal`.
2. Start Apache and MySQL in XAMPP.
3. Open `http://localhost/phpmyadmin`.
4. Create a new database named `ai_job_portal`.
5. Import the SQL schema below.
6. Open `http://localhost/ai_job_portal/register.php` to begin.

---

# 🗄 Database setup

```sql
CREATE DATABASE ai_job_portal;
USE ai_job_portal;

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('admin','employer','jobseeker') NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE categories (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE jobs (
    id INT AUTO_INCREMENT PRIMARY KEY,
    employer_id INT NOT NULL,
    category_id INT NOT NULL,
    title VARCHAR(150) NOT NULL,
    description TEXT NOT NULL,
    location VARCHAR(100),
    salary VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (employer_id) REFERENCES users(id) ON DELETE CASCADE,
    FOREIGN KEY (category_id) REFERENCES categories(id) ON DELETE CASCADE
);

CREATE TABLE applications (
    id INT AUTO_INCREMENT PRIMARY KEY,
    job_id INT NOT NULL,
    jobseeker_id INT NOT NULL,
    resume VARCHAR(255),
    status VARCHAR(50) DEFAULT 'Pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (job_id) REFERENCES jobs(id) ON DELETE CASCADE,
    FOREIGN KEY (jobseeker_id) REFERENCES users(id) ON DELETE CASCADE
);

INSERT INTO users (name, email, password, role)
VALUES ('Admin', 'admin@gmail.com', '12345', 'admin');

INSERT INTO categories (name) VALUES
('IT'),
('Marketing'),
('Finance'),
('HR'),
('Sales');
```

---

# ⚠️ Important note

- The sample admin password is stored as plain text.
- For production, replace it with a secure hashed password.
- Use secure database credentials before deploying.

---

# 👩‍💻 Developer

Amina Simran — UI/UX and web development
