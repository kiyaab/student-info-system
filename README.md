<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Robe Secondary School - Student Info System</title>
  <style>
    /* Global Reset */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Arial', sans-serif;
    }

    body {
      display: flex;
      min-height: 100vh;
      transition: background-color 0.3s ease, color 0.3s ease;
      background-color: var(--background-color);
      color: var(--text-color);
    }

    /* Dark theme variables */
    :root {
      --primary-color: #007BFF;
      --secondary-color: #1f2a3d;
      --highlight-color: #1d8ee5;
      --text-color: #ffffff;
      --background-color: #121212;
    }

    /* Light theme variables */
    body.light-mode {
      --primary-color: #1a73e8;
      --secondary-color: #f1f1f1;
      --highlight-color: #007BFF;
      --text-color: #121212;
      --background-color: #f1f1f1;
    }

    /* Sidebar Styles */
    .sidebar {
      height: 100%;
      width: 250px;
      position: fixed;
      top: 0;
      left: 0;
      background-color: var(--secondary-color);
      padding: 20px;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      box-shadow: 2px 0 15px rgba(0, 0, 0, 0.5);
    }

    .sidebar a {
      color: var(--text-color);
      padding: 10px;
      text-decoration: none;
      font-size: 18px;
      margin-bottom: 10px;
      transition: background-color 0.3s ease;
    }

    .sidebar a:hover {
      background-color: var(--highlight-color);
      border-radius: 4px;
    }

    /* Main Content */
    .content {
      margin-left: 250px;
      padding: 20px;
      width: 100%;
      transition: margin-left 0.3s ease;
    }

    /* Header */
    header {
      background: linear-gradient(135deg, var(--primary-color), var(--highlight-color));
      padding: 20px;
      text-align: center;
      color: var(--text-color);
      box-shadow: 0 6px 15px rgba(0, 0, 0, 0.4);
    }

    .profile {
      position: absolute;
      top: 20px;
      right: 20px;
      display: flex;
      align-items: center;
      color: var(--text-color);
    }

    .profile img {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      margin-right: 15px;
      transition: transform 0.3s ease;
    }

    .profile img:hover {
      transform: scale(1.2);
    }

    /* Hero Section */
    .hero {
      color: var(--highlight-color);
      text-align: center;
      padding: 120px 20px;
      position: relative;
    }

    .hero h1 {
      font-size: 60px;
      text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.4);
      margin-bottom: 20px;
    }

    .hero p {
      font-size: 24px;
      max-width: 800px;
      margin: 0 auto;
      text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.6);
    }

    .hero button {
      padding: 15px 30px;
      background-color: var(--highlight-color);
      border: none;
      color: var(--text-color);
      font-size: 20px;
      border-radius: 6px;
      cursor: pointer;
      transition: background-color 0.3s ease, transform 0.3s ease;
    }

    .hero button:hover {
      background-color: var(--primary-color);
      transform: scale(1.1);
    }

    /* About Section */
    section {
      padding: 80px 20px;
      margin: 40px 0;
      background-color: var(--secondary-color);
      border-radius: 10px;
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.6);
      text-align: center;
    }

    section h1 {
      font-size: 36px;
      color: var(--highlight-color);
      margin-bottom: 25px;
    }

    section p {
      font-size: 20px;
      color: var(--text-color);
      margin-bottom: 25px;
    }

    .books ul {
      list-style-type: none;
      padding: 0;
      margin-top: 40px;
    }

    .books ul li {
      background-color: #333;
      margin: 10px 0;
      padding: 15px;
      border-radius: 6px;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
      font-size: 20px;
      display: flex;
      justify-content: space-between;
      transition: transform 0.3s ease, background-color 0.3s ease;
    }

    .books ul li:hover {
      background-color: #444;
      transform: translateY(-7px);
    }

    /* Teachers Section */
    #teachers {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      margin-top: 30px;
    }

    .teacher {
      background-color: #2e2e2e;
      padding: 20px;
      margin: 20px;
      border-radius: 8px;
      text-align: center;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
      transition: transform 0.3s ease;
      width: 200px;
    }

    .teacher img {
      width: 100px;
      height: 100px;
      border-radius: 50%;
      margin-bottom: 15px;
      cursor: pointer;
    }

    .teacher:hover {
      transform: scale(1.05);
    }

    .teacher h3 {
      color: var(--highlight-color);
      font-size: 24px;
    }

    .teacher p {
      color: var(--text-color);
      font-size: 18px;
    }

    footer {
      background-color: var(--secondary-color);
      color: var(--text-color);
      text-align: center;
      padding: 30px;
      font-size: 18px;
    }

    /* Dark Mode and Light Mode Toggle */
    .mode-toggle {
      position: fixed;
      top: 20px;
      right: 20px;
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 30px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    .mode-toggle:hover {
      background-color: var(--highlight-color);
    }

    /* Login Page */
    .login-page {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      background-color: var(--background-color);
    }

    .login-form {
      background-color: var(--secondary-color);
      padding: 40px;
      border-radius: 8px;
      box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2);
      width: 400px;
      text-align: center;
    }

    .login-form h2 {
      color: var(--highlight-color);
      margin-bottom: 20px;
    }

    .login-form input {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: none;
      border-radius: 5px;
      background-color: #444;
      color: var(--text-color);
      font-size: 18px;
    }

    .login-form button {
      padding: 10px 20px;
      width: 100%;
      background-color: var(--primary-color);
      color: white;
      border: none;
      border-radius: 5px;
      font-size: 18px;
      cursor: pointer;
    }

    .login-form button:hover {
      background-color: var(--highlight-color);
    }

    /* Contact Page */
    #contact {
      padding: 80px 20px;
      background-color: var(--secondary-color);
      margin-top: 40px;
      border-radius: 10px;
      box-shadow: 0 8px 30px rgba(0, 0, 0, 0.6);
    }

    #contact h1 {
      font-size: 36px;
      color: var(--highlight-color);
      margin-bottom: 25px;
    }

    #contact form {
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    #contact form input,
    #contact form textarea {
      width: 80%;
      padding: 10px;
      margin: 10px 0;
      border: none;
      border-radius: 5px;
      background-color: #444;
      color: var(--text-color);
      font-size: 18px;
    }

    #contact form button {
      width: 80%;
      padding: 12px;
      background-color: var(--primary-color);
      border: none;
      color: white;
      font-size: 18px;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }

    #contact form button:hover {
      background-color: var(--highlight-color);
    }
  </style>
