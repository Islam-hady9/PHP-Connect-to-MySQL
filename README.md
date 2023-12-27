# Connecting MySQL Database with PHP

## Description:

This repository demonstrates the integration of a MySQL database with PHP for web applications. Follow the steps below to set up the connection:

### 1. Clone the Repository:

```bash
git clone https://github.com/Islam-hady9/PHP-Connect-to-MySQL.git
cd PHP-Connect-to-MySQL
```

### 2. Database Configuration:

Edit the `config.php` file to set your MySQL database credentials:

```php
<?php
// config.php

$host = "localhost";
$username = "your_username";
$password = "your_password";
$database = "your_database";

$conn = new mysqli($host, $username, $password, $database);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

Replace `your_username`, `your_password`, and `your_database` with your MySQL database credentials.

### 3. Sample Database Schema:

Create a sample table in your MySQL database:

```sql
CREATE TABLE IF NOT EXISTS users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL
);
```

### 4. PHP Usage:

Use the connection in your PHP files. For example, to retrieve data:

```php
<?php
// index.php

include 'config.php';

$sql = "SELECT * FROM users";
$result = $conn->query($sql);

if ($result->num_rows > 0) {
    while($row = $result->fetch_assoc()) {
        echo "ID: " . $row["id"]. " - Name: " . $row["username"]. " - Email: " . $row["email"]. "<br>";
    }
} else {
    echo "0 results";
}

$conn->close();
?>
```

This repository serves as a foundation for PHP and MySQL integration. Feel free to expand it based on your project requirements.

## Note:

Remember to secure your database credentials and avoid hardcoding sensitive information in publicly accessible files. Use environment variables or other secure methods for production applications.
