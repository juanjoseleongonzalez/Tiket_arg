<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>tiket_arg - Venta Oficial de Entradas en Argentina</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Generador de QR -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700;800;900&display=swap');
        body { font-family: 'Plus Jakarta Sans', sans-serif; }
    </style>
</head>
<body class="bg-zinc-950 text-zinc-100 antialiased selection:bg-red-600 selection:text-white">

    <!-- ================= BANNER SUPERIOR INFORMATIVO ================= -->
    <div class="bg-gradient-to-r from-red-700 via-rose-600 to-red-600 text-white text-xs font-bold py-2 px-4 text-center tracking-wide flex items-center justify-center gap-2 shadow-inner">
        <span>🔥 Giras 2026 Confirmadas:</span>
        <span class="underline underline-offset-2 opacity-95">¡Encontrá tus artistas favoritos al mejor precio y con cupos oficiales!</span>
    </div>

    <!-- ================= PASO 1: CABEZAL / HEADER OFICIAL ================= -->
    <header class="sticky top-0 z-50 bg-zinc-950/95 backdrop-blur-md border-b border-zinc-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-24 flex items-center justify-between">
            <!-- Logo con Imagen Integrada -->
            <div class="flex items-center space-x-3 cursor-pointer group" onclick="resetApp()">
                <div class="w-12 h-12 rounded-xl overflow-hidden border border-red-500/40 shadow-lg shadow-red-950/40 flex-shrink-0 bg-zinc-900">
                    <!-- Imagen añadida en el logo del header -->
                    <img src="1000171439.png" alt="tiket_arg Logo" class="w-full h-full object-cover group-hover:scale-110 transition duration-300">
                </div>
                <div class="flex flex-col">
                    <div class="flex items-center space-x-1">
                        <span class="text-3xl sm:text-4xl font-black tracking-tighter text-white group-hover:text-red-500 transition">tiket<span class="text-red-600">_arg</span></span>
                        <span class="text-[9px] uppercase font-extrabold bg-red-600/20 text-red-500 border border-red-500/30 px-2 py-0.5 rounded-full ml-1 self-start">Oficial</span>
                    </div>
                    <span class="text-[11px] text-zinc-400 font-medium tracking-wide">Plataforma de eTickets</span>
                </div>
            </div>

            <!-- Navegación -->
            <nav class="hidden md:flex space-x-8 text-sm font-semibold text-zinc-300">
                <a href="#" onclick="resetApp(); return false;" class="hover:text-red-500 transition">Conciertos</a>
                <a href="#" onclick="filterByGira(); return false;" class="hover:text-red-500 transition">Giras 2026</a>
                <a href="#" onclick="showMyTicketsInfo(); return false;" class="hover:text-red-500 transition">Mis #eTickets</a>
            </nav>

            <!-- Seguridad SSL -->
            <div class="flex items-center space-x-2">
                <span class="text-xs bg-zinc-900 text-zinc-300 border border-zinc-800 px-3.5 py-2 rounded-full font-medium flex items-center gap-1.5 shadow-inner">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span> Venta Segura SSL
                </span>
            </div>
        </div>
    </header>

    <!-- ================= PASO 2: VISTA PRINCIPAL (INICIO, HERO Y CATÁLOGO) ================= -->
    <div id="view-home">
        <!-- Hero / Presentación -->
        <section class="relative py-20 lg:py-28 overflow-hidden border-b border-zinc-800/80 bg-gradient-to-b from-zinc-900 to-zinc-950 text-center px-4">
            <div class="absolute inset-0 opacity-15 bg-[radial-gradient(#dc2626_1px,transparent_1px)] [background-size:16px_16px]"></div>
            
            <div class="relative max-w-4xl mx-auto space-y-6">
                <!-- Imagen del Recital / Concierto en el Cuerpo Principal -->
                <div class="max-w-3xl mx-auto rounded-3xl overflow-hidden border border-red-500/30 shadow-2xl shadow-red-950/40 mb-8 relative group">
                    <img src="https://images.unsplash.com/photo-1470225620780-dba8ba36b745?auto=format&fit=crop&w=1200&q=80" alt="Conciertos en Vivo 2026" class="w-full h-64 sm:h-80 object-cover group-hover:scale-105 transition duration-700">
                    <div class="absolute inset-0 bg-gradient-to-t from-zinc-950 via-zinc-950/20 to-transparent"></div>
                    <div class="absolute bottom-4 left-6 right-6 flex items-center justify-between text-xs font-bold text-zinc-300">
                        <span class="bg-red-600/90 text-white px-3 py-1.5 rounded-full uppercase tracking-wider backdrop-blur">🎸 Estadios Argentina 2026</span>
                        <span class="bg-zinc-900/80 px-3 py-1.5 rounded-full border border-zinc-700 backdrop-blur">Cupos Oficiales Disponibles</span>
                    </div>
                </div>

                <div class="inline-flex items-center gap-2.5 bg-zinc-900/90 border border-zinc-800 text-zinc-300 text-xs font-bold px-5 py-2 rounded-full shadow-lg">
                    <span class="flex h-2 w-2 relative">
                      <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-red-400 opacity-75"></span>
                      <span class="relative inline-flex rounded-full h-2 w-2 bg-red-600"></span>
                    </span>
                    <span>Estadios 2026 • Rock, Folklore, Chamamé, Tango, Cumbia, RKT & Trap</span>
                </div>
                
                <h1 class="text-4xl sm:text-7xl font-black tracking-tight text-white leading-tight">
                    Viví la música en vivo <span class="text-transparent bg-clip-text bg-gradient-to-r from-red-500 via-rose-500 to-red-600">sin límites</span>
                </h1>
                
                <p class="text-zinc-400 text-base sm:text-xl max-w-2xl mx-auto font-medium">
                    Encontrá cartelera de artistas, ubicaciones en estadios y comprá tus entradas oficiales en segundos de forma 100% segura.
                </p>
                
                <!-- Buscador Rápido y Botón con Catálogo Lateral -->
                <div class="max-w-2xl mx-auto relative pt-4 flex flex-col sm:flex-row gap-3 justify-center items-center">
                    <div class="flex items-center px-4 bg-zinc-900/90 backdrop-blur rounded-2xl border-2 border-red-600/60 shadow-2xl shadow-red-950/30 flex-grow w-full">
                        <span class="text-zinc-500 text-lg mr-2">🔍</span>
                        <input type="text" id="searchInput" oninput="filterConcerts()" onfocus="showSuggestions()" placeholder="Buscá tu artista (ej: Abel Pintos, Chango Spasiuk, Callejero Fino)..." class="w-full bg-transparent py-4 text-white placeholder-zinc-500 focus:outline-none text-sm font-semibold">
                    </div>

                    <!-- Botón "Buscar" que activa el Panel Lateral -->
                    <div class="w-full sm:w-auto">
                        <button type="button" onclick="toggleCatalogDropdown()" class="w-full sm:w-auto bg-gradient-to-r from-red-600 to-rose-600 hover:from-red-500 hover:to-rose-500 text-white font-bold px-8 py-4 rounded-2xl transition text-sm border border-red-500/40 flex items-center justify-center gap-2 shadow-xl shadow-red-950/50 whitespace-nowrap cursor-pointer">
                            <span>🔍 Buscar Artistas</span>
                            <span class="text-xs opacity-75 font-normal">→</span>
                        </button>
                    </div>

                    <!-- Sugerencias de búsqueda -->
                    <div id="suggestionsBox" class="absolute left-0 right-0 top-24 mt-2 bg-zinc-900 border border-zinc-800 rounded-2xl shadow-2xl z-40 hidden max-h-64 overflow-y-auto p-2 text-left">
                        <div class="px-3 py-2 text-xs font-bold text-zinc-400 uppercase tracking-wider border-b border-zinc-800 mb-1">Artistas sugeridos:</div>
                        <div id="suggestionsList" class="grid grid-cols-2 gap-1"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Galería de Sponsors / Artistas Destacados -->
        <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 border-b border-zinc-900">
            <div class="flex items-center justify-between mb-6">
                <h3 class="text-xs font-bold uppercase tracking-widest text-zinc-400">⭐ Sponsors y Shows Destacados 2026</h3>
                <span class="text-[10px] bg-red-600/10 text-red-500 border border-red-500/20 px-2.5 py-1 rounded-md font-bold uppercase">Oficiales</span>
            </div>
            <div id="quickArtistsGrid" class="grid grid-cols-2 sm:grid-cols-4 md:grid-cols-8 gap-3 text-center"></div>
        </section>

        <!-- Cartelera Completa de Conciertos -->
        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
            <div class="mb-10 flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
                <div>
                    <h2 class="text-2xl sm:text-3xl font-black tracking-tight text-white">Cartelera Completa de Conciertos</h2>
                    <p class="text-zinc-400 text-sm mt-1">Fechas oficiales confirmadas, horarios de apertura y estadios en Argentina.</p>
                </div>
                <div class="flex items-center gap-3">
                    <button onclick="clearSearch()" id="btnClear" class="text-xs text-red-500 hover:underline font-bold hidden">Limpiar filtro ✕</button>
                    <div id="eventCount" class="text-xs bg-zinc-900 text-zinc-300 border border-zinc-800 font-bold px-3 py-1.5 rounded-lg uppercase tracking-wider">0 eventos</div>
                </div>
            </div>

            <!-- Estado: Sin Resultados -->
            <div id="noResults" class="text-center py-20 bg-zinc-900/40 rounded-3xl border border-zinc-800 hidden">
                <p class="text-zinc-400 text-lg font-semibold">No encontramos conciertos para tu búsqueda.</p>
                <button onclick="clearSearch()" class="mt-4 bg-red-600 text-white px-6 py-2.5 rounded-xl text-sm font-bold shadow hover:bg-red-700 transition">Ver todos los eventos</button>
            </div>

            <!-- Grilla Dinámica -->
            <div id="concertsGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8"></div>
        </main>
    </div>

    <!-- ================= PANEL LATERAL (SIDEBAR) DE ARTISTAS Y PRECIOS ================= -->
    <div id="catalogBackdrop" class="fixed inset-0 bg-black/70 backdrop-blur-sm z-50 hidden transition-opacity" onclick="toggleCatalogDropdown()"></div>
    <div id="catalogDropdown" class="fixed top-0 right-0 h-full w-full sm:w-[440px] bg-zinc-900 border-l border-zinc-800 shadow-2xl z-50 transform translate-x-full transition-transform duration-300 ease-in-out flex flex-col">
        <!-- Cabecera del Panel -->
        <div class="p-5 border-b border-zinc-800 flex items-center justify-between bg-zinc-950">
            <div class="flex items-center space-x-2">
                <span class="text-xl font-black text-white">Listado de Artistas</span>
                <span class="text-[10px] bg-red-600/20 text-red-500 border border-red-500/30 px-2 py-0.5 rounded-full font-bold">Precios Oficiales</span>
            </div>
            <button onclick="toggleCatalogDropdown()" class="w-9 h-9 bg-zinc-900 hover:bg-zinc-800 border border-zinc-700 text-zinc-300 rounded-xl flex items-center justify-center font-bold transition">✕</button>
        </div>
        
        <!-- Cuerpo con la Lista Desplazable -->
        <div id="catalogDropdownList" class="p-4 space-y-3 overflow-y-auto flex-grow bg-zinc-900"></div>

        <!-- Pie del Panel -->
        <div class="p-4 border-t border-zinc-800 bg-zinc-950 text-center">
            <p class="text-xs text-zinc-500">Seleccioná un artista para acceder directo a las ubicaciones.</p>
        </div>
    </div>

    <!-- ================= PASO 3: SALA DE ESPERA / FILA VIRTUAL ================= -->
    <div id="view-queue" class="max-w-xl mx-auto px-4 py-32 text-center hidden">
        <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-8 sm:p-12 shadow-2xl space-y-6">
            <div class="w-16 h-16 bg-red-600/10 text-red-500 rounded-full flex items-center justify-center text-2xl mx-auto border border-red-500/20 animate-pulse">⏳</div>
            <div>
                <span class="text-xs uppercase font-bold text-red-500 tracking-wider">Sala de Espera Virtual tiket_arg</span>
                <h2 class="text-2xl font-black text-white mt-1">Estás formado en la fila</h2>
                <p class="text-zinc-400 text-sm mt-2">Hay alta demanda para este show. Aguardá unos segundos para ingresar al sistema seguro de ubicaciones.</p>
            </div>
            <div class="bg-zinc-950 p-6 rounded-2xl border border-zinc-800 space-y-2">
                <p class="text-xs text-zinc-500">Tu lugar aproximado en la fila:</p>
                <p id="queuePosText" class="text-4xl font-black text-red-500">42</p>
                <p class="text-xs text-zinc-400 pt-2">Acceso estimado en: <span class="font-bold text-zinc-200">Menos de 1 minuto</span></p>
            </div>
            <p class="text-xs text-zinc-500">No cierres esta ventana para no perder tu turno.</p>
        </div>
    </div>

    <!-- ================= PASO 4: SELECCIÓN DE ENTRADAS Y PRECIOS ================= -->
    <div id="view-select" class="max-w-4xl mx-auto px-4 py-12 hidden">
        <div class="bg-red-600 text-white px-6 py-3.5 rounded-2xl mb-6 flex items-center justify-between shadow-lg shadow-red-600/20">
            <span class="text-xs font-semibold uppercase tracking-wider">⏱ Tiempo reservado para completar tu compra:</span>
            <span id="timerText" class="text-lg font-black">5:00</span>
        </div>

        <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-6 sm:p-10 shadow-xl">
            <div class="flex flex-col sm:flex-row justify-between sm:items-center gap-2 border-b border-zinc-800 pb-4 mb-6">
                <div>
                    <span id="selConcertMeta" class="text-xs font-bold text-red-500 uppercase tracking-widest"></span>
                    <h2 id="selConcertTitle" class="text-3xl font-black text-white mt-1"></h2>
                </div>
                <span id="selConcertLoc" class="text-sm font-semibold text-zinc-400 bg-zinc-950 px-3 py-1.5 rounded-xl self-start border border-zinc-800"></span>
            </div>

            <h3 class="text-lg font-bold text-white mb-4">Seleccioná tus ubicaciones y costos oficiales:</h3>
            
            <div id="ticketsListContainer" class="space-y-4 mb-8"></div>

            <div class="bg-zinc-950 p-6 rounded-2xl border border-zinc-800 flex flex-col sm:flex-row items-center justify-between gap-4">
                <div>
                    <p class="text-xs text-zinc-400">Total a abonar:</p>
                    <p id="totalPriceText" class="text-3xl font-black text-red-500">$0</p>
                </div>
                <button onclick="proceedToCheckout()" id="btnCheckout" disabled class="w-full sm:w-auto bg-red-600 hover:bg-red-700 disabled:bg-zinc-800 disabled:text-zinc-600 text-white font-bold px-8 py-4 rounded-2xl transition text-sm shadow-lg">
                    Continuar al Pago Seguro →
                </button>
            </div>
        </div>
    </div>

    <!-- ================= PASO 5: PASARELA DE PAGO SEGURO ================= -->
    <div id="view-checkout" class="max-w-2xl mx-auto px-4 py-12 hidden">
        <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-6 sm:p-10 shadow-xl">
            <h2 class="text-2xl font-bold text-white mb-2">Finalizar Compra (#eTicket)</h2>
            <p class="text-zinc-400 text-sm mb-6">Ingresá tus datos para coordinar el pago y emitir tu entrada oficial con código QR.</p>
            
            <form onsubmit="processPayment(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-400 mb-1">Nombre y Apellido del Titular</label>
                    <input type="text" id="buyerName" required placeholder="Ej: Juan Pérez" class="w-full bg-zinc-950 border border-zinc-800 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-red-600 font-medium">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-400 mb-1">Correo Electrónico (Para recibir el #eTicket)</label>
                    <input type="email" id="buyerEmail" required placeholder="tu@correo.com" class="w-full bg-zinc-950 border border-zinc-800 rounded-xl px-4 py-3 text-sm text-white focus:outline-none focus:border-red-600 font-medium">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-400 mb-1">Seleccionar Método de Pago</label>
                    <select id="paymentMethod" class="w-full bg-zinc-950 border border-zinc-800 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-red-600 text-white font-medium">
                        <option value="WhatsApp - Mercado Pago / Transferencia">Mercado Pago / Transferencia Bancaria (Vía WhatsApp)</option>
                        <option value="WhatsApp - Efectivo / Rapipago / Pago Fácil">Efectivo / Rapipago / Pago Fácil (Vía WhatsApp)</option>
                        <option value="WhatsApp - Tarjeta de Crédito/Débito">Tarjeta de Crédito / Débito (Vía WhatsApp)</option>
                    </select>
                </div>

                <div class="pt-4 border-t border-zinc-800 flex items-center justify-between">
                    <div>
                        <p class="text-xs text-zinc-400">Total final a abonar:</p>
                        <p id="checkoutTotalText" class="text-2xl font-black text-red-500">$0</p>
                    </div>
                    <button type="submit" class="bg-emerald-600 hover:bg-emerald-500 text-white font-bold px-6 sm:px-8 py-4 rounded-2xl transition text-sm shadow-lg shadow-emerald-950/50 flex items-center gap-2">
                        <span>Solicitar pago 💬</span>
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- ================= PASO 6: COMPRA EXITOSA Y QR DE ACCESO ================= -->
    <div id="view-success" class="max-w-xl mx-auto px-4 py-12 text-center hidden">
        <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-8 sm:p-10 shadow-xl">
            <div class="w-16 h-16 bg-emerald-500/10 text-emerald-500 rounded-full flex items-center justify-center text-3xl mx-auto mb-4 border border-emerald-500/20">✓</div>
            <h2 class="text-2xl font-bold text-white mb-1">¡Solicitud Enviada a WhatsApp!</h2>
            <p class="text-zinc-400 text-sm mb-6">Tu orden fue procesada. Se abrió WhatsApp para que completes tu pago y recibas tu código QR de acceso oficial.</p>
            
            <!-- CARTEL DE AVISO AGREGADO -->
            <div class="bg-emerald-950/40 border border-emerald-500/30 text-emerald-300 text-xs font-semibold p-3.5 rounded-2xl mb-6 flex items-center justify-center gap-2 shadow-inner">
                <span>✨</span>
                <span>Gracias por usar nuestra página, su entrada estará validada al finalizar el pago.</span>
            </div>

            <div class="bg-zinc-950 border border-zinc-800 rounded-2xl p-6 text-left mb-6 space-y-3 shadow-inner">
                <div class="flex justify-between items-center border-b border-zinc-800 pb-3">
                    <span id="successTitle" class="text-xs uppercase font-bold text-red-500"></span>
                    <span id="successDate" class="text-xs text-zinc-400"></span>
                </div>
                <div>
                    <p class="text-xs text-zinc-500">Titular del Ticket:</p>
                    <p id="successBuyer" class="text-sm font-semibold text-zinc-200"></p>
                </div>
                <div>
                    <p class="text-xs text-zinc-500">Estadio / Recinto Oficial:</p>
                    <p id="successLoc" class="text-sm font-semibold text-zinc-200"></p>
                </div>
                <div class="pt-3 border-t border-zinc-800 flex flex-col items-center justify-center">
                    <p class="text-xs text-zinc-500 mb-2">Código QR de Reserva:</p>
                    <div id="qrcode" class="bg-white p-3 rounded-xl border border-zinc-800 shadow-sm"></div>
                </div>
            </div>

            <button onclick="resetApp()" class="w-full bg-white hover:bg-zinc-200 text-zinc-950 font-bold py-3.5 rounded-2xl transition text-sm shadow">
                Volver al Inicio de tiket_arg
            </button>
        </div>
    </div>

    <!-- ================= SCRIPT DE LÓGICA COMPLETA ================= -->
    <script>
        const concerts = [
            {
                id: 1,
                artist: 'Maria Becerra',
                title: 'Maria Becerra - Gira Oficial',
                date: '13 de Noviembre, 2026',
                time: '21:00 hs',
                location: 'Movistar Arena, Buenos Aires',
                badge: 'Sponsor Oficial',
                image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo General', description: 'Acceso a pista general de pie', price: 48000, qty: 0 },
                    { type: 'Platea Baja', description: 'Ubicación numerada preferencial', price: 79000, qty: 0 },
                    { type: 'Experiencia VIP', description: 'Acceso prioritario + Merchandising', price: 128000, qty: 0 }
                ]
            },
            {
                id: 2,
                artist: 'Duki',
                title: 'Duki - Estadios Tour',
                date: '25 de Octubre, 2026',
                time: '20:30 hs',
                location: 'Estadio Vélez Sarsfield, Buenos Aires',
                badge: 'Alta Demanda',
                image: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Pista general', price: 45000, qty: 0 },
                    { type: 'Platea Preferencial', description: 'Sector baja numerado', price: 82000, qty: 0 }
                ]
            },
            {
                id: 3,
                artist: 'Emilia',
                title: 'Emilia - .MP3 Tour Argentina',
                date: '18 de Noviembre, 2026',
                time: '21:00 hs',
                location: 'Movistar Arena, Buenos Aires',
                badge: 'Sponsor Oficial',
                image: 'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo General', description: 'Acceso general pista', price: 46000, qty: 0 },
                    { type: 'Platea Baja', description: 'Ubicación numerada', price: 75000, qty: 0 }
                ]
            },
            {
                id: 4,
                artist: 'Trueno',
                title: 'Trueno - El Último Baile Tour',
                date: '02 de Diciembre, 2026',
                time: '21:30 hs',
                location: 'Luna Park, Buenos Aires',
                badge: 'Nuevo Show',
                image: 'https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Pista de pie', price: 39000, qty: 0 },
                    { type: 'Platea', description: 'Sector numerado', price: 62000, qty: 0 }
                ]
            },
            {
                id: 5,
                artist: 'La Renga',
                title: 'La Renga - Banquete de Rock',
                date: '06 de Diciembre, 2026',
                time: '21:00 hs',
                location: 'Estadio Único de La Plata, Buenos Aires',
                badge: 'Rock Nacional',
                image: 'https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Campo de pie', price: 40000, qty: 0 },
                    { type: 'Platea', description: 'Tribuna numerada', price: 65000, qty: 0 }
                ]
            },
            {
                id: 6,
                artist: 'Ke Personajes',
                title: 'Ke Personajes - Cumbia Tour Nacional',
                date: '10 de Diciembre, 2026',
                time: '22:00 hs',
                location: 'Movistar Arena, Buenos Aires',
                badge: 'Cumbia',
                image: 'https://images.unsplash.com/photo-1501386761578-eac5c94b800a?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista General', description: 'Baile y pista general', price: 35000, qty: 0 },
                    { type: 'Platea Baja', description: 'Asiento preferencial', price: 60000, qty: 0 }
                ]
            },
            {
                id: 7,
                artist: 'Q\' Lokura',
                title: 'Q\' Lokura - Cuarteto en Vivo',
                date: '14 de Diciembre, 2026',
                time: '23:30 hs',
                location: 'Luna Park, Buenos Aires',
                badge: 'Cuarteto',
                image: 'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista Baile', description: 'Pista principal', price: 32000, qty: 0 },
                    { type: 'Platea VIP', description: 'Sector preferencial numerado', price: 58000, qty: 0 }
                ]
            },
            {
                id: 8,
                artist: 'L-Gante',
                title: 'L-Gante - Cumbia 420 & RKT Tour',
                date: '18 de Diciembre, 2026',
                time: '21:30 hs',
                location: 'Tecnópolis, Buenos Aires',
                badge: 'RKT / Cumbia',
                image: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo General', description: 'Pista libre', price: 30000, qty: 0 },
                    { type: 'VIP RKT', description: 'Zona exclusiva', price: 55000, qty: 0 }
                ]
            },
            {
                id: 9,
                artist: 'Ciro y los Persas',
                title: 'Ciro y los Persas - Rock Tour',
                date: '21 de Diciembre, 2026',
                time: '21:00 hs',
                location: 'Estadio Vélez Sarsfield, Buenos Aires',
                badge: 'Rock Nacional',
                image: 'https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Pista general', price: 38000, qty: 0 },
                    { type: 'Platea Preferencial', description: 'Ubicación numerada', price: 72000, qty: 0 }
                ]
            },
            {
                id: 10,
                artist: 'Los Palmeras',
                title: 'Los Palmeras - La Fiesta de la Cumbia',
                date: '28 de Diciembre, 2026',
                time: '21:00 hs',
                location: 'Luna Park, Buenos Aires',
                badge: 'Cumbia Tradicional',
                image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista', description: 'Pista general', price: 34000, qty: 0 },
                    { type: 'Platea', description: 'Sector numerado', price: 58000, qty: 0 }
                ]
            },
            {
                id: 11,
                artist: 'La Konga',
                title: 'La Konga - Gira Federal Cuarteto',
                date: '04 de Enero, 2027',
                time: '23:00 hs',
                location: 'Movistar Arena, Buenos Aires',
                badge: 'Cuarteto Top',
                image: 'https://images.unsplash.com/photo-1501386761578-eac5c94b800a?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista General', description: 'Pista de baile', price: 35000, qty: 0 },
                    { type: 'Platea Baja', description: 'Asiento preferencial', price: 70000, qty: 0 }
                ]
            },
            {
                id: 12,
                artist: 'Callejero Fino',
                title: 'Callejero Fino - RKT Session Tour',
                date: '08 de Enero, 2027',
                time: '22:00 hs',
                location: 'Teatro Vorterix, Buenos Aires',
                badge: 'RKT',
                image: 'https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'General', description: 'Campo de pie', price: 28000, qty: 0 },
                    { type: 'Balcón', description: 'Sector alto', price: 45000, qty: 0 }
                ]
            },
            {
                id: 13,
                artist: 'Divididos',
                title: 'Divididos - La Aplanadora del Rock',
                date: '15 de Enero, 2027',
                time: '21:00 hs',
                location: 'Estadio Obras Sanitarias, Buenos Aires',
                badge: 'Rock',
                image: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Pista general', price: 36000, qty: 0 },
                    { type: 'Platea', description: 'Tribuna', price: 62000, qty: 0 }
                ]
            },
            {
                id: 14,
                artist: 'Damas Gratis',
                title: 'Damas Gratis - Cumbia Villera Tour',
                date: '20 de Enero, 2027',
                time: '23:00 hs',
                location: 'Luna Park, Buenos Aires',
                badge: 'Cumbia',
                image: 'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista General', description: 'Pista de baile', price: 30000, qty: 0 },
                    { type: 'Platea', description: 'Asiento numerado', price: 50000, qty: 0 }
                ]
            },
            {
                id: 15,
                artist: 'Ulises Bueno',
                title: 'Ulises Bueno - El Caño Tour',
                date: '25 de Enero, 2027',
                time: '23:30 hs',
                location: 'Movistar Arena, Buenos Aires',
                badge: 'Cuarteto',
                image: 'https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista', description: 'Pista general', price: 33000, qty: 0 },
                    { type: 'Platea Preferencial', description: 'Platea baja', price: 64000, qty: 0 }
                ]
            },
            {
                id: 16,
                artist: 'No Te Va Gustar',
                title: 'NTVG - Gira Sudamericana',
                date: '02 de Febrero, 2027',
                time: '21:00 hs',
                location: 'Estadio Único de La Plata, Buenos Aires',
                badge: 'Rock / Pop Rock',
                image: 'https://images.unsplash.com/photo-1501386761578-eac5c94b800a?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Campo general', price: 39000, qty: 0 },
                    { type: 'Platea', description: 'Tribuna numerada', price: 68000, qty: 0 }
                ]
            },
            {
                id: 17,
                artist: 'Abel Pintos',
                title: 'Abel Pintos - Gira Folklore y Canciones',
                date: '10 de Febrero, 2027',
                time: '21:00 hs',
                location: 'Movistar Arena, Buenos Aires',
                badge: 'Folklore',
                image: 'https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo General', description: 'Pista de pie', price: 38000, qty: 0 },
                    { type: 'Platea Preferencial', description: 'Asiento numerado', price: 74000, qty: 0 }
                ]
            },
            {
                id: 18,
                artist: 'Soledad',
                title: 'Soledad Pastorutti - Fiesta y Tradición',
                date: '14 de Febrero, 2027',
                time: '21:30 hs',
                location: 'Luna Park, Buenos Aires',
                badge: 'Folklore',
                image: 'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista', description: 'Campo general', price: 32000, qty: 0 },
                    { type: 'Platea', description: 'Sector numerado', price: 60000, qty: 0 }
                ]
            },
            {
                id: 19,
                artist: 'Chango Spasiuk',
                title: 'Chango Spasiuk - Antología del Chamamé',
                date: '18 de Febrero, 2027',
                time: '20:30 hs',
                location: 'Centro Cultural Kirchner (CCK), Buenos Aires',
                badge: 'Chamamé',
                image: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Auditorio General', description: 'Ubicación general', price: 25000, qty: 0 },
                    { type: 'Palco VIP', description: 'Palco preferencial', price: 45000, qty: 0 }
                ]
            },
            {
                id: 20,
                artist: 'Los Alonsitos',
                title: 'Los Alonsitos - Puro Chamamé',
                date: '22 de Febrero, 2027',
                time: '21:00 hs',
                location: 'Teatro Gran Rex, Buenos Aires',
                badge: 'Chamamé',
                image: 'https://images.unsplash.com/photo-1501386761578-eac5c94b800a?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Platea Baja', description: 'Sector preferencial', price: 30000, qty: 0 },
                    { type: 'Platea Alta', description: 'Ubicación alta', price: 20000, qty: 0 }
                ]
            },
            {
                id: 21,
                artist: 'Raúl Lavié',
                title: 'Raúl Lavié - Noche de Tango y Leyenda',
                date: '26 de Febrero, 2027',
                time: '20:30 hs',
                location: 'Teatro Cúpula / Café Tortoni, Buenos Aires',
                badge: 'Tango',
                image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Mesa Preferencial', description: 'Mesa con consumición y vista cercana', price: 42000, qty: 0 },
                    { type: 'General', description: 'Asiento general', price: 28000, qty: 0 }
                ]
            },
            {
                id: 22,
                artist: 'Amelita Baltar',
                title: 'Amelita Baltar - Vivir en Tango',
                date: '03 de Marzo, 2027',
                time: '21:00 hs',
                location: 'Usina del Arte, Buenos Aires',
                badge: 'Tango',
                image: 'https://images.unsplash.com/photo-1492684223066-81342ee5ff30?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Platea Principal', description: 'Asiento numerado', price: 30000, qty: 0 },
                    { type: 'Balcón', description: 'Sector superior', price: 22000, qty: 0 }
                ]
            },
            {
                id: 23,
                artist: 'Gonzalo Nahuel',
                title: 'Gonzalo Nahuel - Gira Acústica y Tropical',
                date: '08 de Marzo, 2027',
                time: '21:30 hs',
                location: 'Teatro Broadway, Buenos Aires',
                badge: 'Cumbia / Tropical',
                image: 'https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Platea Baja', description: 'Ubicación preferencial', price: 29000, qty: 0 },
                    { type: 'Pullman', description: 'Sector general', price: 19000, qty: 0 }
                ]
            },
            {
                id: 24,
                artist: 'Ráfaga',
                title: 'Ráfaga - Éxitos de Siempre Tour',
                date: '12 de Marzo, 2027',
                time: '22:00 hs',
                location: 'Luna Park, Buenos Aires',
                badge: 'Cumbia Clásica',
                image: 'https://images.unsplash.com/photo-1501386761578-eac5c94b800a?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Pista', description: 'Pista de baile general', price: 31000, qty: 0 },
                    { type: 'Platea', description: 'Asiento numerado', price: 54000, qty: 0 }
                ]
            },
            {
                id: 25,
                artist: 'Agapornis',
                title: 'Agapornis - Cumbia Pop Tour',
                date: '16 de Marzo, 2027',
                time: '21:00 hs',
                location: 'Movistar Arena, Buenos Aires',
                badge: 'Cumbia Pop',
                image: 'https://images.unsplash.com/photo-1514525253161-7a46d19cd819?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo General', description: 'Pista', price: 34000, qty: 0 },
                    { type: 'Platea Baja', description: 'Platea baja numerada', price: 62000, qty: 0 }
                ]
            }
        ];

        let selectedConcert = null;
        let timerInterval = null;
        let timerSeconds = 300;

        function initApp() {
            renderConcerts(concerts);
            renderQuickArtists();
            renderSuggestionsList();
        }

        function renderQuickArtists() {
            const container = document.getElementById('quickArtistsGrid');
            const topArtists = concerts.slice(0, 8);
            container.innerHTML = topArtists.map(c => `
                <div onclick="triggerQueue(${c.id})" class="bg-zinc-900/60 hover:bg-zinc-900 hover:border-red-600/50 border border-zinc-800 p-3 rounded-xl cursor-pointer transition group">
                    <div class="w-12 h-12 rounded-full overflow-hidden mx-auto mb-2 border border-red-500/30 group-hover:scale-110 transition shadow-md bg-zinc-950">
                        <img src="${c.image}" alt="${c.artist}" class="w-full h-full object-cover">
                    </div>
                    <h4 class="font-bold text-xs text-white truncate">${c.artist}</h4>
                </div>
            `).join('');
        }

        function renderSuggestionsList() {
            const list = document.getElementById('suggestionsList');
            list.innerHTML = concerts.map(c => `
                <div onclick="selectSuggestion('${c.artist}')" class="px-3 py-2 text-xs font-medium text-zinc-300 hover:bg-red-600/20 hover:text-white rounded-lg cursor-pointer transition truncate flex items-center gap-2">
                    <img src="${c.image}" class="w-5 h-5 rounded-full object-cover" alt=""> <span>${c.artist}</span>
                </div>
            `).join('');
        }

        function showSuggestions() {
            document.getElementById('suggestionsBox').classList.remove('hidden');
        }

        function selectSuggestion(artistName) {
            document.getElementById('searchInput').value = artistName;
            document.getElementById('suggestionsBox').classList.add('hidden');
            const foundConcert = concerts.find(c => c.artist.toLowerCase() === artistName.toLowerCase());
            if (foundConcert) {
                triggerQueue(foundConcert.id);
            } else {
                filterConcerts();
            }
        }

        function toggleCatalogDropdown() {
            const dropdown = document.getElementById('catalogDropdown');
            const backdrop = document.getElementById('catalogBackdrop');
            const isOpen = !dropdown.classList.contains('translate-x-full');
            document.getElementById('suggestionsBox').classList.add('hidden');

            if (!isOpen) {
                renderCatalogDropdownList();
                backdrop.classList.remove('hidden');
                dropdown.classList.remove('translate-x-full');
            } else {
                dropdown.classList.add('translate-x-full');
                setTimeout(() => backdrop.classList.add('hidden'), 300);
            }
        }

        function renderCatalogDropdownList() {
            const listContainer = document.getElementById('catalogDropdownList');
            listContainer.innerHTML = concerts.map(c => `
                <div onclick="selectArtistFromCatalog(${c.id})" class="bg-zinc-950 hover:bg-red-600/10 border border-zinc-800 hover:border-red-600/50 p-3.5 rounded-xl cursor-pointer transition group flex items-center gap-3">
                    <img src="${c.image}" class="w-12 h-12 rounded-lg object-cover flex-shrink-0 border border-zinc-800" alt="">
                    <div class="flex-grow min-w-0">
                        <div class="flex justify-between items-center">
                            <h4 class="font-black text-sm text-white group-hover:text-red-500 transition truncate">${c.artist}</h4>
                            <span class="text-[10px] bg-red-600/20 text-red-500 px-2 py-0.5 rounded-full font-bold flex-shrink-0">${c.date.split(',')[0]}</span>
                        </div>
                        <p class="text-[11px] text-zinc-400 truncate mt-0.5">📍 ${c.location}</p>
                        <div class="mt-1.5 pt-1.5 border-t border-zinc-800/80 flex justify-between items-center text-[11px]">
                            <span class="text-zinc-500">Entradas y Precios:</span>
                            <span class="font-bold text-red-400">Desde $${Math.min(...c.tickets.map(t => t.price)).toLocaleString()}</span>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        function selectArtistFromCatalog(id) {
            toggleCatalogDropdown();
            triggerQueue(id);
        }

        function filterConcerts() {
            const query = document.getElementById('searchInput').value.toLowerCase().trim();
            document.getElementById('suggestionsBox').classList.add('hidden');

            if (!query) {
                renderConcerts(concerts);
                return;
            }

            const foundConcert = concerts.find(c => 
                c.artist.toLowerCase().includes(query) || 
                c.title.toLowerCase().includes(query) ||
                c.location.toLowerCase().includes(query)
            );

            if (foundConcert && (query.length > 2 || concerts.some(c => c.artist.toLowerCase() === query))) {
                triggerQueue(foundConcert.id);
            } else {
                const filtered = concerts.filter(c => 
                    c.artist.toLowerCase().includes(query) || 
                    c.title.toLowerCase().includes(query) || 
                    c.location.toLowerCase().includes(query) ||
                    c.date.toLowerCase().includes(query)
                );
                renderConcerts(filtered);
            }
        }

        function renderConcerts(list) {
            const grid = document.getElementById('concertsGrid');
            const noResults = document.getElementById('noResults');
            const eventCount = document.getElementById('eventCount');
            const btnClear = document.getElementById('btnClear');

            eventCount.innerText = `${list.length} evento${list.length !== 1 ? 's' : ''}`;
            if (list.length > 0) btnClear.classList.remove('hidden');
            else btnClear.classList.add('hidden');

            if (list.length === 0) {
                grid.innerHTML = '';
                noResults.classList.remove('hidden');
                return;
            }

            noResults.classList.add('hidden');
            
            grid.innerHTML = list.map(c => {
                const minPrice = Math.min(...c.tickets.map(t => t.price));
                return `
                    <div class="bg-zinc-900 rounded-3xl overflow-hidden border border-zinc-800 hover:border-red-600/60 transition-all duration-300 group flex flex-col justify-between shadow-xl">
                        <div>
                            <div class="relative h-52 bg-zinc-950 overflow-hidden">
                                <img src="${c.image}" alt="${c.artist}" class="w-full h-full object-cover group-hover:scale-105 transition duration-700 opacity-85">
                                <div class="absolute inset-0 bg-gradient-to-t from-zinc-900 via-zinc-900/30 to-transparent"></div>
                                <span class="absolute top-3 left-3 bg-red-600 text-white text-[11px] font-black px-3 py-1 rounded-full shadow-md uppercase tracking-wider">${c.badge}</span>
                                <div class="absolute bottom-3 left-4 right-4">
                                    <h3 class="text-xl font-black text-white drop-shadow-md">${c.title}</h3>
                                </div>
                            </div>
                            
                            <div class="p-6 space-y-4">
                                <div class="flex items-center justify-between text-xs font-bold text-red-500 uppercase tracking-wider">
                                    <span class="flex items-center gap-1">📅 ${c.date}</span>
                                    <span class="bg-zinc-950 px-2.5 py-1 rounded-lg border border-zinc-800 text-zinc-300">🕒 ${c.time}</span>
                                </div>
                                <p class="text-zinc-400 text-sm flex items-center gap-1.5">
                                    📍 <span class="font-medium text-zinc-200">${c.location}</span>
                                </p>
                                <div class="pt-2 border-t border-zinc-800/80 flex items-center justify-between">
                                    <span class="text-xs text-zinc-400 uppercase font-bold tracking-wider">Entradas desde:</span>
                                    <span class="text-lg font-black text-white">$${minPrice.toLocaleString()}</span>
                                </div>
                            </div>
                        </div>

                        <div class="p-6 pt-0">
                            <button onclick="triggerQueue(${c.id})" class="w-full bg-zinc-800 hover:bg-red-600 text-white font-bold py-3.5 rounded-2xl transition shadow-md text-sm flex items-center justify-center gap-2">
                                Comprar Entradas Oficiales 🎟️
                            </button>
                        </div>
                    </div>
                `;
            }).join('');
        }

        function clearSearch() {
            document.getElementById('searchInput').value = '';
            document.getElementById('suggestionsBox').classList.add('hidden');
            renderConcerts(concerts);
        }

        function filterByGira() {
            resetApp();
            window.scrollTo({ top: 400, behavior: 'smooth' });
        }

        function showMyTicketsInfo() {
            alert("Para ver tus #eTickets comprados, completá el proceso de compra de cualquier concierto para generar tu código QR oficial.");
        }

        function triggerQueue(id) {
            selectedConcert = JSON.parse(JSON.stringify(concerts.find(c => c.id === id)));
            selectedConcert.tickets.forEach(t => t.qty = 0);

            document.getElementById('view-home').classList.add('hidden');
            document.getElementById('view-queue').classList.remove('hidden');
            document.getElementById('queuePosText').innerText = Math.floor(Math.random() * 50) + 10;

            setTimeout(() => {
                document.getElementById('view-queue').classList.add('hidden');
                document.getElementById('view-select').classList.remove('hidden');
                setupSelectTickets();
                startTimer();
            }, 1500);
        }

        function setupSelectTickets() {
            document.getElementById('selConcertMeta').innerText = selectedConcert.date + ' - ' + selectedConcert.time;
            document.getElementById('selConcertTitle').innerText = selectedConcert.title;
            document.getElementById('selConcertLoc').innerText = selectedConcert.location;

            const container = document.getElementById('ticketsListContainer');
            container.innerHTML = selectedConcert.tickets.map((t, idx) => `
                <div class="flex items-center justify-between bg-zinc-950 p-4 sm:p-5 rounded-2xl border border-zinc-800">
                    <div>
                        <h4 class="font-bold text-base text-white">${t.type}</h4>
                        <p class="text-xs text-zinc-400">${t.description}</p>
                        <span class="text-red-500 font-black text-base mt-1 block">$${t.price.toLocaleString()}</span>
                    </div>
                    <div class="flex items-center gap-3">
                        <button onclick="changeQty(${idx}, -1)" class="w-10 h-10 bg-zinc-900 border border-zinc-700 hover:bg-zinc-800 rounded-xl font-bold text-white transition">-</button>
                        <span id="qty-${idx}" class="w-8 text-center font-bold text-lg text-white">${t.qty}</span>
                        <button onclick="changeQty(${idx}, 1)" class="w-10 h-10 bg-red-600 hover:bg-red-700 text-white rounded-xl font-bold transition">+</button>
                    </div>
                </div>
            `).join('');
            updateTotal();
        }

        function changeQty(idx, delta) {
            selectedConcert.tickets[idx].qty = Math.max(0, selectedConcert.tickets[idx].qty + delta);
            document.getElementById(`qty-${idx}`).innerText = selectedConcert.tickets[idx].qty;
            updateTotal();
        }

        function updateTotal() {
            let total = selectedConcert.tickets.reduce((sum, t) => sum + (t.price * t.qty), 0);
            document.getElementById('totalPriceText').innerText = '$' + total.toLocaleString();
            document.getElementById('checkoutTotalText').innerText = '$' + total.toLocaleString();
            
            const btn = document.getElementById('btnCheckout');
            if (total > 0) btn.removeAttribute('disabled');
            else btn.setAttribute('disabled', 'true');
        }

        function startTimer() {
            timerSeconds = 300;
            clearInterval(timerInterval);
            timerInterval = setInterval(() => {
                if (timerSeconds > 0) {
                    timerSeconds--;
                    let m = Math.floor(timerSeconds / 60);
                    let s = timerSeconds % 60;
                    document.getElementById('timerText').innerText = `${m}:${s < 10 ? '0' : ''}${s}`;
                } else {
                    clearInterval(timerInterval);
                    alert('El tiempo de reserva expiró.');
                    resetApp();
                }
            }, 1000);
        }

        function proceedToCheckout() {
            clearInterval(timerInterval);
            document.getElementById('view-select').classList.add('hidden');
            document.getElementById('view-checkout').classList.remove('hidden');
        }

        function processPayment(e) {
            e.preventDefault();
            const name = document.getElementById('buyerName').value;
            const email = document.getElementById('buyerEmail').value;
            const paymentMethod = document.getElementById('paymentMethod').value;

            let total = 0;
            let ticketsSummary = "";
            selectedConcert.tickets.forEach(t => {
                if(t.qty > 0) {
                    ticketsSummary += `\n- ${t.qty}x ${t.type} ($${(t.price * t.qty).toLocaleString()})`;
                    total += t.price * t.qty;
                }
            });

            const whatsappNumber = "5492364281582";
            const message = `Hola! 👋 Quiero confirmar mi compra en tiket_arg:\n\n🎤 *Artista/Show:* ${selectedConcert.title}\n📍 *Lugar:* ${selectedConcert.location}\n📅 *Fecha:* ${selectedConcert.date}\n\n🎟️ *Entradas:* ${ticketsSummary}\n\n💰 *Total a Pagar:* $${total.toLocaleString()}\n💳 *Método de Pago:* ${paymentMethod}\n\n👤 *Titular:* ${name}\n📧 *Email:* ${email}`;
            const whatsappUrl = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;

            document.getElementById('view-checkout').classList.add('hidden');
            document.getElementById('view-success').classList.remove('hidden');

            document.getElementById('successTitle').innerText = selectedConcert.title;
            document.getElementById('successDate').innerText = selectedConcert.date + ' - ' + selectedConcert.time;
            document.getElementById('successBuyer').innerText = name;
            document.getElementById('successLoc').innerText = selectedConcert.location;

            setTimeout(() => {
                const qrContainer = document.getElementById("qrcode");
                qrContainer.innerHTML = "";
                new QRCode(qrContainer, {
                    text: `TIKEARG-WHATSAPP-RESERVA-${selectedConcert.artist}-${name}`,
                    width: 140,
                    height: 140
                });

                window.open(whatsappUrl, '_blank');
            }, 100);
        }

        function resetApp() {
            clearInterval(timerInterval);
            document.getElementById('view-queue').classList.add('hidden');
            document.getElementById('view-select').classList.add('hidden');
            document.getElementById('view-checkout').classList.add('hidden');
            document.getElementById('view-success').classList.add('hidden');
            document.getElementById('view-home').classList.remove('hidden');
            
            const dropdown = document.getElementById('catalogDropdown');
            const backdrop = document.getElementById('catalogBackdrop');
            dropdown.classList.add('translate-x-full');
            backdrop.classList.add('hidden');
            
            clearSearch();
        }

        initApp();
    </script>
</body>
</html>
