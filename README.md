<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mockup Sistema EDV - Paletas de Colores</title>
    <!-- Tailwind CSS para los estilos -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Lucide Icons para los iconos -->
    <script src="https://unpkg.com/lucide@latest"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;700;900&display=swap');
        body { font-family: 'Inter', sans-serif; }
        .no-scrollbar::-webkit-scrollbar { display: none; }
        .transition-all { transition: all 0.5s ease-in-out; }
    </style>
</head>
<body class="bg-gray-200 p-6 flex flex-col items-center min-h-screen">

    <!-- Panel de Control (Tabs) -->
    <div class="mb-8 w-full max-w-6xl bg-white/90 backdrop-blur p-4 rounded-2xl shadow-xl border border-white">
        <div class="flex items-center justify-between mb-4 px-2">
            <span class="text-[11px] uppercase font-black text-gray-400 tracking-[0.2em]">Configuración de Interfaz (10 Combinaciones)</span>
        </div>
        <div id="palette-grid" class="grid grid-cols-2 md:grid-cols-5 gap-2">
            <!-- Los botones se generarán con JS -->
        </div>
    </div>

    <!-- Mockup del Sistema -->
    <div class="w-full max-w-6xl bg-[#0f172a] rounded-t-[2rem] p-2 pb-0 shadow-2xl overflow-hidden">
        
        <!-- Cabecera -->
        <header id="main-header" class="transition-all relative z-50 rounded-t-[1.6rem] text-white">
            <!-- Barra Superior -->
            <div class="px-8 py-2.5 flex justify-between items-center text-[10px] border-b border-black/5 opacity-75">
                <div class="flex items-center gap-4">
                    <span class="flex items-center gap-1.5"><i data-lucide="globe" class="w-3 h-3"></i> Entorno Producción</span>
                    <span class="h-3 w-px bg-current opacity-20"></span>
                    <span class="italic">Terminal 082</span>
                </div>
                <div class="flex gap-6 font-bold uppercase">
                    <span>Usuario: <span class="opacity-70 font-normal">PPRUEBA</span></span>
                    <span>Inst: <span class="opacity-70 font-normal">EDV BOLIVIA S.A.</span></span>
                </div>
            </div>

            <!-- Navegación -->
            <div class="px-6 flex items-center justify-between">
                <div class="flex" id="nav-menu">
                    <div class="relative">
                        <button onclick="toggleSubmenu()" class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest transition-all flex items-center gap-2 whitespace-nowrap">
                            Fondos <i data-lucide="chevron-down" id="arrow-icon" class="w-4 h-4 transition-transform"></i>
                        </button>
                        <!-- Submenú -->
                        <div id="submenu" class="hidden absolute top-full left-0 w-72 shadow-2xl rounded-b-2xl overflow-hidden border-t border-white/10 p-2">
                            <div class="submenu-item flex items-center gap-4 p-4 hover:bg-white/10 rounded-xl cursor-pointer">
                                <i data-lucide="folder" class="w-4 h-4 accent-icon"></i> <span class="text-[10px] font-bold uppercase">Administración de Carteras</span>
                            </div>
                            <div class="submenu-item flex items-center gap-4 p-4 hover:bg-white/10 rounded-xl cursor-pointer">
                                <i data-lucide="file-text" class="w-4 h-4 accent-icon"></i> <span class="text-[10px] font-bold uppercase">Reportes de Fondos</span>
                            </div>
                            <div class="submenu-item flex items-center gap-4 p-4 hover:bg-white/10 rounded-xl cursor-pointer">
                                <i data-lucide="database" class="w-4 h-4 accent-icon"></i> <span class="text-[10px] font-bold uppercase">Saldos y Movimientos</span>
                            </div>
                        </div>
                    </div>
                    <button class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest transition-all">Liquidación</button>
                    <button class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest transition-all">Corporativos</button>
                    <button class="nav-item px-6 py-5 text-[11px] font-black uppercase tracking-widest transition-all">Servicios</button>
                </div>
                <div class="flex gap-6 px-8 items-center opacity-80">
                    <i data-lucide="settings" class="w-5 h-5 cursor-pointer"></i>
                    <i data-lucide="user" class="w-5 h-5 cursor-pointer"></i>
                    <i data-lucide="log-out" class="w-5 h-5 cursor-pointer text-red-400"></i>
                </div>
            </div>
        </header>

        <!-- Área de Contenido -->
        <div id="content-area" class="h-[500px] relative transition-all flex flex-col items-center justify-center p-12 overflow-hidden">
            <div class="z-10 text-center max-w-xl">
                <h1 class="text-4xl font-black text-slate-800 mb-4 tracking-tight">SISTEMA <span class="font-light text-slate-400 italic">CORE</span></h1>
                <div id="accent-line" class="h-1.5 w-24 mx-auto mb-8 rounded-full shadow-sm"></div>
                <p class="text-slate-400 text-sm font-medium leading-relaxed">
                    Plataforma integrada para la custodia y liquidación de valores. 
                    Utilice el menú superior para navegar entre los módulos operativos.
                </p>
            </div>
            <!-- Footer del Mockup -->
            <div id="bottom-bar" class="absolute bottom-0 left-0 w-full h-14 transition-all flex items-center justify-between px-10">
                <span class="text-[10px] text-white/80 font-bold uppercase tracking-[0.2em]">Conectado: Nodo Central</span>
                <span class="text-[9px] text-white/50 font-medium tracking-widest uppercase">EDV BOLIVIA v3.1.0</span>
            </div>
        </div>
    </div>

    <script>
        const palettes = {
            original: { name: "Original Imagen", header: "#177090", hover: "#203764", dropdown: "#203764", content: "#f4f1ea", bottom: "#177090", accent: "#95c11f", text: "white" },
            marino: { name: "Marino Premium", header: "#203764", hover: "#177090", dropdown: "#177090", content: "#ffffff", bottom: "#203764", accent: "#95c11f", text: "white" },
            tech: { name: "Tech Celeste", header: "#69b7c6", hover: "#203764", dropdown: "#203764", content: "#f8fafc", bottom: "#177090", accent: "#203764", text: "white" },
            lima: { name: "Lima Energy", header: "#95c11f", hover: "#203764", dropdown: "#203764", content: "#ffffff", bottom: "#177090", accent: "#69b7c6", text: "white" },
            gris: { name: "Gris Ejecutivo", header: "#9d9d9c", hover: "#177090", dropdown: "#177090", content: "#f9fafb", bottom: "#203764", accent: "#95c11f", text: "white" },
            petroleo: { name: "Petróleo Deep", header: "#177090", hover: "#95c11f", dropdown: "#0c3a4d", content: "#f8fafc", bottom: "#9d9d9c", accent: "#95c11f", text: "white" },
            contraste: { name: "High Contrast", header: "#203764", hover: "#69b7c6", dropdown: "#69b7c6", content: "#ffffff", bottom: "#95c11f", accent: "#177090", text: "white" },
            minimal: { name: "Minimal Sky", header: "#f8fafc", hover: "#69b7c6", dropdown: "#ffffff", content: "#ffffff", bottom: "#69b7c6", accent: "#177090", text: "#203764" },
            forest: { name: "Forest Night", header: "#203764", hover: "#9d9d9c", dropdown: "#9d9d9c", content: "#f1f5f9", bottom: "#177090", accent: "#95c11f", text: "white" },
            monocromo: { name: "Monocromo+", header: "#9d9d9c", hover: "#69b7c6", dropdown: "#69b7c6", content: "#ffffff", bottom: "#9d9d9c", accent: "#203764", text: "white" }
        };

        function setPalette(key, btnElement) {
            const p = palettes[key];
            const header = document.getElementById('main-header');
            const content = document.getElementById('content-area');
            const bottom = document.getElementById('bottom-bar');
            const accentLine = document.getElementById('accent-line');
            const dropdown = document.getElementById('submenu');
            const navItems = document.querySelectorAll('.nav-item');
            const accentIcons = document.querySelectorAll('.accent-icon');

            header.style.backgroundColor = p.header;
            header.style.color = p.text;
            content.style.backgroundColor = p.content;
            bottom.style.backgroundColor = p.bottom;
            accentLine.style.backgroundColor = p.accent;
            dropdown.style.backgroundColor = p.dropdown;

            navItems.forEach(item => {
                item.onmouseover = () => item.style.backgroundColor = p.hover;
                item.onmouseout = () => item.style.backgroundColor = 'transparent';
            });

            accentIcons.forEach(icon => icon.style.color = p.accent);

            // Actualizar botones del selector
            document.querySelectorAll('.palette-btn').forEach(btn => {
                btn.classList.remove('bg-[#203764]', 'text-white');
                btn.classList.add('bg-white', 'text-gray-500');
            });
            
            // Si el cambio se hizo desde un botón del grid, lo resaltamos
            if (btnElement) {
                btnElement.classList.remove('bg-white', 'text-gray-500');
                btnElement.classList.add('bg-[#203764]', 'text-white');
            }
        }

        function toggleSubmenu() {
            const submenu = document.getElementById('submenu');
            const arrow = document.getElementById('arrow-icon');
            submenu.classList.toggle('hidden');
            arrow.style.transform = submenu.classList.contains('hidden') ? 'rotate(0deg)' : 'rotate(180deg)';
        }

        // Generar botones de paleta
        const grid = document.getElementById('palette-grid');
        Object.keys(palettes).forEach(key => {
            const btn = document.createElement('button');
            btn.innerText = palettes[key].name;
            btn.className = `palette-btn px-3 py-2.5 rounded-xl text-[10px] font-bold transition-all uppercase tracking-tight border border-gray-100 hover:bg-gray-50`;
            btn.onclick = (e) => setPalette(key, e.currentTarget);
            if(key === 'original') btn.classList.add('bg-[#203764]', 'text-white');
            grid.appendChild(btn);
        });

        // Inicializar
        window.onload = () => {
            lucide.createIcons();
            // Para la carga inicial, buscamos el botón 'original' en el DOM
            const initialBtn = document.querySelector('.palette-btn');
            setPalette('original', initialBtn);
        };
    </script>
</body>
</html>
