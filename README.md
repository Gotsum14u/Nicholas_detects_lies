# README

## Project Overview

This project is designed to detect lies using a unique set of algorithms and logic.

## Corrected Logic

The logic has been adjusted to ensure accurate assessments of input data. Please refer to the documentation for an in-depth explanation of the algorithms utilized.

## GitHub Pages

Visit our GitHub Pages for more information: [GitHub Pages URL](https://gotsum14u.github.io/Nicholas_detects_lies)<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Smart Lie Detector | Advanced Truth Analysis System</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Share+Tech+Mono&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Share Tech Mono', monospace;
            overflow: hidden;
        }
        
        .scan-line {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: rgba(0, 255, 255, 0.5);
            box-shadow: 0 0 10px rgba(0, 255, 255, 0.8);
            animation: scan 2s linear infinite;
            z-index: 50;
            display: none;
        }

        @keyframes scan {
            0% { top: 0%; opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { top: 100%; opacity: 0; }
        }

        .shake {
            animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) both;
        }

        @keyframes shake {
            10%, 90% { transform: translate3d(-1px, 0, 0); }
            20%, 80% { transform: translate3d(2px, 0, 0); }
            30%, 50%, 70% { transform: translate3d(-4px, 0, 0); }
            40%, 60% { transform: translate3d(4px, 0, 0); }
        }

        .glitch {
            position: relative;
        }
        
        .glitch::before,
        .glitch::after {
            content: attr(data-text);
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: inherit; 
        }

        .glitch::before {
            left: 2px;
            text-shadow: -1px 0 red;
            clip: rect(24px, 550px, 90px, 0);
            animation: glitch-anim-2 3s infinite linear alternate-reverse;
        }

        .glitch::after {
            left: -2px;
            text-shadow: -1px 0 blue;
            clip: rect(85px, 550px, 140px, 0);
            animation: glitch-anim-1 2.5s infinite linear alternate-reverse;
        }

        @keyframes glitch-anim-1 {
            0% { clip: rect(20px, 9999px, 15px, 0); }
            20% { clip: rect(50px, 9999px, 60px, 0); }
            40% { clip: rect(80px, 9999px, 5px, 0); }
            60% { clip: rect(10px, 9999px, 90px, 0); }
            80% { clip: rect(40px, 9999px, 20px, 0); }
            100% { clip: rect(70px, 9999px, 100px, 0); }
        }

        @keyframes glitch-anim-2 {
            0% { clip: rect(10px, 9999px, 80px, 0); }
            20% { clip: rect(80px, 9999px, 10px, 0); }
            40% { clip: rect(30px, 9999px, 50px, 0); }
            60% { clip: rect(60px, 9999px, 90px, 0); }
            80% { clip: rect(20px, 9999px, 60px, 0); }
            100% { clip: rect(90px, 9999px, 10px, 0); }
        }

        .radar-ping {
            animation: ping 1s cubic-bezier(0, 0, 0.2, 1) infinite;
        }

        @keyframes ping {
            75%, 100% {
                transform: scale(2);
                opacity: 0;
            }
        }

        .crt::before {
            content: " ";
            display: block;
            position: absolute;
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            background: linear-gradient(rgba(18, 16, 16, 0) 50%, rgba(0, 0, 0, 0.25) 50%), linear-gradient(90deg, rgba(255, 0, 0, 0.06), rgba(0, 255, 0, 0.02), rgba(0, 0, 255, 0.06));
            z-index: 2;
            background-size: 100% 2px, 3px 100%;
            pointer-events: none;
        }
        
        .bg-grid {
            background-size: 40px 40px;
            background-image: linear-gradient(to right, rgba(255, 255, 255, 0.05) 1px, transparent 1px),
                              linear-gradient(to bottom, rgba(255, 255, 255, 0.05) 1px, transparent 1px);
        }

        .blink {
            animation: blinker 1s linear infinite;
        }

        @keyframes blinker {
            50% { opacity: 0; }
        }
    </style>
