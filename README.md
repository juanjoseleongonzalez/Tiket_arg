<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>tike_arg - Venta Oficial de Entradas en Argentina</title>
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

    <!-- ================= PASO 1: CABEZAL / HEADER OFICIAL ================= -->
    <header class="sticky top-0 z-50 bg-zinc-950/95 backdrop-blur-md border-b border-zinc-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <!-- Logo -->
            <div class="flex items-center space-x-2 cursor-pointer group" onclick="resetApp()">
                <span class="text-2xl font-black tracking-tight text-white group-hover:text-red-500 transition">tike<span class="text-red-600">_arg</span></span>
                <span class="text-[10px] uppercase font-extrabold bg-red-600/20 text-red-500 border border-red-500/30 px-2 py-0.5 rounded-full">Oficial</span>
            </div>

            <!-- Navegación -->
            <nav class="hidden md:flex space-x-8 text-sm font-semibold text-zinc-300">
                <a href="#" onclick="resetApp(); return false;" class="hover:text-red-500 transition">Conciertos</a>
                <a href="#" onclick="filterByGira(); return false;" class="hover:text-red-500 transition">Giras 2026</a>
                <a href="#" onclick="showMyTicketsInfo(); return false;" class="hover:text-red-500 transition">Mis #eTickets</a>
            </nav>

            <!-- Seguridad SSL -->
            <div class="flex items-center space-x-2">
                <span class="text-xs bg-zinc-900 text-zinc-300 border border-zinc-800 px-3.5 py-1.5 rounded-full font-medium flex items-center gap-1.5 shadow-inner">
                    <span class="w-2 h-2 rounded-full bg-emerald-500 animate-pulse"></span> Venta Segura SSL
                </span>
            </div>
        </div>
    </header>

    <!-- ================= PASO 2: VISTA PRINCIPAL (INICIO, HERO Y SPONSORS) ================= -->
    <div id="view-home">
        <!-- Hero / Presentación Atractiva -->
        <section class="relative py-20 lg:py-28 overflow-hidden border-b border-zinc-800/80 bg-gradient-to-b from-zinc-900 to-zinc-950 text-center px-4">
            <div class="absolute inset-0 opacity-20 bg-[radial-gradient(#dc2626_1px,transparent_1px)] [background-size:16px_16px]"></div>
            
            <div class="relative max-w-4xl mx-auto space-y-6">
                <div class="inline-flex items-center gap-2 bg-red-600/10 border border-red-600/30 text-red-500 text-xs font-bold px-4 py-1.5 rounded-full uppercase tracking-widest shadow-sm">
                    ⚡ Plataforma Nº1 de Venta de Entradas en Argentina
                </div>
                
                <h1 class="text-4xl sm:text-7xl font-black tracking-tight text-white">
                    Vivir la música <span class="text-transparent bg-clip-text bg-gradient-to-r from-red-500 to-rose-600">nunca fue tan fácil</span>
                </h1>
                
                <p class="text-zinc-400 text-base sm:text-xl max-w-2xl mx-auto font-medium">
                    Encontrá tus artistas favoritos, consultá fechas, horarios y estadios, y asegurá tus entradas oficiales en segundos.
                </p>
                
                <!-- Buscador Rápido y Botón Lista de Artistas y Precios -->
                <div class="max-w-2xl mx-auto relative pt-2 flex flex-col sm:flex-row gap-3 justify-center items-center">
                    <div class="flex items-center px-3 bg-zinc-900/90 backdrop-blur rounded-2xl border-2 border-red-600/60 shadow-2xl shadow-red-950/30 flex-grow w-full">
                        <span class="text-zinc-500 text-lg mr-2">🔍</span>
                        <input type="text" id="searchInput" oninput="filterConcerts()" onfocus="showSuggestions()" placeholder="Buscá tu artista (ej: Maria Becerra, Duki, Emilia)..." class="w-full bg-transparent py-3.5 text-white placeholder-zinc-500 focus:outline-none text-sm font-semibold">
                    </div>

                    <!-- Botón Lista con desplegable de Artistas y Precios -->
                    <div class="relative w-full sm:w-auto">
                        <button type="button" onclick="toggleCatalogDropdown()" class="w-full bg-zinc-800 hover:bg-zinc-700 text-white font-bold px-6 py-4 rounded-2xl transition text-sm border border-zinc-700 flex items-center justify-center gap-2 shadow-xl whitespace-nowrap">
                            📋 Lista de Artistas y Precios ▾
                        </button>

                        <!-- Menú Desplegable con los Artistas y sus Precios -->
                        <div id="catalogDropdown" class="absolute left-0 sm:right-0 sm:left-auto mt-2 w-full sm:w-96 bg-zinc-900 border border-zinc-800 rounded-2xl shadow-2xl z-50 hidden max-h-96 overflow-y-auto p-3 text-left">
                            <div class="px-3 py-2 text-xs font-bold text-zinc-400 uppercase tracking-wider border-b border-zinc-800 mb-2 flex justify-between items-center">
                                <span>Seleccioná un Artista</span>
                                <span class="text-[10px] text-red-500">Ver precios</span>
                            </div>
                            <div id="catalogDropdownList" class="space-y-2">
                                <!-- Se llena por JavaScript -->
                            </div>
                        </div>
                    </div>

                    <!-- Sugerencias de búsqueda -->
                    <div id="suggestionsBox" class="absolute left-0 right-0 top-20 mt-2 bg-zinc-900 border border-zinc-800 rounded-2xl shadow-2xl z-50 hidden max-h-64 overflow-y-auto p-2 text-left">
                        <div class="px-3 py-2 text-xs font-bold text-zinc-400 uppercase tracking-wider border-b border-zinc-800 mb-1">Artistas sugeridos:</div>
                        <div id="suggestionsList" class="grid grid-cols-2 gap-1"></div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Galería de Sponsors / Artistas Destacados del Año -->
        <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 border-b border-zinc-900">
            <div class="flex items-center justify-between mb-6">
                <h3 class="text-xs font-bold uppercase tracking-widest text-zinc-400">⭐ Sponsors y Shows Destacados 2026</h3>
                <span class="text-[10px] bg-red-600/10 text-red-500 border border-red-500/20 px-2.5 py-1 rounded-md font-bold uppercase">Oficiales</span>
            </div>
            <div id="quickArtistsGrid" class="grid grid-cols-2 sm:grid-cols-4 md:grid-cols-8 gap-3 text-center">
                <!-- Se llena por JS dinámicamente -->
            </div>
        </section>

        <!-- Cuerpo de la Página: Cartelera Completa -->
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

            <!-- Grilla Dinámica de Conciertos -->
            <div id="concertsGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8"></div>
        </main>
    </div>

    <!-- ================= PASO 3: SALA DE ESPERA / FILA VIRTUAL ================= -->
    <div id="view-queue" class="max-w-xl mx-auto px-4 py-32 text-center hidden">
        <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-8 sm:p-12 shadow-2xl space-y-6">
            <div class="w-16 h-16 bg-red-600/10 text-red-500 rounded-full flex items-center justify-center text-2xl mx-auto border border-red-500/20 animate-pulse">⏳</div>
            <div>
                <span class="text-xs uppercase font-bold text-red-500 tracking-wider">Sala de Espera Virtual tike_arg</span>
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
            <p class="text-zinc-400 text-sm mb-6">Ingresá tus datos para emitir las entradas oficiales con código QR de acceso al estadio.</p>
            
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
                    <label class="block text-xs font-semibold uppercase text-zinc-400 mb-1">Método de Pago Seleccionado</label>
                    <select class="w-full bg-zinc-950 border border-zinc-800 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-red-600 text-white font-medium">
                        <option value="mercadopago">Mercado Pago / Tarjeta de Crédito / Débito / Rapipago</option>
                    </select>
                </div>

                <div class="pt-4 border-t border-zinc-800 flex items-center justify-between">
                    <div>
                        <p class="text-xs text-zinc-400">Total final a pagar:</p>
                        <p id="checkoutTotalText" class="text-2xl font-black text-red-500">$0</p>
                    </div>
                    <button type="submit" class="bg-red-600 hover:bg-red-700 text-white font-bold px-8 py-4 rounded-2xl transition text-sm shadow-lg shadow-red-600/30">
                        Pagar de Forma Segura 🔒
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- ================= PASO 6: COMPRA EXITOSA Y QR DE ACCESO ================= -->
    <div id="view-success" class="max-w-xl mx-auto px-4 py-12 text-center hidden">
        <div class="bg-zinc-900 border border-zinc-800 rounded-3xl p-8 sm:p-10 shadow-xl">
            <div class="w-16 h-16 bg-emerald-500/10 text-emerald-500 rounded-full flex items-center justify-center text-3xl mx-auto mb-4 border border-emerald-500/20">✓</div>
            <h2 class="text-2xl font-bold text-white mb-1">¡Compra Exitosa (#eTicket)!</h2>
            <p class="text-zinc-400 text-sm mb-6">Tu pago fue aprobado con éxito. Presentá este código QR dinámico directamente desde tu celular en el ingreso al estadio.</p>
            
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
                    <p class="text-xs text-zinc-500 mb-2">Código QR Verificado:</p>
                    <div id="qrcode" class="bg-white p-3 rounded-xl border border-zinc-800 shadow-sm"></div>
                </div>
            </div>

            <button onclick="resetApp()" class="w-full bg-white hover:bg-zinc-200 text-zinc-950 font-bold py-3.5 rounded-2xl transition text-sm shadow">
                Volver al Inicio de tike_arg
            </button>
        </div>
    </div>

    <!-- ================= SCRIPT DE LÓGICA PASO A PASO ================= -->
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
                artist: 'Lali',
                title: 'Lali - Disciplina Tour',
                date: '08 de Diciembre, 2026',
                time: '21:00 hs',
                location: 'DirecTV Arena, Buenos Aires',
                badge: 'Destacado',
                image: 'https://images.unsplash.com/photo-1501386761578-eac5c94b800a?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Acceso general', price: 44000, qty: 0 },
                    { type: 'Platea Preferencial', description: 'Asiento reservado', price: 78000, qty: 0 }
                ]
            },
            {
                id: 6,
                artist: 'Tini',
                title: 'Tini - Tour Oficial 2026',
                date: '15 de Diciembre, 2026',
                time: '20:30 hs',
                location: 'Tecnópolis, Buenos Aires',
                badge: 'Popular',
                image: 'https://images.unsplash.com/photo-1511671782779-c97d3d27a1d4?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo General', description: 'Pista libre', price: 42000, qty: 0 },
                    { type: 'Platea VIP', description: 'Cercano al escenario', price: 85000, qty: 0 }
                ]
            },
            {
                id: 7,
                artist: 'Bizarrap',
                title: 'Bizarrap - Live Experience',
                date: '20 de Diciembre, 2026',
                time: '22:00 hs',
                location: 'Hipódromo de Palermo, Buenos Aires',
                badge: 'Fiesta Total',
                image: 'https://images.unsplash.com/photo-1516450360452-9312f5e86fc7?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo General', description: 'Pista principal', price: 50000, qty: 0 },
                    { type: 'VIP Deck', description: 'Sector exclusivo con barra', price: 115000, qty: 0 }
                ]
            },
            {
                id: 8,
                artist: 'Wos',
                title: 'Wos - Descartable Tour',
                date: '22 de Diciembre, 2026',
                time: '21:00 hs',
                location: 'Estadio Único de La Plata, Buenos Aires',
                badge: 'Últimas Fechas',
                image: 'https://images.unsplash.com/photo-1470225620780-dba8ba36b745?auto=format&fit=crop&w=800&q=80',
                tickets: [
                    { type: 'Campo', description: 'Campo general', price: 43000, qty: 0 },
                    { type: 'Platea', description: 'Tribuna numerada', price: 71000, qty: 0 }
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

        // Renderiza los artistas sponsors en el hero
        function renderQuickArtists() {
            const container = document.getElementById('quickArtistsGrid');
            const topArtists = concerts.slice(0, 8);
            container.innerHTML = topArtists.map(c => `
                <div onclick="triggerQueue(${c.id})" class="bg-zinc-900/60 hover:bg-zinc-900 hover:border-red-600/50 border border-zinc-800 p-3 rounded-xl cursor-pointer transition group">
                    <div class="w-10 h-10 bg-red-600/10 text-red-500 rounded-full flex items-center justify-center font-black text-xs mx-auto mb-1 group-hover:scale-110 transition border border-red-500/20">
                        ${c.artist.substring(0, 2).toUpperCase()}
                    </div>
                    <h4 class="font-bold text-xs text-white truncate">${c.artist}</h4>
                </div>
            `).join('');
        }

        // Renderiza sugerencias rápidas en el buscador
        function renderSuggestionsList() {
            const list = document.getElementById('suggestionsList');
            list.innerHTML = concerts.map(c => `
                <div onclick="selectSuggestion('${c.artist}')" class="px-3 py-2 text-xs font-medium text-zinc-300 hover:bg-red-600/20 hover:text-white rounded-lg cursor-pointer transition truncate">
                    🎤 ${c.artist}
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

        // Desplegable del botón "Lista de Artistas y Precios"
        function toggleCatalogDropdown() {
            const dropdown = document.getElementById('catalogDropdown');
            const isHidden = dropdown.classList.contains('hidden');
            document.getElementById('suggestionsBox').classList.add('hidden');

            if (isHidden) {
                renderCatalogDropdownList();
                dropdown.classList.remove('hidden');
            } else {
                dropdown.classList.add('hidden');
            }
        }

        function renderCatalogDropdownList() {
            const listContainer = document.getElementById('catalogDropdownList');
            listContainer.innerHTML = concerts.map(c => `
                <div onclick="selectArtistFromCatalog(${c.id})" class="bg-zinc-950 hover:bg-red-600/10 border border-zinc-800 hover:border-red-600/50 p-3 rounded-xl cursor-pointer transition group">
                    <div class="flex justify-between items-center">
                        <h4 class="font-black text-sm text-white group-hover:text-red-500 transition">🎤 ${c.artist}</h4>
                        <span class="text-[10px] bg-red-600/20 text-red-500 px-2 py-0.5 rounded-full font-bold">${c.date.split(',')[0]}</span>
                    </div>
                    <p class="text-[11px] text-zinc-400 truncate mt-1">📍 ${c.location}</p>
                    <div class="mt-2 pt-2 border-t border-zinc-800/80 flex justify-between items-center text-[11px]">
                        <span class="text-zinc-500">Entradas y Precios:</span>
                        <span class="font-bold text-red-400">Desde $${Math.min(...c.tickets.map(t => t.price)).toLocaleString()}</span>
                    </div>
                </div>
            `).join('');
        }

        function selectArtistFromCatalog(id) {
            document.getElementById('catalogDropdown').classList.add('hidden');
            triggerQueue(id);
        }

        // Buscador inteligente en tiempo real
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

        // Renderizado de la cartelera principal
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
                                <img src="${c.image}" alt="${c.artist}" class="w-full h-full object-cover group-hover:scale-105 transition duration-700 opacity-80">
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

        // Fila virtual de espera
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

        // Selección de ubicaciones y precios
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

        // Procesamiento de pago seguro y generación de QR
        function processPayment(e) {
            e.preventDefault();
            const name = document.getElementById('buyerName').value;

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
                    text: `TIKEARG-OFICIAL-VERIFICADO-${selectedConcert.artist}-${name}`,
                    width: 140,
                    height: 140
                });
            }, 100);
        }

        function resetApp() {
            clearInterval(timerInterval);
            document.getElementById('view-queue').classList.add('hidden');
            document.getElementById('view-select').classList.add('hidden');
            document.getElementById('view-checkout').classList.add('hidden');
            document.getElementById('view-success').classList.add('hidden');
            document.getElementById('view-home').classList.remove('hidden');
            document.getElementById('catalogDropdown').classList.add('hidden');
            clearSearch();
        }

        // Cierre de menús al hacer clic fuera
        document.addEventListener('click', function(e) {
            const dropdown = document.getElementById('catalogDropdown');
            const catalogBtn = document.querySelector('button[onclick="toggleCatalogDropdown()"]');
            if (dropdown && catalogBtn && !dropdown.contains(e.target) && !catalogBtn.contains(e.target)) {
                dropdown.classList.add('hidden');
            }
        });

        // Inicialización general
        initApp();
    </script>
</body>
</html>
