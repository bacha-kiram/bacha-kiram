## Hi there 👋

<!--
**bacha-kiram/bacha-kiram** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

<?php
// Database configuration
$host = 'localhost';
$dbname = 'user_data';
$username = 'root';
$password = ''; // Change this based on your setup (e.g., 'root' with no password for XAMPP)

// Create a PDO connection
try {
    $pdo = new PDO("mysql:host=$host;dbname=$dbname;charset=utf8", $username, $password);
} catch (PDOException $e) {
    die("Database connection failed: " . $e->getMessage());
}

// Get form data
$name = $_POST['name'];
$height = floatval($_POST['height']);
$weight = floatval($_POST['weight']);
$age = intval($_POST['age']);

// Prepare and execute the insert query
$sql = "INSERT INTO persons (name, height, weight, age) VALUES (?, ?, ?, ?)";
$stmt = $pdo->prepare($sql);
$stmt->execute([$name, $height, $weight, $age]);

echo "User data saved successfully!";
?>

