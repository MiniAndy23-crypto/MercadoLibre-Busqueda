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

    <!-- Configuración de Tailwind -->
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    fontFamily: {
                        sans: ['Inter', 'sans-serif'],
                    },
                    colors: {
                        ml: {
                            yellow: '#ffe600',
                            blue: '#3483FA',
                            dark: '#333333',
                            green: '#00a650'
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
        /* Estilos personalizados para Glassmorphism */
        .glass-panel {
            background: rgba(255, 255, 255, 0.15);
            backdrop-filter: blur(12px);
            -webkit-backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 8px 32px 0 rgba(0, 0, 0, 0.2);
        }

        .glass-panel-dark {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.2);
            box-shadow: 0 12px 40px 0 rgba(0, 0, 0, 0.3);
        }

        .glass-combo {
            background: rgba(255, 255, 255, 0.85);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(255, 255, 255, 0.5);
            box-shadow: 0 -4px 30px rgba(0, 0, 0, 0.15);
        }

        /* Transición suave para el fondo inmersivo */
        #bg-scene-container {
            perspective: 1000px;
        }

        #bg-scene {
            transition: filter 0.8s ease-in-out, transform 0.1s ease-out;
            will-change: transform, filter;
        }

        .scene-blurred {
            filter: blur(20px) brightness(0.6);
        }

        ::-webkit-scrollbar {
            width: 0px;
        }
    </style>
