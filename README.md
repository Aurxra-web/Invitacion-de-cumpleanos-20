3<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¡Mis 20 Años! - Aurora 🌸</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Playfair Display (elegancia), Inter (legibilidad) y Great Vibes (cursiva sofisticada) -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..900;1,400..900&family=Inter:wght@300;400;500;600;700&family=Great+Vibes&display=swap" rel="stylesheet">
    <!-- FontAwesome para iconos hermosos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Confetti Library para efectos de celebración -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FFF0F5; /* LavenderBlush / Rosa pastel muy sutil */
            overflow-x: hidden;
        }
        .font-serif-elegant {
            font-family: 'Playfair Display', serif;
        }
        .font-cursive {
            font-family: 'Great Vibes', cursive;
        }
        
        /* Animaciones personalizadas */
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-10px) rotate(1.5deg); }
        }
        .animate-float {
            animation: float 5s ease-in-out infinite;
        }

        @keyframes pulse-soft {
            0%, 100% { transform: scale(1); box-shadow: 0 4px 20px rgba(244, 143, 177, 0.4); }
            50% { transform: scale(1.04); box-shadow: 0 10px 25px rgba(244, 143, 177, 0.6); }
        }
        .animate-pulse-soft {
            animation: pulse-soft 2s ease-in-out infinite;
        }

        /* Degradados Rosa Pastel Premium */
        .bg-pastel-pink {
            background: linear-gradient(135deg, #FFF0F5 0%, #FFE4E1 50%, #FFD1DC 100%);
        }
        .text-gold {
            color: #C5A059;
        }
        
        /* Estilos del Sobre Realista Tridimensional */
        .envelope-container {
            perspective: 1000px;
            width: 320px;
            height: 220px;
            position: relative;
        }
        .envelope-wrapper {
            width: 100%;
            height: 100%;
            background-color: #ffd8e1;
            border-radius: 0 0 12px 12px;
            box-shadow: 0 15px 35px rgba(244, 143, 177, 0.4);
            cursor: pointer;
            position: relative;
            transition: transform 0.4s ease;
            transform-style: preserve-3d;
        }
        .envelope-wrapper:hover {
            transform: translateY(-5px);
        }
        /* Solapa de arriba del sobre */
        .envelope-flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 160px solid transparent;
            border-right: 160px solid transparent;
            border-top: 110px solid #ffaeb9;
            transform-origin: top;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 4;
        }
        .open .envelope-flap {
            transform: rotateX(180deg);
            z-index: 1;
        }
        /* Solapas laterales e inferior */
        .envelope-left {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 160px solid #ffd1dc;
            border-top: 110px solid transparent;
            border-bottom: 110px solid #ffd1dc;
            z-index: 3;
            border-radius: 0 0 0 12px;
        }
        .envelope-right {
            position: absolute;
            bottom: 0;
            right: 0;
            width: 0;
            height: 0;
            border-right: 160px solid #ffd1dc;
            border-top: 110px solid transparent;
            border-bottom: 110px solid #ffd1dc;
            z-index: 3;
            border-radius: 0 0 12px 0;
        }
        .envelope-bottom {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 160px solid transparent;
            border-right: 160px solid transparent;
            border-bottom: 110px solid #ffb6c1;
            z-index: 3;
            border-radius: 0 0 12px 12px;
        }
        /* Carta que se desliza desde adentro */
        .letter-preview {
            position: absolute;
            bottom: 10px;
            left: 15px;
            right: 15px;
            height: 180px;
            background: #ffffff;
            border-radius: 8px;
            z-index: 2;
            transition: transform 0.7s cubic-bezier(0.4, 0, 0.2, 1) 0.3s;
            box-shadow: 0 4px 12px rgba(0,0,0,0.06);
            padding: 15px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: 1px solid #ffe4e1;
        }
        .open .letter-preview {
            transform: translateY(-90px);
            z-index: 5;
        }
        /* Sello de cera digital */
        .wax-seal {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -40%);
            width: 60px;
            height: 60px;
            background: radial-gradient(circle, #f48fb1 0%, #ec407a 100%);
            border-radius: 50%;
            box-shadow: 0 4px 10px rgba(236, 64, 122, 0.4), inset 0 2px 4px rgba(255,255,255,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-family: 'Great Vibes', cursive;
            font-size: 32px;
            z-index: 10;
            transition: transform 0.4s ease, opacity 0.3s ease;
            border: 1px dashed rgba(255, 255, 255, 0.5);
        }
        .open .wax-seal {
            transform: translate(-50%, -150px) scale(0.5);
            opacity: 0;
            pointer-events: none;
        }

        /* Canvas de pétalos flotantes */
        #petal-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 40;
        }
    </style>
