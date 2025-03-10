<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Harshith's Portfolio</title>
    <style>
        /* General Styles */
        body {
            font-family: Arial, sans-serif;
            background: #ffffff;
            color: #1E3A8A;
            margin: 0;
            padding: 0;
            overflow-x: hidden;
            scroll-behavior: smooth;
        }

        /* Navigation Bar */
        nav {
            position: fixed;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 60%;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            display: flex;
            justify-content: space-around;
            padding: 15px 20px;
            border-radius: 50px;
            z-index: 1000;
        }
        
        nav ul {
            list-style: none;
            display: flex;
            gap: 20px;
        }

        nav ul li {
            cursor: pointer;
            font-size: 18px;
            font-weight: bold;
            transition: color 0.3s;
        }

        nav ul li:hover {
            color: #2563EB;
        }

        /* Sections */
        section {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 80px;
            position: relative;
        }

        /* Home Section */
        #home {
            display: flex;
            align-items: center;
            gap: 50px;
        }

        .text-content {
            max-width: 50%;
            font-weight: 500;
        }

        .image-container img {
            width: 699px;
            animation: wave 3s infinite ease-in-out;
        }

        @keyframes wave {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(5px); }
        }

        /* About Section */
        #about {
            background: #f0faff;
            flex-direction: column;
        }

        .about-container {
            display: flex;
            width: 80%;
            height: 60vh;
            background: rgba(240, 248, 255, 0.8);
            border-radius: 20px;
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
            overflow: hidden;
            position: relative;
        }

        .left-panel {
            display: flex;
            flex-direction: column;
            width: 30%;
            padding: 20px;
            gap: 15px;
            background: linear-gradient(135deg, #dbeafe, #bfdbfe);
            border-top-left-radius: 20px;
            border-bottom-left-radius: 20px;
        }

        .left-panel button {
            background: rgba(173, 216, 230, 0.4);
            border: none;
            padding: 15px;
            font-size: 16px;
            cursor: pointer;
            border-radius: 10px;
            transition: all 0.3s ease-in-out;
            color: #1E3A8A;
            font-weight: bold;
            outline: none;
        }

        .left-panel button:hover {
            background: rgba(100, 149, 237, 0.7);
            transform: scale(1.05);
            color: white;
        }

        .right-panel {
            flex-grow: 1;
            padding: 30px;
            font-size: 18px;
            color: #1E3A8A;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: 500;
            text-align: center;
            position: relative;
        }

        .typing-text {
            font-size: 18px;
            font-weight: bold;
            min-height: 50px;
        }

        /* Floating Circles */
        .circle {
            position: absolute;
            width: 120px;
            height: 120px;
            background: rgba(173, 216, 230, 0.5);
            border-radius: 50%;
            animation: float 6s infinite alternate ease-in-out;
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: -1;
        }

        .circle.one { top: 10%; left: 15%; animation-delay: 1s; }
        .circle.two { bottom: 5%; left: 40%; animation-delay: 2s; }
        .circle.three { top: 15%; right: 10%; animation-delay: 3s; }

        @keyframes float {
            0% { transform: translateY(0px); }
            100% { transform: translateY(20px); }
        }

    </style>
</head>
<body>

    <!-- Navigation Bar -->
    <nav>
        <h1>Harshith</h1>
        <ul>
            <li onclick="scrollToSection('home')">Home</li>
            <li onclick="scrollToSection('about')">About</li>
            <li><onclick="scrollToSection('projects')">Projects</li>
<li><onclick="scrollToSection('contact')">Contact</a></li>

<script>
function scrollToSection(sectionId) {
    const section = document.getElementById(sectionId);
    if (section) {
        section.scrollIntoView({ behavior: "smooth" });
    } else {
        // Redirect if the section is not on the current page
        window.location.href = sectionId + ".html";
    }
}
</script>

        </ul>
    </nav>

    <!-- Home Section -->
    <section id="home">
        <div class="text-content">
            <h2>Hey there, I'm Harshith! 👋✨</h2>
            <p><strong>🚀 Web Alchemist | 🔗 Blockchain Aficionado</strong></p>
            <p>I blend <strong>pixels & logic</strong> to craft immersive web experiences, infuse <strong>blockchain magic</strong> into digital realms. Always experimenting, always evolving—because the future is built by those who dare to create!</p>
            <p style="color: #2563EB; font-weight: bold;">🔄 Hover, click, or scroll—you might just discover something unexpected! 😁</p>
        </div>
        <div class="image-container">
            <img src="devmale.jpg" alt="Web Developer Illustration">
        </div>
        <div class="circle one"></div>
        <div class="circle two"></div>
    </section>

    <!-- About Section -->
    <section id="about">
        <h1>About Me</h1>
        <div class="about-container">
            <div class="left-panel">
                <button onclick="showContent('education')">Education</button>
                <button onclick="showContent('experience')">Experience</button>
                <button onclick="showContent('achievements')">Achievements</button>
            </div>
            <div class="right-panel">
                <div class="typing-text" id="text-box">Click on any option to view details!</div>
            </div>
        </div>
    </section>

    <script>
        let currentType = "";
        let typingInterval;

        function showContent(type) {
            if (currentType === type) return;
            currentType = type;

            let content = "";
            if (type === "education") {
                content = "🎓 I earned my B.Tech in Electrical and Electronics Engineering (EEE) from Amrita Vishwa Vidyapeetham, Coimbatore, in July 2024, graduating with distinction and a CGPA of 7.65. My research project on blockchain-enabled peer-to-peer transactions in smart grids is currently under IEEE review for publication. I pursued my higher secondary education at Narayana Institutes, Tirupati, excelling in MPC with an impressive 95% in my board exams.";
            } else if (type === "experience") {
                content = "💼 I am currently working as a Graduate Engineer Trainee at IFB Industries in the Home Appliance division, where I am developing leadership skills and honing my ability to diagnose and resolve technical issues. My role has taken me to various parts of India, providing firsthand exposure to on-ground challenges and customer expectations. Additionally, I have developed a website that enables customers to conveniently book service complaints, enhancing their overall experience and streamlining the process.";
            } else if (type === "achievements") {
                content = "🏆 I have actively participated in several hackathons, including ETH India 2023, Unfold by CoinDCX, W3 Tech Summit, and ETH For All, where I gained valuable skills in blockchain and web development. Additionally, I have completed multiple certifications in blockchain (KBA) and frontend development, further strengthening my technical expertise.";
            }

            let textBox = document.getElementById("text-box");
            clearTimeout(typingInterval);
            textBox.innerHTML = "";
            let i = 0;

            function typeEffect() {
                if (i < content.length) {
                    textBox.innerHTML += content.charAt(i);
                    i++;
                    typingInterval = setTimeout(typeEffect, 30);
                }
            }

            typeEffect();
        }
    </script>
    </script>

</body>
</html>
<section id="projects">
    <h1>Projects</h1>
    <div class="projects-container">
        
        <div class="project-card" onmouseover="expandProject(this)" onmouseout="shrinkProject(this)">
            <div class="project-overlay"></div>
            <h2>Blockchain P2P Transactions</h2>
            <p>🔗 A decentralized platform for peer-to-peer energy transactions using blockchain technology.</p>
            <div class="tech-stack">
                <span>Ethereum</span>
                <span>Smart Contracts</span>
                <span>Rust</span>
            </div>
        </div>
        
        <div class="project-card" onmouseover="expandProject(this)" onmouseout="shrinkProject(this)">
            <div class="project-overlay"></div>
            <h2>Tech Fest Registration</h2>
            <p>📌 Built an interactive and secure online registration system for Anokha Tech Fest.</p>
            <div class="tech-stack">
                <span>Html5</span>
                <span>CSS</span>
                <span>Java Script</span>
            </div>
        </div>
        
        <div class="project-card" onmouseover="expandProject(this)" onmouseout="shrinkProject(this)">
            <div class="project-overlay"></div>
            <h2>complaint booking Webpage</h2>
            <p>🌐 Designed a complaint booking web page to enchance the cutomer service experience.</p>
            <div class="tech-stack">
                <span>HTML</span>
                <span>CSS</span>
                <span>JavaScript</span>
            </div>
        </div>
        
    </div>
</section>

<!-- Contact Me Section -->
<section id="contact">
    <h1>Contact Me</h1>
    <div class="contact-container">
        <div class="contact-left">
            <img src="contact me.gif" alt="Contact Image" class="contact-image">
        </div>
        <div class="contact-right">
            <div class="contact-box">
                <input type="text" placeholder="Your Name" required>
                <input type="email" placeholder="Your Email" required>
            </div>
            <div class="contact-box">
                <input type="text" placeholder="Purpose" required>
            </div>
            <div class="contact-box">
                <textarea placeholder="Description" rows="5" required></textarea>
            </div>
            <button type="submit">Send Message</button>
        </div>
    </div>
</section>


<style>
    #projects {
        background: #f0faff;
        text-align: center;
        padding: 80px;
    }
    
    .projects-container {
        display: flex;
        justify-content: center;
        gap: 50px;
        flex-wrap: wrap;
        margin-top: 40px;
    }
    
    .project-card {
        width: 300px;
        height: 250px;
        background: white;
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        border-radius: 20px;
        padding: 20px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: relative;
        cursor: pointer;
        transition: all 0.3s ease-in-out;
        overflow: hidden;
    }
    
    .project-card:hover {
        transform: scale(1.1);
    }
    
    .project-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(30, 58, 138, 0.1);
        border-radius: 20px;
        transition: opacity 0.3s ease-in-out;
    }
    
    .project-card:hover .project-overlay {
        background: rgba(30, 58, 138, 0.2);
    }
    
    .tech-stack {
        display: flex;
        gap: 10px;
        margin-top: 10px;
        opacity: 0;
        transition: opacity 0.3s ease-in-out;
    }
    
    .project-card:hover .tech-stack {
        opacity: 1;
    }
    
    #contact {
        background: #f0faff;
        text-align: center;
        padding: 60px;
    }
    
    .contact-container {
        display: flex;
        align-items: center;
        justify-content: space-between;
        max-width: 1000px;
        margin: 0 auto;
        gap: 40px;
    }
    
    .contact-left {
        flex: 40%;
        display: flex;
        justify-content: center;
    }
    
    .contact-left img.contact-image {
        width: 100%;
        max-width: 600px;
        border-radius: 10px;
        object-fit: cover;
        border: 3px solid #3b82f6;
    }
    
    .contact-right {
        flex: 60%;
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .contact-box {
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    input, textarea {
        width: 100%;
        padding: 10px;
        border: 2px solid #3b82f6;
        border-radius: 8px;
        font-size: 16px;
    }

    button {
        background: #3b82f6;
        color: white;
        padding: 12px 24px;
        border: none;
        border-radius: 8px;
        cursor: pointer;
        font-size: 18px;
        transition: 0.3s;
    }

    button:hover {
        background: #2563eb;
    }
</style>

<script>
    function expandProject(element) {
        element.style.transform = "scale(1.1)";
    }

    function shrinkProject(element) {
        element.style.transform = "scale(1)";
    }
</script>
<!-- Add Google Font -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

<style>
    /* Apply the new font to headings */
    h1, h2 {
        color: #2563eb; /* Blue color */
        font-family: 'Poppins', sans-serif;
        font-weight: 600; /* Medium-bold for better visibility */
    }

    #projects {
        background: #f0faff;
        text-align: center;
        padding: 80px;
    }
    
    .projects-container {
        display: flex;
        justify-content: center;
        gap: 50px;
        flex-wrap: wrap;
        margin-top: 40px;
    }
    
    .project-card {
        width: 300px;
        height: 250px;
        background: white;
        box-shadow: 0 10px 20px rgba(0, 0, 0, 0.1);
        border-radius: 20px;
        padding: 20px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        position: relative;
        cursor: pointer;
        transition: all 0.3s ease-in-out;
        overflow: hidden;
    }
    
    .project-card:hover {
        transform: scale(1.1);
    }
    
    .project-overlay {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(30, 58, 138, 0.1);
        border-radius: 20px;
        transition: opacity 0.3s ease-in-out;
    }
    
    .project-card:hover .project-overlay {
        background: rgba(30, 58, 138, 0.2);
    }
    
    .tech-stack {
        display: flex;
        gap: 10px;
        margin-top: 10px;
        opacity: 0;
        transition: opacity 0.3s ease-in-out;
    }
    
    .project-card:hover .tech-stack {
        opacity: 1;
    }
    
    #contact {
        background: #f0faff;
        text-align: center;
        padding: 60px;
    }
    
    .contact-container {
        display: flex;
        align-items: center;
        justify-content: space-between;
        max-width: 1000px;
        margin: 0 auto;
        gap: 40px;
    }
    
    .contact-left {
        flex: 40%;
        display: flex;
        justify-content: center;
    }
    
    .contact-left img.contact-image {
        width: 100%;
        max-width: 600px;
        border-radius: 10px;
        object-fit: cover;
        border: 3px solid #3b82f6;
    }
    
    .contact-right {
        flex: 60%;
        display: flex;
        flex-direction: column;
        gap: 20px;
    }

    .contact-box {
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    input, textarea {
        width: 100%;
        padding: 10px;
        border: 2px solid #3b82f6;
        border-radius: 8px;
        font-size: 16px;
        font-family: 'Poppins', sans-serif;
    }

    button {
        background: #3b82f6;
        color: white;
        padding: 12px 24px;
        border: none;
        border-radius: 8px;
        cursor: pointer;
        font-size: 18px;
        transition: 0.3s;
        font-family: 'Poppins', sans-serif;
    }

    button:hover {
        background: #2563eb;
    }

    #projects {
    background: #f0faff;
    text-align: center;
    padding: 80px;
    position: relative;
}

#projects h1 {
    position: absolute;
    top: 20px; /* Adjust as needed */
    left: 50%;
    transform: translateX(-50%);
    color: #2563eb;
    font-family: 'Poppins', sans-serif;
    font-weight: 600;
    font-size: 32px;
    margin: 0;
}

.projects-container {
    display: flex;
    justify-content: center;
    gap: 50px;
    flex-wrap: wrap;
    margin-top: 80px; /* Ensure space below the heading */
}

#contact {
    background: #f0faff;
    text-align: center;
    padding: 60px;
    position: relative;
}

#contact h1 {
    position: absolute;
    top: 20px; /* Keeps the heading at the top */
    left: 50%;
    transform: translateX(-50%);
    color: #2563eb;
    font-family: 'Poppins', sans-serif;
    font-weight: 600;
    font-size: 32px;
    margin: 0;
    margin-bottom: 20px; /* Adjust as needed */
    font-size: 2rem; /* Adjust heading size */
    font-weight: bold;

}

.contact-container {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 1000px;
    margin: 40px auto 0; /* Reduced gap between heading and container */
    gap: 40px;
    

        padding-top: 20px; /* Reduce padding to decrease gap */
}





</style>
