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
                <i data-lucide="palette" class="w-4 h-4"></i> Selector de Tonos Plomo y Transparencias
            </span>
            <div class="flex gap-2">
                <div class="w-3 h-3 rounded-full" style="background-color: #D1D5DB;" title="Plomo Claro"></div>
                <div class="w-3 h-3 rounded-full" style="background-color: #9D9D9C;" title="Plomo Medio"></div>
                <div class="w-3 h-3 rounded-full" style="background-color: #4B5563;" title="Plomo Oscuro"></div>
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

                <!-- El Submenú con Transparencia -->
                <div id="dropdown" class="hidden absolute top-full left-0 w-72 shadow-2xl z-[100] transition-all-custom border-t border-black/5 backdrop-blur-sm">
                    <div class="p-1.5">
                        <div class="flex items-center gap-3 p-3.5 menu-item-hover text-white cursor-pointer rounded-lg transition-colors">
                            <i data-lucide="folder" class="w-4 h-4 opacity-80"></i>
                            <span class="text-[10px] font-bold uppercase tracking-tight">Administración de Carteras</span>
                        </div>
                        <div class="flex items-center gap-3 p-3.5 menu-item-hover text-white cursor-pointer rounded-lg transition-colors">
                            <i data-lucide="file-text" class="w-4 h-4 opacity-80"></i>
                            <span class="text-[10px] font-bold uppercase tracking-tight">Reportes de Fondos</span>
                        </div>
                        <div class="flex items-center gap-3 p-3.5 menu-item-hover text-white cursor-pointer rounded-lg transition-colors">
                            <i data-lucide="database" class="w-4 h-4 opacity-80"></i>
                            <span class="text-[10px] font-bold uppercase tracking-tight">Saldos y Movimientos</span>
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
        <div id="workspace" class="flex-grow relative flex flex-col items-center justify-center bg-gray-50/50">
            <!-- Marca de agua sutil para notar la transparencia -->
            <div class="absolute top-10 left-10 opacity-[0.05] pointer-events-none">
                <h2 class="text-9xl font-black">EDV</h2>
            </div>
            
            <div class="z-10 text-center">
                <div class="flex items-center justify-center gap-3 mb-6">
                    <div class="h-[1px] w-12 bg-slate-200"></div>
                    <span class="text-[10px] font-bold text-slate-400 uppercase tracking-[0.4em]">Configuración de Estilos</span>
                    <div class="h-[1px] w-12 bg-slate-200"></div>
                </div>
                <h1 id="main-title" class="text-7xl font-black text-slate-800 tracking-tighter mb-2 uppercase">
                    EDV <span class="font-light text-slate-400 tracking-normal">Direct</span>
                </h1>
                <div id="accent-line" class="h-1.5 w-24 mx-auto rounded-full mb-8 transition-all-custom"></div>
                
                <div class="bg-white border border-slate-200 p-6 rounded-2xl inline-block shadow-sm">
                    <p class="text-[11px] text-slate-400 font-bold uppercase tracking-widest mb-1">Submenú actual</p>
                    <p id="current-p-name" class="text-xl font-black text-slate-800 uppercase tracking-tighter">Plomo Original</p>
                    <div id="hex-label" class="mt-2 text-[9px] font-mono text-slate-400 bg-slate-100 py-1 px-2 rounded">rgba(157, 157, 156, 0.95)</div>
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
        // Paletas con enfoque en tonos Plomo y distintos niveles de transparencia (rgba)
        const palettes = [
            { name: "Plomo Base", nav: "#9D9D9C", sub: "rgba(157, 157, 156, 0.95)", accent: "#95C11F" },
            { name: "Plomo Cristal", nav: "#9D9D9C", sub: "rgba(157, 157, 156, 0.75)", accent: "#69B7C6" },
            { name: "Gris Nube", nav: "#D1D5DB", sub: "rgba(209, 213, 219, 0.90)", accent: "#177090" },
            { name: "Gris Humo", nav: "#4B5563", sub: "rgba(75, 85, 99, 0.85)", accent: "#95C11F" },
            { name: "Gris Pizarra", nav: "#374151", sub: "rgba(55, 65, 81, 0.92)", accent: "#69B7C6" },
            { name: "Plomo Hielo", nav: "#9D9D9C", sub: "rgba(241, 245, 249, 0.98)", accent: "#203764", text: "#475569" },
            { name: "Plomo & Celeste", nav: "#9D9D9C", sub: "rgba(105, 183, 198, 0.90)", accent: "#177090" },
            { name: "Gris Profundo", nav: "#1F2937", sub: "rgba(31, 41, 55, 0.95)", accent: "#95C11F" }
        ];

        function applyPalette(index, btn) {
            const p = palettes[index];
            
            const navBar = document.getElementById('nav-bar');
            const dropdown = document.getElementById('dropdown');
            const accentLine = document.getElementById('accent-line');
            const currentName = document.getElementById('current-p-name');
            const hexLabel = document.getElementById('hex-label');

            navBar.style.backgroundColor = p.nav;
            dropdown.style.backgroundColor = p.sub;
            accentLine.style.backgroundColor = p.accent;
            currentName.innerText = p.name;
            hexLabel.innerText = p.sub;
            
            // Cambiar color de texto en el submenú si es muy claro
            const subItems = dropdown.querySelectorAll('.menu-item-hover span');
            const subIcons = dropdown.querySelectorAll('.menu-item-hover i');
            const textColor = p.text || "white";
            
            subItems.forEach(s => s.style.color = textColor);
            subIcons.forEach(i => i.style.color = textColor);

            // Gestionar botones del panel
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