</head>
<body class="bg-pastel-pink min-h-screen text-gray-800 antialiased selection:bg-pink-200">

    <!-- Canvas para efecto mágico de pétalos de rosa flotando en segundo plano -->
    <canvas id="petal-canvas"></canvas>

    <!-- Reproductor de YouTube Invisible -->
    <div id="player-container" class="hidden">
        <div id="yt-player"></div>
    </div>

    <!-- PANTALLA DE BIENVENIDA (Sobre interactivo) -->
    <div id="welcome-screen" class="fixed inset-0 z-50 flex flex-col items-center justify-center bg-pink-50 px-4 transition-all duration-700">
        <div class="text-center mb-10 max-w-md px-4">
            <span class="text-sm uppercase tracking-widest text-pink-400 font-bold">Estás cordialmente invitado/a</span>
            <h1 class="text-4xl md:text-5xl font-serif-elegant text-pink-500 mt-2 font-bold">¡Los 20 de Aurora!</h1>
            <div class="w-16 h-0.5 bg-pink-200 mx-auto my-3"></div>
            <p class="text-gray-500 text-sm md:text-base">Haz clic en el sobre para abrir tu hermosa invitación con música de fondo ✨</p>
        </div>

        <!-- Contenedor del Sobre Virtual -->
        <div class="envelope-container" onclick="abrirInvitacion()">
            <div id="virtual-envelope" class="envelope-wrapper">
                <!-- Solapa superior del sobre -->
                <div class="envelope-flap"></div>
                
                <!-- Solapas laterales e inferior para realismo de fondo -->
                <div class="envelope-left"></div>
                <div class="envelope-right"></div>
                <div class="envelope-bottom"></div>
                
                <!-- Sello de cera digital interactivo -->
                <div class="wax-seal">A</div>
                
                <!-- Carta secreta deslizable -->
                <div class="letter-preview">
                    <p class="font-cursive text-pink-500 text-3xl mb-1">Aurora</p>
                    <p class="text-[10px] tracking-widest text-gray-400 uppercase">Mis 20 Años</p>
                    <p class="text-[11px] text-pink-400 mt-2 italic font-medium">✨ Toca para desplegar la magia ✨</p>
                </div>
            </div>
        </div>

        <p class="text-xs text-gray-400 mt-12 italic">Recomendamos activar el sonido de tu dispositivo 🎵</p>
    </div>

    <!-- CONTENIDO PRINCIPAL DE LA INVITACIÓN (Inicialmente oculto) -->
    <div id="main-content" class="opacity-0 transition-opacity duration-1000 max-w-4xl mx-auto px-4 py-8 md:py-16 hidden">
        
        <!-- HEADER / HERO -->
        <header class="text-center mb-12 animate-float">
            <div class="inline-block relative">
                <!-- Corona decorativa -->
                <div class="text-gold text-3xl mb-2"><i class="fa-solid fa-crown"></i></div>
                <h2 class="font-cursive text-5xl md:text-7xl text-pink-500">Aurora</h2>
                <div class="absolute -top-4 -left-8 text-pink-300 text-2xl opacity-60"><i class="fa-solid fa-sparkles"></i></div>
                <div class="absolute -bottom-2 -right-6 text-pink-300 text-2xl opacity-60"><i class="fa-solid fa-sparkles"></i></div>
            </div>
            <h3 class="font-serif-elegant text-2xl md:text-3xl tracking-widest uppercase text-pink-400 font-semibold mt-4">¡Cumplo 20 Años!</h3>
            <div class="w-24 h-0.5 bg-gradient-to-r from-transparent via-pink-300 to-transparent mx-auto mt-4"></div>
            <p class="text-gray-600 italic mt-4 max-w-md mx-auto text-sm md:text-base">"Hay momentos en la vida que son mágicos, y compartirlos con las personas que más quieres los hace inolvidables. ¡Acompáñame a celebrar!"</p>
        </header>

        <!-- SECCIÓN CUENTA REGRESIVA -->
        <section class="bg-white/70 backdrop-blur-md rounded-2xl p-6 md:p-8 shadow-xl border border-pink-100 text-center mb-10 transform transition duration-300 hover:shadow-2xl">
            <h4 class="font-serif-elegant text-pink-500 text-lg uppercase tracking-wider mb-6 font-semibold">Falta muy poco para celebrar...</h4>
            <div class="grid grid-cols-4 gap-2 md:gap-4 max-w-md mx-auto">
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="days" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Días</span>
                </div>
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="hours" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Horas</span>
                </div>
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="minutes" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Min</span>
                </div>
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="seconds" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Seg</span>
                </div>
            </div>
        </section>

        <!-- INFORMACIÓN DE LA FIESTA (CUÁNDO Y DÓNDE) -->
        <div class="grid md:grid-cols-2 gap-8 mb-10">
            <!-- Cuándo -->
            <div class="bg-white/70 backdrop-blur-md rounded-2xl p-8 shadow-xl border border-pink-100 flex flex-col justify-between items-center text-center">
                <div class="text-pink-400 text-4xl mb-4">
                    <i class="fa-regular fa-calendar-check"></i>
                </div>
                <div>
                    <h4 class="font-serif-elegant text-pink-600 text-xl font-bold mb-3">¿Cuándo?</h4>
                    <p class="text-gray-700 font-semibold text-lg">Domingo 31 de Mayo, 2026</p>
                    <p class="text-pink-500 font-bold text-xl mt-1"><i class="fa-regular fa-clock mr-1.5"></i> 7:00 PM</p>
                </div>
                <div class="mt-6 w-full">
                    <span class="inline-block bg-pink-50 text-pink-500 text-xs font-semibold px-4 py-2 rounded-full border border-pink-200">
                        ¡Reserva la fecha en tu calendario! 🗓️
                    </span>
                </div>
            </div>

            <!-- Dónde -->
            <div class="bg-white/70 backdrop-blur-md rounded-2xl p-8 shadow-xl border border-pink-100 flex flex-col justify-between items-center text-center">
                <div class="text-pink-400 text-4xl mb-4">
                    <i class="fa-solid fa-map-location-dot"></i>
                </div>
                <div>
                    <h4 class="font-serif-elegant text-pink-600 text-xl font-bold mb-3">¿Dónde?</h4>
                    <p class="text-gray-700 font-semibold text-lg">Ubicación del Evento</p>
                    <p class="text-gray-500 mt-1 text-sm">Presiona el botón de abajo para ver la dirección exacta del festejo en Google Maps.</p>
                </div>
                <div class="mt-6 w-full">
                    <a href="https://maps.app.goo.gl/Yr2eitdeFZabuev88" target="_blank" 
                       class="inline-flex items-center justify-center w-full bg-pink-500 hover:bg-pink-600 text-white font-bold py-3 px-6 rounded-xl transition duration-300 transform hover:scale-105 shadow-md">
                        <i class="fa-solid fa-location-arrow mr-2"></i> Ver Ubicación en Maps
                    </a>
                </div>
            </div>
        </div>

        <!-- SECCIÓN NOTA DE REGALO (REQUISITO DIVERTIDO SOLICITADO) -->
        <section class="bg-amber-50/70 backdrop-blur-md rounded-2xl p-8 shadow-lg border border-pink-200 text-center mb-10 relative overflow-hidden">
            <!-- Icono decorativo de regalo -->
            <div class="absolute -right-6 -bottom-6 text-pink-200/30 text-8xl transform rotate-12">
                <i class="fa-solid fa-gift"></i>
            </div>
            
            <div class="text-pink-500 text-4xl mb-3 animate-bounce">
                <i class="fa-solid fa-wand-magic-sparkles"></i>
            </div>
            
            <h4 class="font-serif-elegant text-pink-600 text-xl font-bold mb-2">Regla de Oro de Aurora ✨</h4>
            <blockquote class="text-gray-700 italic text-lg font-semibold px-4 py-2 max-w-xl mx-auto">
                "No te olvides traer tu regalo o si no... ¡mejor no vengas!" 😉🎁
            </blockquote>
            <p class="text-xs text-pink-400 mt-2 font-bold uppercase tracking-wider">
                (Mentira... pero si quieres no es mentira. ¡Los 20 se celebran a lo grande!)
            </p>
        </section>

        <!-- SECCIÓN INTELIGENTE CON GEMINI API (NUEVA CARACTERÍSTICA) -->
        <section class="bg-white/80 backdrop-blur-md rounded-2xl p-6 md:p-8 shadow-xl border-2 border-pink-200 mb-10">
            <div class="text-center mb-6">
                <span class="bg-pink-100 text-pink-600 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-widest">
                    <i class="fa-solid fa-circle-nodes mr-1.5 animate-pulse"></i> Zona Interactiva AI
                </span>
                <h4 class="font-serif-elegant text-pink-500 text-2xl font-bold mt-2">¡Prepara tu visita con Inteligencia Artificial!</h4>
                <p class="text-gray-500 text-sm max-w-md mx-auto mt-1">Utiliza nuestra IA integrada para elegir el mejor regalo o redactar la felicitación perfecta para Aurora.</p>
            </div>

            <!-- Selector de Pestañas AI -->
            <div class="flex justify-center border-b border-pink-100 mb-6">
                <button id="tab-gift" onclick="switchAITab('gift')" class="py-2.5 px-4 font-semibold text-sm border-b-2 border-pink-500 text-pink-600 focus:outline-none transition">
                    <i class="fa-solid fa-gift mr-1.5"></i> Ideas de Regalos
                </button>
                <button id="tab-wish" onclick="switchAITab('wish')" class="py-2.5 px-4 font-semibold text-sm border-b-2 border-transparent text-gray-400 hover:text-pink-500 focus:outline-none transition">
                    <i class="fa-solid fa-feather mr-1.5"></i> Dedicatoria Mágica
                </button>
            </div>

            <!-- CONTENIDO PESTAÑA: IDEAS DE REGALOS -->
            <div id="ai-gift-content" class="block space-y-4">
                <p class="text-xs text-gray-500 text-center italic">Para no romper la "Regla de Oro", dinos qué categoría prefieres y nuestro consejero de IA te dará 3 grandes ideas en Ecuador 🇪🇨.</p>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-bold text-gray-500 uppercase mb-1">Categoría del Regalo</label>
                        <select id="gift-category" class="w-full bg-pink-50/50 border border-pink-100 rounded-xl p-3 text-sm focus:ring-2 focus:ring-pink-300 focus:outline-none">
                            <option value="Maquillaje y Skincare 💄">Maquillaje y Cuidado de la Piel</option>
                            <option value="Moda y Accesorios Chic 👗">Moda y Accesorios (Zapatos, Joyas)</option>
                            <option value="Tecnología y Gadgets 📱">Gadgets Tecnológicos o Audífonos</option>
                            <option value="Experiencias divertidas 🎟️">Experiencias (Spa, Entradas, Cenas)</option>
                            <option value="Libros y Arte Creativo 📚">Libros, Papelería o Set de Arte</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-gray-500 uppercase mb-1">Presupuesto Estimado</label>
                        <select id="gift-budget" class="w-full bg-pink-50/50 border border-pink-100 rounded-xl p-3 text-sm focus:ring-2 focus:ring-pink-300 focus:outline-none">
                            <option value="Económico (Sutil pero con amor, menor a $20 USD)">Sutil ($20 USD o menos)</option>
                            <option value="Moderado (Muy genial, entre $20 y $50 USD)">Genial ($20 a $50 USD)</option>
                            <option value="Premium (¡A lo grande!, más de $50 USD)">A lo grande (Más de $50 USD)</option>
                        </select>
                    </div>
                </div>
                
                <button onclick="generarIdeasRegalo()" class="w-full bg-gradient-to-r from-pink-400 to-pink-500 hover:from-pink-500 hover:to-pink-600 text-white font-bold py-3 px-4 rounded-xl transition shadow-md hover:shadow-lg flex items-center justify-center gap-2">
                    <i class="fa-solid fa-sparkles"></i> Consultar Consejero de Regalos AI
                </button>

                <!-- Contenedor de Respuesta del Consejero -->
                <div id="gift-ai-response" class="hidden bg-pink-50/40 rounded-xl p-4 border border-pink-100 mt-4 text-sm text-gray-700 leading-relaxed transition-all duration-300">
                    <!-- Respuestas de la IA van aquí -->
                </div><!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>¡Mis 20 Años! - Aurora 🌸</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Google Fonts: Playfair Display (elegancia), Inter (legibilidad) y Great Vibes (cursiva sofisticada) -->
    <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400..900;1,400..900&family=Inter:wght@300;400;500;600;700&family=Great+Vibes&display=swap" rel="stylesheet">
    <!-- FontAwesome para iconos hermosos -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Confetti Library para efectos de celebración -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FFF0F5; /* LavenderBlush / Rosa pastel muy sutil */
            overflow-x: hidden;
        }
        .font-serif-elegant {
            font-family: 'Playfair Display', serif;
        }
        .font-cursive {
            font-family: 'Great Vibes', cursive;
        }
        
        /* Animaciones personalizadas */
        @keyframes float {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-10px) rotate(1.5deg); }
        }
        .animate-float {
            animation: float 5s ease-in-out infinite;
        }

        @keyframes pulse-soft {
            0%, 100% { transform: scale(1); box-shadow: 0 4px 20px rgba(244, 143, 177, 0.4); }
            50% { transform: scale(1.04); box-shadow: 0 10px 25px rgba(244, 143, 177, 0.6); }
        }
        .animate-pulse-soft {
            animation: pulse-soft 2s ease-in-out infinite;
        }

        /* Degradados Rosa Pastel Premium */
        .bg-pastel-pink {
            background: linear-gradient(135deg, #FFF0F5 0%, #FFE4E1 50%, #FFD1DC 100%);
        }
        .text-gold {
            color: #C5A059;
        }
        
        /* Estilos del Sobre Realista Tridimensional */
        .envelope-container {
            perspective: 1000px;
            width: 320px;
            height: 220px;
            position: relative;
        }
        .envelope-wrapper {
            width: 100%;
            height: 100%;
            background-color: #ffd8e1;
            border-radius: 0 0 12px 12px;
            box-shadow: 0 15px 35px rgba(244, 143, 177, 0.4);
            cursor: pointer;
            position: relative;
            transition: transform 0.4s ease;
            transform-style: preserve-3d;
        }
        .envelope-wrapper:hover {
            transform: translateY(-5px);
        }
        /* Solapa de arriba del sobre */
        .envelope-flap {
            position: absolute;
            top: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 160px solid transparent;
            border-right: 160px solid transparent;
            border-top: 110px solid #ffaeb9;
            transform-origin: top;
            transition: transform 0.6s cubic-bezier(0.4, 0, 0.2, 1);
            z-index: 4;
        }
        .open .envelope-flap {
            transform: rotateX(180deg);
            z-index: 1;
        }
        /* Solapas laterales e inferior */
        .envelope-left {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 160px solid #ffd1dc;
            border-top: 110px solid transparent;
            border-bottom: 110px solid #ffd1dc;
            z-index: 3;
            border-radius: 0 0 0 12px;
        }
        .envelope-right {
            position: absolute;
            bottom: 0;
            right: 0;
            width: 0;
            height: 0;
            border-right: 160px solid #ffd1dc;
            border-top: 110px solid transparent;
            border-bottom: 110px solid #ffd1dc;
            z-index: 3;
            border-radius: 0 0 12px 0;
        }
        .envelope-bottom {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 0;
            height: 0;
            border-left: 160px solid transparent;
            border-right: 160px solid transparent;
            border-bottom: 110px solid #ffb6c1;
            z-index: 3;
            border-radius: 0 0 12px 12px;
        }
        /* Carta que se desliza desde adentro */
        .letter-preview {
            position: absolute;
            bottom: 10px;
            left: 15px;
            right: 15px;
            height: 180px;
            background: #ffffff;
            border-radius: 8px;
            z-index: 2;
            transition: transform 0.7s cubic-bezier(0.4, 0, 0.2, 1) 0.3s;
            box-shadow: 0 4px 12px rgba(0,0,0,0.06);
            padding: 15px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: 1px solid #ffe4e1;
        }
        .open .letter-preview {
            transform: translateY(-90px);
            z-index: 5;
        }
        /* Sello de cera digital */
        .wax-seal {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -40%);
            width: 60px;
            height: 60px;
            background: radial-gradient(circle, #f48fb1 0%, #ec407a 100%);
            border-radius: 50%;
            box-shadow: 0 4px 10px rgba(236, 64, 122, 0.4), inset 0 2px 4px rgba(255,255,255,0.3);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-family: 'Great Vibes', cursive;
            font-size: 32px;
            z-index: 10;
            transition: transform 0.4s ease, opacity 0.3s ease;
            border: 1px dashed rgba(255, 255, 255, 0.5);
        }
        .open .wax-seal {
            transform: translate(-50%, -150px) scale(0.5);
            opacity: 0;
            pointer-events: none;
        }

        /* Canvas de pétalos flotantes */
        #petal-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 40;
        }
    </style>
