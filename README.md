<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alamgir Khan - Software Engineer</title>
    <link rel="stylesheet" href="styles.css">
    <!-- Google Font -->
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" rel="stylesheet">

    <!-- Google Analytics -->
    <script async src="https://www.googletagmanager.com/gtag/js?id=G-W84885HLN0"></script>
    <script>
        window.dataLayer = window.dataLayer || [];
        function gtag(){dataLayer.push(arguments);}
        gtag('js', new Date());
        gtag('config', 'G-W84885HLN0'); // Replace YOUR_TRACKING_ID with actual ID
    </script>
</head>
<body>
    <header>
        <div class="container">
            <div class="logo">Alamgir Khan</div>
            <nav>
                <ul>
                    <li><a href="#about">About Me</a></li>
                    <li><a href="#resume">Resume</a></li>
                    <li><a href="#achievements">Achievements</a></li>
                    <li><a href="#portfolio">Portfolio</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <section id="hero">
        <div class="container hero-content">
            <img src="pic.jpg" alt="Alamgir Khan" class="hero-img">
            <h1>Innovative Software Engineer with a Passion for Problem Solving</h1>
            <a href="#resume" class="cta-button">View My Resume</a>
        </div>
    </section>

    <section id="about">
        <div class="container">
            <h2>About Me</h2>
            <p>I am a software engineer with a Bachelor’s degree in Electronics and communication from NIST, Odisha. My expertise lies in End to end performance testing and engineering, and I have a keen interest in AI and machine learning.</p>
            <h3>Skills</h3>
            <ul>
                <li>JavaScript</li>
                <li>Python</li>
                <li>React</li>
                <li>Node.js</li>
            </ul>
            <h3>Education</h3>
            <p>B.Tech in Electronics and communication engineering from NIST Odisha</p>
        </div>
    </section>

    <section id="resume">
        <div class="container">
            <h2>Resume</h2>
            <p>You can download my resume by clicking the link below:</p>
            <a href="ResumeAlamgirKhan.pdf" class="cta-button" download>Download Resume</a>
            <h3>Experience</h3>
            <p>Company Name | Role | Dates</p>
            <p>Responsibilities and achievements.</p>
            <h3>Certifications</h3>
            <p>Relevant certifications or courses.</p>
        </div>
    </section>

    <section id="achievements">
        <div class="container">
            <h2>Achievements</h2>
            <ul>
                <li>Best Innovator Award at XYZ Conference (2023)</li>
                <li>Developed an award-winning mobile app for XYZ organization</li>
                <li>Article on AI Trends published in Tech Journal</li>
            </ul>
        </div>
    </section>

    <section id="portfolio">
        <div class="container">
            <h2>Portfolio/Projects</h2>
            <div class="project">
                <h3>Project Name</h3>
                <p>Description, technologies used, and a link to the project or case study.</p>
            </div>
            <div class="project">
                <h3>Project Name</h3>
                <p>Description, technologies used, and a link to the project or case study.</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <div class="container">
            <h2>Contact</h2>
            <form id="contact-form" onsubmit="return handleFormSubmit(event)">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>

                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>

                <label for="subject">Subject:</label>
                <input type="text" id="subject" name="subject" required>

                <label for="message">Message:</label>
                <textarea id="message" name="message" rows="4" required></textarea>

                <button type="submit" class="cta-button">Send Message</button>
            </form>
            <p>Email: alamgirctr@gmail.com</p>
            <p>LinkedIn: <a href="https://www.linkedin.com/in/alamgir-khan-24175213b/?utm_source=share&utm_campaign=share_via&utm_content=profile&utm_medium=ios_app">linkedin.com</a></p>
        </div>
    </section>

    <footer>
        <div class="container">
            <p>&copy; 2024 Alamgir Khan. All rights reserved.</p>
        </div>
    </footer>

    <script>
        async function handleFormSubmit(event) {
            event.preventDefault(); // Prevent default form submission
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const subject = document.getElementById('subject').value;
            const message = document.getElementById('message').value;

            const requestBody = {
                sender: { email: "alamgirctr@gmail.com" }, // Your sender email
                to: [{ email: "alamgirctr@gmail.com" }], // Recipient's email
                subject: subject,
                htmlContent: `<p><strong>Name:</strong> ${name}</p>
                              <p><strong>Email:</strong> ${email}</p>
                              <p><strong>Message:</strong> ${message}</p>`
            };

            try {
                const response = await fetch("https://api.brevo.com/v3/smtp/email", {
                    method: "POST",
                    headers: {
                        "Content-Type": "application/json",
                        "api-key": "xkeysib-1795ebe5163a45ee4d2c0bbb8212c29b955e7be5d1962f97d4d1ffd5b276ddc8" // Your Brevo API key
                    },
                    body: JSON.stringify(requestBody),
                });

                const responseText = await response.text(); // Capture the raw response text

                if (response.ok) {
                    alert("Message sent successfully!");
                    document.getElementById('contact-form').reset();
                } else {
                    console.error("Failed to send message:", responseText);
                    alert(`Failed to send the message: ${responseText}`);
                }
            } catch (error) {
                console.error("Error:", error);
                alert("There was an error sending your message.");
            }
        }
    </script>
</body>
</html>