</head>
<body>

  <!-- Dark/Light Mode Toggle Button -->
  <button class="mode-toggle" onclick="toggleMode()">Switch to Light Mode</button>

  <!-- Sidebar Navigation -->
  <div class="sidebar">
    <h2>Robe Secondary School</h2>
    <a href="#home">Home</a>
    <a href="#about">About</a>
    <a href="#teachers">Our Teachers</a>
    <a href="#contact">Contact</a>
    <a href="#books">Books</a>
    <a href="#login">Login</a>
  </div>

  <!-- Main Content -->
  <div class="content">
    <!-- Header -->
    <header>
      <h1>Welcome to Robe Secondary School</h1>
    </header>

    <!-- Home Section -->
    <section id="home" class="hero">
      <h1>Welcome to Robe Secondary School</h1>
      <p>Your gateway to quality education and student management. Discover, learn, and grow with us!</p>
      <button onclick="window.location.href='result.html'">My Result</button>
    </section>

    <!-- About Section -->
    <section id="about">
      <h1>About Robe Secondary School</h1>
      <p>Robe Secondary School, located in Oromia, Bale Robe, Ethiopia, is the oldest and most esteemed high school in the region. With a legacy of excellence in academics and extracurricular activities, we have nurtured countless students who have gone on to achieve great things. Our campus offers modern facilities, experienced faculty, and a supportive environment that fosters holistic development. From science laboratories to cultural activities, we ensure our students are well-prepared for the challenges of the future.</p>
    </section>

    <!-- Teachers Section -->
    <section id="teachers">
        <h1>Our Teachers</h1>
  
        <div class="teacher" onclick="alert('Teacher 1 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 1">
          <h3>Teacher 1</h3>
          <p>Subject: Math</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 2 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 2">
          <h3>Teacher 2</h3>
          <p>Subject: English</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 3 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 3">
          <h3>Teacher 3</h3>
          <p>Subject: Biology</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 4 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 4">
          <h3>Teacher 4</h3>
          <p>Subject: Chemistry</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 5 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 5">
          <h3>Teacher 5</h3>
          <p>Subject: History</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 6 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 6">
          <h3>Teacher 6</h3>
          <p>Subject: Geography</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 7 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 7">
          <h3>Teacher 7</h3>
          <p>Subject: Physics</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 8 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 8">
          <h3>Teacher 8</h3>
          <p>Subject: Computer Science</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 9 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 9">
          <h3>Teacher 9</h3>
          <p>Subject: Physical Education</p>
        </div>
  
        <div class="teacher" onclick="alert('Teacher 10 info')">
          <img src="c:\Users\babi-_fnsh\Downloads\Telegram Desktop\photo_2024-11-15_06-00-19.jpg" alt="Teacher 10">
          <h3>Teacher 10</h3>
          <p>Subject: Art</p>
        </div>
  
        <!-- You can continue adding more teachers here -->
  
      </section>

    <!-- Books Section -->
    <section id="books" class="books">
      <h1>Recommended Books</h1>
      <h2>Grade 9</h2>
      <ul>
        <li><a href="https://fetena.net/" target="_blank">Math</a></li>
        <li><a href="https://fetena.net/" target="_blank">Physics</a></li>
        <li><a href="https://fetena.net/" target="_blank">History</a></li>
        <li><a href="https://fetena.net/" target="_blank">Chemistry</a></li>
      </ul>
      <h2>Grade 10</h2>
      <ul>
        <li><a href="https://fetena.net/" target="_blank">Math</a></li>
        <li><a href="https://fetena.net/" target="_blank">Physics</a></li>
        <li><a href="https://fetena.net/" target="_blank">Biology</a></li>
        <li><a href="https://fetena.net/" target="_blank">English</a></li>
      </ul>
      <h2>Grade 11</h2>
      <ul>
        <li><a href="https://fetena.net/" target="_blank">Chemistry</a></li>
        <li><a href="https://fetena.net/" target="_blank">Mathematics</a></li>
        <li><a href="https://fetena.net/" target="_blank">Physics</a></li>
        <li><a href="https://fetena.net/" target="_blank">English</a></li>
      </ul>
      <h2>Grade 12</h2>
      <ul>
        <li><a href="https://fetena.net/" target="_blank">Math</a></li>
        <li><a href="https://fetena.net/" target="_blank">Physics</a></li>
        <li><a href="https://fetena.net/" target="_blank">History</a></li>
        <li><a href="https://fetena.net/" target="_blank">Chemistry</a></li>
      </ul>
    </section>

    <!-- Login Section -->
    <section id="login" class="login-page">
      <div class="login-form">
        <h2>Login</h2>
        <form id="loginForm">
          <input type="text" id="username" placeholder="Username" required>
          <input type="password" id="password" placeholder="Password" required>
          <button type="submit">Login</button>
        </form>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contact">
      <h1>Contact Us</h1>
      <form id="contact-form">
        <input type="text" id="name" name="name" placeholder="Your Name" required>
        <input type="email" id="email" name="email" placeholder="Your Email" required>
        <textarea id="message" name="message" placeholder="Your Message" required></textarea>
        <button type="submit">Submit</button>
      </form>
    </section>

    <!-- Footer -->
    <footer>
      <p>&copy; 2025 Robe Secondary School | Created by Kiya | All rights reserved</p>
    </footer>
  </div>

  <script>
    let darkMode = true;

    // Toggle Dark/Light Mode
    function toggleMode() {
      document.body.classList.toggle('light-mode');
      darkMode = !darkMode;
      document.querySelector('.mode-toggle').textContent = darkMode ? 'Switch to Light Mode' : 'Switch to Dark Mode';
    }

    // Show teacher information when clicked
    function showTeacherInfo(teacherName) {
      alert('Showing info for: ' + teacherName);
    }
  </script>

</body>
</html>