</head>
<body class="bg-pastel-pink min-h-screen text-gray-800 antialiased selection:bg-pink-200">

    <!-- Canvas para efecto mágico de pétalos de rosa flotando en segundo plano -->
    <canvas id="petal-canvas"></canvas>

    <!-- Reproductor de YouTube Invisible -->
    <div id="player-container" class="hidden">
        <div id="yt-player"></div>
    </div>

    <!-- PANTALLA DE BIENVENIDA (Sobre interactivo) -->
    <div id="welcome-screen" class="fixed inset-0 z-50 flex flex-col items-center justify-center bg-pink-50 px-4 transition-all duration-700">
        <div class="text-center mb-10 max-w-md px-4">
            <span class="text-sm uppercase tracking-widest text-pink-400 font-bold">Estás cordialmente invitado/a</span>
            <h1 class="text-4xl md:text-5xl font-serif-elegant text-pink-500 mt-2 font-bold">¡Los 20 de Aurora!</h1>
            <div class="w-16 h-0.5 bg-pink-200 mx-auto my-3"></div>
            <p class="text-gray-500 text-sm md:text-base">Haz clic en el sobre para abrir tu hermosa invitación con música de fondo ✨</p>
        </div>

        <!-- Contenedor del Sobre Virtual -->
        <div class="envelope-container" onclick="abrirInvitacion()">
            <div id="virtual-envelope" class="envelope-wrapper">
                <!-- Solapa superior del sobre -->
                <div class="envelope-flap"></div>
                
                <!-- Solapas laterales e inferior para realismo de fondo -->
                <div class="envelope-left"></div>
                <div class="envelope-right"></div>
                <div class="envelope-bottom"></div>
                
                <!-- Sello de cera digital interactivo -->
                <div class="wax-seal">A</div>
                
                <!-- Carta secreta deslizable -->
                <div class="letter-preview">
                    <p class="font-cursive text-pink-500 text-3xl mb-1">Aurora</p>
                    <p class="text-[10px] tracking-widest text-gray-400 uppercase">Mis 20 Años</p>
                    <p class="text-[11px] text-pink-400 mt-2 italic font-medium">✨ Toca para desplegar la magia ✨</p>
                </div>
            </div>
        </div>

        <p class="text-xs text-gray-400 mt-12 italic">Recomendamos activar el sonido de tu dispositivo 🎵</p>
    </div>

    <!-- CONTENIDO PRINCIPAL DE LA INVITACIÓN (Inicialmente oculto) -->
    <div id="main-content" class="opacity-0 transition-opacity duration-1000 max-w-4xl mx-auto px-4 py-8 md:py-16 hidden">
        
        <!-- HEADER / HERO -->
        <header class="text-center mb-12 animate-float">
            <div class="inline-block relative">
                <!-- Corona decorativa -->
                <div class="text-gold text-3xl mb-2"><i class="fa-solid fa-crown"></i></div>
                <h2 class="font-cursive text-5xl md:text-7xl text-pink-500">Aurora</h2>
                <div class="absolute -top-4 -left-8 text-pink-300 text-2xl opacity-60"><i class="fa-solid fa-sparkles"></i></div>
                <div class="absolute -bottom-2 -right-6 text-pink-300 text-2xl opacity-60"><i class="fa-solid fa-sparkles"></i></div>
            </div>
            <h3 class="font-serif-elegant text-2xl md:text-3xl tracking-widest uppercase text-pink-400 font-semibold mt-4">¡Cumplo 20 Años!</h3>
            <div class="w-24 h-0.5 bg-gradient-to-r from-transparent via-pink-300 to-transparent mx-auto mt-4"></div>
            <p class="text-gray-600 italic mt-4 max-w-md mx-auto text-sm md:text-base">"Hay momentos en la vida que son mágicos, y compartirlos con las personas que más quieres los hace inolvidables. ¡Acompáñame a celebrar!"</p>
        </header>

        <!-- SECCIÓN CUENTA REGRESIVA -->
        <section class="bg-white/70 backdrop-blur-md rounded-2xl p-6 md:p-8 shadow-xl border border-pink-100 text-center mb-10 transform transition duration-300 hover:shadow-2xl">
            <h4 class="font-serif-elegant text-pink-500 text-lg uppercase tracking-wider mb-6 font-semibold">Falta muy poco para celebrar...</h4>
            <div class="grid grid-cols-4 gap-2 md:gap-4 max-w-md mx-auto">
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="days" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Días</span>
                </div>
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="hours" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Horas</span>
                </div>
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="minutes" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Min</span>
                </div>
                <div class="bg-pink-100/80 rounded-xl p-3 md:p-4 shadow-sm border border-pink-200">
                    <span id="seconds" class="block text-2xl md:text-4xl font-bold text-pink-600">00</span>
                    <span class="text-[10px] md:text-xs uppercase text-pink-400 tracking-wider font-semibold">Seg</span>
                </div>
            </div>
        </section>

        <!-- INFORMACIÓN DE LA FIESTA (CUÁNDO Y DÓNDE) -->
        <div class="grid md:grid-cols-2 gap-8 mb-10">
            <!-- Cuándo -->
            <div class="bg-white/70 backdrop-blur-md rounded-2xl p-8 shadow-xl border border-pink-100 flex flex-col justify-between items-center text-center">
                <div class="text-pink-400 text-4xl mb-4">
                    <i class="fa-regular fa-calendar-check"></i>
                </div>
                <div>
                    <h4 class="font-serif-elegant text-pink-600 text-xl font-bold mb-3">¿Cuándo?</h4>
                    <p class="text-gray-700 font-semibold text-lg">Domingo 31 de Mayo, 2026</p>
                    <p class="text-pink-500 font-bold text-xl mt-1"><i class="fa-regular fa-clock mr-1.5"></i> 7:00 PM</p>
                </div>
                <div class="mt-6 w-full">
                    <span class="inline-block bg-pink-50 text-pink-500 text-xs font-semibold px-4 py-2 rounded-full border border-pink-200">
                        ¡Reserva la fecha en tu calendario! 🗓️
                    </span>
                </div>
            </div>

            <!-- Dónde -->
            <div class="bg-white/70 backdrop-blur-md rounded-2xl p-8 shadow-xl border border-pink-100 flex flex-col justify-between items-center text-center">
                <div class="text-pink-400 text-4xl mb-4">
                    <i class="fa-solid fa-map-location-dot"></i>
                </div>
                <div>
                    <h4 class="font-serif-elegant text-pink-600 text-xl font-bold mb-3">¿Dónde?</h4>
                    <p class="text-gray-700 font-semibold text-lg">Ubicación del Evento</p>
                    <p class="text-gray-500 mt-1 text-sm">Presiona el botón de abajo para ver la dirección exacta del festejo en Google Maps.</p>
                </div>
                <div class="mt-6 w-full">
                    <a href="https://maps.app.goo.gl/Yr2eitdeFZabuev88" target="_blank" 
                       class="inline-flex items-center justify-center w-full bg-pink-500 hover:bg-pink-600 text-white font-bold py-3 px-6 rounded-xl transition duration-300 transform hover:scale-105 shadow-md">
                        <i class="fa-solid fa-location-arrow mr-2"></i> Ver Ubicación en Maps
                    </a>
                </div>
            </div>
        </div>

        <!-- SECCIÓN NOTA DE REGALO (REQUISITO DIVERTIDO SOLICITADO) -->
        <section class="bg-amber-50/70 backdrop-blur-md rounded-2xl p-8 shadow-lg border border-pink-200 text-center mb-10 relative overflow-hidden">
            <!-- Icono decorativo de regalo -->
            <div class="absolute -right-6 -bottom-6 text-pink-200/30 text-8xl transform rotate-12">
                <i class="fa-solid fa-gift"></i>
            </div>
            
            <div class="text-pink-500 text-4xl mb-3 animate-bounce">
                <i class="fa-solid fa-wand-magic-sparkles"></i>
            </div>
            
            <h4 class="font-serif-elegant text-pink-600 text-xl font-bold mb-2">Regla de Oro de Aurora ✨</h4>
            <blockquote class="text-gray-700 italic text-lg font-semibold px-4 py-2 max-w-xl mx-auto">
                "No te olvides traer tu regalo o si no... ¡mejor no vengas!" 😉🎁
            </blockquote>
            <p class="text-xs text-pink-400 mt-2 font-bold uppercase tracking-wider">
                (Mentira... pero si quieres no es mentira. ¡Los 20 se celebran a lo grande!)
            </p>
        </section>

        <!-- SECCIÓN INTELIGENTE CON GEMINI API (NUEVA CARACTERÍSTICA) -->
        <section class="bg-white/80 backdrop-blur-md rounded-2xl p-6 md:p-8 shadow-xl border-2 border-pink-200 mb-10">
            <div class="text-center mb-6">
                <span class="bg-pink-100 text-pink-600 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-widest">
                    <i class="fa-solid fa-circle-nodes mr-1.5 animate-pulse"></i> Zona Interactiva AI
                </span>
                <h4 class="font-serif-elegant text-pink-500 text-2xl font-bold mt-2">¡Prepara tu visita con Inteligencia Artificial!</h4>
                <p class="text-gray-500 text-sm max-w-md mx-auto mt-1">Utiliza nuestra IA integrada para elegir el mejor regalo o redactar la felicitación perfecta para Aurora.</p>
            </div>

            <!-- Selector de Pestañas AI -->
            <div class="flex justify-center border-b border-pink-100 mb-6">
                <button id="tab-gift" onclick="switchAITab('gift')" class="py-2.5 px-4 font-semibold text-sm border-b-2 border-pink-500 text-pink-600 focus:outline-none transition">
                    <i class="fa-solid fa-gift mr-1.5"></i> Ideas de Regalos
                </button>
                <button id="tab-wish" onclick="switchAITab('wish')" class="py-2.5 px-4 font-semibold text-sm border-b-2 border-transparent text-gray-400 hover:text-pink-500 focus:outline-none transition">
                    <i class="fa-solid fa-feather mr-1.5"></i> Dedicatoria Mágica
                </button>
            </div>

            <!-- CONTENIDO PESTAÑA: IDEAS DE REGALOS -->
            <div id="ai-gift-content" class="block space-y-4">
                <p class="text-xs text-gray-500 text-center italic">Para no romper la "Regla de Oro", dinos qué categoría prefieres y nuestro consejero de IA te dará 3 grandes ideas en Ecuador 🇪🇨.</p>
                <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                    <div>
                        <label class="block text-xs font-bold text-gray-500 uppercase mb-1">Categoría del Regalo</label>
                        <select id="gift-category" class="w-full bg-pink-50/50 border border-pink-100 rounded-xl p-3 text-sm focus:ring-2 focus:ring-pink-300 focus:outline-none">
                            <option value="Maquillaje y Skincare 💄">Maquillaje y Cuidado de la Piel</option>
                            <option value="Moda y Accesorios Chic 👗">Moda y Accesorios (Zapatos, Joyas)</option>
                            <option value="Tecnología y Gadgets 📱">Gadgets Tecnológicos o Audífonos</option>
                            <option value="Experiencias divertidas 🎟️">Experiencias (Spa, Entradas, Cenas)</option>
                            <option value="Libros y Arte Creativo 📚">Libros, Papelería o Set de Arte</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-bold text-gray-500 uppercase mb-1">Presupuesto Estimado</label>
                        <select id="gift-budget" class="w-full bg-pink-50/50 border border-pink-100 rounded-xl p-3 text-sm focus:ring-2 focus:ring-pink-300 focus:outline-none">
                            <option value="Económico (Sutil pero con amor, menor a $20 USD)">Sutil ($20 USD o menos)</option>
                            <option value="Moderado (Muy genial, entre $20 y $50 USD)">Genial ($20 a $50 USD)</option>
                            <option value="Premium (¡A lo grande!, más de $50 USD)">A lo grande (Más de $50 USD)</option>
                        </select>
                    </div>
                </div>
                
                <button onclick="generarIdeasRegalo()" class="w-full bg-gradient-to-r from-pink-400 to-pink-500 hover:from-pink-500 hover:to-pink-600 text-white font-bold py-3 px-4 rounded-xl transition shadow-md hover:shadow-lg flex items-center justify-center gap-2">
                    <i class="fa-solid fa-sparkles"></i> Consultar Consejero de Regalos AI
                </button>

                <!-- Contenedor de Respuesta del Consejero -->
                <div id="gift-ai-response" class="hidden bg-pink-50/40 rounded-xl p-4 border border-pink-100 mt-4 text-sm text-gray-700 leading-relaxed transition-all duration-300">
                    <!-- Respuestas de la IA van aquí -->
                </div
