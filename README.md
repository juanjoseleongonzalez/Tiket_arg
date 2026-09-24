<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TuTicket - Venta Oficial de Entradas</title>
    <!-- Tailwind CSS para un diseño profesional y moderno -->
    <script src="https://cdn.tailwindcss.com"></script>
</head>
<body class="bg-slate-950 text-white font-sans antialiased">

    <!-- 1. Barra de Navegación -->
    <header class="sticky top-0 z-50 bg-slate-900/90 backdrop-blur border-b border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <div class="flex items-center space-x-3">
                <span class="text-2xl font-black tracking-wider text-rose-500">TICKET<span class="text-white">PRO</span></span>
            </div>
            <nav class="hidden md:flex space-x-8 text-sm font-medium text-slate-300">
                <a href="#" class="hover:text-rose-500 transition">Conciertos</a>
                <a href="#" class="hover:text-rose-500 transition">Teatro y Festivales</a>
                <a href="#" class="hover:text-rose-500 transition">Mis Entradas</a>
                <a href="#" class="hover:text-rose-500 transition">Ayuda</a>
            </nav>
            <div>
                <button class="bg-rose-600 hover:bg-rose-500 text-white font-semibold px-5 py-2.5 rounded-full text-sm transition shadow-lg shadow-rose-600/30">
                    Iniciar Sesión
                </button>
            </div>
        </div>
    </header>

    <!-- 2. Sección Principal (Hero / Buscador) -->
    <section class="relative py-24 bg-gradient-to-b from-slate-900 to-slate-950 border-b border-slate-800/60 text-center px-4">
        <div class="max-w-3xl mx-auto">
            <span class="inline-block bg-rose-500/10 text-rose-400 text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-wider mb-4 border border-rose-500/20">
                Sitio Oficial de Venta Segura
            </span>
            <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight mb-6">
                Vivir la música en vivo <br><span class="text-transparent bg-clip-text bg-gradient-to-r from-rose-500 to-orange-400">nunca fue tan fácil</span>
            </h1>
            <p class="text-slate-400 text-lg mb-10">
                Encuentra las entradas oficiales para los mejores conciertos y giras de todo el año con máxima seguridad garantizada.
            </p>
            
            <!-- Buscador rápido -->
            <div class="flex flex-col sm:flex-row gap-3 bg-slate-900 p-2 rounded-2xl border border-slate-800 shadow-2xl">
                <input type="text" placeholder="Busca por artista, banda o estadio..." class="flex-grow bg-transparent px-4 py-3 text-white placeholder-slate-500 focus:outline-none text-sm">
                <button class="bg-rose-600 hover:bg-rose-500 text-white font-medium px-8 py-3 rounded-xl transition text-sm">
                    Buscar Concierto
                </button>
            </div>
        </div>
    </section>

    <!-- 3. Cartelera de Conciertos del Año -->
    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
        <div class="flex justify-between items-end mb-10">
            <div>
                <h2 class="text-2xl sm:text-3xl font-bold tracking-tight">Próximos Conciertos</h2>
                <p class="text-slate-400 text-sm mt-1">Asegura tus lugares oficiales antes de que se agoten.</p>
            </div>
            <div class="hidden sm:block">
                <span class="text-sm text-rose-400 font-semibold cursor-pointer hover:underline">Ver calendario completo →</span>
            </div>
        </div>

        <!-- Grid de Conciertos -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            
            <!-- Tarjeta de Concierto 1 -->
            <div class="bg-slate-900 rounded-2xl overflow-hidden border border-slate-800 hover:border-slate-700 transition group flex flex-col justify-between">
                <div>
                    <div class="relative h-48 bg-slate-800 overflow-hidden">
                        <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent z-10"></div>
                        <!-- Simulación de imagen de fondo del artista -->
                        <div class="w-full h-full bg-slate-700 flex items-center justify-center text-slate-500 font-bold text-xl group-hover:scale-105 transition duration-500">
                            [Imagen Artista 1]
                        </div>
                        <span class="absolute top-3 left-3 z-20 bg-rose-600/90 backdrop-blur text-white text-xs font-bold px-3 py-1 rounded-full">
                            ¡Últimas Entradas!
                        </span>
                    </div>
                    <div class="p-6">
                        <p class="text-rose-400 text-xs font-semibold uppercase tracking-wider mb-1">15 de Octubre, 2026</p>
                        <h3 class="text-xl font-bold mb-2 group-hover:text-rose-400 transition">Gira Mundial "Rock & Tour"</h3>
                        <p class="text-slate-400 text-sm flex items-center gap-1 mb-4">
                            📍 Estadio Monumental, Buenos Aires
                        </p>
                    </div>
                </div>
                <div class="p-6 pt-0">
                    <button class="w-full bg-slate-800 hover:bg-rose-600 text-white font-medium py-3 rounded-xl transition text-sm border border-slate-700 hover:border-rose-600">
                        Comprar Entradas
                    </button>
                </div>
            </div>

            <!-- Tarjeta de Concierto 2 -->
            <div class="bg-slate-900 rounded-2xl overflow-hidden border border-slate-800 hover:border-slate-700 transition group flex flex-col justify-between">
                <div>
                    <div class="relative h-48 bg-slate-800 overflow-hidden">
                        <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent z-10"></div>
                        <div class="w-full h-full bg-slate-700 flex items-center justify-center text-slate-500 font-bold text-xl group-hover:scale-105 transition duration-500">
                            [Imagen Artista 2]
                        </div>
                        <span class="absolute top-3 left-3 z-20 bg-emerald-600/90 backdrop-blur text-white text-xs font-bold px-3 py-1 rounded-full">
                            Disponible
                        </span>
                    </div>
                    <div class="p-6">
                        <p class="text-rose-400 text-xs font-semibold uppercase tracking-wider mb-1">03 de Noviembre, 2026</p>
                        <h3 class="text-xl font-bold mb-2 group-hover:text-rose-400 transition">Festival Urbano Summer</h3>
                        <p class="text-slate-400 text-sm flex items-center gap-1 mb-4">
                            📍 Movistar Arena, Buenos Aires
                        </p>
                    </div>
                </div>
                <div class="p-6 pt-0">
                    <button class="w-full bg-slate-800 hover:bg-rose-600 text-white font-medium py-3 rounded-xl transition text-sm border border-slate-700 hover:border-rose-600">
                        Comprar Entradas
                    </button>
                </div>
            </div>

            <!-- Tarjeta de Concierto 3 -->
            <div class="bg-slate-900 rounded-2xl overflow-hidden border border-slate-800 hover:border-slate-700 transition group flex flex-col justify-between">
                <div>
                    <div class="relative h-48 bg-slate-800 overflow-hidden">
                        <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent z-10"></div>
                        <div class="w-full h-full bg-slate-700 flex items-center justify-center text-slate-500 font-bold text-xl group-hover:scale-105 transition duration-500">
                            [Imagen Artista 3]
                        </div>
                        <span class="absolute top-3 left-3 z-20 bg-amber-600/90 backdrop-blur text-white text-xs font-bold px-3 py-1 rounded-full">
                            Preventa Exclusiva
                        </span>
                    </div>
                    <div class="p-6">
                        <p class="text-rose-400 text-xs font-semibold uppercase tracking-wider mb-1">20 de Diciembre, 2026</p>
                        <h3 class="text-xl font-bold mb-2 group-hover:text-rose-400 transition">Concierto Acústico Íntimo</h3>
                        <p class="text-slate-400 text-sm flex items-center gap-1 mb-4">
                            📍 Teatro Vorterix, Buenos Aires
                        </p>
                    </div>
                </div>
                <div class="p-6 pt-0">
                    <button class="w-full bg-slate-800 hover:bg-rose-600 text-white font-medium py-3 rounded-xl transition text-sm border border-slate-700 hover:border-rose-600">
                        Comprar Entradas
                    </button>
                </div>
            </div>

        </div>
    </main>

    <!-- 4. Elementos de Confianza y Seguridad -->
    <section class="bg-slate-900/50 border-t border-slate-800 py-12 px-4 mt-20">
        <div class="max-w-7xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-8 text-center md:text-left">
            <div class="flex items-center gap-4 justify-center md:justify-start">
                <div class="w-12 h-12 rounded-full bg-rose-500/10 flex items-center justify-center text-rose-400 text-xl font-bold">🔒</div>
                <div>
                    <h4 class="font-semibold text-sm">Transacciones 100% Seguras</h4>
                    <p class="text-slate-400 text-xs mt-0.5">Protección de datos con encriptación SSL avanzada.</p>
                </div>
            </div>
            <div class="flex items-center gap-4 justify-center md:justify-start">
                <div class="w-12 h-12 rounded-full bg-rose-500/10 flex items-center justify-center text-rose-400 text-xl font-bold">🎫</div>
                <div>
                    <h4 class="font-semibold text-sm">Entradas Oficiales con QR</h4>
                    <p class="text-slate-400 text-xs mt-0.5">Acceso directo y validado en la puerta del evento.</p>
                </div>
            </div>
            <div class="flex items-center gap-4 justify-center md:justify-start">
                <div class="w-12 h-12 rounded-full bg-rose-500/10 flex items-center justify-center text-rose-400 text-xl font-bold">💳</div>
                <div>
                    <h4 class="font-semibold text-sm">Medios de Pago Oficiales</h4>
                    <p class="text-slate-400 text-xs mt-0.5">Tarjetas de crédito, débito y Mercado Pago.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- 5. Footer -->
    <footer class="bg-slate-950 border-t border-slate-900 py-8 px-4 text-center text-xs text-slate-500">
        <p>&copy; 2026 TicketPro. Todos los derechos reservados. Desarrollado con estándares de seguridad internacionales.</p>
    </footer>

</body>
</html>
