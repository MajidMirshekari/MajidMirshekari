<style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0a0c10;
            font-family: 'Segoe UI', 'Fira Code', 'JetBrains Mono', monospace;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            padding: 40px 20px;
        }

        .ide-container {
            max-width: 1300px;
            width: 100%;
            background: #1e1e2e;
            border-radius: 16px;
            overflow: hidden;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.8), 0 0 0 1px rgba(75, 85, 99, 0.3);
        }

        .title-bar {
            background: #181825;
            padding: 12px 20px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border-bottom: 1px solid #313244;
            flex-wrap: wrap;
            gap: 10px;
        }

        .window-controls {
            display: flex;
            gap: 12px;
        }

        .win-btn {
            width: 14px;
            height: 14px;
            border-radius: 50%;
            transition: 0.2s;
        }

        .close { background: #ff5f56; }
        .min { background: #ffbd2e; }
        .max { background: #27c93f; }

        .ide-title {
            color: #cdd6f4;
            font-size: 13px;
            font-family: monospace;
            background: #313244;
            padding: 4px 12px;
            border-radius: 8px;
        }

        .tabs {
            background: #181825;
            display: flex;
            gap: 4px;
            padding-left: 20px;
            border-bottom: 1px solid #313244;
        }

        .tab {
            padding: 10px 20px;
            color: #a6adc8;
            font-size: 13px;
            cursor: pointer;
            background: #1e1e2e;
            border-radius: 8px 8px 0 0;
            transition: 0.2s;
            display: flex;
            align-items: center;
            gap: 8px;
            font-family: monospace;
        }

        .tab.active {
            background: #1e1e2e;
            color: #89b4fa;
            border-bottom: 2px solid #89b4fa;
        }

        .tab:hover:not(.active) {
            background: #313244;
            color: #cdd6f4;
        }

        .editor-area {
            display: flex;
            min-height: 550px;
        }

        .sidebar {
            width: 250px;
            background: #181825;
            border-right: 1px solid #313244;
            padding: 16px;
        }

        .sidebar-title {
            color: #89b4fa;
            font-size: 11px;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 16px;
        }

        .file-tree {
            list-style: none;
        }

        .file-tree li {
            padding: 6px 0;
            color: #a6adc8;
            font-size: 13px;
            cursor: pointer;
            display: flex;
            align-items: center;
            gap: 8px;
            transition: 0.2s;
        }

        .file-tree li:hover {
            color: #89b4fa;
        }

        .file-tree .active-file {
            color: #89b4fa;
            background: #313244;
            padding-left: 8px;
            border-radius: 6px;
        }

        .content-panel {
            flex: 1;
            padding: 24px;
            overflow-y: auto;
            max-height: 550px;
        }

        .code-window {
            background: #0a0c10;
            border-radius: 12px;
            border: 1px solid #313244;
            overflow: hidden;
            margin-bottom: 20px;
        }

        .code-header {
            background: #181825;
            padding: 8px 16px;
            border-bottom: 1px solid #313244;
            display: flex;
            justify-content: space-between;
            font-size: 12px;
            color: #a6adc8;
        }

        .code-lang {
            color: #89b4fa;
        }

        .code-body {
            padding: 16px;
            font-family: 'Fira Code', monospace;
            font-size: 13px;
            line-height: 1.6;
            color: #cdd6f4;
            overflow-x: auto;
        }

        .code-body pre {
            margin: 0;
            white-space: pre-wrap;
        }

        .skills-icon-group {
            display: flex;
            flex-wrap: wrap;
            justify-content: flex-start;
            gap: 18px;
            margin-top: 20px;
            background: transparent;
            padding: 8px 0;
        }

        .skill-icon-item {
            display: inline-flex;
            flex-direction: column;
            align-items: center;
            gap: 8px;
            background: transparent;
            padding: 8px 12px;
            transition: all 0.2s ease;
            border-radius: 16px;
        }

        .skill-icon-item:hover {
            transform: translateY(-4px);
        }

        .skill-icon-item img {
            width: 48px;
            height: 48px;
            display: block;
        }

        .skill-icon-item span {
            font-size: 13px;
            font-weight: 500;
            color: #cdd6f4;
            font-family: 'Segoe UI', monospace;
            background: transparent;
        }

        .contact-links {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            margin-top: 16px;
        }

        .contact-link {
            background: #181825;
            border: 1px solid #313244;
            padding: 10px 18px;
            border-radius: 40px;
            color: #cdd6f4;
            text-decoration: none;
            font-size: 13px;
            transition: 0.2s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            font-weight: 500;
        }

        .contact-link:hover {
            border-color: #89b4fa;
            color: #89b4fa;
            transform: translateY(-2px);
        }

        .contact-link img {
            width: 18px;
            height: 18px;
        }

        hr {
            border-color: #313244;
            margin: 16px 0;
        }

        .status-line {
            color: #a6e3a1;
            font-family: monospace;
            font-size: 12px;
        }

        ::-webkit-scrollbar {
            width: 8px;
            height: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #181825;
        }
        ::-webkit-scrollbar-thumb {
            background: #313244;
            border-radius: 4px;
        }
    </style>
<div class="ide-container">
    <div class="title-bar">
        <div class="window-controls">
            <div class="win-btn close"></div>
            <div class="win-btn min"></div>
            <div class="win-btn max"></div>
        </div>
        <div class="ide-title">
            <i>📁</i> RadinDev@ide:~/
        </div>
        <div style="width: 70px;"></div>
    </div>

    <div class="tabs">
        <div class="tab active" data-tab="welcome">📄 welcome.md</div>
        <div class="tab" data-tab="about">👤 about.radin</div>
        <div class="tab" data-tab="skills">⚙️ skills.json</div>
        <div class="tab" data-tab="contact">📡 contact.sh</div>
    </div>

    <div class="editor-area">
        <div class="sidebar">
            <div class="sidebar-title">📂 EXPLORER</div>
            <ul class="file-tree">
                <li data-tab="welcome" class="file-item active-file">📄 welcome.md</li>
                <li data-tab="about" class="file-item">📄 about.radin</li>
                <li data-tab="skills" class="file-item">📄 skills.json</li>
                <li data-tab="contact" class="file-item">📄 contact.sh</li>
                <hr style="margin: 12px 0;">
                <li>📁 portfolio/</li>
                <li style="padding-left: 20px;">🌐 bestui.ir</li>
                <li style="padding-left: 20px;">📄 MyResume.jpg</li>
            </ul>
        </div>

        <div class="content-panel" id="contentPanel">
            <div id="welcome-content" class="tab-content" style="display: block;">
                <div class="code-window">
                    <div class="code-header">
                        <span class="code-lang">📄 TERMINAL</span>
                        <span class="status-line">🟢 ONLINE</span>
                    </div>
                    <div class="code-body">
                        <pre>> root@radin:~# whoami</pre>
                        <pre style="color: #89b4fa;">Radin (Majid Mirshekari)</pre>
                        <pre>></pre>
                        <pre>> root@radin:~# cat welcome.txt</pre>
                        <pre>┌─────────────────────────────────────────┐</pre>
                        <pre>│  🚀 Welcome to my Dev Space!            │</pre>
                        <pre>│  👨‍💻 FullStack Developer & Security Geek │</pre>
                        <pre>│  🔐 "Code. Break. Fix. Repeat."         │</pre>
                        <pre>└─────────────────────────────────────────┘</pre>
                        <pre>></pre>
                        <pre>> <span style="color: #a6e3a1;">System ready. Let's build something amazing.</span></pre>
                    </div>
                </div>

                <div class="code-window">
                    <div class="code-header">
                        <span class="code-lang">📊 STATS</span>
                    </div>
                    <div class="code-body">
                        <pre>📅 Started : 2021 (Solar 1400)</pre>
                        <pre>⏱️  Experience : ~4-5 Years</pre>
                        <pre>💼 Current : DooLoop + Freelance</pre>
                        <pre>🌍 Location : Remote / On-site</pre>
                        <pre>🎯 Goal : Master FullStack & Cybersecurity</pre>
                    </div>
                </div>
            </div>

            <div id="about-content" class="tab-content" style="display: none;">
                <div class="code-window">
                    <div class="code-header">
                        <span class="code-lang">📄 about.radin</span>
                    </div>
                    <div class="code-body">
                        <pre>{</pre>
                        <pre>  <span style="color: #89b4fa;">"name"</span>: <span style="color: #a6e3a1;">"Radin (Majid Mirshekari)"</span>,</pre>
                        <pre>  <span style="color: #89b4fa;">"alias"</span>: <span style="color: #a6e3a1;">"Radin"</span>,</pre>
                        <pre>  <span style="color: #89b4fa;">"role"</span>: <span style="color: #a6e3a1;">"FullStack Developer & Security Enthusiast"</span>,</pre>
                        <pre>  <span style="color: #89b4fa;">"experience"</span>: <span style="color: #a6e3a1;">"~4-5 years (2021 - present)"</span>,</pre>
                        <pre>  <span style="color: #89b4fa;">"work"</span>: {</pre>
                        <pre>    <span style="color: #89b4fa;">"company"</span>: <span style="color: #a6e3a1;">"DooLoop"</span>,</pre>
                        <pre>    <span style="color: #89b4fa;">"type"</span>: <span style="color: #a6e3a1;">"On-site + Remote Freelance"</span></pre>
                        <pre>  },</pre>
                        <pre>  <span style="color: #89b4fa;">"mission"</span>: <span style="color: #a6e3a1;">"Always learning, always improving"</span></pre>
                        <pre>}</pre>
                    </div>
                </div>

                <div class="code-window">
                    <div class="code-header">
                        <span class="code-lang">💡 QUOTE</span>
                    </div>
                    <div class="code-body">
                        <pre>"The quieter you become, the more you are able to hear."</pre>
                        <pre>— Kali Linux proverb</pre>
                    </div>
                </div>
            </div>

            <div id="skills-content" class="tab-content" style="display: none;">
                <div class="code-window">
                    <div class="code-header">
                        <span class="code-lang">⚙️ skills.json</span>
                    </div>
                    <div class="code-body">
                        <pre>{</pre>
                        <pre>  <span style="color: #89b4fa;">"frontend"</span>: [<span style="color: #a6e3a1;">"HTML"</span>, <span style="color: #a6e3a1;">"CSS"</span>, <span style="color: #a6e3a1;">"Sass"</span>, <span style="color: #a6e3a1;">"Tailwind"</span>, <span style="color: #a6e3a1;">"JavaScript"</span>],</pre>
                        <pre>  <span style="color: #89b4fa;">"backend"</span>: [<span style="color: #a6e3a1;">"Python"</span>, <span style="color: #a6e3a1;">"PHP"</span>],</pre>
                        <pre>  <span style="color: #89b4fa;">"design"</span>: [<span style="color: #a6e3a1;">"Figma"</span>, <span style="color: #a6e3a1;">"UI/UX"</span>, <span style="color: #a6e3a1;">"WordPress"</span>],</pre>
                        <pre>  <span style="color: #89b4fa;">"tools"</span>: [<span style="color: #a6e3a1;">"Git"</span>, <span style="color: #a6e3a1;">"GitHub"</span>],</pre>
                        <pre>  <span style="color: #89b4fa;">"os"</span>: [<span style="color: #a6e3a1;">"Windows"</span>, <span style="color: #a6e3a1;">"Linux"</span>],</pre>
                        <pre>  <span style="color: #89b4fa;">"security"</span>: [<span style="color: #a6e3a1;">"Network Analysis"</span>, <span style="color: #a6e3a1;">"Ethical Hacking"</span>]</pre>
                        <pre>}</pre>
                    </div>
                </div>

                <div class="skills-icon-group">
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5"><span>HTML5</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3"><span>CSS3</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/sass/sass-original.svg" alt="Sass"><span>Sass</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tailwindcss/tailwindcss-original.svg" alt="Tailwind"><span>Tailwind</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JavaScript"><span>JavaScript</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" alt="Python"><span>Python</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" alt="PHP"><span>PHP</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt="Figma"><span>Figma</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/wordpress/wordpress-original.svg" alt="WordPress"><span>WordPress</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" alt="Git"><span>Git</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" alt="GitHub"><span>GitHub</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/windows8/windows8-original.svg" alt="Windows"><span>Windows</span></div>
                    <div class="skill-icon-item"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linux/linux-original.svg" alt="Linux"><span>Linux</span></div>
                </div>
            </div>

            <div id="contact-content" class="tab-content" style="display: none;">
                <div class="code-window">
                    <div class="code-header">
                        <span class="code-lang">📡 contact.sh</span>
                    </div>
                    <div class="code-body">
                        <pre>#!/bin/bash</pre>
                        <pre># Establish secure connection with Radin</pre>
                        <pre></pre>
                        <pre>TELEGRAM="<span style="color: #89b4fa;">@MajidMirshekari76</span>"</pre>
                        <pre>EMAIL="<span style="color: #89b4fa;">MajidMirshekari6@gmail.com</span>"</pre>
                        <pre>EMAIL2="<span style="color: #89b4fa;">Majid-Mirshekari@Hotmail.com</span>"</pre>
                        <pre>LINKEDIN="<span style="color: #89b4fa;">majid-mirshekari-322005130</span>"</pre>
                        <pre>PORTFOLIO="<span style="color: #89b4fa;">https://www.BestUI.ir</span>"</pre>
                        <pre></pre>
                        <pre>echo "📱 Telegram: $TELEGRAM"</pre>
                        <pre>echo "📧 Email: $EMAIL"</pre>
                        <pre>echo "🌐 Portfolio: $PORTFOLIO"</pre>
                    </div>
                </div>

                <div class="contact-links">
                    <a href="https://t.me/MajidMirshekari76" class="contact-link">
                        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/telegram/telegram-original.svg" width="18" height="18" style="filter: invert(0);"> Telegram
                    </a>
                    <a href="mailto:MajidMirshekari6@gmail.com" class="contact-link">
                        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/google/google-original.svg" width="18" height="18"> Gmail
                    </a>
                    <a href="mailto:Majid-Mirshekari@Hotmail.com" class="contact-link">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/d/df/Microsoft_Office_Outlook_%282018%E2%80%93present%29.svg" width="18" height="18"> Outlook
                    </a>
                    <a href="https://www.linkedin.com/in/majid-mirshekari-322005130/" class="contact-link">
                        <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/linkedin/linkedin-original.svg" width="18" height="18"> LinkedIn
                    </a>
                    <a href="https://www.BestUI.ir" class="contact-link">
                        🌐 BestUI.ir
                    </a>
                </div>

                <hr>

                <div class="code-window">
                    <div class="code-header">
                        <span class="code-lang">📄 RESUME</span>
                    </div>
                    <div class="code-body">
                        <pre>📁 File: MyResume.jpg</pre>
                        <pre>🔗 <a href="/MajidMirshekari/MajidMirshekari/blob/main/MyResume.jpg" style="color: #89b4fa;">Click here to download resume</a></pre>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
    const tabs = document.querySelectorAll('.tab');
    const fileItems = document.querySelectorAll('.file-item');
    const contents = {
        welcome: document.getElementById('welcome-content'),
        about: document.getElementById('about-content'),
        skills: document.getElementById('skills-content'),
        contact: document.getElementById('contact-content')
    };

    function switchTab(tabId) {
        Object.values(contents).forEach(content => {
            if (content) content.style.display = 'none';
        });
        if (contents[tabId]) contents[tabId].style.display = 'block';
        
        tabs.forEach(tab => {
            if (tab.dataset.tab === tabId) tab.classList.add('active');
            else tab.classList.remove('active');
        });
        
        fileItems.forEach(item => {
            if (item.dataset.tab === tabId) item.classList.add('active-file');
            else item.classList.remove('active-file');
        });
    }

    tabs.forEach(tab => {
        tab.addEventListener('click', () => switchTab(tab.dataset.tab));
    });
    fileItems.forEach(item => {
        item.addEventListener('click', () => switchTab(item.dataset.tab));
    });
</script>
