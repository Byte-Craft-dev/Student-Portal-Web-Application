# Student Portal Web Application

A full-stack web application built with HTML, CSS, JavaScript, and PHP, featuring secure user authentication, session management, and responsive design.

## Features

- **User Registration** - Secure registration with form validation and duplicate email prevention
- **User Authentication** - Login system with password hashing and session management
- **Protected Pages** - Profile and contact pages accessible only to authenticated users
- **Contact Form** - Interactive 5-star rating system with feedback submission
- **Form Validation** - Client-side (JavaScript) and server-side (PHP) validation
- **Responsive Design** - Mobile-friendly interface using CSS Flexbox
- **Session Management** - Secure user sessions with proper logout functionality

## Technologies Used

- **Frontend**: HTML5, CSS3, JavaScript
- **Backend**: PHP
- **Database**: MySQL
- **Server**: Apache (XAMPP/Laragon)

## Project Structure

```
student-webapp/
├── index.html              # Home page
├── register.html           # User registration page
├── login.html              # User login page
├── profile.php             # Protected user profile page
├── contact.php             # Protected contact form page
├── css/
│   └── style.css           # Main stylesheet
├── js/
│   └── script.js           # Client-side JavaScript
├── php/
│   ├── config.php          # Database configuration
│   ├── register.php        # Registration handler
│   ├── login.php           # Login handler
│   └── logout.php          # Logout handler
└── database.sql            # Database schema
```

## Installation

### Prerequisites

- XAMPP or Laragon (Apache + MySQL)
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Text editor (VS Code, Sublime Text, etc.)

### Setup Steps

1. **Install and Start Server**
   - Download and install [Laragon](https://laragon.org/) or [XAMPP](https://www.apachefriends.org/)
   - Start Apache and MySQL services

2. **Create Database**
   - Access phpMyAdmin at `http://localhost/phpmyadmin`
   - Create a new database named `student_webapp`
   - Run the following SQL commands:

```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE contacts (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    message TEXT NOT NULL,
    rating INT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

3. **Deploy Application**
   - Copy the `student-webapp` folder to your server's web directory
     - **Laragon**: `C:\laragon\www\student-webapp`
     - **XAMPP**: `C:\xampp\htdocs\student-webapp`

4. **Configure Database Connection**
   - Open `php/config.php`
   - Update database credentials if needed:
     ```php
     $host = "localhost";
     $username = "root";
     $password = "1234";  // Update with your MySQL password
     $database = "student_webapp";
     ```

5. **Access Application**
   - Open browser and navigate to `http://localhost/student-webapp/`

## Usage

### Registration
1. Navigate to the Register page
2. Fill in the registration form:
   - Full Name (required)
   - Email Address (required, valid format)
   - Password (required, minimum 8 characters)
   - Confirm Password (must match)
3. Submit the form
4. Upon success, you'll be redirected to the login page

### Login
1. Navigate to the Login page
2. Enter your registered email and password
3. Click "Login"
4. Upon success, you'll be redirected to your profile page

### Profile
- View your account information
- Access the contact form
- Logout option available

### Contact Form
1. Access from the profile page (requires authentication)
2. Enter your message
3. Select a rating (1-5 stars)
4. Submit feedback

## Security Features

- **Password Security**: All passwords are hashed using PHP's `password_hash()` function
- **SQL Injection Prevention**: Prepared statements for all database queries
- **XSS Prevention**: Input sanitization and output escaping
- **Session Security**: Proper session management with secure logout
- **Access Control**: Protected pages require authentication

## Form Validation

### Client-Side (JavaScript)
- Real-time email format validation
- Password strength checking (minimum 8 characters)
- Password confirmation matching
- Required field validation
- Interactive error messages

### Server-Side (PHP)
- Duplicate validation of all client-side rules
- Email uniqueness verification
- Comprehensive input sanitization
- Type checking and data validation

## Responsive Design

- **Mobile-First Approach**: Base styles optimized for mobile devices
- **Breakpoints**:
  - Mobile: Default (< 768px)
  - Tablet: 768px and above
  - Desktop: 1024px and above
- **Flexible Layouts**: CSS Flexbox for adaptive components
- **Touch-Friendly**: Optimized button sizes and input fields for mobile

## Troubleshooting

### Database Connection Issues
- Verify MySQL service is running
- Check database credentials in `php/config.php`
- Ensure database `student_webapp` exists
- Test connection through phpMyAdmin

### Page Not Found Errors
- Verify files are in the correct directory
- Ensure Apache service is running
- Check file paths in navigation links

### Form Submission Problems
- Check PHP error logs in Laragon/XAMPP
- Verify database tables exist with correct structure
- Ensure form action paths are correct

## Future Enhancements

- Email verification for new registrations
- Password reset functionality
- Profile editing capabilities
- Admin panel for user management
- Contact submission history
- Two-factor authentication
- CSRF protection
- Rate limiting for login attempts

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**K.D. Tharushi Navodya**

- GitHub: [@Byte-Craft-dev](https://github.com/Byte-Craft-dev)
- LinkedIn: [Tharushi Karawgoda](http://www.linkedin.com/in/tharushi-navodya-)
- Email: [tharushi123navo@gmail.com]

## 🙏 Acknowledgments

- PHP community for extensive documentation and resources
- MySQL documentation and best practices guides
- Web development tutorials and educational resources
- Laragon/XAMPP development environment teams
- Open source contributors and developers
- Instructors and mentors who provided guidance throughout the project

