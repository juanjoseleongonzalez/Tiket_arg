<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>tike_arg - Venta Oficial de Entradas</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Alpine.js para la interactividad de la aplicación -->
    <script defer src="https://cdn.jsdelivr.net/npm/alpinejs@3.x.x/dist/cdn.min.js"></script>
    <!-- Librería para generar códigos QR visuales -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/qrcodejs/1.0.0/qrcode.min.js"></script>
</head>
<body class="bg-white text-zinc-900 font-sans antialiased" x-data="ticketApp()">

    <!-- 1. BARRA DE NAVEGACIÓN -->
    <header class="sticky top-0 z-50 bg-white/95 backdrop-blur border-b border-zinc-200">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <div class="flex items-center space-x-3 cursor-pointer" @click="view = 'home'">
                <span class="text-2xl font-black tracking-wider text-red-600">tike<span class="text-zinc-900">_arg</span></span>
            </div>
            <nav class="hidden md:flex space-x-8 text-sm font-medium text-zinc-600">
                <a href="#" @click.prevent="view = 'home'" class="hover:text-red-600 transition">Conciertos</a>
                <a href="#" class="hover:text-red-600 transition">Festivales</a>
                <a href="#" class="hover:text-red-600 transition">Ayuda y Seguridad</a>
            </nav>
            <div>
                <span class="text-xs bg-red-50 text-red-600 border border-red-200 px-3 py-1.5 rounded-full font-medium">
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
        <section class="relative py-20 bg-zinc-50 border-b border-zinc-200 text-center px-4">
            <div class="max-w-3xl mx-auto">
                <span class="inline-block bg-red-100 text-red-700 text-xs font-semibold px-3 py-1 rounded-full uppercase tracking-wider mb-4 border border-red-200">
                    Sitio Oficial de Venta Segura
                </span>
                <h1 class="text-4xl sm:text-6xl font-extrabold tracking-tight mb-6 text-zinc-900">
                    Vivir la música en vivo <br><span class="text-red-600">nunca fue tan fácil</span>
                </h1>
                <p class="text-zinc-600 text-lg mb-10">
                    Encuentra entradas oficiales para los mejores conciertos del año con máxima seguridad garantizada.
                </p>
                
                <!-- Buscador funcional -->
                <div class="flex flex-col sm:flex-row gap-3 bg-white p-2 rounded-2xl border border-zinc-200 shadow-xl">
                    <input type="text" x-model="searchQuery" placeholder="Busca por artista, banda o estadio..." class="flex-grow bg-transparent px-4 py-3 text-zinc-900 placeholder-zinc-400 focus:outline-none text-sm">
                    <button class="bg-red-600 hover:bg-red-700 text-white font-medium px-8 py-3 rounded-xl transition text-sm shadow-md shadow-red-600/20">
                        Buscar Concierto
                    </button>
                </div>
            </div>
        </section>

        <!-- Cartelera de Conciertos -->
        <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-16">
            <div class="mb-10">
                <h2 class="text-2xl sm:text-3xl font-bold tracking-tight text-zinc-900">Próximos Conciertos del Año</h2>
                <p class="text-zinc-500 text-sm mt-1">Selecciona tu evento favorito para asegurar tus lugares oficiales.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
                <template x-for="concert in filteredConcerts" :key="concert.id">
                    <div class="bg-white rounded-2xl overflow-hidden border border-zinc-200 hover:border-red-300 transition group flex flex-col justify-between shadow-sm hover:shadow-md">
                        <div>
                            <div class="relative h-48 bg-zinc-100 overflow-hidden flex items-center justify-center">
                                <div class="absolute inset-0 bg-gradient-to-t from-zinc-900/40 via-transparent to-transparent z-10"></div>
                                <span class="text-zinc-400 font-bold text-xl group-hover:scale-105 transition duration-500" x-text="concert.title"></span>
                                <span class="absolute top-3 left-3 z-20 bg-red-600 text-white text-xs font-bold px-3 py-1 rounded-full shadow" x-text="concert.badge"></span>
                            </div>
                            <div class="p-6">
                                <p class="text-red-600 text-xs font-semibold uppercase tracking-wider mb-1" x-text="concert.date"></p>
                                <h3 class="text-xl font-bold mb-2 text-zinc-900 group-hover:text-red-600 transition" x-text="concert.title"></h3>
                                <p class="text-zinc-500 text-sm flex items-center gap-1 mb-4" x-text="concert.location"></p>
                            </div>
                        </div>
                        <div class="p-6 pt-0">
                            <button @click="selectConcert(concert)" class="w-full bg-zinc-900 hover:bg-red-600 text-white font-medium py-3 rounded-xl transition text-sm shadow">
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
        <button @click="view = 'home'" class="text-sm text-zinc-500 hover:text-zinc-900 mb-6 flex items-center gap-2 font-medium">← Volver a Conciertos</button>
        
        <div class="bg-white border border-zinc-200 rounded-3xl p-6 sm:p-10 shadow-lg">
            <span class="text-xs font-semibold text-red-600 uppercase tracking-widest" x-text="selectedConcert.date"></span>
            <h2 class="text-3xl font-extrabold text-zinc-900 mt-1 mb-2" x-text="selectedConcert.title"></h2>
            <p class="text-zinc-500 text-sm mb-8" x-text="selectedConcert.location"></p>

            <h3 class="text-lg font-bold text-zinc-900 mb-4 border-b border-zinc-100 pb-2">Selecciona tus ubicaciones y cantidad:</h3>
            
            <div class="space-y-4 mb-8">
                <template x-for="ticket in selectedConcert.tickets" :key="ticket.type">
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

            <!-- Resumen y botón de pago -->
            <div class="bg-zinc-50 p-6 rounded-2xl border border-zinc-200 flex flex-col sm:flex-row items-center justify-between gap-4">
                <div>
                    <p class="text-xs text-zinc-500">Total a pagar:</p>
                    <p class="text-2xl font-black text-red-600" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                </div>
                <button @click="proceedToCheckout()" :disabled="calculateTotal() === 0" class="w-full sm:w-auto bg-red-600 hover:bg-red-700 disabled:bg-zinc-200 disabled:text-zinc-400 text-white font-semibold px-8 py-3.5 rounded-xl transition text-sm shadow-md shadow-red-600/20">
                    Continuar al Pago Seguro →
                </button>
            </div>
        </div>
    </div>

    <!-- ========================================== -->
    <!-- VISTA 3: PASARELA DE PAGO                   -->
    <!-- ========================================== -->
    <div x-show="view === 'checkout'" class="max-w-2xl mx-auto px-4 py-12">
        <button @click="view = 'select-tickets'" class="text-sm text-zinc-500 hover:text-zinc-900 mb-6 flex items-center gap-2 font-medium">← Volver</button>
        
        <div class="bg-white border border-zinc-200 rounded-3xl p-6 sm:p-10 shadow-lg">
            <h2 class="text-2xl font-bold text-zinc-900 mb-2">Finalizar Compra</h2>
            <p class="text-zinc-500 text-sm mb-6">Ingresa tus datos personales para enviarte las entradas con código QR.</p>
            
            <form @submit.prevent="processPayment" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Nombre Completo</label>
                    <input type="text" required x-model="buyer.name" placeholder="Ej: León Pérez" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm text-zinc-900 focus:outline-none focus:border-red-600">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Correo Electrónico (Donde enviaremos el QR)</label>
                    <input type="email" required x-model="buyer.email" placeholder="tu@correo.com" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm text-zinc-900 focus:outline-none focus:border-red-600">
                </div>
                <div>
                    <label class="block text-xs font-semibold uppercase text-zinc-500 mb-1">Método de Pago</label>
                    <select x-model="buyer.paymentMethod" class="w-full bg-zinc-50 border border-zinc-200 rounded-xl px-4 py-3 text-sm focus:outline-none focus:border-red-600 text-zinc-900">
                        <option value="mercadopago">Mercado Pago / QR / Dinero en Cuenta</option>
                        <option value="tarjeta">Tarjeta de Crédito o Débito</option>
                    </select>
                </div>

                <div class="pt-4 border-t border-zinc-100 flex items-center justify-between">
                    <div>
                        <p class="text-xs text-zinc-500">Total a abonar:</p>
                        <p class="text-xl font-bold text-red-600" x-text=" '$' + calculateTotal().toLocaleString() "></p>
                    </div>
                    <button type="submit" class="bg-red-600 hover:bg-red-700 text-white font-bold px-8 py-3.5 rounded-xl transition text-sm shadow-md shadow-red-600/20">
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
        <div class="bg-white border border-zinc-200 rounded-3xl p-8 sm:p-10 shadow-xl">
            <div class="w-16 h-16 bg-red-50 text-red-600 rounded-full flex items-center justify-center text-3xl mx-auto mb-4 border border-red-200">✓</div>
            <h2 class="text-2xl font-bold text-zinc-900 mb-1">¡Compra Exitosa!</h2>
            <p class="text-zinc-500 text-sm mb-6">Hemos procesado tu pago correctamente. Tu entrada digital ya está lista.</p>
            
            <!-- Ticket Visual con QR -->
            <div class="bg-zinc-50 border border-zinc-200 rounded-2xl p-6 text-left mb-6 space-y-3 shadow-inner">
                <div class="flex justify-between items-center border-b border-zinc-200 pb-3">
                    <span class="text-xs uppercase font-bold text-red-600" x-text="selectedConcert.title"></span>
                    <span class="text-xs text-zinc-500" x-text="selectedConcert.date"></span>
                </div>
                <div>
                    <p class="text-xs text-zinc-400">Comprador:</p>
                    <p class="text-sm font-semibold text-zinc-800" x-text="buyer.name"></p>
                </div>
                <div>
                    <p class="text-xs text-zinc-400">Lugar:</p>
                    <p class="text-sm font-semibold text-zinc-800" x-text="selectedConcert.location"></p>
                </div>
                <div class="pt-3 border-t border-zinc-200 flex flex-col items-center justify-center">
                    <p class="text-xs text-zinc-400 mb-2">Código QR de Acceso en Puerta:</p>
                    <!-- Contenedor del código QR -->
                    <div id="qrcode" class="bg-white p-3 rounded-xl border border-zinc-200 shadow-sm"></div>
                </div>
            </div>

            <button @click="resetApp()" class="w-full bg-zinc-900 hover:bg-zinc-800 text-white font-semibold py-3 rounded-xl transition text-sm shadow">
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
                            { type: 'Platea Alta', description: 'Vista panorámica del escenario', price: 60000, qty: 0 }
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
                    this.view = 'success';
                    setTimeout(() => {
                        document.getElementById("qrcode").innerHTML = "";
                        new QRCode(document.getElementById("qrcode"), {
                            text: `TIKEARG-VERIFICADO-${this.selectedConcert.title}-${this.buyer.name}`,
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
