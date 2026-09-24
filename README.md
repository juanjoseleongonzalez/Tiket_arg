<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TicketPro - Venta Oficial de Entradas</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Alpine.js para la interactividad de la aplicación -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
    <!-- Librería para generar códigos QR visuales -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
</head>
<body class="bg-slate-950 text-white font-sans antialiased" x-data="ticketApp()">

    <!-- 1. BARRA DE NAVEGACIÓN -->
    <header class="sticky top-0 z-50 bg-slate-900/90 backdrop-blur border-b border-slate-800">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <div class="flex items-center space-x-3 cursor-pointer" @click="view = 'home'">
                <span class="text-2xl font-black tracking-wider text-rose-500">TICKET<span class="text-white">PRO</span></span>
            </div>
            <nav class="hidden md:flex space-x-8 text-sm font-medium text-slate-300">
                <a href="#" @click.prevent="view = 'home'" class="hover:text-rose-500 transition">Conciertos</a>
                <a href="#" class="hover:text-rose-500 transition">Festivales</a>
                <a href="#" class="hover:text-rose-500 transition">Ayuda y Seguridad</a>
            </nav>
            <div>
                <span class="text-xs bg-emerald-500/10 text-emerald-400 border border-emerald-500/20 px-3 py-1.5 rounded-full font-medium">
                    🔒 Conexión Segura SSL
                </span>
            </div>
        </div>
    </header>

    <!-- ========================================== -->
    <!-- VISTA 1: HOME (CARTELERA Y BUSCADOR)       -->
    <!-- ========================================== -->
    <div x-show="view === 'home'">
        <!-- Hero / Buscador -->
        <section class="relative py-20 bg-gradient-to-b from-slate-900 to-slate-950 border-b border-slate-800/60 text-center px-4">
            <div class="max-w-3xl mx-auto">
                <span class="inline-block bg-rose-500/10 text-rose-400 text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-wider mb-4 border border-rose-500/20">
                    Sitio Oficial de Venta Segura
                </span>
                <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight mb-6">
                    Vivir la música en vivo <br><span class="text-transparent bg-clip-text bg-gradient-to-r from-rose-500 to-orange-400">nunca fue tan fácil</span>
                </h1>
                <p class="text-slate-400 text-lg mb-10">
                    Encuentra entradas oficiales para los mejores conciertos del año con máxima seguridad garantizada.
                </p>
                
                <!-- Buscador funcional -->
                <div class="flex flex-col sm:flex-row gap-3 bg-slate-900 p-2 rounded-2xl border border-slate-800 shadow-2xl">
                    <input type="text" x-model="searchQuery" placeholder="Busca por artista, banda o estadio..." class="flex-grow bg-transparent px-4 py-3 text-white placeholder-slate-500 focus:outline-none text-sm">
                    <button class="bg-rose-600 hover:bg-rose-500 text-white font-medium px-8 py-3 rounded-xl transition text-sm">
                        Buscar Concierto
                    </button>
                </div>
            </div>
        </section>

        <!-- Cartelera de Conciertos -->
        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
            <div class="mb-10">
                <h2 class="text-2xl sm:text-3xl font-bold tracking-tight">Próximos Conciertos del Año</h2>
                <p class="text-slate-400 text-sm mt-1">Selecciona tu evento favorito para asegurar tus lugares oficiales.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <template x-for="concert in filteredConcerts" :key="concert.id">
                    <div class="bg-slate-900 rounded-2xl overflow-hidden border border-slate-800 hover:border-slate-700 transition group flex flex-col justify-between">
                        <div>
                            <div class="relative h-48 bg-slate-800 overflow-hidden flex items-center justify-center">
                                <div class="absolute inset-0 bg-gradient-to-t from-slate-900 via-transparent to-transparent z-10"></div>
                                <span class="text-slate-500 font-bold text-xl group-hover:scale-105 transition duration-500" x-text="concert.title"></span>
                                <span class="absolute top-3 left-3 z-20 bg-rose-600/90 backdrop-blur text-white text-xs font-bold px-3 py-1 rounded-full" x-text="concert.badge"></span>
                            </div>
                            <div class="p-6">
                                <p class="text-rose-400 text-xs font-semibold uppercase tracking-wider mb-1" x-text="concert.date"></p>
                                <h3 class="text-xl font-bold mb-2 group-hover:text-rose-400 transition" x-text="concert.title"></h3>
                                <p class="text-slate-400 text-sm flex items-center gap-1 mb-4" x-text="concert.location"></p>
                            </div>
                        </div>
                        <div class="p-6 pt-0">
                            <button @click="selectConcert(concert)" class="w-full bg-slate-800 hover:bg-rose-600 text-white font-medium py-3 rounded-xl transition text-sm border border-slate-700 hover:border-rose-600">
                                Comprar Entradas
                            </button>
                        </div>
                    </div>
                </template>
            </div>
        </main>
    </div>

    <!-- ========================================== -->
    <!-- VISTA 2: SELECCIÓN DE ENTRADAS             -->
    <!-- ========================================== -->
    <div x-show="view === 'select-tickets'" class="max-w-4xl mx-auto px-4 py-12">
        <button @click="view = 'home'" class="text-sm text-slate-400 hover:text-white mb-6 flex items-center gap-2">← Volver a Conciertos</button>
        
        <div class="bg-slate-900 border border-slate-800 rounded-3xl p-6 sm:p-10">
            <span class="text-xs font-semibold text-rose-400 uppercase tracking-widest" x-text="selectedConcert.date"></span>
            <h2 class="text-3xl font-extrabold mt-1 mb-2" x-text="selectedConcert.title"></h2>
            <p class="text-slate-400 text-sm mb-8" x-text="selectedConcert.location"></p>

            <h3 class="text-lg font-bold mb-4 border-b border-slate-800 pb-2">Selecciona tus ubicaciones y cantidad:</h3>
            
            <div class="space-y-4 mb-8">
                <template x-for="ticket in selectedConcert.tickets" :key="ticket.type">
                    <div class="flex items-center justify-between bg-slate-950 p-4 rounded-2xl border border-slate-800">
                        <div>
                            <h4 class="font-bold text-base" x-text="ticket.type"></h4>
                            <p class="text-xs text-slate-400" x-text="ticket.description"></p>
                            <span class="text-rose-400 font-bold text-sm mt-1 block" x-text=" '$' + ticket.price.toLocaleString() "></span>
                        </div>
                        <div class="flex items-center gap-3">
                            <button @click="decrementTicket(ticket)" class="w-9 h-9 bg-slate-800 hover:bg-slate-700 rounded-xl font-bold transition">-</button>
                            <span class="w-6 text-center font-bold" x-text="ticket.qty"></span>
                            <button @click="incrementTicket(ticket)" class="w-9 h-9 bg-rose-600 hover:bg-rose-500 rounded-xl font-bold transition">+</button>
                        </div>
                    </div>
                </template>
            </div>

            <!-- Resumen y botón de pago -->
            <div class="bg-slate-950 p-6 rounded-2xl border border-slate-800 flex flex-col sm:flex-row items-center justify-between gap-4">
                <div>
                    <p class="text-xs text-slate-400">Total a pagar:</p>
                    <p class="text-2xl font-black text-rose-400" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                </div>
                <button @click="proceedToCheckout()" :disabled="calculateTotal() === 0" class="w-full sm:w-auto bg-rose-600 hover:bg-rose-500 disabled:bg-slate-800 disabled:text-slate-600 text-white font-semibold px-8 py-3.5 rounded-xl transition text-sm shadow-lg shadow-rose-600/30">
                    Continuar al Pago Seguro →
                </button>
            </div>
        </div>
    </div>

    <!-- ========================================== -->
    <!-- VISTA 3: PASARELA DE PAGO                   -->
    <!-- ========================================== -->
    <div x-show="view === 'checkout'" class="max-w-2xl mx-auto px-4 py-12">
        <button @click="view = 'select-tickets'" class="text-sm text-slate-400 hover:text-white mb-6 flex items-center gap-2">← Volver</button>
        
        <div class="bg-slate-900 border border-slate-800 rounded-3xl p-6 sm:p-10">
            <h2 class="text-2xl font-bold mb-2">Finalizar Compra</h2>
            <p class="text-slate-400 text-sm mb-6">Ingresa tus datos personales para enviarte las entradas con código QR.</p>
            
            <form @submit.prevent="processPayment" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold uppercase text-slate-400 mb-1">Nombre Completo</label>
                    <input type="text" required x-model="buyer.name" placeholder="Ej: León Pérez" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-rose-500">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-slate-400 mb-1">Correo Electrónico (Donde enviaremos el QR)</label>
                    <input type="email" required x-model="buyer.email" placeholder="tu@correo.com" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-rose-500">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-slate-400 mb-1">Método de Pago</label>
                    <select x-model="buyer.paymentMethod" class="w-full bg-slate-950 border border-slate-800 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-rose-500 text-white">
                        <option value="mercadopago">Mercado Pago / QR / Dinero en Cuenta</option>
                        <option value="tarjeta">Tarjeta de Crédito o Débito</option>
                    </select>
                </div>

                <div class="pt-4 border-t border-slate-800 flex items-center justify-between">
                    <div>
                        <p class="text-xs text-slate-400">Total a abonar:</p>
                        <p class="text-xl font-bold text-rose-400" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                    </div>
                    <button type="submit" class="bg-emerald-600 hover:bg-emerald-500 text-white font-bold px-8 py-3.5 rounded-xl transition text-sm shadow-lg shadow-emerald-600/30">
                        Pagar de Forma Segura 🔒
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- ========================================== -->
    <!-- VISTA 4: ÉXITO Y GENERACIÓN DE QR           -->
    <!-- ========================================== -->
    <div x-show="view === 'success'" class="max-w-xl mx-auto px-4 py-12 text-center">
        <div class="bg-slate-900 border border-slate-800 rounded-3xl p-8 sm:p-10 shadow-2xl">
            <div class="w-16 h-16 bg-emerald-500/10 text-emerald-400 rounded-full flex items-center justify-center text-3xl mx-auto mb-4 border border-emerald-500/20">✓</div>
            <h2 class="text-2xl font-bold mb-1">¡Compra Exitosa!</h2>
            <p class="text-slate-400 text-sm mb-6">Hemos procesado tu pago correctamente. Tu entrada digital ya está lista.</p>
            
            <!-- Ticket Visual con QR -->
            <div class="bg-slate-950 border border-slate-800 rounded-2xl p-6 text-left mb-6 space-y-3">
                <div class="flex justify-between items-center border-b border-slate-800 pb-3">
                    <span class="text-xs uppercase font-bold text-rose-400" x-text="selectedConcert.title"></span>
                    <span class="text-xs text-slate-400" x-text="selectedConcert.date"></span>
                </div>
                <div>
                    <p class="text-xs text-slate-400">Comprador:</p>
                    <p class="text-sm font-semibold" x-text="buyer.name"></p>
                </div>
                <div>
                    <p class="text-xs text-slate-400">Lugar:</p>
                    <p class="text-sm font-semibold" x-text="selectedConcert.location"></p>
                </div>
                <div class="pt-3 border-t border-slate-800 flex flex-col items-center justify-center">
                    <p class="text-xs text-slate-400 mb-2">Código QR de Acceso en Puerta:</p>
                    <!-- Contenedor del código QR -->
                    <div id="qrcode" class="bg-white p-3 rounded-xl"></div>
                </div>
            </div>

            <button @click="resetApp()" class="w-full bg-slate-800 hover:bg-slate-700 text-white font-semibold py-3 rounded-xl transition text-sm">
                Volver al Inicio
            </button>
        </div>
    </div>

    <!-- Script de lógica de la aplicación -->
    <script>
        function ticketApp() {
            return {
                view: 'home',
                searchQuery: '',
                selectedConcert: null,
                buyer: { name: '', email: '', paymentMethod: 'mercadopago' },
                concerts: [
                    {
                        id: 1,
                        title: 'Gira Mundial "Rock & Tour"',
                        date: '15 de Octubre, 2026',
                        location: 'Estadio Monumental, Buenos Aires',
                        badge: '¡Últimas Entradas!',
                        tickets: [
                            { type: 'Campo General', description: 'Acceso general al sector campo', price: 45000, qty: 0 },
                            { type: 'Platea Baja Numerada', description: 'Asiento preferencial numerado', price: 85000, qty: 0 },
                            { type: 'VIP Experience', description: 'Meet & Greet + Sector exclusivo', price: 150000, qty: 0 }
                        ]
                    },
                    {
                        id: 2,
                        title: 'Festival Urbano Summer',
                        date: '03 de Noviembre, 2026',
                        location: 'Movistar Arena, Buenos Aires',
                        badge: 'Disponible',
                        tickets: [
                            { type: 'Campo', description: 'Acceso general', price: 40000, qty: 0 },
                            { type: 'Platea Alta', description: 'Visita panorámica del escenario', price: 60000, qty: 0 }
                        ]
                    },
                    {
                        id: 3,
                        title: 'Concierto Acústico Íntimo',
                        date: '20 de Diciembre, 2026',
                        location: 'Teatro Vorterix, Buenos Aires',
                        badge: 'Preventa Exclusiva',
                        tickets: [
                            { type: 'General', description: 'Entrada general de pie', price: 35000, qty: 0 },
                            { type: 'Palco Alto', description: 'Ubicación exclusiva para 2 personas', price: 90000, qty: 0 }
                        ]
                    }
                ],
                get filteredConcerts() {
                    if (!this.searchQuery) return this.concerts;
                    return this.concerts.filter(c => 
                        c.title.toLowerCase().includes(this.searchQuery.toLowerCase()) || 
                        c.location.toLowerCase().includes(this.searchQuery.toLowerCase())
                    );
                },
                selectConcert(concert) {
                    // Reiniciar cantidades al abrir
                    concert.tickets.forEach(t => t.qty = 0);
                    this.selectedConcert = concert;
                    this.view = 'select-tickets';
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
                    this.view = 'checkout';
                },
                processPayment() {
                    // Simulamos procesamiento de pago exitoso y mostramos el QR
                    this.view = 'success';
                    setTimeout(() => {
                        document.getElementById("qrcode").innerHTML = "";
                        new QRCode(document.getElementById("qrcode"), {
                            text: `TICKETPRO-VERIFICADO-${this.selectedConcert.title}-${this.buyer.name}`,
                            width: 140,
                            height: 140
                        });
                    }, 100);
                },
                resetApp() {
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
