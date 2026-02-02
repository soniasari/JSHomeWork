<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema EDV - 21 Paletas de Colores</title>
    <!-- Carga de Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Carga de Lucide Icons -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700;900&display=swap');
        
        body { 
            font-family: 'Inter', sans-serif; 
            margin: 0;
            padding: 0;
            background-color: #e5e7eb;
        }

        .transition-all { transition: all 0.4s ease-in-out; }
        .hidden { display: none; }
        .nav-item { white-space: nowrap; }
        
        /* Estilo para el grid de botones */
        #palette-grid {
            max-height: 300px;
            overflow-y: auto;
            padding-right: 5px;
        }
        #palette-grid::-webkit-scrollbar {
            width: 4px;
        }
        #palette-grid::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 10px;
        }
    </style>
</head>
<body class="p-4 md:p-8 flex flex-col items-center min-h-screen">

    <!-- Panel de Selección de Temas (Expandido a 21) -->
    <div class="mb-8 w-full max-w-6xl bg-white p-6 rounded-3xl shadow-lg border border-gray-100">
        <div class="flex items-center justify-between mb-4 px-2">
            <span class="text-[11px] uppercase font-black text-gray-400 tracking-widest">Panel de Configuración Visual (21 Combinaciones)</span>
            <span class="text-[10px] text-blue-500 font-bold px-2 py-1 bg-blue-50 rounded-lg">EDV Corporativo</span>
        </div>
        <div id="palette-grid" class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-7 gap-3">
            <!-- Botones generados por JavaScript -->
        </div>
    </div>

    <!-- Contenedor del Mockup -->
    <div class="w-full max-w-6xl bg-slate-900 rounded-[2.5rem] p-2 pb-0 shadow-2xl overflow-hidden border border-black/10">
        
        <!-- Cabecera del Sistema -->
        <header id="main-header" class="transition-all relative z-50 rounded-[2rem] text-white">
            <!-- Barra de Información Superior -->
            <div class="px-8 py-3 flex flex-wrap justify-between items-center text-[10px] border-b border-white/10 opacity-80">
                <div class="flex items-center gap-4">
                    <span class="flex items-center gap-1.5"><i data-lucide="globe" class="w-3.5 h-3.5"></i> PRODUCCIÓN</span>
                    <span class="h-3 w-px bg-white/20"></span>
                    <span class="font-medium tracking-tighter">TERMINAL CENTRAL: 082</span>
                </div>
                <div class="flex gap-6 font-bold uppercase tracking-wider">
                    <span>USUARIO: <span class="font-normal opacity-70">PPRUEBA</span></span>
                    <span>INST: <span class="font-normal opacity-70">EDV BOLIVIA S.A.</span></span>
                </div>
            </div>

            <!-- Menú de Navegación Principal -->
            <div class="px-6 flex items-center justify-between min-h-[64px]">
                <nav class="flex h-full">
                    <!-- Fondos con Submenú -->
                    <div class="relative h-full flex items-center">
                        <button onclick="toggleSubmenu(event)" class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest flex items-center gap-2 hover:bg-black/10 transition-colors">
                            Fondos <i data-lucide="chevron-down" id="arrow-icon" class="w-4 h-4 transition-transform"></i>
                        </button>
                        
                        <!-- Submenú Desplegable -->
                        <div id="submenu" class="hidden absolute top-full left-0 w-72 shadow-2xl rounded-b-2xl overflow-hidden border-t border-white/10 p-2 mt-0 z-[100]">
                            <div class="submenu-item flex items-center gap-4 p-4 hover:bg-white/10 rounded-xl cursor-pointer transition-colors">
                                <i data-lucide="folder" class="w-4 h-4 accent-icon"></i> 
                                <span class="text-[10px] font-bold uppercase">Administración de Carteras</span>
                            </div>
                            <div class="submenu-item flex items-center gap-4 p-4 hover:bg-white/10 rounded-xl cursor-pointer transition-colors">
                                <i data-lucide="file-text" class="w-4 h-4 accent-icon"></i> 
                                <span class="text-[10px] font-bold uppercase">Reportes de Fondos</span>
                            </div>
                            <div class="submenu-item flex items-center gap-4 p-4 hover:bg-white/10 rounded-xl cursor-pointer transition-colors">
                                <i data-lucide="database" class="w-4 h-4 accent-icon"></i> 
                                <span class="text-[10px] font-bold uppercase">Saldos y Movimientos</span>
                            </div>
                        </div>
                    </div>

                    <!-- Otros Items -->
                    <button class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest hover:bg-black/10 transition-colors">Liquidación</button>
                    <button class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest hover:bg-black/10 transition-colors">Corporativos</button>
                    <button class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest hover:bg-black/10 transition-colors hidden lg:block">Servicios</button>
                </nav>

                <!-- Iconos de Acción -->
                <div class="flex gap-6 px-6 items-center border-l border-white/10 ml-4">
                    <i data-lucide="settings" class="w-5 h-5 cursor-pointer opacity-70 hover:opacity-100 hover:rotate-90 transition-all"></i>
                    <i data-lucide="user" class="w-5 h-5 cursor-pointer opacity-70 hover:opacity-100"></i>
                    <div class="h-8 w-px bg-white/10 mx-2"></div>
                    <i data-lucide="log-out" class="w-5 h-5 cursor-pointer text-red-400 hover:scale-110 transition-transform"></i>
                </div>
            </div>
        </header>

        <!-- Área de Contenido Principal -->
        <div id="content-area" class="h-[520px] relative transition-all flex flex-col items-center justify-center p-12 overflow-hidden bg-white">
            <!-- Marca de Agua -->
            <div class="absolute opacity-[0.03] pointer-events-none transform -rotate-12 scale-[3]">
                <i data-lucide="landmark" class="w-64 h-64 text-slate-900"></i>
            </div>

            <div class="z-10 text-center max-w-2xl bg-white/40 backdrop-blur-md p-12 rounded-[3rem] border border-white/60 shadow-sm">
                <h1 class="text-5xl font-black text-slate-800 mb-4 tracking-tighter uppercase">
                    Core <span class="font-light text-slate-400">Bancario</span>
                </h1>
                <div id="accent-line" class="h-2 w-20 mx-auto mb-10 rounded-full"></div>
                <p class="text-slate-500 text-base font-medium leading-relaxed max-w-md mx-auto">
                    Panel de control operativo de valores. Seleccione una paleta de colores arriba para previsualizar la interfaz.
                </p>
            </div>

            <!-- Pie de Página -->
            <div id="bottom-bar" class="absolute bottom-0 left-0 w-full h-16 transition-all flex items-center justify-between px-12 text-white">
                <div class="flex items-center gap-3">
                    <div class="w-2.5 h-2.5 rounded-full bg-white animate-pulse"></div>
                    <span class="text-[10px] font-black uppercase tracking-[0.3em]">Sistema: Estable</span>
                </div>
                <span class="text-[9px] font-bold tracking-widest opacity-60 uppercase">VERSIÓN 3.1.0 • EDV BOLIVIA</span>
            </div>
        </div>
    </div>

    <script>
        // Paletas de Colores (21 variantes ahora)
        const palettes = {
            original: { name: "Original Imagen", header: "#177090", dropdown: "#203764", content: "#f4f1ea", bottom: "#177090", accent: "#95c11f", text: "white" },
            marino: { name: "Marino Premium", header: "#203764", dropdown: "#1a2d52", content: "#ffffff", bottom: "#203764", accent: "#95c11f", text: "white" },
            tech: { name: "Tech Celeste", header: "#69b7c6", dropdown: "#177090", content: "#f8fafc", bottom: "#177090", accent: "#203764", text: "white" },
            lima: { name: "Lima Energy", header: "#95c11f", dropdown: "#203764", content: "#ffffff", bottom: "#177090", accent: "#203764", text: "white" },
            gris: { name: "Gris Ejecutivo", header: "#9d9d9c", dropdown: "#177090", content: "#f9fafb", bottom: "#203764", accent: "#95c11f", text: "white" },
            petroleo: { name: "Petróleo Deep", header: "#177090", dropdown: "#0c3a4d", content: "#f8fafc", bottom: "#9d9d9c", accent: "#95c11f", text: "white" },
            contraste: { name: "High Contrast", header: "#203764", dropdown: "#69b7c6", content: "#ffffff", bottom: "#95c11f", accent: "#177090", text: "white" },
            minimal: { name: "Minimal Sky", header: "#f8fafc", dropdown: "#ffffff", content: "#ffffff", bottom: "#69b7c6", accent: "#177090", text: "#203764" },
            forest: { name: "Forest Night", header: "#203764", dropdown: "#9d9d9c", content: "#f1f5f9", bottom: "#177090", accent: "#95c11f", text: "white" },
            monocromo: { name: "Monocromo+", header: "#9d9d9c", dropdown: "#69b7c6", content: "#ffffff", bottom: "#9d9d9c", accent: "#203764", text: "white" },
            
            marino_suave: { name: "Marino Suave", header: "#203764", dropdown: "#177090", content: "#f1f5f9", bottom: "#69b7c6", accent: "#95c11f", text: "white" },
            petroleo_gris: { name: "Petróleo & Gris", header: "#177090", dropdown: "#9d9d9c", content: "#ffffff", bottom: "#203764", accent: "#69b7c6", text: "white" },
            lima_tech: { name: "Lima Tech", header: "#334155", dropdown: "#203764", content: "#f8fafc", bottom: "#177090", accent: "#95c11f", text: "white" },
            cielo_profundo: { name: "Cielo Profundo", header: "#69b7c6", dropdown: "#203764", content: "#ffffff", bottom: "#203764", accent: "#177090", text: "white" },
            corp_mix: { name: "Corporativo Mix", header: "#177090", dropdown: "#203764", content: "#f4f1ea", bottom: "#95c11f", accent: "#203764", text: "white" },

            bloque_marino: { name: "Bloque Marino", header: "#203764", dropdown: "#177090", content: "#ffffff", bottom: "#203764", accent: "#95c11f", text: "white" },
            bloque_petroleo: { name: "Bloque Petróleo", header: "#177090", dropdown: "#203764", content: "#f1f5f9", bottom: "#177090", accent: "#95c11f", text: "white" },
            bloque_gris: { name: "Bloque Gris Pro", header: "#334155", dropdown: "#177090", content: "#f8fafc", bottom: "#334155", accent: "#69b7c6", text: "white" },

            // 3 NUEVAS PALETAS SOLICITADAS (HEADER Y FOOTER IGUALES CON COLORES ESPECÍFICOS)
            bloque_celeste: { name: "Bloque Celeste Tech", header: "#69b7c6", dropdown: "#203764", content: "#ffffff", bottom: "#69b7c6", accent: "#95c11f", text: "white" },
            bloque_lima: { name: "Bloque Verde Lima", header: "#95c11f", dropdown: "#177090", content: "#ffffff", bottom: "#95c11f", accent: "#203764", text: "white" },
            duo_energetico: { name: "Dúo Energético", header: "#203764", dropdown: "#69b7c6", content: "#f1f5f9", bottom: "#203764", accent: "#95c11f", text: "white" }
        };

        function applyPalette(key, btnElement) {
            const p = palettes[key];
            
            const header = document.getElementById('main-header');
            const content = document.getElementById('content-area');
            const bottom = document.getElementById('bottom-bar');
            const accentLine = document.getElementById('accent-line');
            const dropdown = document.getElementById('submenu');
            const accentIcons = document.querySelectorAll('.accent-icon');

            header.style.backgroundColor = p.header;
            header.style.color = p.text;
            content.style.backgroundColor = p.content;
            bottom.style.backgroundColor = p.bottom;
            accentLine.style.backgroundColor = p.accent;
            dropdown.style.backgroundColor = p.dropdown;
            dropdown.style.color = p.text;

            accentIcons.forEach(icon => icon.style.color = p.accent);

            document.querySelectorAll('.palette-btn').forEach(btn => {
                btn.classList.remove('bg-slate-800', 'text-white', 'border-slate-800', 'scale-105');
                btn.classList.add('bg-white', 'text-gray-500', 'border-gray-100');
            });
            
            if (btnElement) {
                btnElement.classList.add('bg-slate-800', 'text-white', 'border-slate-800', 'scale-105');
                btnElement.classList.remove('bg-white', 'text-gray-500');
            }
        }

        function toggleSubmenu(e) {
            e.stopPropagation();
            const submenu = document.getElementById('submenu');
            const arrow = document.getElementById('arrow-icon');
            const isHidden = submenu.classList.contains('hidden');
            
            if (isHidden) {
                submenu.classList.remove('hidden');
                arrow.style.transform = 'rotate(180deg)';
            } else {
                submenu.classList.add('hidden');
                arrow.style.transform = 'rotate(0deg)';
            }
        }

        document.addEventListener('click', () => {
            const submenu = document.getElementById('submenu');
            const arrow = document.getElementById('arrow-icon');
            if (submenu && !submenu.classList.contains('hidden')) {
                submenu.classList.add('hidden');
                arrow.style.transform = 'rotate(0deg)';
            }
        });

        const grid = document.getElementById('palette-grid');
        Object.keys(palettes).forEach(key => {
            const btn = document.createElement('button');
            btn.innerText = palettes[key].name;
            btn.className = `palette-btn px-3 py-3 rounded-2xl text-[10px] font-bold transition-all uppercase tracking-tighter border shadow-sm hover:shadow-md`;
            btn.onclick = (e) => applyPalette(key, e.currentTarget);
            grid.appendChild(btn);
            
            if(key === 'original') {
                applyPalette(key, btn);
            }
        });

        window.onload = () => {
            if (typeof lucide !== 'undefined') {
                lucide.createIcons();
            }
        };
    </script>
</body>
</html>
