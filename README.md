<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mercado Libre - Escenarios Vivos</title>
    
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    
    <!-- Phosphor Icons -->
    <script src="https://unpkg.com/@phosphor-icons/web"></script>
    
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <!-- Configuración de Tailwind para incluir el amarillo de Mercado Libre -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        ml: {
                            yellow: '#FFF159',
                            blue: '#3483FA',
                            dark: '#333333'
                        }
                    },
                    animation: {
                        'pulse-slow': 'pulse 3s cubic-bezier(0.4, 0, 0.6, 1) infinite',
                        'float': 'float 6s ease-in-out infinite',
                    },
                    keyframes: {
                        float: {
                            '0%, 100%': { transform: 'translateY(0)' },
                            '50%': { transform: 'translateY(-10px)' },
                        }
                    }
                }
            }
        }
    </script>

    <style>
        /* Estilos personalizados para Glassmorphism y animaciones fluidas */
        .glass-panel {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.2);
        }

        .glass-panel-dark {
            background: rgba(0, 0, 0, 0.4);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        /* Transición suave para el fondo inmersivo */
        #bg-scene {
            transition: filter 0.8s ease-in-out, transform 0.8s ease-in-out;
        }

        .scene-blurred {
            filter: blur(15px) brightness(0.6);
            transform: scale(1.05); /* Ligero zoom in para dar efecto de profundidad 3D */
        }

        /* Ocultar barra de desplazamiento */
        ::-webkit-scrollbar {
            width: 0px;
        }
    </style>
