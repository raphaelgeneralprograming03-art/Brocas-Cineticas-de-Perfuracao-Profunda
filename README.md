
<html lang="pt-BR" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SAMS + MHD | Brocas Cinéticas de Perfuração Profunda & Geotermia</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        sci: {
                            950: '#020617',
                            900: '#090d16',
                            800: '#111827',
                            700: '#1f2937',
                            cyan: '#06b6d4',
                            emerald: '#10b981',
                            amber: '#f59e0b',
                            rose: '#f43f5e',
                            purple: '#8b5cf6'
                        }
                    }
                }
            }
        }
    </script>
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=JetBrains+Mono:wght@400;500;700&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Inter', sans-serif; }
        .font-mono { font-family: 'JetBrains Mono', monospace; }
        .glass-panel {
            background: rgba(15, 23, 42, 0.75);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(245, 158, 11, 0.2);
        }
        .glow-amber {
            box-shadow: 0 0 25px rgba(245, 158, 11, 0.25);
        }
        .glow-cyan {
            box-shadow: 0 0 25px rgba(6, 182, 212, 0.25);
        }
        ::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        ::-webkit-scrollbar-track {
            background: #020617;
        }
        ::-webkit-scrollbar-thumb {
            background: #1e293b;
            border-radius: 3px;
        }
        ::-webkit-scrollbar-thumb:hover {
            background: #f59e0b;
        }
    </style>
