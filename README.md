<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>tike_arg - Venta Oficial de Entradas</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Alpine.js -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
    <!-- Generador de QR -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
</head>
<body class="bg-white text-zinc-900 font-sans antialiased" x-data="ticketApp()">

    <!-- BARRA DE NAVEGACIÓN -->
    <header class="sticky top-0 z-50 bg-white/95 backdrop-blur border-b border-zinc-200">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <div class="flex items-center space-x-2 cursor-pointer" @click="resetApp()">
                <span class="text-2xl font-black tracking-wider text-red-600">tike<span class="text-zinc-900">_arg</span></span>
                <span class="text-xs bg-red-100 text-red-700 font-bold px-2 py-0.5 rounded">Oficial</span>
            </div>
            <nav class="hidden md:flex space-x-8 text-sm font-medium text-zinc-600">
                <a href="#" @click.prevent="resetApp()" class="hover:text-red-600 transition">Conciertos</a>
                <a href="#" @click.prevent="resetApp()" class="hover:text-red-600 transition">Giras 2026</a>
                <a href="#" @click.prevent="resetApp()" class="hover:text-red-600 transition">Mis #eTickets</a>
            </nav>
            <div>
                <span class="text-xs bg-red-50 text-red-600 border border-red-200 px-3 py-1.5 rounded-full font-medium">
                    🔒 Venta Segura SSL
                </span>
            </div>
        </div>
    </header>