</head>
<body class="bg-gray-100 text-ml-dark overflow-hidden w-full h-screen font-sans selection:bg-ml-blue selection:text-white">

    <!-- 1. HEADER MERCADO LIBRE -->
    <header class="fixed top-0 left-0 w-full bg-ml-yellow z-40 h-16 flex items-center justify-between px-4 shadow-sm">
        <a href="#" class="flex-shrink-0 flex items-center hidden md:flex">
            <img src="https://http2.mlstatic.com/frontend-assets/ml-web-navigation/ui-navigation/5.21.22/mercadolibre/logo__small@2x.png" alt="Mercado Libre" class="h-8 object-contain">
        </a>
        <a href="#" class="flex-shrink-0 flex items-center md:hidden">
            <img src="https://http2.mlstatic.com/frontend-assets/ml-web-navigation/ui-navigation/5.21.22/mercadolibre/logo__small@2x.png" alt="ML" class="h-8 object-contain w-12 overflow-hidden object-left">
        </a>

        <!-- Barra de Búsqueda Inmersiva -->
        <div class="flex-1 max-w-3xl mx-4 lg:mx-8 transition-all duration-500" id="search-header">
            <div class="bg-white rounded-full flex items-center px-4 py-2 shadow-md hover:shadow-lg transition-shadow border border-transparent focus-within:border-ml-blue">
                <i class="ph-fill ph-sparkle text-ml-blue text-xl mr-2 animate-pulse"></i>
                <input type="text" 
                       value="Voy a acampar a la Patagonia con mi perro..." 
                       class="bg-transparent border-none outline-none text-ml-dark w-full text-sm md:text-base font-medium truncate placeholder-gray-400"
                       readonly>
                <div class="flex items-center gap-3 ml-2 border-l border-gray-200 pl-3">
                    <button class="text-gray-400 hover:text-ml-blue transition-colors" title="Búsqueda por voz"><i class="ph ph-microphone text-xl md:text-2xl"></i></button>
                    <button class="text-gray-400 hover:text-ml-blue transition-colors hidden sm:block" title="Búsqueda por imagen"><i class="ph ph-camera text-xl md:text-2xl"></i></button>
                    <button class="bg-gray-100 text-gray-600 p-1.5 md:p-2 rounded-full hover:bg-ml-blue hover:text-white transition-colors"><i class="ph ph-magnifying-glass text-lg md:text-xl"></i></button>
                </div>
            </div>
        </div>

        <div class="flex items-center gap-4 text-ml-dark text-sm">
            <a href="#" class="hidden lg:block hover:text-black transition-colors font-medium">Mis compras</a>
            <a href="#" class="hidden lg:block hover:text-black transition-colors font-medium">Favoritos</a>
            <button class="hover:text-black transition-colors relative">
                <i class="ph ph-bell text-2xl"></i>
                <span class="absolute top-0 right-0 w-2.5 h-2.5 bg-red-500 rounded-full border border-ml-yellow"></span>
            </button>
            <button class="hover:text-black transition-colors">
                <i class="ph ph-shopping-cart text-2xl"></i>
            </button>
        </div>
    </header>

    <!-- CONTENEDOR PRINCIPAL -->
    <main class="relative w-full h-[calc(100vh-64px)] mt-16 overflow-hidden" id="bg-scene-container">
        
        <!-- 2. ESCENARIO VIVO -->
        <div id="bg-scene" class="absolute inset-[-5%] w-[110%] h-[110%] bg-cover bg-center object-cover" 
             style="background-image: url('https://images.unsplash.com/photo-1464822759023-fed622ff2c3b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');">
        </div>

        <div class="absolute inset-0 bg-gradient-to-t from-black/50 via-transparent to-black/10 pointer-events-none"></div>
        
        <div class="absolute top-6 left-6 z-20 glass-panel text-white px-4 py-2 rounded-full text-sm font-medium flex items-center gap-2">
            <span class="w-2 h-2 rounded-full bg-green-400 animate-pulse"></span>
            Ecosistema: Camping en Patagonia
        </div>

        <!-- 3. CAPA ESPACIAL (Hotspots para Desktop) -->
        
        <!-- Carpa (Izquierda) -->
        <div class="absolute bottom-[20%] left-[25%] z-10 flex flex-col items-center group cursor-pointer animate-float hotspot" data-id="carpa">
            <div class="w-14 h-14 rounded-full bg-ml-yellow/90 backdrop-blur-md flex items-center justify-center border-2 border-white shadow-[0_0_20px_rgba(255,230,0,0.6)] transition-transform duration-300 group-hover:scale-110">
                <i class="ph-fill ph-tent text-ml-dark text-3xl"></i>
            </div>
            <div class="mt-3 glass-panel px-4 py-2 rounded-xl text-sm font-bold text-white opacity-0 group-hover:opacity-100 transition-all duration-300 translate-y-2 group-hover:translate-y-0 flex items-center gap-3">
                <span>Carpa Glamping</span>
                <span class="text-ml-yellow drop-shadow-md">$145.900</span>
            </div>
        </div>

        <!-- Zapatillas (Centro Abajo) -->
        <div class="absolute bottom-[15%] right-[45%] z-10 flex flex-col items-center group cursor-pointer animate-float hotspot" style="animation-delay: 1s;" data-id="botas">
            <div class="w-14 h-14 rounded-full bg-white/50 backdrop-blur-md flex items-center justify-center border-2 border-white shadow-[0_0_15px_rgba(255,255,255,0.4)] transition-all duration-300 group-hover:scale-110 group-hover:bg-ml-yellow/90 group-hover:border-ml-yellow">
                <i class="ph-fill ph-sneaker text-white group-hover:text-ml-dark text-3xl transition-colors"></i>
            </div>
            <div class="mt-3 glass-panel px-4 py-2 rounded-xl text-sm font-bold text-white opacity-0 group-hover:opacity-100 transition-all duration-300 translate-y-2 group-hover:translate-y-0 flex items-center gap-3">
                <span>Salomon XT Pathway</span>
                <span class="text-ml-yellow drop-shadow-md">$85.000</span>
            </div>
        </div>

        <!-- Arnés (Centro Arriba) -->
        <div class="absolute top-[40%] right-[35%] z-10 flex flex-col items-center group cursor-pointer animate-float hotspot" style="animation-delay: 2s;" data-id="arnes">
            <div class="w-14 h-14 rounded-full bg-white/50 backdrop-blur-md flex items-center justify-center border-2 border-white shadow-[0_0_15px_rgba(255,255,255,0.4)] transition-all duration-300 group-hover:scale-110 group-hover:bg-ml-yellow/90 group-hover:border-ml-yellow">
                <i class="ph-fill ph-dog text-white group-hover:text-ml-dark text-3xl transition-colors"></i>
            </div>
            <div class="mt-3 glass-panel px-4 py-2 rounded-xl text-sm font-bold text-white opacity-0 group-hover:opacity-100 transition-all duration-300 translate-y-2 group-hover:translate-y-0 flex items-center gap-3">
                <span>Arnés Táctico</span>
                <span class="text-ml-yellow drop-shadow-md">$25.000</span>
            </div>
        </div>

        <!-- 4. COMBO AVENTURA (Panel Lateral Derecho - Optimizado Desktop) -->
        <div class="absolute top-6 right-6 bottom-6 w-80 lg:w-96 z-30 glass-combo rounded-2xl p-6 flex flex-col justify-between transition-all duration-500 shadow-2xl" id="combo-panel">
            <div>
                <div class="flex items-center justify-between mb-6">
                    <div>
                        <h3 class="text-gray-800 text-2xl font-bold leading-tight">Combo Aventura</h3>
                        <p class="text-ml-green text-sm font-semibold">Lleva el escenario completo</p>
                    </div>
                    <i class="ph-fill ph-sparkle text-ml-blue text-3xl"></i>
                </div>
                
                <div class="flex flex-col gap-4">
                    <!-- Item 1 -->
                    <div class="flex items-center gap-4 bg-white/50 p-2.5 rounded-xl border border-white/50 hover:bg-white/80 transition-colors">
                        <img src="https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?auto=format&fit=crop&w=100&q=80" class="w-16 h-16 rounded-lg object-cover shadow-sm" alt="Carpa">
                        <div class="flex-1">
                            <p class="text-sm font-bold text-gray-800 leading-tight">Carpa Glamping</p>
                            <p class="text-sm text-gray-600 font-medium">$ 145.900</p>
                        </div>
                    </div>
                    <!-- Item 2 -->
                    <div class="flex items-center gap-4 bg-white/50 p-2.5 rounded-xl border border-white/50 hover:bg-white/80 transition-colors">
                        <img src="https://images.unsplash.com/photo-1549298916-b41d501d3772?auto=format&fit=crop&w=100&q=80" class="w-16 h-16 rounded-lg object-cover shadow-sm" alt="Zapatillas">
                        <div class="flex-1">
                            <p class="text-sm font-bold text-gray-800 leading-tight">Salomon XT</p>
                            <p class="text-sm text-gray-600 font-medium">$ 85.000</p>
                        </div>
                    </div>
                    <!-- Item 3 -->
                    <div class="flex items-center gap-4 bg-white/50 p-2.5 rounded-xl border border-white/50 hover:bg-white/80 transition-colors">
                        <img src="https://images.unsplash.com/photo-1522851412497-a640ce1c7a5f?auto=format&fit=crop&w=100&q=80" class="w-16 h-16 rounded-lg object-cover shadow-sm" alt="Arnés">
                        <div class="flex-1">
                            <p class="text-sm font-bold text-gray-800 leading-tight">Arnés Táctico</p>
                            <p class="text-sm text-gray-600 font-medium">$ 25.000</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="mt-6 pt-5 border-t border-gray-300/50">
                <div class="flex justify-between items-end mb-5">
                    <p class="text-gray-600 font-medium pb-1">Total:</p>
                    <div class="text-right">
                        <p class="text-gray-400 line-through text-sm">$ 255.900</p>
                        <p class="text-gray-900 font-bold text-3xl">$ 219.900</p>
                        <p class="text-ml-green text-sm font-bold mt-0.5">15% OFF</p>
                    </div>
                </div>
                <button class="w-full bg-ml-blue hover:bg-blue-600 text-white font-semibold py-3.5 px-6 rounded-xl transition-colors shadow-lg hover:shadow-xl flex items-center justify-center gap-2 text-lg">
                    Comprar Escenario
                    <i class="ph-bold ph-shopping-cart"></i>
                </button>
            </div>
        </div>

    </main>

    <!-- 5. MODAL LÍQUIDO -->
    <div id="product-modal" class="fixed inset-0 z-50 flex items-center justify-center opacity-0 pointer-events-none transition-opacity duration-500 p-4 mt-16">
        
        <button id="close-modal" class="absolute top-6 right-6 z-50 bg-black/50 text-white backdrop-blur-md border border-white/20 rounded-full p-3 hover:bg-black/70 transition-colors flex items-center gap-2 group shadow-lg">
            <i class="ph ph-x text-xl group-hover:rotate-90 transition-transform"></i>
            <span class="hidden md:inline pr-2 text-sm font-medium">Volver a la escena</span>
        </button>

        <div id="modal-content" class="glass-panel-dark w-full max-w-4xl rounded-2xl overflow-hidden flex flex-col md:flex-row transform scale-95 translate-y-10 transition-all duration-700 ease-out shadow-2xl">
            
            <div class="w-full md:w-1/2 h-64 md:h-[450px] relative bg-white flex items-center justify-center p-8 border-r border-gray-100">
                <div class="absolute top-4 left-4 bg-white/80 backdrop-blur-sm px-3 py-1 rounded-full flex items-center gap-2 text-xs font-semibold text-gray-700 shadow-sm border border-gray-200 z-10">
                    <i class="ph ph-cube text-ml-blue"></i>
                    Vista 3D
                </div>
                <img id="modal-img" src="" alt="Producto" class="w-full h-full object-contain drop-shadow-xl transition-transform duration-700 hover:scale-105">
            </div>

            <div class="w-full md:w-1/2 p-8 flex flex-col justify-between bg-white/95">
                <div>
                    <p class="text-xs text-gray-500 uppercase tracking-widest font-semibold mb-2" id="modal-category">Categoría</p>
                    <h2 id="modal-title" class="text-2xl md:text-3xl font-bold text-gray-800 leading-tight mb-2">Nombre del Producto</h2>
                    
                    <div class="flex flex-col mb-4">
                        <span id="modal-price" class="text-3xl md:text-4xl font-normal text-gray-900 tracking-tight"></span>
                        <div class="flex items-center gap-1 text-ml-green mt-2 text-sm font-semibold">
                            <i class="ph-fill ph-truck text-lg"></i>
                            <span>Llega mañana</span>
                            <span class="text-ml-green ml-1 italic font-bold">FULL</span>
                        </div>
                    </div>
                    
                    <p id="modal-desc" class="text-gray-600 text-sm leading-relaxed mb-6"></p>
                </div>

                <div class="mt-4 flex flex-col gap-3">
                    <button class="w-full bg-ml-blue hover:bg-blue-600 text-white font-semibold py-3.5 rounded-lg transition-colors shadow-md flex items-center justify-center gap-2">
                        Comprar ahora
                    </button>
                    <button class="w-full bg-blue-50 hover:bg-blue-100 text-ml-blue font-semibold py-3.5 rounded-lg transition-colors flex items-center justify-center gap-2">
                        Agregar al carrito
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- LÓGICA JAVASCRIPT -->
    <script>
        // Integrando las imágenes estables de Unsplash para ordenador
        const productsData = {
            'carpa': {
                title: 'Carpa Glamping Familiar Verde Exterior',
                price: '$ 145.900',
                img: 'https://images.unsplash.com/photo-1523987355523-c7b5b0dd90a7?auto=format&fit=crop&w=600&q=80',
                desc: 'Carpa espaciosa ideal para glamping. Cuenta con ventanas amplias para ventilación, base impermeable y espacio suficiente para sillas y colchones.',
                category: 'Deportes y Fitness > Camping'
            },
            'botas': {
                title: 'Zapatillas Salomon XT Pathway',
                price: '$ 85.000',
                img: 'https://images.unsplash.com/photo-1549298916-b41d501d3772?auto=format&fit=crop&w=600&q=80',
                desc: 'Zapatillas de trail running con diseño ligero y robusto. Sistema Quicklace para un ajuste perfecto y suela Contagrip para tracción en terrenos difíciles.',
                category: 'Ropa y Accesorios > Calzado Deportivo'
            },
            'arnes': {
                title: 'Arnés Táctico Para Perro + Correa',
                price: '$ 25.000',
                img: 'https://images.unsplash.com/photo-1522851412497-a640ce1c7a5f?auto=format&fit=crop&w=600&q=80',
                desc: 'Conjunto de arnés, collar táctico y correa elástica. Equipado con hebillas de metal resistente, sistema MOLLE y panel de gancho y bucle.',
                category: 'Animales y Mascotas > Perros'
            }
        };

        const hotspots = document.querySelectorAll('.hotspot');
        const modal = document.getElementById('product-modal');
        const modalContent = document.getElementById('modal-content');
        const btnClose = document.getElementById('close-modal');
        const bgScene = document.getElementById('bg-scene');
        const comboPanel = document.getElementById('combo-panel');

        const modTitle = document.getElementById('modal-title');
        const modPrice = document.getElementById('modal-price');
        const modDesc = document.getElementById('modal-desc');
        const modImg = document.getElementById('modal-img');
        const modCategory = document.getElementById('modal-category');

        let isModalOpen = false;

        hotspots.forEach(spot => {
            spot.addEventListener('click', () => {
                isModalOpen = true;
                const id = spot.getAttribute('data-id');
                const data = productsData[id];

                modTitle.textContent = data.title;
                modPrice.textContent = data.price;
                modDesc.textContent = data.desc;
                modImg.src = data.img;
                modCategory.textContent = data.category;
                
                bgScene.classList.add('scene-blurred');
                comboPanel.classList.add('translate-x-[120%]', 'opacity-0'); // Ocultar combo hacia la derecha
                
                hotspots.forEach(h => h.classList.add('opacity-0', 'pointer-events-none'));

                modal.classList.remove('opacity-0', 'pointer-events-none');
                
                setTimeout(() => {
                    modalContent.classList.remove('scale-95', 'translate-y-10');
                    modalContent.classList.add('scale-100', 'translate-y-0');
                }, 50);
            });
        });

        btnClose.addEventListener('click', () => {
            isModalOpen = false;
            
            modalContent.classList.remove('scale-100', 'translate-y-0');
            modalContent.classList.add('scale-95', 'translate-y-10');

            setTimeout(() => {
                modal.classList.add('opacity-0', 'pointer-events-none');
            }, 400);

            bgScene.classList.remove('scene-blurred');
            
            // Restaurar hotspots y panel combo
            hotspots.forEach(h => {
                h.classList.remove('opacity-0', 'pointer-events-none');
            });
            comboPanel.classList.remove('translate-x-[120%]', 'opacity-0');
        });

        const container = document.getElementById('bg-scene-container');
        
        container.addEventListener('mousemove', (e) => {
            if (isModalOpen) return;

            const rect = container.getBoundingClientRect();
            const x = ((e.clientX - rect.left) / rect.width - 0.5) * 2;
            const y = ((e.clientY - rect.top) / rect.height - 0.5) * 2;
            
            const moveX = x * -20;
            const moveY = y * -20;
            
            bgScene.style.transform = `translate(${moveX}px, ${moveY}px) scale(1.05)`;
            
            hotspots.forEach((spot, index) => {
                const factor = index === 0 ? 0.6 : index === 1 ? -0.5 : 0.4;
                spot.style.transform = `translate(${moveX * factor}px, ${moveY * factor}px)`;
            });
        });

        container.addEventListener('mouseleave', () => {
            if (isModalOpen) return;
            bgScene.style.transform = `translate(0px, 0px) scale(1.05)`;
            hotspots.forEach(spot => spot.style.transform = 'translate(0,0)');
        });

    </script>
</body>
</html>

    </script>
</body>
</html>