</head>
<body class="bg-sci-950 text-slate-100 min-h-screen flex flex-col overflow-x-hidden">

    <!-- Header / Navbar -->
    <header class="glass-panel border-b border-amber-500/20 px-6 py-4 flex flex-wrap items-center justify-between gap-4 sticky top-0 z-50">
        <div class="flex items-center space-x-3">
            <div class="relative flex items-center justify-center w-10 h-10 rounded-xl bg-amber-950 border border-amber-500/50 glow-amber">
                <svg class="w-6 h-6 text-amber-400 animate-pulse" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 14l-7 7m0 0l-7-7m7 7V3"/>
                </svg>
            </div>
            <div>
                <h1 class="text-lg font-bold tracking-wider text-transparent bg-clip-text bg-gradient-to-r from-amber-400 to-rose-400">SAMS + MHD DEEP DRILL</h1>
                <p class="text-xs text-slate-400 font-mono">Perfuração Cinética do Manto & Plasma Geotérmico Puro</p>
            </div>
        </div>

        <!-- System Status Pills -->
        <div class="flex items-center gap-3 text-xs font-mono flex-wrap">
            <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-slate-900 border border-slate-700">
                <span id="sams-status-dot" class="w-2.5 h-2.5 rounded-full bg-amber-500 animate-ping"></span>
                <span>SAMS Amortecimento: <strong id="sams-status-text" class="text-amber-400">100% BLINDADO</strong></span>
            </div>
            <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-slate-900 border border-slate-700">
                <span class="w-2.5 h-2.5 rounded-full bg-cyan-500"></span>
                <span>MHD Plasma: <strong id="mhd-status-text" class="text-cyan-400">ATIVO (12,500 K)</strong></span>
            </div>
            <div class="flex items-center gap-2 px-3 py-1.5 rounded-full bg-slate-900 border border-slate-700">
                <span class="w-2.5 h-2.5 rounded-full bg-emerald-500"></span>
                <span>Integridade da Broca: <strong id="integrity-badge" class="text-emerald-400">100.0%</strong></span>
            </div>
        </div>
    </header>

    <!-- Main Workspace -->
    <main class="flex-1 grid grid-cols-1 lg:grid-cols-12 gap-6 p-6 max-w-[1700px] mx-auto w-full">
        
        <!-- Left Sidebar: Geological Strata & Controls -->
        <section class="lg:col-span-3 flex flex-col gap-6">
            
            <!-- Strata / Depth Selection -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl">
                <h2 class="text-sm font-semibold tracking-wide text-amber-400 uppercase mb-4 flex items-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3.055 11H5a2 2 0 012 2v1a2 2 0 002 2 2 2 0 012 2v2.945M8 3.935V5.5A2.5 2.5 0 0010.5 8h.5a2 2 0 012 2 2 2 0 104 0 2 2 0 012-2h1.064M15 20.488V18a2 2 0 012-2h3.064M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/></svg>
                    Camadas Geológicas Terrestres
                </h2>
                <div class="space-y-3">
                    <button onclick="setLayer('crust')" id="layer-crust" class="w-full text-left p-3 rounded-xl border border-amber-500/40 bg-amber-500/10 transition-all hover:bg-amber-500/20 flex items-center justify-between group">
                        <div>
                            <div class="font-semibold text-sm text-amber-300">Crosta Terrestre (0 - 40 km)</div>
                            <div class="text-xs text-slate-400">Granito denso e rochas cristalinas</div>
                        </div>
                        <span class="w-2 h-2 rounded-full bg-amber-400"></span>
                    </button>
                    <button onclick="setLayer('mantle')" id="layer-mantle" class="w-full text-left p-3 rounded-xl border border-slate-700 bg-slate-900/60 transition-all hover:border-orange-500/40 flex items-center justify-between group">
                        <div>
                            <div class="font-semibold text-sm text-slate-200 group-hover:text-orange-300">Manto Superior (40 - 660 km)</div>
                            <div class="text-xs text-slate-400">Peridotito fundido / Alta pressão 24 GPa</div>
                        </div>
                        <span class="w-2 h-2 rounded-full bg-slate-600" id="dot-mantle"></span>
                    </button>
                    <button onclick="setLayer('core')" id="layer-core" class="w-full text-left p-3 rounded-xl border border-slate-700 bg-slate-900/60 transition-all hover:border-rose-500/40 flex items-center justify-between group">
                        <div>
                            <div class="font-semibold text-sm text-slate-200 group-hover:text-rose-300">Núcleo Planetário (2,900+ km)</div>
                            <div class="text-xs text-slate-400">Ferro-níquel líquido / Energia Geotérmica Pura</div>
                        </div>
                        <span class="w-2 h-2 rounded-full bg-slate-600" id="dot-core"></span>
                    </button>
                </div>
            </div>

            <!-- SAMS + MHD Control Unit -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl border-amber-500/30">
                <div class="flex items-center justify-between mb-4">
                    <h2 class="text-sm font-semibold tracking-wide text-amber-400 uppercase flex items-center gap-2">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
                        Sistemas Integrados
                    </h2>
                    <span id="sys-badge" class="px-2.5 py-0.5 rounded text-xs font-mono font-bold bg-amber-500/20 text-amber-300 border border-amber-500/40">ATIVO</span>
                </div>
                
                <div class="space-y-4">
                    <div class="flex items-center justify-between bg-slate-900/80 p-3 rounded-xl border border-slate-800">
                        <div>
                            <div class="text-xs font-medium text-slate-300">SAMS Amortecimento de Fadiga</div>
                            <div class="text-[10px] text-slate-400 font-mono">Neutralização de vibração cíclica</div>
                        </div>
                        <label class="relative inline-flex items-center cursor-pointer">
                            <input type="checkbox" id="samsToggle" checked onchange="toggleSAMS()" class="sr-only peer">
                            <div class="w-11 h-6 bg-slate-700 peer-focus:outline-none rounded-full peer peer-checked:after:translate-x-full peer-checked:after:border-white after:content-[''] after:absolute after:top-[2px] after:left-[2px] after:bg-white after:border-gray-300 after:border after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:bg-amber-500"></div>
                        </label>
                    </div>

                    <div>
                        <div class="flex justify-between text-xs mb-1 font-mono">
                            <span class="text-slate-400">Potência do Jato Plasma MHD</span>
                            <span id="plasma-val" class="text-cyan-400">85%</span>
                        </div>
                        <input type="range" id="plasmaPower" min="30" max="100" value="85" oninput="updatePlasma(this.value)" class="w-full h-2 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-cyan-400">
                    </div>

                    <div>
                        <div class="flex justify-between text-xs mb-1 font-mono">
                            <span class="text-slate-400">Velocidade de Avanço da Broca</span>
                            <span class="text-emerald-400">12.4 m/h</span>
                        </div>
                        <input type="range" min="1" max="25" value="12" class="w-full h-2 bg-slate-800 rounded-lg appearance-none cursor-pointer accent-emerald-400">
                    </div>
                </div>
            </div>

            <!-- Action Triggers -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl flex flex-col gap-3">
                <h2 class="text-sm font-semibold tracking-wide text-amber-400 uppercase mb-1">Comandos Operacionais</h2>
                <button onclick="triggerPlasmaBurst()" class="w-full py-3 px-4 rounded-xl bg-gradient-to-r from-amber-600 to-cyan-600 hover:from-amber-500 hover:to-cyan-500 text-white font-semibold text-sm shadow-lg shadow-amber-900/30 transition-all flex items-center justify-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/></svg>
                    Disparar Explosão de Plasma MHD
                </button>
                <button onclick="recalibrateDrill()" class="w-full py-2.5 px-4 rounded-xl bg-slate-900 hover:bg-slate-800 border border-slate-700 text-slate-300 font-medium text-xs transition-all flex items-center justify-center gap-2">
                    <svg class="w-4 h-4 text-amber-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"/></svg>
                    Recalibrar Giroscópios SAMS
                </button>
            </div>

        </section>

        <!-- Center: Canvas 2D Simulation Viewport -->
        <section class="lg:col-span-6 flex flex-col gap-6">
            <div class="glass-panel rounded-2xl p-4 shadow-2xl relative flex flex-col overflow-hidden border-amber-500/30">
                
                <!-- Viewport Header HUD -->
                <div class="flex items-center justify-between pb-3 mb-3 border-b border-slate-800 text-xs font-mono">
                    <div class="flex items-center gap-2">
                        <span class="w-2 h-2 rounded-full bg-amber-400 animate-pulse"></span>
                        <span class="text-slate-300">CORTE GEOLÓGICO - PERFURAÇÃO CINÉTICA PROFUNDA</span>
                    </div>
                    <div class="flex items-center gap-4 text-slate-400">
                        <span>Profundidade: <strong id="hud-depth" class="text-amber-400">12,450 m</strong></span>
                        <span>Temperatura: <strong id="hud-temp" class="text-rose-400">3,850 °C</strong></span>
                    </div>
                </div>

                <!-- Canvas Container -->
                <div class="relative w-full aspect-[4/3] bg-slate-950 rounded-xl overflow-hidden border border-slate-800 shadow-inner">
                    <canvas id="simCanvas" class="w-full h-full block"></canvas>
                    
                    <!-- HUD Instructions / Legend -->
                    <div class="absolute bottom-4 left-4 pointer-events-none bg-slate-900/80 backdrop-blur-md px-3 py-2 rounded-lg border border-amber-500/30 text-[11px] font-mono text-amber-300 space-y-1">
                        <div>⛏️ SAMS neutraliza a fadiga cíclica nas rochas densas</div>
                        <div>🔥 Jato de plasma MHD derrete e abre caminho geotérmico</div>
                    </div>

                    <!-- Fatigue Warning Banner -->
                    <div id="fatigue-banner" class="absolute top-4 inset-x-4 pointer-events-none hidden transition-all duration-300">
                        <div class="bg-rose-950/90 border border-rose-500 text-rose-200 px-4 py-2 rounded-xl text-xs font-mono font-bold flex items-center justify-center gap-2 animate-bounce">
                            <svg class="w-4 h-4 text-rose-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/></svg>
                            ALERTA: SAMS DESLIGADO! VIBRAÇÃO CÍCLICA CAUSANDO FRATURA ESTRESSE NA BROCA!
                        </div>
                    </div>
                </div>

                <!-- Quick Metrics Bar -->
                <div class="grid grid-cols-3 gap-3 mt-4 text-center font-mono">
                    <div class="bg-slate-900/60 p-2.5 rounded-xl border border-slate-800">
                        <div class="text-[10px] text-slate-400">Estabilidade da Broca</div>
                        <div id="metric-stability" class="text-sm font-bold text-amber-400">100.0%</div>
                    </div>
                    <div class="bg-slate-900/60 p-2.5 rounded-xl border border-slate-800">
                        <div class="text-[10px] text-slate-400">Temperatura da Broca</div>
                        <div id="metric-drill-temp" class="text-sm font-bold text-cyan-400">450 °C (Resfriado)</div>
                    </div>
                    <div class="bg-slate-900/60 p-2.5 rounded-xl border border-slate-800">
                        <div class="text-[10px] text-slate-400">Energia Geotérmica Coletada</div>
                        <div id="metric-energy" class="text-sm font-bold text-emerald-400">480 MW (Limpio)</div>
                    </div>
                </div>

            </div>
        </section>

        <!-- Right Sidebar: Telemetry & SAMS+MHD AI Console -->
        <section class="lg:col-span-3 flex flex-col gap-6">
            
            <!-- Geothermal Telemetry -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl">
                <h2 class="text-sm font-semibold tracking-wide text-amber-400 uppercase mb-4 flex items-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19v-6a2 2 0 00-2-2H5a2 2 0 00-2 2v6a2 2 0 002 2h2a2 2 0 002-2zm0 0V9a2 2 0 012-2h2a2 2 0 012 2v10m-6 0a2 2 0 002 2h2a2 2 0 002-2m0 0V5a2 2 0 012-2h2a2 2 0 012 2v14a2 2 0 01-2 2h-2a2 2 0 01-2-2z"/></svg>
                    Telemetria Geotérmica
                </h2>
                <div class="space-y-3 font-mono text-xs">
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Pressão Litostática</span>
                        <span class="text-cyan-400 font-bold">1.8 GPa</span>
                    </div>
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Frequência SAMS</span>
                        <span class="text-amber-400 font-bold">18.5 kHz</span>
                    </div>
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Fluxo de Plasma MHD</span>
                        <span class="text-emerald-400 font-bold">2,400 L/s</span>
                    </div>
                    <div class="flex justify-between items-center bg-slate-900/80 p-2.5 rounded-xl border border-slate-800">
                        <span class="text-slate-400">Turbinas de Conversão</span>
                        <span class="text-purple-400 font-bold">99.2% Eficiência</span>
                    </div>
                </div>
            </div>

            <!-- SAMS + MHD AI Console -->
            <div class="glass-panel rounded-2xl p-5 shadow-xl flex flex-col flex-1 min-h-[260px]">
                <h2 class="text-sm font-semibold tracking-wide text-amber-400 uppercase mb-3 flex items-center gap-2">
                    <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 9l3 3-3 3m5 0h3M5 20h14a2 2 0 002-2V6a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z"/></svg>
                    Console SAMS + MHD AI
                </h2>
                <div id="ai-console" class="flex-1 bg-slate-950/80 rounded-xl p-3 border border-slate-900 font-mono text-[11px] text-slate-300 space-y-1.5 overflow-y-auto max-h-[220px]">
                    <div class="text-slate-500">[00:00:01] Sistema de Perfuração Profunda SAMS+MHD ativado.</div>
                    <div class="text-amber-400">[00:00:03] SAMS isolando vibrações cíclicas contra rocha ultra-densa.</div>
                    <div class="text-cyan-400">[00:00:05] Jato de plasma MHD estabilizado a 12,500 K.</div>
                </div>
            </div>

        </section>

    </main>

    <!-- Footer -->
    <footer class="text-center py-4 text-xs text-slate-500 border-t border-slate-900 font-mono">
        SAMS (Smart Active Micro-Vibration Suppression) & MHD (Magnetohydrodynamic) &bull; Brocas Cinéticas de Perfuração v4.1
    </footer>

    <!-- JavaScript Simulation Engine -->
    <script>
        // --- Simulation State ---
        let state = {
            layer: 'crust', // 'crust', 'mantle', 'core'
            samsActive: true,
            plasmaPower: 85,
            drillDepth: 12450,
            drillIntegrity: 100,
            time: 0,
            burstActive: false
        };

        // DOM Elements
        const canvas = document.getElementById('simCanvas');
        const ctx = canvas.getContext('2d');
        const samsToggleEl = document.getElementById('samsToggle');
        const sysBadgeEl = document.getElementById('sys-badge');
        const fatigueBannerEl = document.getElementById('fatigue-banner');
        const hudDepthEl = document.getElementById('hud-depth');
        const hudTempEl = document.getElementById('hud-temp');
        const metricStabilityEl = document.getElementById('metric-stability');
        const integrityBadgeEl = document.getElementById('integrity-badge');
        const aiConsole = document.getElementById('ai-console');

        // Audio Helper
        let audioCtx = null;
        function initAudio() {
            if (!audioCtx) audioCtx = new (window.AudioContext || window.webkitAudioContext)();
        }

        function playBeep(freq = 440, type = 'sine', duration = 0.1) {
            try {
                initAudio();
                if (!audioCtx) return;
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.type = type;
                osc.frequency.value = freq;
                gain.gain.setValueAtTime(0.04, audioCtx.currentTime);
                gain.gain.exponentialRampToValueAtTime(0.0001, audioCtx.currentTime + duration);
                osc.connect(gain);
                gain.connect(audioCtx.destination);
                osc.start();
                osc.stop(audioCtx.currentTime + duration);
            } catch (e) {}
        }

        // Resize Canvas
        function resizeCanvas() {
            const rect = canvas.getBoundingClientRect();
            canvas.width = rect.width * window.devicePixelRatio;
            canvas.height = rect.height * window.devicePixelRatio;
            ctx.setTransform(window.devicePixelRatio, 0, 0, window.devicePixelRatio, 0, 0);
        }

        window.addEventListener('resize', resizeCanvas);

        // Control Handlers
        function setLayer(layer) {
            state.layer = layer;
            ['crust', 'mantle', 'core'].forEach(l => {
                const btn = document.getElementById(`layer-${l}`);
                if (l === layer) {
                    btn.className = "w-full text-left p-3 rounded-xl border border-amber-500/40 bg-amber-500/10 transition-all flex items-center justify-between group";
                } else {
                    btn.className = "w-full text-left p-3 rounded-xl border border-slate-700 bg-slate-900/60 transition-all hover:border-slate-500 flex items-center justify-between group";
                }
            });

            if (layer === 'crust') {
                state.drillDepth = 12450;
                logAI("Profundidade ajustada para a Crosta Terrestre (Granito denso).");
                playBeep(440, 'sine', 0.15);
            } else if (layer === 'mantle') {
                state.drillDepth = 420000;
                logAI("Profundidade ajustada para o Manto Superior (Peridotito fundido).");
                playBeep(520, 'triangle', 0.15);
            } else {
                state.drillDepth = 2900000;
                logAI("Profundidade ajustada para o Núcleo Terrestre (Ferro líquido e plasma puro).");
                playBeep(650, 'sawtooth', 0.2);
            }
        }

        function toggleSAMS() {
            state.samsActive = samsToggleEl.checked;
            if (state.samsActive) {
                sysBadgeEl.textContent = "ATIVO";
                sysBadgeEl.className = "px-2.5 py-0.5 rounded text-xs font-mono font-bold bg-amber-500/20 text-amber-300 border border-amber-500/40";
                fatigueBannerEl.classList.add('hidden');
                logAI("SAMS reativado: Fadiga cíclica e vibrações aniquiladas em 100%.");
                playBeep(880, 'sine', 0.2);
            } else {
                sysBadgeEl.textContent = "VULNERÁVEL";
                sysBadgeEl.className = "px-2.5 py-0.5 rounded text-xs font-mono font-bold bg-rose-500/20 text-rose-300 border border-rose-500/40";
                fatigueBannerEl.classList.remove('hidden');
                logAI("ALERTA: SAMS desativado! Fadiga cíclica destruindo a estrutura da broca!");
                playBeep(180, 'sawtooth', 0.3);
            }
        }

        function updatePlasma(val) {
            state.plasmaPower = parseInt(val);
            document.getElementById('plasma-val').textContent = val + '%';
        }

        function triggerPlasmaBurst() {
            state.burstActive = true;
            logAI("🔥 Explosão de plasma MHD disparada! Fusão instantânea de rochas a 15,000 K.");
            playBeep(1200, 'square', 0.3);
            setTimeout(() => { state.burstActive = false; }, 1500);
        }

        function recalibrateDrill() {
            logAI("🔄 Giroscópios piezoelétricos do SAMS recalibrados. Alinhamento perfeito.");
            playBeep(750, 'sine', 0.2);
        }

        function logAI(message) {
            const timeStr = new Date().toTimeString().split(' ')[0];
            const div = document.createElement('div');
            div.className = "text-slate-300";
            div.innerHTML = `<span class="text-slate-500">[${timeStr}]</span> ${message}`;
            aiConsole.appendChild(div);
            aiConsole.scrollTop = aiConsole.scrollHeight;
        }

        // --- Main Animation & Simulation Loop ---
        function updateSimulation() {
            state.time += 0.04;

            if (state.samsActive) {
                if (state.drillIntegrity < 100) state.drillIntegrity = Math.min(100, state.drillIntegrity + 0.2);
            } else {
                state.drillIntegrity = Math.max(12, state.drillIntegrity - 0.35);
            }

            drawCanvas();
            requestAnimationFrame(updateSimulation);
        }

        function drawCanvas() {
            const width = canvas.clientWidth;
            const height = canvas.clientHeight;
            
            ctx.clearRect(0, 0, width, height);

            // Draw strata background based on layer
            let bgGrad = ctx.createLinearGradient(0, 0, 0, height);
            if (state.layer === 'crust') {
                bgGrad.addColorStop(0, '#111827');
                bgGrad.addColorStop(1, '#33291e'); // rock brown
            } else if (state.layer === 'mantle') {
                bgGrad.addColorStop(0, '#33291e');
                bgGrad.addColorStop(1, '#7c2d12'); // magma red/orange
            } else {
                bgGrad.addColorStop(0, '#7c2d12');
                bgGrad.addColorStop(1, '#b91c1c'); // molten core white/red
            }
            ctx.fillStyle = bgGrad;
            ctx.fillRect(0, 0, width, height);

            // Draw rock texture lines and strata layers
            ctx.strokeStyle = 'rgba(255, 255, 255, 0.05)';
            ctx.lineWidth = 1;
            for (let y = 0; y < height; y += 30) {
                ctx.beginPath();
                ctx.moveTo(0, y + Math.sin(state.time + y) * 5);
                ctx.lineTo(width, y + Math.cos(state.time + y) * 5);
                ctx.stroke();
            }

            // Draw Borehole shaft in the center
            const shaftWidth = 50;
            const shaftX = (width - shaftWidth) / 2;
            ctx.fillStyle = '#020617';
            ctx.fillRect(shaftX, 0, shaftWidth, height);

            // Draw Drill Rig at the top surface
            ctx.fillStyle = '#1e293b';
            ctx.strokeStyle = '#f59e0b';
            ctx.lineWidth = 2;
            ctx.fillRect(shaftX - 35, 0, shaftWidth + 70, 45);
            ctx.strokeRect(shaftX - 35, 0, shaftWidth + 70, 45);

            // Drill Head Position (oscillating or shaking based on SAMS)
            let drillShake = 0;
            if (!state.samsActive) {
                drillShake = (Math.random() - 0.5) * 16;
            }

            const drillHeadX = shaftX + shaftWidth / 2 + drillShake;
            const drillHeadY = height * 0.65;

            // Draw Drill String (Rotating segmented rods)
            ctx.strokeStyle = '#64748b';
            ctx.lineWidth = 8;
            ctx.beginPath();
            ctx.moveTo(shaftX + shaftWidth / 2, 45);
            ctx.lineTo(drillHeadX, drillHeadY);
            ctx.stroke();

            // Draw Advanced Kinetic Drill Bit
            ctx.save();
            ctx.translate(drillHeadX, drillHeadY);

            ctx.fillStyle = '#0f172a';
            ctx.strokeStyle = '#f59e0b';
            ctx.lineWidth = 3;
            ctx.beginPath();
            ctx.moveTo(-18, -25);
            ctx.lineTo(18, -25);
            ctx.lineTo(25, 10);
            ctx.lineTo(0, 35);
            ctx.lineTo(-25, 10);
            ctx.closePath();
            ctx.fill();
            ctx.stroke();

            // MHD Plasma Thermal Jet at the tip
            const plasmaIntensity = (state.plasmaPower / 100) * (state.burstActive ? 2.0 : 1.0);
            const plasmaGrad = ctx.createRadialGradient(0, 35, 2, 0, 55, 30);
            plasmaGrad.addColorStop(0, '#fef08a');
            plasmaGrad.addColorStop(0.5, '#06b6d4');
            plasmaGrad.addColorStop(1, 'rgba(6, 182, 212, 0)');

            ctx.fillStyle = plasmaGrad;
            ctx.beginPath();
            ctx.arc(0, 45, 25 * plasmaIntensity, 0, Math.PI * 2);
            ctx.fill();

            // Spark particles flying off
            for (let i = 0; i < 8; i++) {
                const angle = Math.random() * Math.PI;
                const dist = 15 + Math.random() * 25;
                ctx.fillStyle = Math.random() > 0.5 ? '#f59e0b' : '#38bdf8';
                ctx.fillRect(Math.cos(angle) * dist, 35 + Math.sin(angle) * dist, 3, 3);
            }

            ctx.restore();

            // Update UI telemetry badges dynamically
            if (state.samsActive) {
                metricStabilityElement = 100.0;
                metricStabilityEl.textContent = "100.0%";
                metricStabilityEl.className = "text-sm font-bold text-amber-400";
                integrityBadgeEl.textContent = "100.0% (Blindado)";
                integrityBadgeEl.className = "text-emerald-400";
            } else {
                metricStabilityEl.textContent = Math.round(state.drillIntegrity) + "% (Vibração!)";
                metricStabilityEl.className = "text-sm font-bold text-rose-400";
                integrityBadgeEl.textContent = Math.round(state.drillIntegrity) + "% (Crítico)";
                integrityBadgeEl.className = "text-rose-400";
            }

            if (state.layer === 'crust') {
                hudTempEl.textContent = "450 °C";
            } else if (state.layer === 'mantle') {
                hudTempEl.textContent = "2,400 °C";
            } else {
                hudTempEl.textContent = "5,800 °C";
            }

            hudDepthEl.textContent = state.drillDepth.toLocaleString() + " m";
        }

        // Initialize on load
        window.onload = function() {
            resizeCanvas();
            updateSimulation();
        };
    </script>
</body>
</html>
