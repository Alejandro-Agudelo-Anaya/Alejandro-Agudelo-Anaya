<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Alejandro Agudelo Anaya | Backend, AI & Cloud Developer</title>
    <!-- FontAwesome para iconos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2 family=Fira+Code:wght@400;600&family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    
    <style>
        :root {
            --bg-color: #0b0f19;
            --card-bg: rgba(22, 31, 49, 0.7);
            --accent-green: #00ffcc;
            --accent-blue: #00b8ff;
            --accent-purple: #7000ff;
            --text-main: #e2e8f0;
            --text-muted: #94a3b8;
            --border-color: rgba(255, 255, 255, 0.1);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
            scroll-behavior: smooth;
        }

        body {
            background-color: var(--bg-color);
            color: var(--text-main);
            overflow-x: hidden;
            position: relative;
        }

        /* Background Animated Canvas */
        #particles-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            pointer-events: none;
        }

        /* Container & Glassmorphism */
        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 2rem;
        }

        .glass-card {
            background: var(--card-bg);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid var(--border-color);
            border-radius: 16px;
            padding: 2rem;
            margin-bottom: 2rem;
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.37);
            transition: transform 0.3s ease, border-color 0.3s ease, box-shadow 0.3s ease;
        }

        .glass-card:hover {
            transform: translateY(-5px);
            border-color: var(--accent-green);
            box-shadow: 0 12px 40px 0 rgba(0, 255, 204, 0.15);
        }

        /* Header / Profile Section */
        header {
            display: flex;
            flex-wrap: wrap;
            align-items: center;
            justify-content: space-between;
            gap: 2rem;
            margin-top: 1rem;
        }

        .profile-info {
            flex: 1;
            min-width: 300px;
        }

        .profile-info h1 {
            font-size: 2.8rem;
            font-weight: 700;
            background: linear-gradient(135deg, var(--accent-green), var(--accent-blue));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            margin-bottom: 0.5rem;
        }

        .profile-info h2 {
            font-size: 1.2rem;
            color: var(--text-muted);
            font-weight: 400;
            margin-bottom: 1rem;
        }

        .badge-container {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-top: 1rem;
        }

        .badge {
            background: rgba(0, 255, 204, 0.1);
            color: var(--accent-green);
            border: 1px solid rgba(0, 255, 204, 0.3);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.85rem;
            font-weight: 600;
        }

        .social-links {
            display: flex;
            gap: 1rem;
            margin-top: 1.5rem;
        }

        .social-btn {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.6rem 1.2rem;
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.05);
            color: var(--text-main);
            text-decoration: none;
            border: 1px solid var(--border-color);
            transition: all 0.3s ease;
            font-size: 0.9rem;
        }

        .social-btn:hover {
            background: var(--accent-green);
            color: var(--bg-color);
            font-weight: bold;
            transform: scale(1.05);
        }

        /* Interactive Terminal */
        .terminal {
            background-color: #050811;
            border-radius: 10px;
            border: 1px solid var(--border-color);
            font-family: 'Fira Code', monospace;
            overflow: hidden;
            margin-bottom: 2rem;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
        }

        .terminal-header {
            background: #111827;
            padding: 0.6rem 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
        }
        .dot-red { background: #ff5f56; }
        .dot-yellow { background: #ffbd2e; }
        .dot-green { background: #27c93f; }

        .terminal-title {
            color: var(--text-muted);
            font-size: 0.8rem;
            margin-left: auto;
        }

        .terminal-body {
            padding: 1.2rem;
            color: #a7f3d0;
            font-size: 0.9rem;
            min-height: 160px;
        }

        .terminal-input-line {
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-top: 0.5rem;
        }

        .prompt {
            color: var(--accent-blue);
        }

        .terminal-input {
            background: transparent;
            border: none;
            color: #fff;
            font-family: 'Fira Code', monospace;
            font-size: 0.9rem;
            outline: none;
            width: 100%;
        }

        /* Section Titles */
        .section-title {
            font-size: 1.6rem;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.8rem;
            color: var(--text-main);
            border-bottom: 2px solid var(--border-color);
            padding-bottom: 0.5rem;
        }

        .section-title i {
            color: var(--accent-green);
        }

        /* Grid Layouts */
        .grid-2 {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 1.5rem;
        }

        /* Skills Bars */
        .skill-item {
            margin-bottom: 1rem;
        }

        .skill-info {
            display: flex;
            justify-content: space-between;
            margin-bottom: 0.3rem;
            font-size: 0.9rem;
        }

        .skill-bar {
            height: 8px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            overflow: hidden;
        }

        .skill-progress {
            height: 100%;
            background: linear-gradient(90deg, var(--accent-blue), var(--accent-green));
            border-radius: 10px;
            width: 0%; /* Animated via JS */
            transition: width 1.5s ease-in-out;
        }

        /* Project Cards */
        .project-card {
            background: rgba(15, 23, 42, 0.6);
            border: 1px solid var(--border-color);
            border-radius: 12px;
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            transition: all 0.3s ease;
        }

        .project-card:hover {
            border-color: var(--accent-blue);
            transform: scale(1.02);
        }

        .project-title {
            font-size: 1.2rem;
            color: var(--accent-green);
            margin-bottom: 0.5rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .project-desc {
            font-size: 0.9rem;
            color: var(--text-muted);
            margin-bottom: 1rem;
            line-height: 1.5;
        }

        .project-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.4rem;
        }

        .tag {
            font-size: 0.75rem;
            background: rgba(112, 0, 255, 0.2);
            color: #c084fc;
            padding: 0.2rem 0.6rem;
            border-radius: 4px;
            border: 1px solid rgba(112, 0, 255, 0.4);
        }

        /* Personal Touch / Interests */
        .interests-flex {
            display: flex;
            gap: 1.5rem;
            flex-wrap: wrap;
        }

        .interest-item {
            display: flex;
            align-items: center;
            gap: 0.6rem;
            background: rgba(255, 255, 255, 0.03);
            padding: 0.6rem 1.2rem;
            border-radius: 30px;
            border: 1px solid var(--border-color);
            font-size: 0.9rem;
        }

        .interest-item i {
            color: var(--accent-blue);
        }

        footer {
            text-align: center;
            padding: 2rem;
            color: var(--text-muted);
            font-size: 0.85rem;
            border-top: 1px solid var(--border-color);
            margin-top: 2rem;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .profile-info h1 { font-size: 2.2rem; }
            .container { padding: 1rem; }
        }
    </style>
</head>
<body>

    <canvas id="particles-canvas"></canvas>

    <div class="container">
        <!-- HEADER / PROFILE SECTION -->
        <header class="glass-card">
            <div class="profile-info">
                <h1 id="name-heading">Alejandro Agudelo Anaya</h1>
                <h2>Estudiante de Ingeniería de Sistemas e Informática | Universidad Nacional de Colombia</h2>
                <p style="color: var(--text-muted); font-size: 0.95rem; line-height: 1.6;">
                    Backend Developer apasionado por la Arquitectura de Software, Inteligencia Artificial (IA Generativa & Agentes) y Cloud/DevOps. Orientado a la resolución de problemas técnicos complejos y al aprendizaje continuo.
                </p>
                
                <div class="badge-container">
                    <span class="badge"><i class="fa-solid fa-location-dot"></i> Medellín, Colombia</span>
                    <span class="badge"><i class="fa-solid fa-code"></i> Backend</span>
                    <span class="badge"><i class="fa-solid fa-brain"></i> AI & RAG</span>
                    <span class="badge"><i class="fa-solid fa-cloud"></i> Cloud / DevOps</span>
                </div>

                <div class="social-links">
                    <a href="https://linkedin.com/in/alejandro-agudelo-dev" target="_blank" class="social-btn"><i class="fa-brands fa-linkedin"></i> LinkedIn</a>
                    <a href="https://github.com/Alejandro-Agudelo-Anaya" target="_blank" class="social-btn"><i class="fa-brands fa-github"></i> GitHub</a>
                    <a href="mailto:alagudeloa@unal.edu.co" class="social-btn"><i class="fa-solid fa-envelope"></i> Contacto</a>
                </div>
            </div>
        </header>

        <!-- INTERACTIVE TERMINAL WIDGET -->
        <div class="terminal">
            <div class="terminal-header">
                <div class="dot dot-red"></div>
                <div class="dot dot-yellow"></div>
                <div class="dot dot-green"></div>
                <span class="terminal-title">bash - alejandro@dev-portfolio:~</span>
            </div>
            <div class="terminal-body" id="terminal-output">
                <div>Escribe <span style="color: var(--accent-green); font-weight: bold;">'help'</span> para ver la lista de comandos disponibles...</div>
            </div>
            <div class="terminal-input-line" style="padding: 0 1.2rem 1.2rem 1.2rem;">
                <span class="prompt">guest@agudelo-dev:~$</span>
                <input type="text" id="terminal-input" class="terminal-input" autofocus autocomplete="off">
            </div>
        </div>

        <!-- SPECIALIZATION & SKILLS -->
        <section class="glass-card">
            <h3 class="section-title"><i class="fa-solid fa-layer-group"></i> Áreas de Especialización & Habilidades</h3>
            <div class="grid-2">
                <div>
                    <h4 style="color: var(--accent-blue); margin-bottom: 1rem;"><i class="fa-solid fa-server"></i> Backend & Lenguajes</h4>
                    <div class="skill-item">
                        <div class="skill-info"><span>Python (FastAPI)</span><span>85%</span></div>
                        <div class="skill-bar"><div class="skill-progress" data-width="85%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>Java (Spring Boot)</span><span>70%</span></div>
                        <div class="skill-bar"><div class="skill-progress" data-width="70%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>SQL & Bases de Datos</span><span>65%</span></div>
                        <div class="skill-bar"><div class="skill-progress" data-width="65%"></div></div>
                    </div>
                </div>

                <div>
                    <h4 style="color: var(--accent-green); margin-bottom: 1rem;"><i class="fa-solid fa-robot"></i> AI, Cloud & Infrastructure</h4>
                    <div class="skill-item">
                        <div class="skill-info"><span>Generative AI / RAG / AI Agents</span><span>65%</span></div>
                        <div class="skill-bar"><div class="skill-progress" data-width="65%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>Machine Learning & Data</span><span>65%</span></div>
                        <div class="skill-bar"><div class="skill-progress" data-width="65%"></div></div>
                    </div>
                    <div class="skill-item">
                        <div class="skill-info"><span>Git / Linux / AWS / Networking</span><span>60%</span></div>
                        <div class="skill-bar"><div class="skill-progress" data-width="60%"></div></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- FEATURED PROJECTS -->
        <section class="glass-card">
            <h3 class="section-title"><i class="fa-solid fa-code-fork"></i> Proyectos Destacados</h3>
            <div class="grid-2">
                <!-- Project 1 -->
                <div class="project-card">
                    <div>
                        <div class="project-title">
                            <span>Asistente IA - Legislación Laboral</span>
                            <i class="fa-solid fa-scale-balanced"></i>
                        </div>
                        <p class="project-desc">
                            Sistema modular con arquitectura RAG y agentes de IA expuesto con FastAPI. Implementa un pipeline con LangChain y LangGraph para clasificación de intención, búsqueda semántica en Chroma DB y orquestación de LLMs (Gemini, Llama, Groq).
                        </p>
                    </div>
                    <div class="project-tags">
                        <span class="tag">Python</span>
                        <span class="tag">FastAPI</span>
                        <span class="tag">LangChain</span>
                        <span class="tag">LangGraph</span>
                        <span class="tag">ChromaDB</span>
                        <span class="tag">RAG</span>
                    </div>
                </div>

                <!-- Project 2 -->
                <div class="project-card">
                    <div>
                        <div class="project-title">
                            <span>ShareIt</span>
                            <i class="fa-solid fa-users-gear"></i>
                        </div>
                        <p class="project-desc">
                            Proyecto de Ingeniería de Software bajo marco de trabajo Scrum. Desarrollo de componentes backend integrados con APIs y BD. Enfocado en testing, documentación técnica e incidencias (Alineado con ISO/IEC 25010).
                        </p>
                    </div>
                    <div class="project-tags">
                        <span class="tag">APIs REST</span>
                        <span class="tag">Scrum</span>
                        <span class="tag">Git</span>
                        <span class="tag">Software Quality</span>
                        <span class="tag">Databases</span>
                    </div>
                </div>
            </div>
        </section>

        <!-- PERSONAL PROFILE & INTERESTS -->
        <section class="glass-card">
            <h3 class="section-title"><i class="fa-solid fa-user-astronaut"></i> Perfil Personal e Intereses</h3>
            <p style="color: var(--text-muted); line-height: 1.6; margin-bottom: 1.5rem;">
                Soy una persona autodidacta y perseverante. Me fascina entender el <i>por qué</i> de las cosas y cómo optimizar sistemas en backend e infraestructura. Fuera del ámbito técnico, mantengo un equilibrio activo cultivando diversas actividades:
            </p>
            <div class="interests-flex">
                <div class="interest-item"><i class="fa-solid fa-person-running"></i> Running</div>
                <div class="interest-item"><i class="fa-solid fa-palette"></i> Dibujo</div>
                <div class="interest-item"><i class="fa-solid fa-music"></i> Baile</div>
                <div class="interest-item"><i class="fa-solid fa-language"></i> Inglés (B1 Intermedio)</div>
            </div>
        </section>
    </div>

    <footer>
        <p>Diseñado para GitHub | Alejandro Agudelo Anaya &copy; 2026</p>
    </footer>

    <!-- INTERACTIVE JAVASCRIPT -->
    <script>
        // 1. Particle Background Animation
        const canvas = document.getElementById('particles-canvas');
        const ctx = canvas.getContext('2d');
        let particles = [];

        function resizeCanvas() {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resizeCanvas);
        resizeCanvas();

        class Particle {
            constructor() {
                this.x = Math.random() * canvas.width;
                this.y = Math.random() * canvas.height;
                this.size = Math.random() * 2 + 1;
                this.speedX = Math.random() * 0.5 - 0.25;
                this.speedY = Math.random() * 0.5 - 0.25;
                this.color = Math.random() > 0.5 ? 'rgba(0, 255, 204, 0.3)' : 'rgba(0, 184, 255, 0.3)';
            }
            update() {
                this.x += this.speedX;
                this.y += this.speedY;
                if (this.x < 0 || this.x > canvas.width) this.speedX *= -1;
                if (this.y < 0 || this.y > canvas.height) this.speedY *= -1;
            }
            draw() {
                ctx.fillStyle = this.color;
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fill();
            }
        }

        function initParticles() {
            particles = [];
            for (let i = 0; i < 60; i++) {
                particles.push(new Particle());
            }
        }
        initParticles();

        function animateParticles() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            requestAnimationFrame(animateParticles);
        }
        animateParticles();

        // 2. Animate Skill Bars on Load
        window.addEventListener('load', () => {
            const skillProgresses = document.querySelectorAll('.skill-progress');
            skillProgresses.forEach(progress => {
                const targetWidth = progress.getAttribute('data-width');
                progress.style.width = targetWidth;
            });
        });

        // 3. Interactive Terminal Logic
        const terminalInput = document.getElementById('terminal-input');
        const terminalOutput = document.getElementById('terminal-output');

        const commands = {
            'help': 'Comandos disponibles: <span style="color:var(--accent-green)">bio</span>, <span style="color:var(--accent-green)">skills</span>, <span style="color:var(--accent-green)">projects</span>, <span style="color:var(--accent-green)">contact</span>, <span style="color:var(--accent-green)">clear</span>',
            'bio': 'Alejandro Agudelo Anaya | Estudiante de Ing. de Sistemas (UNAL Medellín). Enfocado en Backend, AI Agents, RAG y DevOps.',
            'skills': 'Backend: Java, Spring Boot, Python, FastAPI, SQL | AI: ML, Generative AI, LangChain, LangGraph | Cloud: AWS, Linux, Networking Cisco',
            'projects': '1. Asistente IA Legislación Laboral (FastAPI + RAG) \n2. ShareIt (Scrum + Software Architecture)',
            'contact': 'Email: alagudeloa@unal.edu.co | Teléfono: 312 654 6012 | LinkedIn: linkedin.com/in/alejandro-agudelo-dev'
        };

        terminalInput.addEventListener('keydown', (e) => {
            if (e.key === 'Enter') {
                const command = terminalInput.value.trim().toLowerCase();
                terminalInput.value = '';

                const line = document.createElement('div');
                line.style.marginTop = '0.4rem';

                if (command === 'clear') {
                    terminalOutput.innerHTML = '';
                    return;
                }

                if (commands[command]) {
                    line.innerHTML = `<span style="color: var(--accent-blue)">guest@agudelo-dev:~$ ${command}</span><br>${commands[command]}`;
                } else if (command !== '') {
                    line.innerHTML = `<span style="color: var(--accent-blue)">guest@agudelo-dev:~$ ${command}</span><br><span style="color: #ff5f56">Comando no reconocido. Escribe 'help' para ayuda.</span>`;
                }
                terminalOutput.appendChild(line);
                terminalOutput.scrollTop = terminalOutput.scrollHeight;
            }
        });
    </script>
</body>
</html>