>    <!-- ================= VISTA 1: PRESENTACIÓN E INICIO ================= -->
    <div x-show="view === 'home'">
        <!-- Presentación Principal y Buscador -->
        <section class="relative py-20 bg-gradient-to-b from-zinc-50 to-white border-b border-zinc-200 text-center px-4">
            <div class="max-w-4xl mx-auto">
                <span class="inline-block bg-red-600 text-white text-xs font-bold px-4 py-1.5 rounded-full uppercase tracking-widest mb-6 shadow-sm">
                    Plataforma Nº1 de Venta de Entradas en Argentina
                </span>
                <h1 class="text-4xl sm:text-7xl font-black tracking-tight mb-6 text-zinc-900">
                    tike<span class="text-red-600">_arg</span>
                </h1>
                <p class="text-zinc-600 text-lg sm:text-xl mb-10 max-w-2xl mx-auto">
                    Encontrá de forma rápida y cómoda a tus artistas favoritos, consultá sus horarios y asegurá tus entradas oficiales.
                </p>
                
                <!-- Buscador ultra cómodo -->
                <div class="max-w-2xl mx-auto flex flex-col sm:flex-row gap-3 bg-white p-2 rounded-2xl border-2 border-red-500 shadow-2xl">
                    <input type="text" x-model.debounce.300ms="searchQuery" placeholder="Buscá por artista (ej: Maria Becerra, Duki, Ed Sheeran)..." class="flex-grow bg-transparent px-4 py-3 text-zinc-900 placeholder-zinc-400 focus:outline-none text-sm sm:text-base font-medium">
                    <button type="button" class="bg-red-600 hover:bg-red-700 text-white font-bold px-8 py-3.5 rounded-xl transition text-sm shadow-md">
                        Buscar Artista
                    </button>
                </div>
            </div>
        </section

        <!-- Galería de Presentación: Artistas Destacados de la Argentina -->
        <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12 border-b border-zinc-100">
            <h3 class="text-sm font-bold uppercase tracking-wider text-zinc-400 mb-6 text-center">Artistas Destacados en Cartelera</h3>
            <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-6 gap-4 text-center">
                <div @click="searchQuery = 'Maria Becerra'" class="bg-zinc-50 hover:border-red-500 border border-zinc-200 p-4 rounded-2xl cursor-pointer transition group">
                    <div class="w-16 h-16 bg-red-100 text-red-600 rounded-full flex items-center justify-center font-black text-xl mx-auto mb-2 group-hover:scale-110 transition">MB</div>
                    <h4 class="font-bold text-sm text-zinc-900">Maria Becerra</h4>
                </div>
                <div @click="searchQuery = 'Duki'" class="bg-zinc-50 hover:border-red-500 border border-zinc-200 p-4 rounded-2xl cursor-pointer transition group">
                    <div class="w-16 h-16 bg-red-100 text-red-600 rounded-full flex items-center justify-center font-black text-xl mx-auto mb-2 group-hover:scale-110 transition">DK</div>
                    <h4 class="font-bold text-sm text-zinc-900">Duki</h4>
                </div>
                <div @click="searchQuery = 'Ed Sheeran'" class="bg-zinc-50 hover:border-red-500 border border-zinc-200 p-4 rounded-2xl cursor-pointer transition group">
                    <div class="w-16 h-16 bg-red-100 text-red-600 rounded-full flex items-center justify-center font-black text-xl mx-auto mb-2 group-hover:scale-110 transition">ES</div>
                    <h4 class="font-bold text-sm text-zinc-900">Ed Sheeran</h4>
                </div>
                <div @click="searchQuery = 'Coldplay'" class="bg-zinc-50 hover:border-red-500 border border-zinc-200 p-4 rounded-2xl cursor-pointer transition group">
                    <div class="w-16 h-16 bg-red-100 text-red-600 rounded-full flex items-center justify-center font-black text-xl mx-auto mb-2 group-hover:scale-110 transition">CP</div>
                    <h4 class="font-bold text-sm text-zinc-900">Coldplay</h4>
                </div>
                <div @click="searchQuery = 'Shakira'" class="bg-zinc-50 hover:border-red-500 border border-zinc-200 p-4 rounded-2xl cursor-pointer transition group">
                    <div class="w-16 h-16 bg-red-100 text-red-600 rounded-full flex items-center justify-center font-black text-xl mx-auto mb-2 group-hover:scale-110 transition">SK</div>
                    <h4 class="font-bold text-sm text-zinc-900">Shakira</h4>
                </div>
                <div @click="searchQuery = 'Maná'" class="bg-zinc-50 hover:border-red-500 border border-zinc-200 p-4 rounded-2xl cursor-pointer transition group">
                    <div class="w-16 h-16 bg-red-100 text-red-600 rounded-full flex items-center justify-center font-black text-xl mx-auto mb-2 group-hover:scale-110 transition">MN</div>
                    <h4 class="font-bold text-sm text-zinc-900">Maná</h4>
                </div>
            </div>
        </section>

        <!-- Cartelera General con Fechas y Horarios Reales -->
        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
            <div class="mb-10 flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
                <div>
                    <h2 class="text-2xl sm:text-3xl font-extrabold tracking-tight text-zinc-900">Próximos Conciertos y Shows</h2>
                    <p class="text-zinc-500 text-sm mt-1">Fechas oficiales, horarios de apertura y estadios en Argentina.</p>
                </div>
                <div class="text-xs bg-zinc-100 text-zinc-600 font-bold px-3 py-1.5 rounded-lg uppercase tracking-wider" x-text="filteredConcerts.length + ' eventos disponibles'"></div>
            </div>

            <!-- Sin resultados -->
            <div x-show="filteredConcerts.length === 0" class="text-center py-20 bg-zinc-50 rounded-3xl border border-zinc-200">
                <p class="text-zinc-600 text-lg font-semibold">No encontramos conciertos para tu búsqueda.</p>
                <button @click="searchQuery = ''" class="mt-4 bg-red-600 text-white px-6 py-2.5 rounded-xl text-sm font-bold shadow hover:bg-red-700 transition">Ver todos los eventos</button>
            </div>

            <!-- Grilla de Conciertos Real -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <template x-for="concert in filteredConcerts" :key="concert.id">
                    <div class="bg-white rounded-3xl overflow-hidden border border-zinc-200 hover:border-red-400 transition-all duration-300 group flex flex-col justify-between shadow-sm hover:shadow-xl">
                        <div>
                            <!-- Cabecera de la Tarjeta -->
                            <div class="relative h-48 bg-zinc-900 overflow-hidden flex items-center justify-center p-6 text-center">
                                <div class="absolute inset-0 bg-gradient-to-t from-zinc-950 via-zinc-900/60 to-transparent z-10"></div>
                                <span class="relative z-20 text-white font-black text-2xl group-hover:scale-105 transition duration-500" x-text="concert.artist"></span>
                                <span class="absolute top-3 left-3 z-30 bg-red-600 text-white text-xs font-bold px-3 py-1 rounded-full shadow" x-text="concert.badge"></span>
                            </div>
                            
                            <!-- Información y Horarios Reales -->
                            <div class="p-6 space-y-3">
                                <div class="flex items-center justify-between text-xs font-bold text-red-600 uppercase tracking-wider">
                                    <span x-text="concert.date"></span>
                                    <span class="bg-red-50 px-2.5 py-1 rounded-md border border-red-200" x-text="'🕒 ' + concert.time"></span>
                                </div>
                                <h3 class="text-xl font-bold text-zinc-900" x-text="concert.title"></h3>
                                <p class="text-zinc-500 text-sm flex items-center gap-1.5">
                                    📍 <span class="font-medium text-zinc-700" x-text="concert.location"></span>
                                </p>
                            </div>
                        </div>

                        <!-- Botón de Compra -->
                        <div class="p-6 pt-0">
                            <button @click="triggerQueue(concert)" class="w-full bg-zinc-900 hover:bg-red-600 text-white font-bold py-3.5 rounded-2xl transition shadow-md text-sm">
                                Comprar Entradas Oficiales
                            </button>
                        </div>
                    </div>
                </template>
            </div>
        </main>
    </div>

    <!-- ================= VISTA 2: FILA VIRTUAL ================= -->
    <div x-show="view === 'queue'" class="max-w-xl mx-auto px-4 py-24 text-center">
        <div class="bg-white border border-zinc-200 rounded-3xl p-8 sm:p-12 shadow-2xl space-y-6">
            <div class="w-16 h-16 bg-red-50 text-red-600 rounded-full flex items-center justify-center text-2xl mx-auto border border-red-200 animate-pulse">⏳</div>
            <div>
                <span class="text-xs uppercase font-bold text-red-600 tracking-wider">Sala de Espera Virtual tike_arg</span>
                <h2 class="text-2xl font-black text-zinc-900 mt-1">Estás formados en la fila</h2>
                <p class="text-zinc-500 text-sm mt-2">Hay alta demanda para este show. Aguardá unos segundos para ingresar al sistema seguro de ubicaciones.</p>
            </div>

            <div class="bg-zinc-50 p-6 rounded-2xl border border-zinc-200 space-y-2">
                <p class="text-xs text-zinc-400">Tu lugar aproximado:</p>
                <p class="text-4xl font-black text-red-600" x-text="queuePosition"></p>
                <p class="text-xs text-zinc-500 pt-2">Acceso estimado en: <span class="font-bold text-zinc-800">Menos de 1 minuto</span></p>
            </div>

            <p class="text-xs text-zinc-400">No cierres esta ventana para no perder tu turno.</p>
        </div>
    </div>

    <!-- ================= VISTA 3: SELECCIÓN DE ENTRADAS + CRONÓMETRO ================= -->
    <div x-show="view === 'select-tickets'" class="max-w-4xl mx-auto px-4 py-12">
        <div class="bg-red-600 text-white px-6 py-3.5 rounded-2xl mb-6 flex items-center justify-between shadow-md">
            <span class="text-xs font-semibold uppercase tracking-wider">⏱ Tiempo reservado para completar tu compra:</span>
            <span class="text-lg font-black" x-text="formatTime(timerSeconds)"></span>
        </div>

        <div class="bg-white border border-zinc-200 rounded-3xl p-6 sm:p-10 shadow-xl">
            <div class="flex flex-col sm:flex-row justify-between sm:items-center gap-2 border-b border-zinc-100 pb-4 mb-6">
                <div>
                    <span class="text-xs font-bold text-red-600 uppercase tracking-widest" x-text="selectedConcert?.date + ' - ' + selectedConcert?.time"></span>
                    <h2 class="text-3xl font-extrabold text-zinc-900 mt-1" x-text="selectedConcert?.title"></h2>
                </div>
                <span class="text-sm font-medium text-zinc-500 bg-zinc-100 px-3 py-1.5 rounded-xl self-start" x-text="selectedConcert?.location"></span>
            </div>

            <h3 class="text-lg font-bold text-zinc-900 mb-4">Seleccioná tus ubicaciones y costos:</h3>
            
            <div class="space-y-4 mb-8">
                <template x-for="ticket in selectedConcert?.tickets" :key="ticket.type">
                    <div class="flex items-center justify-between bg-zinc-50 p-4 sm:p-5 rounded-2xl border border-zinc-200">
                        <div>
                            <h4 class="font-bold text-base text-zinc-900" x-text="ticket.type"></h4>
                            <p class="text-xs text-zinc-500" x-text="ticket.description"></p>
                            <span class="text-red-600 font-black text-base mt-1 block" x-text=" '$' + ticket.price.toLocaleString() "></span>
                        </div>
                        <div class="flex items-center gap-3">
                            <button @click="decrementTicket(ticket)" class="w-10 h-10 bg-white border border-zinc-300 hover:bg-zinc-100 rounded-xl font-bold text-zinc-800 transition">-</button>
                            <span class="w-8 text-center font-bold text-lg text-zinc-900" x-text="ticket.qty"></span>
                            <button @click="incrementTicket(ticket)" class="w-10 h-10 bg-red-600 hover:bg-red-700 text-white rounded-xl font-bold transition">+</button>
                        </div>
                    </div>
                </template>
            </div>

            <div class="bg-zinc-50 p-6 rounded-2xl border border-zinc-200 flex flex-col sm:flex-row items-center justify-between gap-4">
                <div>
                    <p class="text-xs text-zinc-500">Total a abonar:</p>
                    <p class="text-3xl font-black text-red-600" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                </div>
                <button @click="proceedToCheckout()" :disabled="calculateTotal() === 0" class="w-full sm:w-auto bg-red-600 hover:bg-red-700 disabled:bg-zinc-200 disabled:text-zinc-400 text-white font-bold px-8 py-4 rounded-2xl transition text-sm shadow-md">
                    Continuar al Pago Seguro →
                </button>
            </div>
        </div>
    </div>

    <!-- ================= VISTA 4: PAGO SEGURO ================= -->
    <div x-show="view === 'checkout'" class="max-w-2xl mx-auto px-4 py-12">
        <div class="bg-white border border-zinc-200 rounded-3xl p-6 sm:p-10 shadow-xl">
            <h2 class="text-2xl font-bold text-zinc-900 mb-2">Finalizar Compra (#eTicket)</h2>
            <p class="text-zinc-500 text-sm mb-6">Ingresá tus datos para emitir las entradas oficiales con código QR.</p>
            
            <form @submit.prevent="processPayment" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Nombre y Apellido del Titular</label>
                    <input type="text" required x-model="buyer.name" placeholder="Ej: León Pérez" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm text-zinc-900 focus:outline-none focus:border-red-600">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Correo Electrónico (Para recibir el acceso QR)</label>
                    <input type="email" required x-model="buyer.email" placeholder="tu@correo.com" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm text-zinc-900 focus:outline-none focus:border-red-600">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Medio de Pago</label>
                    <select x-model="buyer.paymentMethod" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-red-600 text-zinc-900">
                        <option value="mercadopago">Mercado Pago / Tarjeta de Crédito / Débito</option>
                    </select>
                </div>

                <div class="pt-4 border-t border-zinc-100 flex items-center justify-between">
                    <div>
                        <p class="text-xs text-zinc-500">Total final:</p>
                        <p class="text-2xl font-black text-red-600" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                    </div>
                    <button type="submit" class="bg-red-600 hover:bg-red-700 text-white font-bold px-8 py-4 rounded-2xl transition text-sm shadow-md">
                        Pagar de Forma Segura 🔒
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- ================= VISTA 5: #eTICKET EXITOSO Y QR ================= -->
    <div x-show="view === 'success'" class="max-w-xl mx-auto px-4 py-12 text-center">
        <div class="bg-white border border-zinc-200 rounded-3xl p-8 sm:p-10 shadow-xl">
            <div class="w-16 h-16 bg-red-50 text-red-600 rounded-full flex items-center justify-center text-3xl mx-auto mb-4 border border-red-200">✓</div>
            <h2 class="text-2xl font-bold text-zinc-900 mb-1">¡Compra Exitosa (#eTicket)!</h2>
            <p class="text-zinc-500 text-sm mb-6">Tu pago fue aprobado con éxito. Presentá este código QR directamente desde tu celular en el ingreso al estadio.</p>
            
            <div class="bg-zinc-50 border border-zinc-200 rounded-2xl p-6 text-left mb-6 space-y-3 shadow-inner">
                <div class="flex justify-between items-center border-b border-zinc-200 pb-3">
                    <span class="text-xs uppercase font-bold text-red-600" x-text="selectedConcert?.title"></span>
                    <span class="text-xs text-zinc-500" x-text="selectedConcert?.date + ' - ' + selectedConcert?.time"></span>
                </div>
                <div>
                    <p class="text-xs text-zinc-400">Titular:</p>
                    <p class="text-sm font-semibold text-zinc-800" x-text="buyer.name"></p>
                </div>
                <div>
                    <p class="text-xs text-zinc-400">Estadio / Recinto:</p>
                    <p class="text-sm font-semibold text-zinc-800" x-text="selectedConcert?.location"></p>
                </div>
                <div class="pt-3 border-t border-zinc-200 flex flex-col items-center justify-center">
                    <p class="text-xs text-zinc-400 mb-2">Código QR Dinámico de Acceso:</p>
                    <div id="qrcode" class="bg-white p-3 rounded-xl border border-zinc-200 shadow-sm"></div>
                </div>
            </div>

            <button @click="resetApp()" class="w-full bg-zinc-900 hover:bg-zinc-800 text-white font-semibold py-3.5 rounded-2xl transition text-sm shadow">
                Volver al Inicio de tike_arg
            </button>
        </div>
    </div>

    <!-- Script de lógica con la cartelera real, fechas, horarios y presentación -->
    <script>
        function ticketApp() {
            return {
                view: 'home',
                searchQuery: '',
                selectedConcert: null,
                queuePosition: 118,
                timerSeconds: 300,
                timerInterval: null,
                buyer: { name: '', email: '', paymentMethod: 'mercadopago' },
                concerts: [
                    {
                        id: 1,
                        artist: 'Maria Becerra',
                        title: 'Maria Becerra - Gira Oficial',
                        date: '13 de Noviembre, 2026',
                        time: '21:00 hs',
                        location: 'Movistar Arena, Buenos Aires',
                        badge: '¡Alta Demanda!',
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
                        badge: 'Últimas Entradas',
                        tickets: [
                            { type: 'Campo', description: 'Pista general', price: 45000, qty: 0 },
                            { type: 'Platea Preferencial', description: 'Sector baja numerado', price: 82000, qty: 0 }
                        ]
                    },
                    {
                        id: 3,
                        artist: 'Ed Sheeran',
                        title: 'Ed Sheeran - Mathematics Tour',
                        date: '29 de Noviembre, 2026',
                        time: '21:00 hs',
                        location: 'Estadio Tomás Adolfo Ducó (Huracán), Buenos Aires',
                        badge: 'Internacional',
                        tickets: [
                            { type: 'Campo General', description: 'Sector general', price: 65000, qty: 0 },
                            { type: 'Platea Baja', description: 'Asiento numerado', price: 110000, qty: 0 },
                            { type: 'VIP Gold', description: 'Cercanía al escenario principal', price: 195000, qty: 0 }
                        ]
                    },
                    {
                        id: 4,
                        artist: 'Coldplay',
                        title: 'Coldplay - Music of the Spheres',
                        date: '12 de Diciembre, 2026',
                        time: '21:00 hs',
                        location: 'Estadio Monumental, Buenos Aires',
                        badge: 'Preventa',
                        tickets: [
                            { type: 'Campo General', description: 'Acceso a campo', price: 58000, qty: 0 },
                            { type: 'Platea San Martín / Belgrano', description: 'Inferior numerada', price: 105000, qty: 0 }
                        ]
                    },
                    {
                        id: 5,
                        artist: 'Shakira',
                        title: 'Shakira - Las Mujeres Ya No Lloran Tour',
                        date: '04 de Diciembre, 2026',
                        time: '20:00 hs',
                        location: 'Campo Argentino de Polo, Buenos Aires',
                        badge: 'Destacado',
                        tickets: [
                            { type: 'Campo Delantero', description: 'Cerca del escenario', price: 95000, qty: 0 },
                            { type: 'Campo General', description: 'Pista general', price: 50000, qty: 0 },
                            { type: 'Platea VIP', description: 'Asiento reservado', price: 140000, qty: 0 }
                        ]
                    },
                    {
                        id: 6,
                        artist: 'Maná',
                        title: 'Maná - México Lindo y Querido Tour',
                        date: '10 de Diciembre, 2026',
                        time: '21:00 hs',
                        location: 'Estadio Mâs Monumental, Buenos Aires',
                        badge: 'Disponible',
                        tickets: [
                            { type: 'Campo', description: 'Acceso general', price: 42000, qty: 0 },
                            { type: 'Platea Baja', description: 'Ubicación numerada', price: 88000, qty: 0 }
                        ]
                    }
                ],
                get filteredConcerts() {
                    if (!this.searchQuery || this.searchQuery.trim() === '') {
                        return this.concerts;
                    }
                    const q = this.searchQuery.toLowerCase().trim();
                    return this.concerts.filter(c => 
                        c.artist.toLowerCase().includes(q) || 
                        c.title.toLowerCase().includes(q) || 
                        c.location.toLowerCase().includes(q)
                    );
                },
                triggerQueue(concert) {
                    concert.tickets.forEach(t => t.qty = 0);
                    this.selectedConcert = concert;
                    this.queuePosition = Math.floor(Math.random() * 150) + 20;
                    this.view = 'queue';

                    setTimeout(() => {
                        this.view = 'select-tickets';
                        this.startTimer();
                    }, 3000);
                },
                startTimer() {
                    this.timerSeconds = 300;
                    clearInterval(this.timerInterval);
                    this.timerInterval = setInterval(() => {
                        if (this.timerSeconds > 0) {
                            this.timerSeconds--;
                        } else {
                            clearInterval(this.timerInterval);
                            alert('El tiempo de reserva expiró. Volviendo al inicio.');
                            this.resetApp();
                        }
                    }, 1000);
                },
                formatTime(seconds) {
                    const m = Math.floor(seconds / 60);
                    const s = seconds % 60;
                    return `${m}:${s < 10 ? '0' : ''}${s}`;
                },
                incrementTicket(ticket) {
                    ticket.qty++;
                },
                decrementTicket(ticket) {
                    if (ticket.qty > 0) ticket.qty--;
                },
                calculateTotal() {
                    if (!this.selectedConcert) return 0;
                    return this.selectedConcert.tickets.reduce((sum, t) => sum + (t.price * t.qty), 0);
                },
                proceedToCheckout() {
                    clearInterval(this.timerInterval);
                    this.view = 'checkout';
                },
                processPayment() {
                    this.view = 'success';
                    setTimeout(() => {
                        const qrContainer = document.getElementById("qrcode");
                        if (qrContainer) {
                            qrContainer.innerHTML = "";
                            new QRCode(qrContainer, {
                                text: `TIKEARG-OFICIAL-VERIFICADO-${this.selectedConcert.artist}-${this.buyer.name}`,
                                width: 140,
                                height: 140
                            });
                        }
                    }, 100);
                },
                resetApp() {
                    clearInterval(this.timerInterval);
                    this.view = 'home';
                    this.searchQuery = '';
                    this.selectedConcert = null;
                    this.buyer = { name: '', email: '', paymentMethod: 'mercadopago' };
                }
            }
        }
    </script>
</body>
</html>
