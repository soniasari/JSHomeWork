<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema EDV - Previsualizador de Colores</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap');
        
        body { 
            font-family: 'Inter', sans-serif; 
            background-color: #f1f5f9;
        }

        .transition-all-custom { 
            transition: all 0.3s ease-in-out; 
        }

        .edv-shadow {
            box-shadow: 0 10px 50px -12px rgba(0, 0, 0, 0.25);
        }

        #palette-grid::-webkit-scrollbar { width: 4px; }
        #palette-grid::-webkit-scrollbar-thumb { background: #cbd5e1; border-radius: 10px; }

        /* Animación del menú */
        .submenu-show {
            display: block !important;
            animation: fadeIn 0.2s ease-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-5px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Hover dinámico para los botones de navegación */
        .menu-item-hover:hover {
            background-color: rgba(0,0,0,0.15);
        }
    </style>
</head>
<body class="p-4 flex flex-col items-center">

    <!-- Panel de Control Superior -->
    <div class="mb-6 w-full max-w-7xl bg-white p-5 rounded-2xl shadow-sm border border-gray-200">
        <div class="flex items-center justify-between mb-4 px-2">
            <span class="text-[10px] uppercase font-extrabold text-slate-400 tracking-[0.2em] flex items-center gap-2">
                <i data-lucide="palette" class="w-4 h-4"></i> Selector de Combinaciones de Menú
            </span>
            <div class="flex gap-2">
                <div class="w-3 h-3 rounded-full" style="background-color: #95C11F;" title="Verde Lima"></div>
                <div class="w-3 h-3 rounded-full" style="background-color: #203764;" title="Azul Marino"></div>
                <div class="w-3 h-3 rounded-full" style="background-color: #9D9D9C;" title="Gris"></div>
                <div class="w-3 h-3 rounded-full" style="background-color: #69B7C6;" title="Celeste"></div>
                <div class="w-3 h-3 rounded-full" style="background-color: #177090;" title="Petróleo"></div>
            </div>
        </div>
        <div id="palette-grid" class="grid grid-cols-2 sm:grid-cols-4 md:grid-cols-6 lg:grid-cols-8 gap-2 max-h-[160px] overflow-y-auto">
            <!-- Botones generados por JS -->
        </div>
    </div>

    <!-- Contenedor del Sistema -->
    <div class="w-full max-w-7xl bg-white edv-shadow rounded-lg overflow-hidden flex flex-col border border-gray-200 min-h-[700px]">
        
        <!-- Top Bar (FIJO PETRÓLEO) -->
        <div id="top-bar" class="h-12 flex items-center justify-between px-6 text-white text-[11px] font-medium" style="background-color: #177090;">
            <div class="flex items-center gap-6">
                <span>Usuario <span class="font-bold">PPRUEBA</span> Tipo de Institucion <span class="font-bold">EDV</span></span>
            </div>
            <div class="flex items-center gap-8">
                <span>Institución <span class="font-bold uppercase">Entidad de Depósito de Valores de Bolivia S.A.</span></span>
                <!-- Logo EDV sin icono -->
                <div class="flex items-center gap-2 border-l border-white/20 pl-4">
                   <div class="flex flex-col items-end leading-none">
                        <span class="text-[18px] font-black tracking-tighter">EDV</span>
                        <span class="text-[6px] uppercase opacity-60 tracking-[0.2em]">Bolivia</span>
                   </div>
                </div>
            </div>
        </div>

        <!-- Nav Bar (DINÁMICO) -->
        <div id="nav-bar" class="h-10 flex items-center px-4 transition-all-custom shadow-inner">
            <div class="flex h-full items-center relative">
                <!-- Item con Submenú -->
                <button onclick="toggleMenu(event)" id="btn-fondos" class="h-full px-8 text-white text-[12px] font-semibold menu-item-hover transition-colors flex items-center gap-2">
                    Fondos <i data-lucide="chevron-down" id="arrow" class="w-3 h-3 transition-transform"></i>
                </button>

                <!-- El Submenú -->
                <div id="dropdown" class="hidden absolute top-full left-0 w-64 shadow-xl z-[100] transition-all-custom border-t border-black/10">
                    <div class="p-1">
                        <div class="flex items-center gap-3 p-3 menu-item-hover text-white cursor-pointer rounded-md transition-colors">
                            <i data-lucide="folder" class="w-4 h-4 opacity-70"></i>
                            <span class="text-[10px] font-bold uppercase">Administración de Carteras</span>
                        </div>
                        <div class="flex items-center gap-3 p-3 menu-item-hover text-white cursor-pointer rounded-md transition-colors">
                            <i data-lucide="file-text" class="w-4 h-4 opacity-70"></i>
                            <span class="text-[10px] font-bold uppercase">Reportes de Fondos</span>
                        </div>
                        <div class="flex items-center gap-3 p-3 menu-item-hover text-white cursor-pointer rounded-md transition-colors">
                            <i data-lucide="database" class="w-4 h-4 opacity-70"></i>
                            <span class="text-[10px] font-bold uppercase">Saldos y Movimientos</span>
                        </div>
                    </div>
                </div>

                <button class="h-full px-8 text-white text-[12px] font-semibold menu-item-hover transition-colors">Liquidacion</button>
                <button class="h-full px-8 text-white text-[12px] font-semibold menu-item-hover transition-colors">Corporativos</button>
                <button class="h-full px-8 text-white text-[12px] font-semibold menu-item-hover transition-colors">Servicios</button>
                <button class="h-full px-8 text-white text-[12px] font-semibold menu-item-hover transition-colors">Contabilidad</button>
                <button class="h-full px-8 text-white text-[12px] font-semibold menu-item-hover transition-colors">Derechos Economicos</button>
            </div>
        </div>

        <!-- Área de Trabajo -->
        <div id="workspace" class="flex-grow relative flex flex-col items-center justify-center bg-white">
            <div class="z-10 text-center">
                <div class="flex items-center justify-center gap-3 mb-6">
                    <div class="h-[1px] w-12 bg-slate-200"></div>
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-[0.4em]">Interfaz Corporativa</span>
                    <div class="h-[1px] w-12 bg-slate-200"></div>
                </div>
                <h1 id="main-title" class="text-7xl font-black text-slate-800 tracking-tighter mb-2 uppercase">
                    EDV <span class="font-light text-slate-300 tracking-normal">Direct</span>
                </h1>
                <div id="accent-line" class="h-1.5 w-24 mx-auto rounded-full mb-8 transition-all-custom"></div>
                
                <div class="bg-slate-50 border border-slate-100 p-4 rounded-xl inline-block shadow-sm">
                    <p class="text-[11px] text-slate-500 font-bold uppercase tracking-wider">
                        Color Barra Menú: <span id="current-p-name" class="font-extrabold">Gris Ejecutivo</span>
                    </p>
                </div>
            </div>
        </div>

        <!-- Footer (FIJO PETRÓLEO) -->
        <div id="footer-bar" class="h-10 flex items-center justify-between px-8 text-white text-[10px] font-bold" style="background-color: #177090;">
            <div class="flex items-center gap-3 uppercase tracking-widest">
                <div class="w-2 h-2 bg-white rounded-full animate-pulse"></div>
                SISTEMA: ESTABLE
            </div>
            <div class="uppercase tracking-[0.2em] opacity-80">
                Versión 3.1.0 • Entidad de Depósito de Valores de Bolivia
            </div>
        </div>
    </div>

    <script>
        // Paletas enfocadas en el Menú y Submenú
        const palettes = [
            { name: "Gris Ejecutivo", nav: "#9D9D9C", sub: "#9D9D9C", accent: "#95C11F" },
            { name: "Azul Marino", nav: "#203764", sub: "#203764", accent: "#95C11F" },
            { name: "Verde Lima", nav: "#95C11F", sub: "#95C11F", accent: "#203764" },
            { name: "Celeste Tech", nav: "#69B7C6", sub: "#69B7C6", accent: "#177090" },
            { name: "Petróleo Menú", nav: "#177090", sub: "#177090", accent: "#95C11F" },
            { name: "Marino & Celeste", nav: "#203764", sub: "#69B7C6", accent: "#95C11F" },
            { name: "Gris & Marino", nav: "#9D9D9C", sub: "#203764", accent: "#177090" },
            { name: "Petróleo & Lima", nav: "#177090", sub: "#95C11F", accent: "#203764" }
        ];

        function applyPalette(index, btn) {
            const p = palettes[index];
            
            const navBar = document.getElementById('nav-bar');
            const dropdown = document.getElementById('dropdown');
            const accentLine = document.getElementById('accent-line');
            const currentName = document.getElementById('current-p-name');

            navBar.style.backgroundColor = p.nav;
            dropdown.style.backgroundColor = p.sub;
            accentLine.style.backgroundColor = p.accent;
            currentName.innerText = p.name;
            currentName.style.color = p.nav;
            
            document.querySelectorAll('.palette-btn').forEach(b => {
                b.classList.remove('border-slate-800', 'bg-slate-800', 'text-white', 'scale-105');
                b.classList.add('border-gray-100', 'bg-white', 'text-slate-500');
            });
            btn.classList.add('border-slate-800', 'bg-slate-800', 'text-white', 'scale-105');
            btn.classList.remove('bg-white', 'text-slate-500');
        }

        function toggleMenu(e) {
            e.stopPropagation();
            const menu = document.getElementById('dropdown');
            const arrow = document.getElementById('arrow');
            const isHidden = menu.classList.contains('hidden');

            if(isHidden) {
                menu.classList.remove('hidden');
                menu.classList.add('submenu-show');
                arrow.style.transform = 'rotate(180deg)';
            } else {
                menu.classList.add('hidden');
                menu.classList.remove('submenu-show');
                arrow.style.transform = 'rotate(0deg)';
            }
        }

        document.addEventListener('click', () => {
            document.getElementById('dropdown').classList.add('hidden');
            document.getElementById('arrow').style.transform = 'rotate(0deg)';
        });

        const grid = document.getElementById('palette-grid');
        palettes.forEach((p, index) => {
            const btn = document.createElement('button');
            btn.className = "palette-btn px-2 py-2.5 rounded-xl text-[9px] font-bold uppercase tracking-tighter border transition-all-custom shadow-sm hover:shadow-md bg-white text-slate-500 border-gray-100";
            btn.innerText = p.name;
            btn.onclick = (e) => applyPalette(index, e.currentTarget);
            grid.appendChild(btn);
            
            if(index === 0) applyPalette(0, btn);
        });

        window.onload = () => lucide.createIcons();
    </script>
</body>
</html>
