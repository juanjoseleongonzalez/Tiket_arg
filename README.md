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
            <div class="flex items-center space-x-3 cursor-pointer" @click="view = 'home'">
                <span class="text-2xl font-black tracking-wider text-red-600">tike<span class="text-zinc-900">_arg</span></span>
            </div>
            <nav class="hidden md:flex space-x-8 text-sm font-medium text-zinc-600">
                <a href="#" @click.prevent="view = 'home'" class="hover:text-red-600 transition">Conciertos</a>
                <a href="#" @click.prevent="view = 'home'" class="hover:text-red-600 transition">Festivales</a>
                <a href="#" @click.prevent="view = 'home'" class="hover:text-red-600 transition">Mi Cuenta / eTicket</a>
            </nav>
            <div>
                <span class="text-xs bg-red-50 text-red-600 border border-red-200 px-3 py-1.5 rounded-full font-medium">
                    🔒 Sitio Oficial Protegido
                </span>
            </div>
        </div>
    </header>

    <!-- ================= VISTA 1: HOME ================= -->
    <div x-show="view === 'home'">
        <section class="relative py-20 bg-zinc-50 border-b border-zinc-200 text-center px-4">
            <div class="max-w-3xl mx-auto">
                <span class="inline-block bg-red-100 text-red-700 text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-wider mb-4 border border-red-200">
                    Plataforma Oficial de Venta de Entradas
                </span>
                <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight mb-6 text-zinc-900">
                    Sentí la música en vivo <br><span class="text-red-600">asegurate tu lugar</span>
                </h1>
                <p class="text-zinc-600 text-lg mb-10">
                    Encontrá la cartelera completa con todos los conciertos del año, preventas y fila virtual segura.
                </p>
                
                <div class="flex flex-col sm:flex-row gap-3 bg-white p-2 rounded-2xl border border-zinc-200 shadow-xl">
                    <input type="text" x-model="searchQuery" placeholder="Buscá por artista (ej: Coldplay, Duki, Shakira), banda o estadio..." class="flex-grow bg-transparent px-4 py-3 text-zinc-900 placeholder-zinc-400 focus:outline-none text-sm">
                    <button class="bg-red-600 hover:bg-red-700 text-white font-medium px-8 py-3 rounded-xl transition text-sm shadow-md">
                        Buscar
                    </button>
                </div>
            </div>
        </section>

        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
            <div class="mb-10 flex flex-col sm:flex-row sm:items-center sm:justify-between gap-4">
                <div>
                    <h2 class="text-2xl sm:text-3xl font-bold tracking-tight text-zinc-900">Cartelera Completa 2026</h2>
                    <p class="text-zinc-500 text-sm mt-1">Mostrando todos los eventos musicales disponibles para la venta.</p>
                </div>
                <div class="text-xs text-zinc-400 font-semibold uppercase tracking-wider" x-text="filteredConcerts.length + ' conciertos encontrados'"></div>
            </div>

            <!-- Si no hay resultados -->
            <div x-show="filteredConcerts.length === 0" class="text-center py-20 bg-zinc-50 rounded-2xl border border-zinc-200">
                <p class="text-zinc-500 text-lg font-medium">No se encontraron conciertos con ese nombre.</p>
                <button @click="searchQuery = ''" class="mt-4 text-red-600 font-semibold hover:underline text-sm">Ver todos los conciertos</button>
            </div>

            <!-- Grilla de Conciertos -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <template x-for="concert in filteredConcerts" :key="concert.id">
                    <div class="bg-white rounded-2xl overflow-hidden border border-zinc-200 hover:border-red-300 transition group flex flex-col justify-between shadow-sm hover:shadow-md">
                        <div>
                            <div class="relative h-48 bg-zinc-900 overflow-hidden flex items-center justify-center p-4 text-center">
                                <div class="absolute inset-0 bg-gradient-to-t from-zinc-950 via-zinc-900/60 to-transparent z-10"></div>
                                <span class="relative z-20 text-white font-black text-xl group-hover:scale-105 transition duration-500" x-text="concert.title"></span>
                                <span class="absolute top-3 left-3 z-30 bg-red-600 text-white text-xs font-bold px-3 py-1 rounded-full shadow" x-text="concert.badge"></span>
                            </div>
                            <div class="p-6">
                                <p class="text-red-600 text-xs font-semibold uppercase tracking-wider mb-1" x-text="concert.date"></p>
                                <h3 class="text-xl font-bold mb-2 text-zinc-900 group-hover:text-red-600 transition" x-text="concert.title"></h3>
                                <p class="text-zinc-500 text-sm flex items-center gap-1 mb-4" x-text="concert.location"></p>
                            </div>
                        </div>
                        <div class="p-6 pt-0">
                            <button @click="triggerQueue(concert)" class="w-full bg-zinc-900 hover:bg-red-600 text-white font-medium py-3 rounded-xl transition text-sm shadow">
                                Comprar Entradas
                            </button>
                        </div>
                    </div>
                </template>
            </div>
        </main>
    </div>

    <!-- ================= VISTA 2: FILA VIRTUAL ================= -->
    <div x-show="view === 'queue'" class="max-w-xl mx-auto px-4 py-24 text-center">
        <div class="bg-white border border-zinc-200 rounded-3xl p-8 sm:p-12 shadow-xl space-y-6">
            <div class="w-16 h-16 bg-red-50 text-red-600 rounded-full flex items-center justify-center text-2xl mx-auto border border-red-200 animate-pulse">⏳</div>
            <div>
                <span class="text-xs uppercase font-bold text-red-600 tracking-wider">Sistema de Alta Demanda</span>
                <h2 class="text-2xl font-black text-zinc-900 mt-1">Estás en la Fila Virtual</h2>
                <p class="text-zinc-500 text-sm mt-2">Para garantizar una experiencia justa y evitar caídas en el sistema, aguardá un momento mientras te asignamos tu turno.</p>
            </div>

            <div class="bg-zinc-50 p-6 rounded-2xl border border-zinc-200 space-y-2">
                <p class="text-xs text-zinc-400">Tu número aproximado en fila:</p>
                <p class="text-4xl font-black text-red-600" x-text="queuePosition"></p>
                <p class="text-xs text-zinc-500 pt-2">Tiempo estimado de acceso: <span class="font-bold text-zinc-800">Menos de 1 minuto</span></p>
            </div>

            <p class="text-xs text-zinc-400">No cierres ni recargues esta ventana o perderás tu lugar asignado.</p>
        </div>
    </div>

    <!-- ================= VISTA 3: SELECCIÓN DE ENTRADAS + CRONÓMETRO ================= -->
    <div x-show="view === 'select-tickets'" class="max-w-4xl mx-auto px-4 py-12">
        <div class="bg-red-600 text-white px-6 py-3 rounded-2xl mb-6 flex items-center justify-between shadow-md">
            <span class="text-xs font-semibold uppercase tracking-wider">⏱ Tiempo reservado para tu compra:</span>
            <span class="text-lg font-black" x-text="formatTime(timerSeconds)"></span>
        </div>

        <div class="bg-white border border-zinc-200 rounded-3xl p-6 sm:p-10 shadow-lg">
            <span class="text-xs font-semibold text-red-600 uppercase tracking-widest" x-text="selectedConcert?.date"></span>
            <h2 class="text-3xl font-extrabold text-zinc-900 mt-1 mb-2" x-text="selectedConcert?.title"></h2>
            <p class="text-zinc-500 text-sm mb-8" x-text="selectedConcert?.location"></p>

            <h3 class="text-lg font-bold text-zinc-900 mb-4 border-b border-zinc-100 pb-2">Seleccioná tus ubicaciones:</h3>
            
            <div class="space-y-4 mb-8">
                <template x-for="ticket in selectedConcert?.tickets" :key="ticket.type">
                    <div class="flex items-center justify-between bg-zinc-50 p-4 rounded-2xl border border-zinc-200">
                        <div>
                            <h4 class="font-bold text-base text-zinc-900" x-text="ticket.type"></h4>
                            <p class="text-xs text-zinc-500" x-text="ticket.description"></p>
                            <span class="text-red-600 font-bold text-sm mt-1 block" x-text=" '$' + ticket.price.toLocaleString() "></span>
                        </div>
                        <div class="flex items-center gap-3">
                            <button @click="decrementTicket(ticket)" class="w-9 h-9 bg-white border border-zinc-300 hover:bg-zinc-100 rounded-xl font-bold text-zinc-800 transition">-</button>
                            <span class="w-6 text-center font-bold text-zinc-900" x-text="ticket.qty"></span>
                            <button @click="incrementTicket(ticket)" class="w-9 h-9 bg-red-600 hover:bg-red-700 text-white rounded-xl font-bold transition">+</button>
                        </div>
                    </div>
                </template>
            </div>

            <div class="bg-zinc-50 p-6 rounded-2xl border border-zinc-200 flex flex-col sm:flex-row items-center justify-between gap-4">
                <div>
                    <p class="text-xs text-zinc-500">Total a pagar:</p>
                    <p class="text-2xl font-black text-red-600" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                </div>
                <button @click="proceedToCheckout()" :disabled="calculateTotal() === 0" class="w-full sm:w-auto bg-red-600 hover:bg-red-700 disabled:bg-zinc-200 disabled:text-zinc-400 text-white font-semibold px-8 py-3.5 rounded-xl transition text-sm shadow-md">
                    Avanzar al Pago →
                </button>
            </div>
        </div>
    </div>

    <!-- ================= VISTA 4: PAGO SEGURO ================= -->
    <div x-show="view === 'checkout'" class="max-w-2xl mx-auto px-4 py-12">
        <div class="bg-white border border-zinc-200 rounded-3xl p-6 sm:p-10 shadow-lg">
            <h2 class="text-2xl font-bold text-zinc-900 mb-2">Datos de Facturación y #eTicket</h2>
            <p class="text-zinc-500 text-sm mb-6">Completá tus datos para emitir las entradas oficiales con código QR dinámico.</p>
            
            <form @submit.prevent="processPayment" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Nombre y Apellido (Titular)</label>
                    <input type="text" required x-model="buyer.name" placeholder="Ej: León Pérez" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm text-zinc-900 focus:outline-none focus:border-red-600">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Correo Electrónico (Para recibir el #eTicket)</label>
                    <input type="email" required x-model="buyer.email" placeholder="tu@correo.com" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm text-zinc-900 focus:outline-none focus:border-red-600">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Medio de Pago Seleccionado</label>
                    <select x-model="buyer.paymentMethod" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-red-600 text-zinc-900">
                        <option value="mercadopago">Tarjeta de Crédito / Débito / Mercado Pago</option>
                    </select>
                </div>

                <div class="pt-4 border-t border-zinc-100 flex items-center justify-between">
                    <div>
                        <p class="text-xs text-zinc-500">Total final:</p>
                        <p class="text-xl font-bold text-red-600" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                    </div>
                    <button type="submit" class="bg-red-600 hover:bg-red-700 text-white font-bold px-8 py-3.5 rounded-xl transition text-sm shadow-md">
                        Confirmar y Pagar 🔒
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
            <p class="text-zinc-500 text-sm mb-6">Tu operación fue procesada de forma segura. Presentá este código QR directamente desde tu celular en la puerta del evento.</p>
            
            <div class="bg-zinc-50 border border-zinc-200 rounded-2xl p-6 text-left mb-6 space-y-3 shadow-inner">
                <div class="flex justify-between items-center border-b border-zinc-200 pb-3">
                    <span class="text-xs uppercase font-bold text-red-600" x-text="selectedConcert?.title"></span>
                    <span class="text-xs text-zinc-500" x-text="selectedConcert?.date"></span>
                </div>
                <div>
                    <p class="text-xs text-zinc-400">Titular:</p>
                    <p class="text-sm font-semibold text-zinc-800" x-text="buyer.name"></p>
                </div>
                <div>
                    <p class="text-xs text-zinc-400">Ubicación / Recinto:</p>
                    <p class="text-sm font-semibold text-zinc-800" x-text="selectedConcert?.location"></p>
                </div>
                <div class="pt-3 border-t border-zinc-200 flex flex-col items-center justify-center">
                    <p class="text-xs text-zinc-400 mb-2">Código QR Dinámico de Acceso:</p>
                    <div id="qrcode" class="bg-white p-3 rounded-xl border border-zinc-200 shadow-sm"></div>
                </div>
            </div>

            <button @click="resetApp()" class="w-full bg-zinc-900 hover:bg-zinc-800 text-white font-semibold py-3 rounded-xl transition text-sm shadow">
                Volver al Inicio de tike_arg
            </button>
        </div>
    </div>

    <!-- Script con la cartelera completa de conciertos -->
    <script>
        function ticketApp() {
            return {
                view: 'home',
                searchQuery: '',
                selectedConcert: null,
                queuePosition: 142,
                timerSeconds: 300,
                timerInterval: null,
                buyer: { name: '', email: '', paymentMethod: 'mercadopago' },
                concerts: [
                    {
                        id: 1,
                        title: 'Coldplay - Music of the Spheres',
                        date: '12 de Noviembre, 2026',
                        location: 'Estadio Monumental, Buenos Aires',
                        badge: '¡Últimas Entradas!',
                        tickets: [
                            { type: 'Campo General', description: 'Acceso general al campo', price: 55000, qty: 0 },
                            { type: 'Platea Baja', description: 'Asiento preferencial numerado', price: 98000, qty: 0 },
                            { type: 'VIP Package', description: 'Acceso exclusivo + Merchandising', price: 180000, qty: 0 }
                        ]
                    },
                    {
                        id: 2,
                        title: 'Duki - Gira Mundial',
                        date: '25 de Octubre, 2026',
                        location: 'Estadio Vélez Sarsfield, Buenos Aires',
                        badge: 'Alta Demanda',
                        tickets: [
                            { type: 'Campo', description: 'Sector general de pie', price: 42000, qty: 0 },
                            { type: 'Platea Preferencial', description: 'Ubicación numerada en platea baja', price: 75000, qty: 0 }
                        ]
                    },
                    {
                        id: 3,
                        title: 'Shakira - Las Mujeres Ya No Lloran World Tour',
                        date: '04 de Diciembre, 2026',
                        location: 'Campo Argentino de Polo, Buenos Aires',
                        badge: 'Preventa Exclusiva',
                        tickets: [
                            { type: 'Campo Delantero', description: 'Cerca del escenario principal', price: 95000, qty: 0 },
                            { type: 'Campo General', description: 'Acceso general', price: 50000, qty: 0 },
                            { type: 'Platea VIP', description: 'Asiento reservado', price: 140000, qty: 0 }
                        ]
                    },
                    {
                        id: 4,
                        title: 'Airbag - Tour 2026',
                        date: '18 de Noviembre, 2026',
                        location: 'Luna Park, Buenos Aires',
                        badge: 'Disponible',
                        tickets: [
                            { type: 'Platea', description: 'Asiento numerado', price: 38000, qty: 0 },
                            { type: 'Cabecera / General', description: 'Sin numerar', price: 25000, qty: 0 }
                        ]
                    },
                    {
                        id: 5,
                        title: 'Bizarrap - Live Sessions Arena',
                        date: '30 de Octubre, 2026',
                        location: 'Movistar Arena, Buenos Aires',
                        badge: 'Últimos Lugares',
                        tickets: [
                            { type: 'Campo General', description: 'Pista de pie', price: 45000, qty: 0 },
                            { type: 'Platea Baja', description: 'Sector baja numerado', price: 70000, qty: 0 }
                        ]
                    },
                    {
                        id: 6,
                        title: 'Lali - Disciplina Tour',
                        date: '05 de Diciembre, 2026',
                        location: 'Movistar Arena, Buenos Aires',
                        badge: 'Disponible',
                        tickets: [
                            { type: 'Campo', description: 'Acceso al campo', price: 39000, qty: 0 },
                            { type: 'Platea Alta', description: 'Visita panorámica', price: 48000, qty: 0 }
                        ]
                    }
                ],
                get filteredConcerts() {
                    if (!this.searchQuery) return this.concerts;
                    const q = this.searchQuery.toLowerCase();
                    return this.concerts.filter(c => 
                        c.title.toLowerCase().includes(q) || 
                        c.location.toLowerCase().includes(q)
                    );
                },
                triggerQueue(concert) {
                    concert.tickets.forEach(t => t.qty = 0);
                    this.selectedConcert = concert;
                    this.queuePosition = Math.floor(Math.random() * 250) + 30;
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
                        document.getElementById("qrcode").innerHTML = "";
                        new QRCode(document.getElementById("qrcode"), {
                            text: `TIKEARG-ETICKET-VERIFICADO-${this.selectedConcert.title}-${this.buyer.name}`,
                            width: 140,
                            height: 140
                        });
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