</head>
<body class="bg-slate-900 text-white min-h-screen flex items-center justify-center relative crt transition-colors duration-700" id="mainBody">

    <canvas id="bgCanvas" class="absolute top-0 left-0 w-full h-full z-0"></canvas>
    <div id="scanLine" class="scan-line"></div>

    <div id="interfaceContainer" class="relative z-10 w-full max-w-md p-6 transition-all duration-500">
        
        <div class="text-center mb-8 relative">
            <div class="absolute -top-10 left-1/2 transform -translate-x-1/2 w-20 h-20 bg-cyan-500 rounded-full opacity-20 blur-xl animate-pulse"></div>
            <h1 class="text-4xl md:text-5xl font-black text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-600 font-['Orbitron'] tracking-wider drop-shadow-[0_0_10px_rgba(0,255,255,0.5)]">
                LIE DETECTOR
            </h1>
            <div class="flex justify-center items-center gap-2 mt-2">
                <div class="h-1 w-12 bg-cyan-500 rounded-full"></div>
                <p class="text-cyan-300 text-xs tracking-[0.3em] uppercase">Neural Analysis System v2.4</p>
                <div class="h-1 w-12 bg-cyan-500 rounded-full"></div>
            </div>
        </div>

        <div class="bg-slate-800/80 backdrop-blur-md border border-slate-700 rounded-2xl p-8 shadow-[0_0_40px_rgba(0,0,0,0.5)] relative overflow-hidden group">
            <div class="absolute top-0 left-0 w-4 h-4 border-t-2 border-l-2 border-cyan-500 rounded-tl-lg"></div>
            <div class="absolute top-0 right-0 w-4 h-4 border-t-2 border-r-2 border-cyan-500 rounded-tr-lg"></div>
            <div class="absolute bottom-0 left-0 w-4 h-4 border-b-2 border-l-2 border-cyan-500 rounded-bl-lg"></div>
            <div class="absolute bottom-0 right-0 w-4 h-4 border-b-2 border-r-2 border-cyan-500 rounded-br-lg"></div>

            <div class="space-y-6">
                <div class="relative">
                    <label for="statementInput" class="block text-cyan-400 text-sm font-bold mb-2 uppercase tracking-wider">
                        Enter what you want to say
                    </label>
                    <div class="relative">
                        <input type="text" id="statementInput" 
                            class="w-full bg-slate-900/50 border border-slate-600 text-cyan-100 text-lg rounded-lg focus:ring-2 focus:ring-cyan-500 focus:border-cyan-500 block w-full p-4 placeholder-slate-500 transition-all outline-none font-['Share_Tech_Mono']"
                            placeholder="Enter what you want to say..." autocomplete="off">
                        <div class="absolute right-3 top-3">
                            <div id="inputStatusIcon" class="w-3 h-3 rounded-full bg-slate-600"></div>
                        </div>
                    </div>
                    <p class="text-slate-500 text-xs mt-2 flex items-center gap-1">
                        <svg class="w-3 h-3" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 16h-1v-4h-1m1-4h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        System monitors language patterns for optimal analysis.
                    </p>
                </div>

                <button id="detectBtn" class="w-full group relative overflow-hidden rounded-lg bg-gradient-to-r from-cyan-600 to-blue-600 p-4 font-bold text-white shadow-lg transition-all hover:scale-[1.02] hover:shadow-cyan-500/25 active:scale-95">
                    <div class="absolute inset-0 bg-white/20 translate-y-full transition-transform duration-300 group-hover:translate-y-0"></div>
                    <span class="relative flex items-center justify-center gap-2 text-lg tracking-widest uppercase">
                        <svg class="w-5 h-5 animate-pulse" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                        Start Detection
                    </span>
                </button>
            </div>

            <div id="analysisPanel" class="hidden mt-8 border-t border-slate-700 pt-6">
                <div class="flex justify-between items-end mb-2">
                    <span class="text-xs text-cyan-400 uppercase">Analyzing Voice Stress...</span>
                    <span id="percentDisplay" class="text-xl font-bold text-white">0%</span>
                </div>
                <div class="w-full bg-slate-700 rounded-full h-2.5 mb-6 overflow-hidden">
                    <div id="progressBar" class="bg-cyan-500 h-2.5 rounded-full transition-all duration-100" style="width: 0%"></div>
                </div>
                <div class="flex items-center justify-center gap-1 h-12 mb-4" id="waveform"></div>
            </div>

            <div id="resultPanel" class="hidden mt-6 text-center p-4 rounded-lg border transition-all duration-500 transform scale-95 opacity-0">
                <div id="resultIcon" class="mx-auto w-16 h-16 mb-3 rounded-full flex items-center justify-center text-3xl"></div>
                <h2 id="resultTitle" class="text-2xl font-bold mb-1 font-['Orbitron']"></h2>
                <p id="resultMessage" class="text-sm opacity-90"></p>
            </div>
        </div>
        
        <div class="mt-6 flex justify-between text-[10px] text-slate-500 uppercase tracking-widest">
            <span>Sys.Status: <span class="text-green-500">Online</span></span>
            <span>Lat: 34.0522 N // Long: 118.2437 W</span>
        </div>
    </div>

    <div id="alertOverlay" class="fixed inset-0 z-50 bg-red-950/90 backdrop-blur-xl hidden flex-col items-center justify-center text-center p-4 crt">
        <div class="absolute inset-0 bg-grid opacity-20"></div>
        
        <div class="relative z-10 max-w-2xl w-full border-2 border-red-600 bg-black/80 p-8 rounded-lg shadow-[0_0_50px_rgba(220,38,38,0.6)]">
            <div class="flex justify-center mb-6">
                <div class="relative">
                    <div class="w-24 h-24 bg-red-600 rounded-full flex items-center justify-center animate-pulse">
                        <svg class="w-12 h-12 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"></path></svg>
                    </div>
                    <div class="absolute inset-0 rounded-full border-4 border-red-500 radar-ping"></div>
                </div>
            </div>

            <h1 class="text-5xl md:text-7xl font-black text-red-500 mb-2 font-['Orbitron'] tracking-tighter glitch" data-text="SECURITY BREACH">SECURITY BREACH</h1>
            
            <div class="space-y-4 my-8">
                <div class="bg-red-900/30 border border-red-500/50 p-4 rounded">
                    <p class="text-red-400 text-sm uppercase tracking-widest mb-1">Protocol Initiated</p>
                    <p class="text-2xl md:text-3xl font-bold text-white blink">Location locked</p>
                </div>
                
                <div class="bg-red-900/30 border border-red-500/50 p-4 rounded">
                    <p class="text-red-400 text-sm uppercase tracking-widest mb-1">Emergency Response</p>
                    <p class="text-2xl md:text-3xl font-bold text-white blink">110 dialed</p>
                </div>
            </div>

            <div class="text-red-300/70 text-xs font-mono border-t border-red-900 pt-4">
                <p>TRACE ID: <span id="traceId">8492-AX-99</span></p>
                <p>ENCRYPTION: NONE // PACKET SNIFFING: ACTIVE</p>
                <p class="mt-2 animate-pulse">DO NOT RESIST. REMAIN SEATED.</p>
            </div>
            
            <button onclick="resetSystem()" class="mt-8 px-6 py-2 border border-red-600 text-red-500 hover:bg-red-600 hover:text-white transition-colors uppercase text-sm tracking-widest">
                Attempt System Override (Admin)
            </button>
        </div>
    </div>

    <script>
        const state = { isAnalyzing: false, isAlert: false };
        const els = {
            body: document.getElementById('mainBody'),
            input: document.getElementById('statementInput'),
            btn: document.getElementById('detectBtn'),
            scanLine: document.getElementById('scanLine'),
            analysisPanel: document.getElementById('analysisPanel'),
            progressBar: document.getElementById('progressBar'),
            percentDisplay: document.getElementById('percentDisplay'),
            waveform: document.getElementById('waveform'),
            resultPanel: document.getElementById('resultPanel'),
            resultTitle: document.getElementById('resultTitle'),
            resultMessage: document.getElementById('resultMessage'),
            resultIcon: document.getElementById('resultIcon'),
            alertOverlay: document.getElementById('alertOverlay'),
            traceId: document.getElementById('traceId'),
            inputStatusIcon: document.getElementById('inputStatusIcon')
        };

        document.addEventListener('DOMContentLoaded', () => {
            initWaveform();
            initParticles();
            
            els.input.addEventListener('input', (e) => {
                const val = e.target.value;
                els.inputStatusIcon.className = val.length > 0 ? "w-3 h-3 rounded-full bg-yellow-400 animate-pulse" : "w-3 h-3 rounded-full bg-slate-600";
            });

            els.btn.addEventListener('click', handleDetection);
            els.traceId.innerText = Math.random().toString(36).substring(2, 15).toUpperCase() + '-' + Math.floor(Math.random()*1000);
        });

        function handleDetection() {
            if (state.isAnalyzing) return;
            const text = els.input.value.trim();
            if (!text) { shakeInput(); return; }

            state.isAnalyzing = true;
            els.btn.disabled = true;
            els.btn.classList.add('opacity-50', 'cursor-not-allowed');
            
            els.scanLine.style.display = 'block';
            els.analysisPanel.classList.remove('hidden');
            els.resultPanel.classList.add('hidden');
            els.resultPanel.classList.remove('scale-100', 'opacity-100');
            
            runAnalysisAnimation(() => evaluateResult(text));
        }

        function runAnalysisAnimation(callback) {
            let progress = 0;
            const interval = setInterval(() => {
                progress += Math.random() * 5;
                if (progress > 100) progress = 100;
                els.progressBar.style.width = `${progress}%`;
                els.percentDisplay.innerText = `${Math.floor(progress)}%`;
                updateWaveform();
                if (progress === 100) { clearInterval(interval); setTimeout(callback, 500); }
            }, 50);
        }

        function evaluateResult(text) {
            const hasChinese = /\p{Script=Han}/u.test(text);
            els.scanLine.style.display = 'none';
            els.analysisPanel.classList.add('hidden');
            els.resultPanel.classList.remove('hidden');
            void els.resultPanel.offsetWidth; 
            els.resultPanel.classList.add('scale-100', 'opacity-100');

            if (!hasChinese) triggerAlertMode();
            else showTruthResult();

            state.isAnalyzing = false;
            els.btn.disabled = false;
            els.btn.classList.remove('opacity-50', 'cursor-not-allowed');
        }

        function showTruthResult() {
            els.resultPanel.className = "mt-6 text-center p-6 rounded-lg border border-green-500/50 bg-green-900/20 shadow-[0_0_20px_rgba(34,197,94,0.2)] transition-all duration-500 transform scale-100 opacity-100";
            els.resultIcon.className = "mx-auto w-16 h-16 mb-4 rounded-full flex items-center justify-center text-3xl bg-green-500/20 text-green-400 border border-green-500";
            els.resultIcon.innerHTML = `<svg class="w-8 h-8" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7"></path></svg>`;
            els.resultTitle.innerText = "Detection passed!";
            els.resultTitle.className = "text-2xl font-bold mb-2 font-['Orbitron'] text-green-400";
            els.resultMessage.innerText = "You told the truth!";
            els.resultMessage.className = "text-green-200";
        }

        function triggerAlertMode() {
            state.isAlert = true;
            setTimeout(() => {
                els.alertOverlay.classList.remove('hidden');
                els.alertOverlay.classList.add('flex');
                startSirenEffect();
                els.body.classList.remove('from-slate-900', 'to-slate-800');
                els.body.style.backgroundColor = '#450a0a';
            }, 500);
        }

        function resetSystem() {
            state.isAlert = false;
            els.alertOverlay.classList.add('hidden');
            els.alertOverlay.classList.remove('flex');
            els.input.value = '';
            els.resultPanel.classList.add('hidden');
            els.resultPanel.classList.remove('scale-100', 'opacity-100');
            els.body.style.backgroundColor = '';
            els.body.classList.add('from-slate-900', 'to-slate-800');
            els.inputStatusIcon.className = "w-3 h-3 rounded-full bg-slate-600";
        }

        function shakeInput() {
            els.input.parentElement.classList.add('shake');
            els.input.classList.add('border-red-500');
            setTimeout(() => {
                els.input.parentElement.classList.remove('shake');
                els.input.classList.remove('border-red-500');
            }, 500);
        }

        function initWaveform() {
            for(let i=0; i<20; i++) {
                const bar = document.createElement('div');
                bar.className = "w-1 bg-cyan-500 rounded-full transition-all duration-75";
                bar.style.height = '20%';
                els.waveform.appendChild(bar);
            }
        }

        function updateWaveform() {
            const bars = els.waveform.children;
            for(let bar of bars) {
                const h = Math.floor(Math.random() * 80) + 10;
                bar.style.height = `${h}%`;
                bar.className = h > 70 ? "w-1 bg-red-500 rounded-full transition-all duration-75" : "w-1 bg-cyan-500 rounded-full transition-all duration-75";
            }
        }

        function startSirenEffect() {
            let toggle = false;
            const sirenInterval = setInterval(() => {
                if(!state.isAlert) { clearInterval(sirenInterval); return; }
                els.alertOverlay.style.backgroundColor = toggle ? 'rgba(50, 0, 0, 0.9)' : 'rgba(20, 0, 0, 0.95)';
                toggle = !toggle;
            }, 200);
        }

        function initParticles() {
            const canvas = document.getElementById('bgCanvas');
            const ctx = canvas.getContext('2d');
            let width, height;
            let particles = [];

            function resize() {
                width = window.innerWidth;
                height = window.innerHeight;
                canvas.width = width;
                canvas.height = height;
            }
            
            window.addEventListener('resize', resize);
            resize();

            class Particle {
                constructor() {
                    this.x = Math.random() * width;
                    this.y = Math.random() * height;
                    this.vx = (Math.random() - 0.5) * 0.5;
                    this.vy = (Math.random() - 0.5) * 0.5;
                    this.size = Math.random() * 2;
                    this.alpha = Math.random() * 0.5 + 0.1;
                }
                update() {
                    this.x += this.vx;
                    this.y += this.vy;
                    if (this.x < 0) this.x = width;
                    if (this.x > width) this.x = 0;
                    if (this.y < 0) this.y = height;
                    if (this.y > height) this.y = 0;
                }
                draw() {
                    ctx.fillStyle = `rgba(6, 182, 212, ${this.alpha})`;
                    ctx.beginPath();
                    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                    ctx.fill();
                }
            }

            for (let i = 0; i < 100; i++) particles.push(new Particle());

            function animate() {
                ctx.clearRect(0, 0, width, height);
                ctx.strokeStyle = 'rgba(6, 182, 212, 0.05)';
                ctx.lineWidth = 1;
                
                for (let i = 0; i < particles.length; i++) {
                    particles[i].update();
                    particles[i].draw();
                    for (let j = i; j < particles.length; j++) {
                        const dx = particles[i].x - particles[j].x;
                        const dy = particles[i].y - particles[j].y;
                        const distance = Math.sqrt(dx * dx + dy * dy);
                        if (distance < 100) {
                            ctx.beginPath();
                            ctx.moveTo(particles[i].x, particles[i].y);
                            ctx.lineTo(particles[j].x, particles[j].y);
                            ctx.stroke();
                        }
                    }
                }
                requestAnimationFrame(animate);
            }
            animate();
        }
    </script>
</body>
</html>
