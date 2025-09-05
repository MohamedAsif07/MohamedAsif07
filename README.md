<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mohamed Asif - Animated Interactive Profile</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Courier New', monospace;
            background: linear-gradient(135deg, #0a0a0a, #1a1a1a, #0f0f23, #1a1a1a);
            background-size: 400% 400%;
            color: #00d4ff;
            margin: 0;
            padding: 20px;
            min-height: 100vh;
            animation: gradientShift 8s ease infinite;
            position: relative;
            overflow-x: hidden;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .stars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .star {
            position: absolute;
            width: 2px;
            height: 2px;
            background: #00d4ff;
            border-radius: 50%;
            animation: twinkle 3s infinite;
        }

        @keyframes twinkle {
            0%, 100% { opacity: 0; transform: scale(0.5); }
            50% { opacity: 1; transform: scale(1.2); }
        }

        .floating-particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .particle {
            position: absolute;
            width: 4px;
            height: 4px;
            background: rgba(0, 212, 255, 0.6);
            border-radius: 50%;
            animation: float 20s infinite linear;
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 1;
            }
            90% {
                opacity: 1;
            }
            100% {
                transform: translateY(-100vh) rotate(360deg);
                opacity: 0;
            }
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(0, 0, 0, 0.9);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 0 50px rgba(0, 212, 255, 0.4);
            border: 2px solid rgba(0, 212, 255, 0.3);
            position: relative;
            backdrop-filter: blur(10px);
            animation: containerPulse 4s ease-in-out infinite;
        }

        @keyframes containerPulse {
            0%, 100% { box-shadow: 0 0 50px rgba(0, 212, 255, 0.4); }
            50% { box-shadow: 0 0 80px rgba(0, 212, 255, 0.6); }
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            position: relative;
        }

        .header h1 {
            font-size: 3em;
            margin: 0;
            background: linear-gradient(45deg, #00d4ff, #ff6b35, #00ff9f, #ff3366);
            background-size: 300% 300%;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            animation: rainbowText 3s ease-in-out infinite, bounce 2s ease-in-out infinite;
        }

        @keyframes rainbowText {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .typewriter {
            font-size: 1.2em;
            margin: 20px 0;
            min-height: 30px;
            border-right: 2px solid #00d4ff;
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 50% { border-right-color: transparent; }
            51%, 100% { border-right-color: #00d4ff; }
        }

        .console {
            background: linear-gradient(135deg, #000, #111);
            border: 3px solid #00d4ff;
            border-radius: 15px;
            padding: 25px;
            margin: 30px 0;
            font-family: 'Courier New', monospace;
            overflow-x: auto;
            position: relative;
            animation: consoleGlow 3s ease-in-out infinite;
        }

        @keyframes consoleGlow {
            0%, 100% { 
                border-color: #00d4ff;
                box-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
            }
            50% { 
                border-color: #ff6b35;
                box-shadow: 0 0 30px rgba(255, 107, 53, 0.7);
            }
        }

        .console::before {
            content: "●●●";
            position: absolute;
            top: 10px;
            right: 15px;
            color: #ff6b35;
            animation: consoleLights 2s ease-in-out infinite;
        }

        @keyframes consoleLights {
            0%, 100% { color: #ff6b35; }
            50% { color: #00ff9f; }
        }

        .output {
            color: #00ff00;
            white-space: pre-wrap;
            line-height: 1.6;
            animation: textGlow 2s ease-in-out infinite alternate;
        }

        @keyframes textGlow {
            from { text-shadow: 0 0 5px #00ff00; }
            to { text-shadow: 0 0 15px #00ff00, 0 0 25px #00ff00; }
        }

        .button {
            background: linear-gradient(45deg, #00d4ff, #0099cc, #ff6b35, #ff3366);
            background-size: 300% 300%;
            border: none;
            border-radius: 12px;
            color: white;
            padding: 15px 30px;
            margin: 12px;
            cursor: pointer;
            font-size: 16px;
            font-weight: bold;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 6px 20px rgba(0, 212, 255, 0.4);
            position: relative;
            overflow: hidden;
            animation: buttonShimmer 3s ease infinite;
        }

        @keyframes buttonShimmer {
            0%, 100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }

        .button::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
            transition: left 0.5s;
        }

        .button:hover {
            transform: translateY(-5px) scale(1.05);
            box-shadow: 0 10px 30px rgba(0, 212, 255, 0.7);
            animation-play-state: paused;
        }

        .button:hover::before {
            left: 100%;
        }

        .button:active {
            transform: translateY(-2px) scale(1.02);
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 25px;
            margin: 30px 0;
        }

        .card {
            background: linear-gradient(135deg, rgba(0, 212, 255, 0.1), rgba(255, 107, 53, 0.1));
            border: 2px solid transparent;
            background-clip: padding-box;
            border-radius: 15px;
            padding: 25px;
            transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(45deg, #00d4ff, #ff6b35, #00ff9f, #ff3366);
            margin: -2px;
            border-radius: inherit;
            z-index: -1;
            animation: borderRotate 4s linear infinite;
        }

        @keyframes borderRotate {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        .card:hover {
            transform: translateY(-10px) rotateX(5deg);
            box-shadow: 0 15px 40px rgba(0, 212, 255, 0.5);
        }

        .card h3 {
            margin-top: 0;
            color: #00d4ff;
            font-size: 1.4em;
            animation: titlePulse 2s ease-in-out infinite;
        }

        @keyframes titlePulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.02); }
        }

        .tech-tag {
            display: inline-block;
            background: linear-gradient(45deg, rgba(0, 212, 255, 0.3), rgba(255, 107, 53, 0.3));
            color: #00d4ff;
            padding: 6px 12px;
            margin: 3px;
            border-radius: 20px;
            font-size: 12px;
            border: 1px solid rgba(0, 212, 255, 0.5);
            transition: all 0.3s ease;
            animation: tagFloat 3s ease-in-out infinite;
        }

        .tech-tag:hover {
            background: linear-gradient(45deg, rgba(0, 212, 255, 0.6), rgba(255, 107, 53, 0.6));
            transform: scale(1.1);
            box-shadow: 0 5px 15px rgba(0, 212, 255, 0.4);
        }

        @keyframes tagFloat {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-2px); }
        }

        .loading-bar {
            width: 100%;
            height: 4px;
            background: rgba(0, 212, 255, 0.2);
            border-radius: 2px;
            overflow: hidden;
            margin: 20px 0;
        }

        .loading-progress {
            height: 100%;
            background: linear-gradient(90deg, #00d4ff, #ff6b35, #00ff9f);
            background-size: 200% 100%;
            animation: loadingAnimation 2s ease-in-out infinite;
            width: 0%;
            transition: width 0.5s ease;
        }

        @keyframes loadingAnimation {
            0%, 100% { background-position: 0% 0%; }
            50% { background-position: 100% 0%; }
        }

        .matrix-rain {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -2;
            opacity: 0.1;
        }

        .status-indicator {
            display: inline-block;
            width: 12px;
            height: 12px;
            background: #00ff00;
            border-radius: 50%;
            animation: statusBlink 1.5s ease-in-out infinite;
            margin-right: 8px;
        }

        @keyframes statusBlink {
            0%, 100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.3; transform: scale(0.8); }
        }

        .hologram {
            animation: hologramEffect 3s ease-in-out infinite;
        }

        @keyframes hologramEffect {
            0%, 100% { 
                text-shadow: 0 0 5px #00d4ff; 
                opacity: 1;
            }
            50% { 
                text-shadow: 0 0 20px #00d4ff, 0 0 30px #00d4ff; 
                opacity: 0.8;
            }
        }

        .cyber-grid {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: 
                linear-gradient(rgba(0, 212, 255, 0.05) 1px, transparent 1px),
                linear-gradient(90deg, rgba(0, 212, 255, 0.05) 1px, transparent 1px);
            background-size: 50px 50px;
            pointer-events: none;
            z-index: -3;
            animation: gridMove 20s linear infinite;
        }

        @keyframes gridMove {
            0% { transform: translate(0, 0); }
            100% { transform: translate(50px, 50px); }
        }

        @media (max-width: 768px) {
            .container { padding: 20px; }
            .header h1 { font-size: 2em; }
            .grid { grid-template-columns: 1fr; }
            .button { padding: 12px 20px; margin: 8px; }
        }
    </style>
</head>
<body>
    <div class="cyber-grid"></div>
    <div class="stars" id="stars"></div>
    <div class="floating-particles" id="particles"></div>
    <canvas class="matrix-rain" id="matrixCanvas"></canvas>

    <div class="container">
        <div class="header">
            <h1 class="hologram">🚀 Mohamed Asif 🛡️</h1>
            <div class="typewriter" id="typewriter"></div>
            <div class="loading-bar">
                <div class="loading-progress" id="loadingProgress"></div>
            </div>
        </div>

        <div style="text-align: center;">
            <button class="button" onclick="initializeProfile()">🌟 Initialize Profile</button>
            <button class="button" onclick="showCurrentStatus()">📊 Current Status</button>
            <button class="button" onclick="showContactInfo()">📞 Contact Portal</button>
            <button class="button" onclick="showTechnologies()">💻 Tech Arsenal</button>
            <button class="button" onclick="showLearning()">📚 Learning Path</button>
            <button class="button" onclick="showFunFacts()">🎭 Personality</button>
            <button class="button" onclick="hackTheMatrix()">🔮 Hack Matrix</button>
        </div>

        <div class="console" id="console">
            <div class="output" id="output">
                <span class="status-indicator"></span>System initializing... Welcome to the digital universe!
            </div>
        </div>

        <div id="dynamicContent"></div>
    </div>

    <script>
        class MohamedAsif {
            constructor() {
                this.profile = {
                    name: "Mohamed Asif",
                    role: "🚀 Android Developer & 🛡️ Cybersecurity Enthusiast",
                    location: "🌍 Earth • 🏙️ Digital Realm",
                    pronouns: ["He", "Him"],
                    status: "💫 Building the future, one app at a time"
                };
                
                this.currentMission = [
                    "🔐 Crafting Secure Android Applications",
                    "🛡️ Developing Advanced Cybersecurity Tools", 
                    "🌟 Contributing to Open Source Revolution",
                    "🎯 Mentoring Next-Gen Developers"
                ];
                
                this.codeArsenal = {
                    mobile: {
                        "📱 Native Android": ["☕ Java", "🟣 Kotlin", "🎨 XML", "🚀 Jetpack Compose"],
                        "🦋 Cross-Platform": ["🎯 Dart", "💙 Flutter", "📐 Material Design"]
                    },
                    
                    backend: {
                        "⚡ Languages": ["🐍 Python", "☕ Java", "⚙️ C/C++"],
                        "🏗️ Frameworks": ["🌿 Spring Boot", "🔥 Django", "⚡ FastAPI", "🌪️ Flask"],
                        "📦 Build Tools": ["🐘 Gradle", "📋 Maven", "🔧 CMake"]
                    },
                    
                    cloudNative: {
                        "☁️ Platforms": ["🔶 AWS", "🔵 Google Cloud", "🟦 Azure"],
                        "🐳 Containerization": ["🐋 Docker", "☸️ Kubernetes", "🔄 Docker Compose"],
                        "🚀 CI/CD": ["🏗️ Jenkins", "⚙️ GitHub Actions", "🔄 GitLab CI"]
                    },
                    
                    cybersecurity: {
                        "🛡️ Offensive": ["🐉 Kali Linux", "💥 Metasploit", "🔍 Nmap", "🦈 Wireshark"],
                        "🔒 Defensive": ["🛡️ OWASP", "🔐 Burp Suite", "🕵️ Penetration Testing"],
                        "🎯 Specialization": ["📱 Mobile Security", "🌐 Web App Security", "🔗 API Security"]
                    }
                };
                
                this.currentlyLearning = [
                    "🤖 Advanced Android Architecture (MVVM, Clean Architecture)",
                    "🔥 Firebase ML Kit & Advanced Features",
                    "🛠️ Custom Kali Linux Tools Development",
                    "☁️ Cloud-Native Security & Zero Trust Architecture",
                    "🧠 Machine Learning for Cybersecurity",
                    "🌐 Web3 & Blockchain Security"
                ];
                
                this.personalityCore = [
                    "🕵️ I debug with the precision of Sherlock Holmes",
                    "🎯 I hunt vulnerabilities like a digital bounty hunter",
                    "☕ Coffee is the fuel that powers my midnight coding sessions",
                    "🌙 My best code emerges when the world sleeps",
                    "🚀 I believe secure code isn't just good practice—it's art",
                    "💡 Every bug is a puzzle waiting to be solved"
                ];
                
                this.motto = "💫 Code with purpose, secure with passion, innovate with impact!";
                this.hackMessages = [
                    "🔮 Accessing mainframe...",
                    "🛡️ Bypassing security protocols...",
                    "💾 Downloading universe.exe...",
                    "🌐 Connecting to the Matrix...",
                    "⚡ Overclocking reality.dll...",
                    "🎯 Reality hacked successfully!"
                ];
            }
            
            getCurrentStatus() {
                return {
                    "🚀": "Building next-generation secure mobile applications",
                    "🛡️": "Researching advanced cybersecurity methodologies", 
                    "💼": "Open for exciting collaboration opportunities",
                    "📚": "Always learning, always evolving",
                    "🎯": "Focused on making the digital world safer"
                };
            }
            
            getContactPortal() {
                return {
                    "📧 Email": "mohamedasifappdev@gmail.com",
                    "🐙 GitHub": "@mohamedasif07",
                    "🌐 Portfolio": "🚧 Crafting something extraordinary...",
                    "⏰ Timezone": "UTC+5:30 (IST)",
                    "💬 Status": "Always ready to discuss innovative projects!"
                };
            }
            
            executeWelcomeSequence() {
                return `🌟 ================================ 🌟
   Welcome to Mohamed Asif's Digital Universe!
🌟 ================================ 🌟

✨ Let's build something extraordinary together! ✨`;
            }
        }

        // Initialize the profile
        const mohamed = new MohamedAsif();
        let typewriterIndex = 0;
        let currentText = "";
        let isDeleting = false;

        const typewriterTexts = [
            "Interactive Developer Profile Loading...",
            "Android Developer & Cybersecurity Expert",
            "Building Secure Digital Solutions",
            "Innovating the Future of Mobile Security"
        ];

        function typeWriter() {
            const fullText = typewriterTexts[typewriterIndex];
            
            if (isDeleting) {
                currentText = fullText.substring(0, currentText.length - 1);
            } else {
                currentText = fullText.substring(0, currentText.length + 1);
            }
            
            document.getElementById('typewriter').textContent = currentText;
            
            let typeSpeed = 100;
            
            if (isDeleting) {
                typeSpeed = 50;
            }
            
            if (!isDeleting && currentText === fullText) {
                typeSpeed = 2000;
                isDeleting = true;
            } else if (isDeleting && currentText === '') {
                isDeleting = false;
                typewriterIndex = (typewriterIndex + 1) % typewriterTexts.length;
                typeSpeed = 500;
            }
            
            setTimeout(typeWriter, typeSpeed);
        }

        function updateOutput(content) {
            document.getElementById('output').innerHTML = `<span class="status-indicator"></span>${content}`;
        }

        function updateDynamicContent(content) {
            document.getElementById('dynamicContent').innerHTML = content;
        }

        function animateLoadingBar(targetWidth) {
            const loadingProgress = document.getElementById('loadingProgress');
            let width = 0;
            const interval = setInterval(() => {
                if (width >= targetWidth) {
                    clearInterval(interval);
                } else {
                    width++;
                    loadingProgress.style.width = width + '%';
                }
            }, 20);
        }

        function initializeProfile() {
            animateLoadingBar(100);
            updateOutput(mohamed.executeWelcomeSequence());
            updateDynamicContent(`
                <div class="card">
                    <h3>👨‍💻 Profile Overview</h3>
                    <p><strong>Name:</strong> ${mohamed.profile.name}</p>
                    <p><strong>Role:</strong> ${mohamed.profile.role}</p>
                    <p><strong>Location:</strong> ${mohamed.profile.location}</p>
                    <p><strong>Motto:</strong> ${mohamed.motto}</p>
                </div>
            `);
        }

        function showCurrentStatus() {
            const status = mohamed.getCurrentStatus();
            let output = "📊 CURRENT STATUS REPORT:\n\n";
            for (const [emoji, description] of Object.entries(status)) {
                output += `${emoji} ${description}\n\n`;
            }
            updateOutput(output);
            animateLoadingBar(75);
        }

        function showContactInfo() {
            const contact = mohamed.getContactPortal();
            let output = "📞 CONTACT INFORMATION:\n\n";
            for (const [platform, info] of Object.entries(contact)) {
                output += `${platform}: ${info}\n\n`;
            }
            updateOutput(output);
            animateLoadingBar(60);
        }

        function showTechnologies() {
            let content = '<div class="grid">';
            
            for (const [category, technologies] of Object.entries(mohamed.codeArsenal)) {
                content += `<div class="card">`;
                content += `<h3>${category.charAt(0).toUpperCase() + category.slice(1)}</h3>`;
                
                for (const [subcategory, techs] of Object.entries(technologies)) {
                    content += `<p><strong>${subcategory}:</strong><br>`;
                    techs.forEach(tech => {
                        content += `<span class="tech-tag">${tech}</span>`;
                    });
                    content += `</p>`;
                }
                content += `</div>`;
            }
            content += '</div>';
            
            updateDynamicContent(content);
            updateOutput("💻 Tech Arsenal loaded! Check the animated cards below.");
            animateLoadingBar(90);
        }

        function showLearning() {
            let output = "📚 CURRENT LEARNING PATH:\n\n";
            mohamed.currentlyLearning.forEach((item, index) => {
                output += `${index + 1}. ${item}\n\n`;
            });
            updateOutput(output);
            animateLoadingBar(65);
        }

        function showFunFacts() {
            let output = "🎭 PERSONALITY CORE TRAITS:\n\n";
            mohamed.personalityCore.forEach((fact, index) => {
                output += `${index + 1}. ${fact}\n\n`;
            });
            updateOutput(output);
            animateLoadingBar(80);
        }

        function hackTheMatrix() {
            let messageIndex = 0;
            const hackInterval = setInterval(() => {
                if (messageIndex < mohamed.hackMessages.length) {
                    updateOutput(mohamed.hackMessages[messageIndex]);
                    messageIndex++;
                } else {
                    clearInterval(hackInterval);
                    createMatrixEffect();
                }
            }, 1000);
            animateLoadingBar(100);
        }

        function createMatrixEffect() {
            const canvas = document.getElementById('matrixCanvas');
            const ctx = canvas.getContext('2d');
            
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            
            const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789@#$%^&*()';
            const columns = Math.floor(canvas.width / 20);
            const drops = [];
            
            for (let i = 0; i < columns; i++) {
                drops[i] = 1;
            }
            
            function drawMatrix() {
                ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
                ctx.fillRect(0, 0, canvas.width, canvas.height);
                
                ctx.fillStyle = '#00d4ff';
                ctx.font = '16px monospace';
                
                for (let i = 0; i < drops.length; i++) {
                    const char = characters[Math.floor(Math.random() * characters.length)];
                    ctx.fillText(char, i * 20, drops[i] * 20);
                    
                    if (drops[i] * 20 > canvas.height && Math.random() > 0.975) {
                        drops[i] = 0;
                    }
                    drops[i]++;
                }
            }
            
            const matrixInterval = setInterval(drawMatrix, 100);
            
            setTimeout(() => {
                clearInterval(matrixInterval);
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                updateOutput("🎯 Matrix successfully hacked! Reality.exe has been modified.");
            }, 5000);
        }

        function createStars() {
            const starsContainer = document.getElementById('stars');
            for (let i = 0; i < 100; i++) {
                const star = document.createElement('div');
                star.className = 'star';
                star.style.left = Math.random() * 100 + '%';
                star.style.top = Math.random() * 100 + '%';
                star.style.animationDelay = Math.random() * 3 + 's';
                starsContainer.appendChild(star);
            }
        }

        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            for (let i = 0; i < 50; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.animationDelay = Math.random() * 20 + 's';
                particle.style.animationDuration = (Math.random() * 10 + 15) + 's';
                particlesContainer.appendChild(particle);
            }
        }

        // Initialize everything
        document.addEventListener('DOMContentLoaded', () => {
            createStars();
            createParticles();
            typeWriter();
            
            setTimeout(() => {
                initializeProfile();
            }, 2000);
        });

        // Resize canvas when window resizes
        window.addEventListener('resize', () => {
            const canvas = document.getElementById('matrixCanvas');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
    </script>
</body>
</html>