</head>
<body class="bg-gray-900 text-white overflow-hidden w-full h-screen font-sans selection:bg-ml-yellow selection:text-black">

    <!-- 1. ESCENARIO VIVO (Fondo Inmersivo) -->
    <!-- Imagen de alta calidad de la Patagonia -->
    <div id="bg-scene" class="absolute inset-0 w-full h-full bg-cover bg-center object-cover origin-center" 
         style="background-image: url('https://images.unsplash.com/photo-1510312305653-8ed496efae75?q=80&w=2574&auto=format&fit=crop');">
    </div>

    <!-- Gradiente sutil superior para legibilidad de la barra de búsqueda -->
    <div class="absolute inset-0 bg-gradient-to-b from-black/40 via-transparent to-black/20 pointer-events-none transition-opacity duration-500" id="ambient-overlay"></div>

    <!-- 2. INTERFAZ DE BÚSQUEDA (El "Prompt") -->
    <header class="absolute top-6 left-1/2 -translate-x-1/2 w-11/12 max-w-3xl z-20 flex flex-col items-center gap-2 transition-all duration-500" id="search-header">
        <div class="glass-panel w-full rounded-full flex items-center px-6 py-3 transition-transform hover:scale-[1.01]">
            <i class="ph ph-sparkle text-ml-yellow text-2xl mr-3"></i>
            <input type="text" 
                   value="Voy a acampar a la Patagonia con mi perro" 
                   class="bg-transparent border-none outline-none text-white w-full text-lg placeholder-white/70 font-medium"
                   readonly>
            <div class="flex items-center gap-4 ml-4 border-l border-white/20 pl-4">
                <button class="text-white hover:text-ml-yellow transition-colors"><i class="ph ph-microphone text-2xl"></i></button>
                <button class="bg-ml-yellow text-ml-dark p-2 rounded-full hover:bg-yellow-400 transition-colors shadow-lg"><i class="ph ph-magnifying-glass text-xl"></i></button>
            </div>
        </div>
        <span class="text-xs text-white/70 bg-black/30 px-3 py-1 rounded-full backdrop-blur-sm">Generando Ecosistema 3D...</span>
    </header>

    <!-- 3. CAPA ESPACIAL (Puntos de Interacción / Hotspots) -->
    <!-- Elemento 1: Carpa -->
    <div class="absolute top-[55%] left-[20%] md:left-[30%] z-10 flex flex-col items-center group cursor-pointer animate-float hotspot" data-id="carpa">
        <div class="w-10 h-10 rounded-full bg-ml-yellow/80 backdrop-blur-md flex items-center justify-center border-2 border-white shadow-[0_0_15px_rgba(255,241,89,0.5)] transition-transform group-hover:scale-110">
            <i class="ph-fill ph-tent text-ml-dark text-xl"></i>
        </div>
        <div class="mt-2 glass-panel px-3 py-1 rounded-lg text-sm font-semibold opacity-0 group-hover:opacity-100 transition-opacity translate-y-2 group-hover:translate-y-0 flex items-center gap-2">
            <span>Carpa Térmica</span>
            <span class="text-ml-yellow">$145.900</span>
        </div>
    </div>

    <!-- Elemento 2: Botas -->
    <div class="absolute top-[75%] left-[65%] md:left-[55%] z-10 flex flex-col items-center group cursor-pointer animate-float hotspot" style="animation-delay: 1s;" data-id="botas">
        <div class="w-10 h-10 rounded-full bg-white/30 backdrop-blur-md flex items-center justify-center border-2 border-white shadow-[0_0_15px_rgba(255,255,255,0.3)] transition-transform group-hover:scale-110 group-hover:bg-ml-yellow/80 group-hover:border-ml-yellow">
            <i class="ph-fill ph-boot text-white group-hover:text-ml-dark text-xl transition-colors"></i>
        </div>
        <div class="mt-2 glass-panel px-3 py-1 rounded-lg text-sm font-semibold opacity-0 group-hover:opacity-100 transition-opacity translate-y-2 group-hover:translate-y-0 flex items-center gap-2">
            <span>Botas Trekking</span>
            <span class="text-ml-yellow">$85.000</span>
        </div>
    </div>

    <!-- Elemento 3: Arnés Perro -->
    <div class="absolute top-[65%] left-[80%] md:left-[70%] z-10 flex flex-col items-center group cursor-pointer animate-float hotspot" style="animation-delay: 2s;" data-id="arnes">
        <div class="w-10 h-10 rounded-full bg-white/30 backdrop-blur-md flex items-center justify-center border-2 border-white shadow-[0_0_15px_rgba(255,255,255,0.3)] transition-transform group-hover:scale-110 group-hover:bg-ml-yellow/80 group-hover:border-ml-yellow">
            <i class="ph-fill ph-dog text-white group-hover:text-ml-dark text-xl transition-colors"></i>
        </div>
        <div class="mt-2 glass-panel px-3 py-1 rounded-lg text-sm font-semibold opacity-0 group-hover:opacity-100 transition-opacity translate-y-2 group-hover:translate-y-0 flex items-center gap-2">
            <span>Arnés Táctico</span>
            <span class="text-ml-yellow">$25.000</span>
        </div>
    </div>

    <!-- 4. MODAL LÍQUIDO (Detalle del Producto) -->
    <div id="product-modal" class="fixed inset-0 z-50 flex items-center justify-center opacity-0 pointer-events-none transition-opacity duration-500 p-4">
        
        <!-- Botón Volver al Escenario -->
        <button id="close-modal" class="absolute top-8 right-8 z-50 glass-panel rounded-full p-3 hover:bg-white/20 transition-colors flex items-center gap-2 group">
            <i class="ph ph-x text-2xl group-hover:rotate-90 transition-transform"></i>
            <span class="hidden md:inline pr-2 text-sm font-medium">Volver al entorno</span>
        </button>

        <!-- Contenedor Principal del Producto -->
        <div id="modal-content" class="glass-panel-dark w-full max-w-4xl rounded-3xl overflow-hidden flex flex-col md:flex-row transform scale-95 translate-y-10 transition-all duration-700 ease-out">
            
            <!-- Simulador de Visor 3D / Imagen -->
            <div class="w-full md:w-1/2 h-64 md:h-[500px] relative bg-black/20 flex items-center justify-center p-8">
                <div class="absolute top-4 left-4 glass-panel px-3 py-1 rounded-full flex items-center gap-2 text-xs">
                    <span class="w-2 h-2 rounded-full bg-red-500 animate-pulse"></span>
                    Vista 360°
                </div>
                <img id="modal-img" src="" alt="Producto" class="w-full h-full object-contain drop-shadow-2xl transition-transform duration-700 hover:scale-110 cursor-grab">
            </div>

            <!-- Detalles y Compra -->
            <div class="w-full md:w-1/2 p-8 md:p-10 flex flex-col justify-between">
                <div>
                    <div class="flex items-center gap-2 text-ml-blue mb-3 text-sm font-semibold">
                        <span>Llega mañana</span>
                        <i class="ph-fill ph-lightning"></i>
                        <span class="text-white/50 font-normal">FULL</span>
                    </div>
                    <h2 id="modal-title" class="text-2xl md:text-4xl font-bold leading-tight mb-2">Nombre del Producto</h2>
                    <div class="flex items-baseline gap-3 mb-6">
                        <span id="modal-price" class="text-3xl md:text-5xl font-light text-white"></span>
                    </div>
                    
                    <p id="modal-desc" class="text-white/70 text-sm md:text-base leading-relaxed mb-6"></p>

                    <div class="space-y-3">
                        <h3 class="text-sm uppercase tracking-wider text-white/50 font-semibold">Especificaciones de la escena</h3>
                        <ul id="modal-specs" class="space-y-2 text-sm">
                            <!-- Las specs se inyectan por JS -->
                        </ul>
                    </div>
                </div>

                <div class="mt-8 flex flex-col gap-3">
                    <button class="w-full bg-ml-blue hover:bg-blue-600 text-white font-semibold py-4 rounded-xl transition-colors shadow-lg shadow-blue-500/30 flex items-center justify-center gap-2">
                        Comprar ahora
                    </button>
                    <button class="w-full bg-ml-yellow hover:bg-yellow-400 text-ml-dark font-semibold py-4 rounded-xl transition-colors shadow-lg shadow-yellow-500/20 flex items-center justify-center gap-2">
                        <i class="ph ph-shopping-cart text-xl"></i>
                        Agregar al carrito
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- 5. LOGICA JAVASCRIPT -->
    <script>
        // Base de datos simulada para los productos espaciales
        const productsData = {
            'carpa': {
                title: 'Carpa Doite Hi-Camper 4 Personas Montaña',
                price: '$ 145.900',
                img: 'https://images.unsplash.com/photo-1534880606858-29b0e8a24e8d?q=80&w=800&auto=format&fit=crop&bg=transparent', // Unsplash tent
                desc: 'Diseñada específicamente para soportar los fuertes vientos de la Patagonia. Estructura de duraluminio y columnas de agua de 5000mm. Retiene el 90% del calor corporal.',
                specs: [
                    '<i class="ph ph-wind text-ml-yellow"></i> Resistencia aerodinámica testeada',
                    '<i class="ph ph-drop text-ml-yellow"></i> Impermeabilidad extrema',
                    '<i class="ph ph-thermometer text-ml-yellow"></i> Aislamiento térmico -10°C'
                ]
            },
            'botas': {
                title: 'Botas Trekking Salomon X Ultra 4 Gore-Tex',
                price: '$ 85.000',
                img: 'https://images.unsplash.com/photo-1520639887900-47d34177d63d?q=80&w=800&auto=format&fit=crop',
                desc: 'Agilidad de calzado de trail running con la estabilidad y el agarre necesarios para enfrentar terrenos técnicos. Membrana impermeable GORE-TEX para cruzar ríos patagónicos.',
                specs: [
                    '<i class="ph ph-mountains text-ml-yellow"></i> Suela All Terrain Contagrip®️',
                    '<i class="ph ph-shield-check text-ml-yellow"></i> Advanced Chassis™️ para articulaciones',
                    '<i class="ph ph-cloud-rain text-ml-yellow"></i> Membrana Gore-Tex 100% impermeable'
                ]
            },
            'arnes': {
                title: 'Arnés Táctico Ruffwear Web Master Para Perros',
                price: '$ 25.000',
                img: 'https://images.unsplash.com/photo-1601646270631-f9ebc7e99732?q=80&w=800&auto=format&fit=crop',
                desc: 'Seguridad y soporte para maniobrar y ayudar a tu perro a superar obstáculos. Ideal para senderismo exigente. Incluye agarre anatómico y zonas reflectantes.',
                specs: [
                    '<i class="ph ph-paw-print text-ml-yellow"></i> 5 puntos de ajuste ergonómico',
                    '<i class="ph ph-hand-grabbing text-ml-yellow"></i> Asa acolchada para asistencia',
                    '<i class="ph ph-moon-stars text-ml-yellow"></i> Tiras reflectantes para visibilidad nocturna'
                ]
            }
        };

        // Referencias a elementos del DOM
        const hotspots = document.querySelectorAll('.hotspot');
        const modal = document.getElementById('product-modal');
        const modalContent = document.getElementById('modal-content');
        const btnClose = document.getElementById('close-modal');
        const bgScene = document.getElementById('bg-scene');
        const searchHeader = document.getElementById('search-header');
        const ambientOverlay = document.getElementById('ambient-overlay');

        // Referencias a elementos del modal
        const modTitle = document.getElementById('modal-title');
        const modPrice = document.getElementById('modal-price');
        const modDesc = document.getElementById('modal-desc');
        const modImg = document.getElementById('modal-img');
        const modSpecs = document.getElementById('modal-specs');

        // Función para abrir el modal (Efecto Líquido)
        hotspots.forEach(spot => {
            spot.addEventListener('click', () => {
                const id = spot.getAttribute('data-id');
                const data = productsData[id];

                // Llenar datos
                modTitle.textContent = data.title;
                modPrice.textContent = data.price;
                modDesc.textContent = data.desc;
                modImg.src = data.img;
                
                // Llenar specs
                modSpecs.innerHTML = '';
                data.specs.forEach(spec => {
                    const li = document.createElement('li');
                    li.className = 'flex items-center gap-2';
                    li.innerHTML = spec;
                    modSpecs.appendChild(li);
                });

                // Animar el entorno (Blur)
                bgScene.classList.add('scene-blurred');
                searchHeader.classList.add('opacity-0', '-translate-y-10', 'pointer-events-none');
                ambientOverlay.classList.add('opacity-0');
                
                // Ocultar hotspots suavemente
                hotspots.forEach(h => h.classList.add('opacity-0', 'pointer-events-none'));

                // Mostrar Modal
                modal.classList.remove('opacity-0', 'pointer-events-none');
                
                // Pequeño delay para la animación de entrada del contenido
                setTimeout(() => {
                    modalContent.classList.remove('scale-95', 'translate-y-10');
                    modalContent.classList.add('scale-100', 'translate-y-0');
                }, 50);
            });
        });

        // Función para cerrar el modal y volver al escenario
        btnClose.addEventListener('click', () => {
            // Animación de salida del contenido
            modalContent.classList.remove('scale-100', 'translate-y-0');
            modalContent.classList.add('scale-95', 'translate-y-10');

            // Ocultar modal
            setTimeout(() => {
                modal.classList.add('opacity-0', 'pointer-events-none');
            }, 300);

            // Restaurar el entorno
            bgScene.classList.remove('scene-blurred');
            searchHeader.classList.remove('opacity-0', '-translate-y-10', 'pointer-events-none');
            ambientOverlay.classList.remove('opacity-0');

            // Mostrar hotspots de nuevo
            hotspots.forEach(h => {
                h.classList.remove('opacity-0', 'pointer-events-none');
            });
        });

        // Interacción extra: Efecto Parallax muy sutil con el movimiento del ratón para dar sensación de 3D
        document.addEventListener('mousemove', (e) => {
            // Solo si el modal NO está abierto
            if(modal.classList.contains('opacity-0')) {
                const x = (e.clientX / window.innerWidth - 0.5) * 20; // max 10px move
                const y = (e.clientY / window.innerHeight - 0.5) * 20;
                
                bgScene.style.transform = `translate(${x}px, ${y}px) scale(1.02)`;
                
                hotspots.forEach((spot, index) => {
                    // Diferente velocidad para crear profundidad
                    const factor = index === 0 ? 1 : index === 1 ? -1.5 : 0.8;
                    spot.style.transform = `translate(${x * factor}px, ${y * factor}px)`;
                });
            } else {
                bgScene.style.transform = '';
            }
        });

    </script>
</body>
</html>
