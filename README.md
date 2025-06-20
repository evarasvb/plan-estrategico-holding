<By FirmaVB>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plan Estratégico y Tareas Asignadas Holding y FirmaVB</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Chart.js para gráficos -->
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/chartjs-plugin-datalabels@2.0.0"></script>
    <!-- Fuente Inter -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700;800&display=swap" rel="stylesheet">
    <style>
        /* Paleta de Colores Seleccionada: "Energetic & Playful" */
        /* - Coral: #FF6B6B */
        /* - Sunglow Yellow: #FFD166 */
        /* - Caribbean Green: #06D6A0 */
        /* - Blue Munsell: #118AB2 */
        /* - Midnight Green (Dark Blue): #073B4C */
        /* - Backgrounds: #F8FAFC (slate-50), #FFFFFF (white) */
        /* - Textos: #0F172A (slate-900), #334155 (slate-700) */

        body {
            font-family: 'Inter', sans-serif;
            background-color: #F8FAFC; /* slate-50 */
            color: #0F172A; /* slate-900 */
        }

        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 350px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 320px;
            }
        }

        /* Estilos para las tarjetas de contenido (existentes y nuevos) */
        .content-card, .section-card { /* Combinado para aplicar el mismo estilo */
            background-color: white;
            border-radius: 0.75rem; /* rounded-xl */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1); /* shadow-lg más sutil */
            padding: 1.5rem; /* p-6 */
            margin-bottom: 1.5rem; /* mb-6 */
            transition: transform 0.3s ease-in-out, box-shadow 0.3s ease-in-out; /* Transición para hover */
        }
        .section-card:hover { /* Solo para las nuevas secciones, para un efecto sutil */
            transform: translateY(-3px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }

        /* Estilos para títulos de sección (existentes y nuevos) */
        .section-heading, .section-title { /* Combinado para aplicar el mismo estilo */
            font-size: 1.875rem; /* text-3xl */
            font-weight: 700; /* font-bold */
            color: #073B4C; /* Midnight Green (Dark Blue) */
            margin-bottom: 1.25rem; /* mb-5 */
            padding-bottom: 0.5rem; /* pb-2 */
            border-bottom: 2px solid #06D6A0; /* Caribbean Green */
            text-align: center;
        }
        .section-title { /* Ajuste para los títulos de las nuevas secciones */
            display: inline-block; /* Para que el borde inferior se ajuste al texto */
            margin-left: auto;
            margin-right: auto;
        }

        /* Estilos para subtítulos (existentes y nuevos) */
        .sub-heading, .subsection-title { /* Combinado para aplicar el mismo estilo */
            font-size: 1.25rem; /* text-xl */
            font-weight: 600; /* font-semibold */
            color: #118AB2; /* Blue Munsell */
            margin-top: 1rem;
            margin-bottom: 0.75rem;
        }

        /* Estilos para texto principal (existentes y nuevos) */
        .text-main {
            font-size: 0.9375rem; /* text-base- (slightly smaller) */
            line-height: 1.6;
            color: #334155; /* slate-700 */
            margin-bottom: 0.75rem;
        }

        .highlight { color: #06D6A0; font-weight: 600; } /* Caribbean Green */
        .critical-highlight { color: #FF6B6B; font-weight: 600; } /* Coral */

        /* Navegación principal */
        #main-nav {
            position: sticky;
            top: 0;
            z-index: 50;
            background-color: rgba(7, 59, 76, 0.97); /* Midnight Green con transparencia */
            backdrop-filter: blur(5px);
            padding: 0.5rem 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }
        #main-nav a {
            color: #FFD166; /* Sunglow Yellow */
            padding: 0.5rem 1rem;
            margin: 0 0.25rem;
            border-radius: 0.375rem;
            font-weight: 600;
            font-size: 0.875rem;
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        #main-nav a:hover, #main-nav a.active {
            background-color: #FFD166; /* Sunglow Yellow */
            color: #073B4C; /* Midnight Green */
        }

        /* Estilos para la tabla Gantt - SECCIÓN ELIMINADA, PERO MANTENGO ESTILOS POR SI SE REINCORPORA O AFECTA OTROS ELEMENTOS */
        .gantt-simplified {
            font-size: 0.8rem;
            background-color: #fff;
            padding: 1rem;
            border-radius: 0.5rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }
        .gantt-row-simplified {
            display: grid;
            grid-template-columns: 180px repeat(6, 1fr); /* Task name + 6 time units (Semanas) */
            align-items: center;
            gap: 2px;
            padding: 0.3rem 0;
            border-bottom: 1px solid #E2E8F0; /* slate-200 */
        }
        .gantt-row-simplified:last-child { border-bottom: none; }
        .gantt-task-name-simplified {
            font-weight: 600;
            color: #0F172A;
            padding-right: 0.5rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .gantt-bar-container-simplified {
            position: relative;
            height: 20px;
            grid-column-start: var(--start-col);
            grid-column-end: span var(--span-col);
        }
        .gantt-bar-simplified {
            position: absolute;
            height: 100%;
            border-radius: 0.25rem;
            opacity: 0.9;
            background: linear-gradient(to right, var(--bar-start-color), var(--bar-end-color));
            transition: transform 0.2s ease-in-out, box-shadow 0.2s ease-in-out;
        }
        .gantt-bar-simplified:hover {
            transform: scale(1.02);
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
        }
        .gantt-bar-simplified.milestone {
            background-color: #FF6B6B; /* Coral */
            width: 10px !important; /* For milestones */
            left: calc(var(--milestone-pos) - 5px); /* Center milestone */
        }
        .gantt-header-simplified {
            font-weight: 600;
            text-align: center;
            color: #118AB2; /* Blue Munsell */
            padding-bottom: 0.5rem;
            font-size: 0.75rem;
        }
        .gantt-timeline-header-simplified {
            display: grid;
            grid-template-columns: 180px repeat(6, 1fr);
            gap: 2px;
        }
        .current-week-highlight {
            background-color: #e0f2fe !important; /* Tailwind blue-100 */
            color: #1e40af !important; /* Tailwind blue-800 */
            border-radius: 0.25rem;
        }

        /* Estilos para tablas generales (plan de trabajo) */
        .table-plan {
            min-width: 100%;
            border-collapse: collapse;
        }
        .table-plan th, .table-plan td {
            padding: 0.75rem;
            text-align: left;
            border-bottom: 1px solid #E2E8F0; /* slate-200 */
            font-size: 0.875rem;
        }
        .table-plan thead th {
            background-color: #073B4C; /* Midnight Green */
            color: #FFD166; /* Sunglow Yellow */
            font-weight: 600;
        }
        .table-plan tbody tr:hover {
            background-color: #F1F5F9; /* slate-100 */
        }

        /* Estilos específicos para los nuevos pilares y acciones clave */
        .bg-blue-50-custom { /* Para los pilares */
            background-color: #E6F4FF; /* Un azul muy claro, cercano al Blue Munsell */
        }
        .text-blue-600-custom { /* Para el texto de los pilares */
            color: #118AB2; /* Blue Munsell */
        }
        .bg-green-50-custom { /* Para Comercial */
            background-color: #E6FFF2; /* Un verde muy claro, cercano al Caribbean Green */
        }
        .text-green-700-custom { /* Para texto Comercial */
            color: #06D6A0; /* Caribbean Green */
        }
        .bg-yellow-50-custom { /* Para Compras */
            background-color: #FFF9E6; /* Un amarillo muy claro, cercano al Sunglow Yellow */
        }
        .text-yellow-700-custom { /* Para texto Compras */
            color: #FFD166; /* Sunglow Yellow */
        }
        .bg-red-50-custom { /* Para Administración y Finanzas */
            background-color: #FFE6E6; /* Un rojo muy claro, cercano al Coral */
        }
        .text-red-700-custom { /* Para texto Administración y Finanzas */
            color: #FF6B6B; /* Coral */
        }
        .bg-purple-50-custom { /* Para Postventa y Logística, usando un tono de azul */
            background-color: #E6F4FF; /* Reutilizando el azul claro */
        }
        .text-purple-700-custom { /* Para texto Postventa y Logística */
            color: #118AB2; /* Blue Munsell */
        }
        /* Viñetas personalizadas para las nuevas listas */
        .new-list-item::before {
            content: '•';
            color: #06D6A0; /* Caribbean Green */
            font-weight: bold;
            display: inline-block;
            width: 1em;
            margin-left: -1.5em;
            position: absolute;
            left: 0;
        }
    </style>
</head>
<body class="antialiased">

    <!-- Navegación Principal -->
    <nav id="main-nav" class="hidden md:block">
        <div class="container mx-auto px-4">
            <div class="flex justify-center items-center flex-wrap">
                <a href="#diagnostico_simple">Diagnóstico Holding</a>
                <a href="#objetivos_simple">Objetivos Holding</a>
                <a href="#estrategia_clientes_simple">Estrategia Clientes Holding</a>
                <a href="#plan_trabajo_simple">Plan de Trabajo Holding</a>
                <!-- <a href="#gantt_simple">Gantt Holding</a> -->
                <a href="#kpis_simple">KPIs Holding</a>
                <a href="#introduccion_firmavb">Introducción FirmaVB</a>
                <a href="#fundamentos_firmavb">Fundamentos FirmaVB</a>
                <a href="#categorias_firmavb">Categorías FirmaVB</a>
                <a href="#nivel_servicio_firmavb">Servicio FirmaVB</a>
                <a href="#acciones_clave_firmavb">Acciones FirmaVB</a>
                <a href="#nuevo_rumbo_compromiso">Nuevo Rumbo y Compromiso</a>
                <a href="#foco_comercial_presupuesto">Foco Comercial y Presupuesto</a>
                <a href="#comunicados_oficiales">Comunicados Oficiales</a>
                <a href="#procedimiento_facturas">Procedimiento Facturas</a>
                <a href="#conclusion_firmavb">Conclusión FirmaVB</a>
            </div>
        </div>
    </nav>

    <!-- Encabezado Principal (Existente) -->
    <header class="bg-gradient-to-r from-[#073B4C] to-[#118AB2] py-10 text-white text-center">
        <div class="container mx-auto px-4">
            <h1 class="text-3xl md:text-4xl font-bold mb-2">Plan Estratégico Consolidado</h1>
            <p class="text-lg md:text-xl font-light">Foco en Rentabilidad, Clientes Clave y Servicio Excepcional</p>
        </div>
    </header>

    <main class="container mx-auto px-4 py-6">

        <!-- Sección: Diagnóstico y Desafíos Clave (Existente) -->
        <section id="diagnostico_simple" class="mb-8 content-card">
            <h2 class="section-heading">Diagnóstico y Desafíos Clave (Holding)</h2>
            <p class="text-main text-center mb-6 max-w-2xl mx-auto">
                El análisis Ene-Abr 2025 muestra la necesidad urgente de un cambio estratégico para mejorar la rentabilidad y eficiencia.
            </p>
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-center">
                <div class="p-4 bg-red-50 rounded-md">
                    <p class="text-sm text-red-700 font-semibold">Resultado Operacional</p>
                    <p class="text-2xl font-bold text-red-600">- $7.6M</p>
                </div>
                <div class="p-4 bg-yellow-50 rounded-md">
                    <p class="text-sm text-yellow-700 font-semibold">Margen Bruto Holding (Actual)</p>
                    <p class="text-2xl font-bold text-yellow-600">13.31%</p>
                </div>
                <div class="sm:col-span-2 p-4 bg-blue-50 rounded-md mt-2">
                    <p class="text-sm text-blue-700 font-semibold mb-1">Otros Desafíos Importantes:</p>
                    <ul class="text-xs text-blue-600 list-disc list-inside text-left space-y-0.5">
                        <li>Alta dependencia del factoring.</li>
                        <li>Márgenes bajos: Cloudbook (13.02%), Comercializadora MP (10.29%). Grumpy destaca (22.39%).</li>
                        <li>Ineficiencias en inventario.</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- Sección: Objetivos Estratégicos Principales (Existente) -->
        <section id="objetivos_simple" class="mb-8 content-card">
            <h2 class="section-heading">Objetivos Estratégicos Principales (6-12 Meses) (Holding)</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-main">
                <div class="flex items-center p-3 bg-slate-50 rounded-md">
                    <span class="text-2xl mr-3">🎯</span>
                    <div><strong>Rentabilidad:</strong> Margen Bruto Consolidado <strong class="highlight">>18%</strong>.</div>
                </div>
                <div class="flex items-center p-3 bg-slate-50 rounded-md">
                    <span class="text-2xl mr-3">📈</span>
                    <div><strong>Resultado Operacional:</strong> Punto de equilibrio (6m), utilidad (12m).</div>
                </div>
                <div class="flex items-center p-3 bg-slate-50 rounded-md">
                    <span class="text-2xl mr-3">💰</span>
                    <div><strong>Flujo de Caja:</strong> Reducir dependencia factoring 30-40%.</div>
                </div>
                <div class="flex items-center p-3 bg-slate-50 rounded-md">
                    <span class="text-2xl mr-3">📦</span>
                    <div><strong>Inventario:</strong> Control con nuevo ERP (Jorge L., 6m), reducir sobrante 70% (9m).</div>
                </div>
                <div class="flex items-center p-3 bg-slate-50 rounded-md md:col-span-2">
                    <span class="text-2xl mr-3">🤖</span>
                    <div><strong>Robot Postulaciones (Mary):</strong> Rentabilidad neta positiva (6-9m), enfocando en licitaciones y categorías rentables.</div>
                </div>
            </div>
        </section>

        <!-- Sección: Estrategia de Foco en Clientes (Existente) -->
        <section id="estrategia_clientes_simple" class="mb-8 content-card">
            <h2 class="section-heading">Estrategia de Foco en Clientes (Resumen) (Holding)</h2>
            <p class="text-main mb-4">Clasificaremos a los clientes según su margen y condición de pago para aplicar estrategias diferenciadas:</p>
            <div class="overflow-x-auto shadow rounded-md">
                <table class="min-w-full bg-white text-xs">
                    <thead>
                        <tr>
                            <th class="p-2">Margen / Pago</th>
                            <th class="p-2 text-[#06D6A0]">Buen Pagador</th>
                            <th class="p-2 text-[#FFD166]">Pagador Promedio</th>
                            <th class="p-2 text-[#FF6B6B]">Mal Pagador</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr class="text-center border-b">
                            <td class="p-2 font-semibold bg-slate-50">Alto Margen</td>
                            <td class="p-2 bg-green-50">⭐ FOCO 1: Fidelizar</td>
                            <td class="p-2 bg-yellow-50">🎯 FOCO 2: Mejorar Pago</td>
                            <td class="p-2 bg-red-50">🔍 EVALUAR</td>
                        </tr>
                        <tr class="text-center border-b">
                            <td class="p-2 font-semibold bg-slate-50">Margen Medio</td>
                            <td class="p-2 bg-green-50">📈 OPTIMIZAR MARGEN</td>
                            <td class="p-2 bg-yellow-50">⚖️ MANTENER/OPTIMIZAR</td>
                            <td class="p-2 bg-red-50">🚨 ALERTA</td>
                        </tr>
                        <tr class="text-center">
                            <td class="p-2 font-semibold bg-slate-50">Bajo Margen</td>
                            <td class="p-2 bg-orange-50">🛠️ OPTIMIZAR URGENTE</td>
                            <td class="p-2 bg-gray-100">📉 BAJA PRIORIDAD</td>
                            <td class="p-2 bg-red-100">🚫 NO TRABAJAR</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <p class="text-main mt-4"><strong>Acciones Clave del Equipo Comercial (Mary, Paz, Erick, Tomás):</strong> Aplicar estas estrategias, negociar condiciones, buscar cross/up-selling en clientes FOCO.</p>
            <p class="text-main mt-2"><strong>Análisis de Categorías:</strong> Se priorizará la rentabilidad en <strong class="highlight">Mobiliario</strong> (meta >25%), se optimizará <strong class="highlight">Art. Oficina</strong> (evitando márgenes bajos como Prisa 4-9%) y se buscará eficiencia en <strong class="highlight">Desechables</strong>.</p>
        </section>

        <!-- Sección: Plan de Trabajo y Tareas Asignadas (Existente) -->
        <section id="plan_trabajo_simple" class="mb-8 content-card">
            <h2 class="section-heading">Plan de Trabajo y Tareas Asignadas (Holding)</h2>
            <div class="overflow-x-auto">
                <table class="table-plan">
                    <thead>
                        <tr>
                            <th>Actividad Principal</th>
                            <th>Responsable(s)</th>
                            <th>Plazo Estimado</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>1. Finalizar Análisis Rentabilidad Clientes y Pagos</td>
                            <td>Enrique V., Mauricio R., Juanita</td>
                            <td>~14 Junio</td>
                        </tr>
                        <tr>
                            <td>2. Definir Segmentos y Listados Finales de Clientes</td>
                            <td>Enrique V., Mauricio R.</td>
                            <td>Hasta 21 Junio</td>
                        </tr>
                        <tr>
                            <td>3. Capacitar Equipo Comercial en Estrategias</td>
                            <td>Enrique V.</td>
                            <td>Semana 24 Junio</td>
                        </tr>
                        <tr>
                            <td>4. Revisar Carteras Individuales con Ejecutivos</td>
                            <td>Ejecutivos Comerciales con Enrique V.</td>
                            <td>Hasta 5 Julio</td>
                        </tr>
                        <tr>
                            <td>5. Implementar Estrategias de Clientes y Proyectos</td>
                            <td>Equipo Comercial, Mary (Robot), Jorge L. (ERP)</td>
                            <td>Desde Julio (Continuo)</td>
                        </tr>
                        <tr>
                            <td>6. Implementación Nuevo ERP (Fases Clave)</td>
                            <td>Jorge L.</td>
                            <td>Q4 2025 (Puesta en Marcha)</td>
                        </tr>
                        <tr>
                            <td>7. Seguimiento Mensual de KPIs</td>
                            <td>Enrique V., Mauricio R., Líderes</td>
                            <td>Mensual (1ª rev. fines Julio)</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <!-- Sección: Carta Gantt Simplificada (ELIMINADA) -->
        <!-- La sección completa de la Carta Gantt ha sido eliminada según la solicitud. -->
        <!-- <section id="gantt_simple" class="mb-8 content-card"> ... </section> -->

        <!-- Sección: KPIs Esenciales para Seguimiento (Existente) -->
        <section id="kpis_simple" class="mb-8 content-card">
            <h2 class="section-heading">KPIs Esenciales para Seguimiento (Holding)</h2>
            <ul class="grid grid-cols-1 sm:grid-cols-2 gap-3 text-sm text-main">
                <li class="flex items-center"><span class="text-lg mr-2 text-[#06D6A0]">✔️</span>Margen Bruto Promedio por Cliente y Segmento.</li>
                <li class="flex items-center"><span class="text-lg mr-2 text-[#06D6A0]">✔️</span>% Ventas/Margen de Clientes FOCO.</li>
                <li class="flex items-center"><span class="text-lg mr-2 text-[#06D6A0]">✔️</span>Días Promedio de Cobro (DSO).</li>
                <li class="flex items-center"><span class="text-lg mr-2 text-[#06D6A0]">✔️</span>% Cartera Vencida.</li>
                <li class="flex items-center"><span class="text-lg mr-2 text-[#06D6A0]">✔️</span>Rentabilidad Neta Robot Postulaciones.</li>
                <li class="flex items-center"><span class="text-lg mr-2 text-[#06D6A0]">✔️</span>Exactitud y Rotación de Inventario (Post-ERP).</li>
            </ul>
        </section>

        <!-- NUEVAS SECCIONES DEL PLAN ESTRATÉGICO FIRMAVB -->

        <!-- Sección 1: Introducción - Visión de Océanos Azules (FirmaVB) -->
        <section id="introduccion_firmavb" class="section-card">
            <h2 class="section-title">1. Introducción: Visión de Océanos Azules (FirmaVB)</h2>
            <p class="text-lg leading-relaxed text-main">
                FirmaVB ha decidido alinear toda su estrategia empresarial bajo una tesis central: los **océanos azules** —espacios competitivos con alto margen y poca saturación— solo pueden ser alcanzados mediante un **nivel de servicio excepcional**. No se trata solo de competir, sino de diferenciarnos radicalmente por la experiencia que ofrecemos.
            </p>
        </section>

        <!-- Nueva Sección: El Nuevo Rumbo y Nuestro Compromiso -->
        <section id="nuevo_rumbo_compromiso" class="section-card">
            <h2 class="section-title">El Nuevo Rumbo y Nuestro Compromiso</h2>
            <p class="text-lg leading-relaxed text-main mb-4">
                Estimado Equipo de FirmaVB, me dirijo a ustedes hoy, no solo como Gerente General, sino como el capitán de este barco que con orgullo y gran esfuerzo hemos construido juntos. Quiero compartir una reflexión estratégica y los próximos pasos que daremos para asegurar un futuro próspero y fiel a nuestra esencia.
            </p>
            <p class="text-lg leading-relaxed text-main mb-4">
                Hemos decidido **corregir el rumbo**. No es un giro brusco, sino una evolución inteligente, un ajuste fino de nuestra estrategia aprovechando todo lo aprendido. Volveremos a nuestro origen: la comercialización de productos que nos den el **margen que necesitamos** para seguir creciendo de forma sana y sostenible.
            </p>
            <p class="text-lg leading-relaxed text-main">
                Nuestra mayor fortaleza es, y debe ser siempre, ver oportunidades donde otros solo ven dificultades. Este ajuste nos llevará a mejorar los resultados de la compañía y a navegar hacia aguas más prósperas.
            </p>
        </section>

        <!-- Sección 2: Fundamentos de la Estrategia (FirmaVB) -->
        <section id="fundamentos_firmavb" class="section-card">
            <h2 class="section-title">2. Fundamentos de la Estrategia (FirmaVB)</h2>
            <p class="text-lg mb-6 text-main">Nuestro modelo se apoya en cuatro pilares estratégicos que fortalecen esta búsqueda:</p>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="bg-blue-50-custom p-6 rounded-lg shadow-sm flex items-start space-x-3">
                    <span class="text-blue-600-custom text-2xl font-bold">1.</span>
                    <p class="text-lg font-medium text-gray-700">Nivel de servicio como ventaja competitiva real.</p>
                </div>
                <div class="bg-blue-50-custom p-6 rounded-lg shadow-sm flex items-start space-x-3">
                    <span class="text-blue-600-custom text-2xl font-bold">2.</span>
                    <p class="text-lg font-medium text-gray-700">Optimización del flujo de caja (menos capital atrapado).</p>
                </div>
                <div class="bg-blue-50-custom p-6 rounded-lg shadow-sm flex items-start space-x-3">
                    <span class="text-blue-600-custom text-2xl font-bold">3.</span>
                    <p class="text-lg font-medium text-gray-700">Consolidación de proveedores estratégicos.</p>
                </div>
                <div class="bg-blue-50-custom p-6 rounded-lg shadow-sm flex items-start space-x-3">
                    <span class="text-blue-600-custom text-2xl font-bold">4.</span>
                    <p class="text-lg font-medium text-gray-700">Mix de productos con foco en rentabilidad sostenible.</p>
                </div>
            </div>
        </section>

        <!-- Sección 3: Categorías Estratégicas y Proveedores Clave (FirmaVB) -->
        <section id="categorias_firmavb" class="section-card">
            <h2 class="section-title">3. Categorías Estratégicas y Proveedores Clave (FirmaVB)</h2>
            <div class="overflow-x-auto">
                <table class="table-plan"> <!-- Usando la clase de tabla existente -->
                    <thead>
                        <tr>
                            <th>Categoría</th>
                            <th>Proveedores Estratégicos</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>Artículos de Oficina</td>
                            <td>Acco Brands, Torre, Distec Pronobel, Adiofice, Dipisa, Prisa (pivote), [Nuevo Proveedor 7]</td>
                        </tr>
                        <tr>
                            <td>Mobiliario (Ergonómico, Oficina, Escolar)</td>
                            <td>Acco Brands (ergonomía), HP Muebles, Full Muebles, Ofix Chile, TokStok, Sodimac (pivote)</td>
                        </tr>
                        <tr>
                            <td>Desechables</td>
                            <td>Foodpack, DPS, Darnel, Akipack</td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <p class="text-main mt-4">
                A partir de ahora, en la categoría de artículos de oficina, concentraremos nuestro esfuerzo estratégico y comercial trabajando exclusivamente con **siete proveedores claves y estratégicos**: Acco Brands, Torre, Distec Pronobel, Adiofice, Dipisa, Prisa, y un séptimo proveedor a definir. Reduciremos nuestra base de 16 proveedores a solo estos 7 socios estratégicos. Esta consolidación nos permitirá fortalecer nuestras relaciones, mejorar la eficiencia, optimizar nuestras compras y, en definitiva, entregar un mejor servicio y valor a nuestros clientes.
            </p>
            <p class="text-main mt-2">
                Respecto a las demás categorías, realizaremos una revisión exhaustiva durante el mes de junio para asegurar que todas estén alineadas con nuestra estrategia central de rentabilidad y "océanos azules".
            </p>
        </section>

        <!-- Sección 4: Nivel de Servicio como Clave Estratégica (FirmaVB) -->
        <section id="nivel_servicio_firmavb" class="section-card">
            <h2 class="section-title">4. Nivel de Servicio como Clave Estratégica (FirmaVB)</h2>
            <p class="text-lg mb-6 text-main">El nivel de servicio no es un valor adicional, sino el **núcleo** desde el cual construimos una ventaja competitiva sostenible. Esto implica:</p>
            <ul>
                <li class="text-main new-list-item">Cumplimiento de plazos</li>
                <li class="text-main new-list-item">Agilidad en gestión de órdenes</li>
                <li class="text-main new-list-item">Atención cercana y empática</li>
                <li class="text-main new-list-item">Capacidad de adaptación al cliente</li>
                <li class="text-main new-list-item">Excelencia en logística y postventa</li>
            </ul>
        </section>

        <!-- Sección 5: Acciones Clave por Área (FirmaVB) -->
        <section id="acciones_clave_firmavb" class="section-card">
            <h2 class="section-title">5. Acciones Clave por Área (FirmaVB)</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <div class="bg-green-50-custom p-6 rounded-lg shadow-sm">
                    <h3 class="subsection-title text-green-700-custom">Comercial</h3>
                    <p class="text-gray-700 text-main">Foco en las categorías definidas y en productos con márgenes saludables. **Prioridad en los 7 proveedores estratégicos de artículos de oficina.**</p>
                </div>
                <div class="bg-yellow-50-custom p-6 rounded-lg shadow-sm">
                    <h3 class="subsection-title text-yellow-700-custom">Compras</h3>
                    <p class="text-gray-700 text-main">Consolidar proveedores, estandarizar condiciones y negociar líneas de crédito efectivas. **Reducción a 7 proveedores clave.**</p>
                </div>
                <div class="bg-red-50-custom p-6 rounded-lg shadow-sm">
                    <h3 class="subsection-title text-red-700-custom">Administración y Finanzas</h3>
                    <p class="text-gray-700 text-main">Priorizar a clientes que sí pagan. Minimizar uso de factoring. Control estricto de flujo de caja. **Asegurar que cada venta se traduzca en flujo de caja positivo.**</p>
                </div>
                <div class="bg-purple-50-custom p-6 rounded-lg shadow-sm">
                    <h3 class="subsection-title text-purple-700-custom">Postventa y Logística</h3>
                    <p class="text-gray-700 text-main">Garantizar un nivel de servicio excepcional en cada entrega y postventa institucional.</p>
                </div>
            </div>
        </section>

        <!-- Nueva Sección: Foco Comercial y Cumplimiento de Presupuesto -->
        <section id="foco_comercial_presupuesto" class="section-card">
            <h2 class="section-title">Foco Comercial y Cumplimiento de Presupuesto</h2>
            <p class="text-lg leading-relaxed text-main mb-4">
                Esta medida de ajuste estratégico debe ir acompañada de un **foco implacable en la rentabilidad**. Por ello, es fundamental priorizar a los clientes que sí pagan. Nuestro equipo de Administración y Finanzas jugará un rol crucial aquí, manteniéndonos alerta y asegurando que cada venta que cerremos contribuya positivamente al resultado final.
            </p>
            <p class="text-lg leading-relaxed text-main">
                El esfuerzo de venta es valioso solo cuando se traduce en **flujo de caja**. Continuaremos monitoreando de cerca el cumplimiento del presupuesto, asegurando que nuestras operaciones comerciales no solo generen ventas, sino que estas sean rentables y se conviertan en liquidez para la compañía.
            </p>
        </section>

        <!-- Sección: Comunicados Oficiales -->
        <section id="comunicados_oficiales" class="section-card">
            <h2 class="section-title">Comunicados Oficiales de FirmaVB</h2>
            <p class="text-lg leading-relaxed text-main mb-4">
                A continuación, se presenta la información relevante que hemos comunicado al equipo, detallando el camino que estamos tomando, las tareas que vamos absorbiendo, las responsabilidades y el foco estratégico.
            </p>

            <h3 class="subsection-title">Comunicado Oficial: Aumento de Margen y Estabilidad Financiera (Parte 1)</h3>
            <p class="text-main mb-2">
                Estimado Equipo de FirmaVB,
                Me dirijo a ustedes hoy, no solo como Gerente General, sino como el capitán de este barco que con orgullo y gran esfuerzo hemos construido juntos. Quiero compartir una reflexión estratégica y los próximos pasos que daremos para asegurar un futuro próspero y fiel a nuestra esencia.
            </p>
            <p class="text-main mb-2">
                Como saben, nuestra filosofía siempre ha sido navegar en océanos azules: encontrar y dominar aquellos nichos donde el valor y el margen son nuestros verdaderos motores. Nuestra mayor fortaleza es, y debe ser siempre, ver oportunidades donde otros solo ven dificultades.
            </p>
            <p class="text-main mb-2">
                Recientemente, hemos dedicado una energía considerable a la categoría de artículos de oficina. Ha sido un mercado complejo y desafiante que, sin duda, nos ha puesto a prueba. Quiero ser claro: el esfuerzo ha sido tremendo y hemos logrado crecer en ventas en un terreno muy competitivo. Este viaje nos ha dejado aprendizajes invaluables en todas las áreas: ventas, compras, logística, administración y, muy importante, en cobranzas. Cada desafío ha sido una lección que hoy nos hace más fuertes y más sabios.
            </p>
            <p class="text-main mb-2">
                Uno de esos grandes aprendizajes es la importancia de ser fieles a nuestra estrategia: cazar margen, buscar oportunidades únicas y materializarlas con agilidad. La pasada por esta categoría nos ha recordado que nuestro verdadero talento no está en competir en guerras de precios, sino en nuestra versatilidad y nuestra visión.
            </p>
            <p class="text-main mb-4">
                Por todo esto, hemos decidido corregir el rumbo. No es un giro brusco, sino una evolución inteligente, un ajuste fino de nuestra estrategia aprovechando todo lo aprendido. Volveremos a nuestro origen: la comercialización de productos que nos den el margen que necesitamos para seguir creciendo de forma sana y sostenible.
            </p>

            <h3 class="subsection-title">Consolidación de Proveedores y Foco en Rentabilidad (Continuación)</h3>
            <p class="text-main mb-2">
                El primer gran paso en esta dirección lo daremos en la categoría de artículos de oficina. A partir de ahora, concentraremos todo nuestro esfuerzo estratégico y comercial trabajando exclusivamente con **siete proveedores claves y estratégicos**: Acco Brands, Torre, Distec Pronobel, Adiofice, Dipisa y Prisa. Reduciremos nuestra base de 16 proveedores a solo estos 7 socios estratégicos. Esta consolidación nos permitirá fortalecer nuestras relaciones, mejorar la eficiencia, optimizar nuestras compras y, en definitiva, entregar un mejor servicio y valor a nuestros clientes.
            </p>
            <p class="text-main mb-2">
                Esta medida debe ir acompañada de un foco implacable en la rentabilidad. Por ello, es fundamental priorizar a los clientes que sí pagan. Nuestro equipo de Administración y Finanzas jugará un rol crucial aquí, manteniéndonos alerta y asegurando que cada venta que cerremos contribuya positivamente al resultado final. El esfuerzo de venta es valioso solo cuando se traduce en flujo de caja.
            </p>
            <p class="text-main mb-4">
                Respecto a las demás categorías, realizaremos una revisión exhaustiva durante el mes de junio para asegurar que todas estén alineadas con nuestra estrategia central de rentabilidad y "océanos azules".
            </p>

            <p class="text-main italic">
                Confío plenamente en la capacidad de este equipo. Nuestra habilidad para ver donde otros no ven es lo que nos define. Este ajuste de rumbo nos llevará a mejorar los resultados de la compañía y a navegar hacia aguas más prósperas. Agradezco el compromiso y la resiliencia de todos. Ahora, ¡a ejecutar con la excelencia de siempre!
            </p>
            <p class="text-main text-right mt-4">
                Atentamente,<br>
                Enrique E. Varas B. | FirmaVB<br>
                Gerente General
            </p>

            <hr class="my-8 border-t-2 border-gray-200"> <!-- Separador entre comunicados -->

            <h3 class="subsection-title">Comunicado Oficial: Mirar donde otros no ven... Parte 2 - Mobiliario</h3>
            <p class="text-main mb-2">
                Estimado Equipo de FirmaVB,
                Dando continuidad a nuestra visión estratégica de navegar en "océanos azules" y asegurar un futuro próspero para FirmaVB, hoy quiero enfocar nuestra atención en la categoría de **Mobiliario**. Esta categoría, que abarca oficina, mobiliario escolar y ergonómico, es crucial para nuestro crecimiento y rentabilidad, pero presenta desafíos específicos que abordaremos con determinación y estrategia.
            </p>
            <p class="text-main mb-2">
                Hemos identificado que, si bien el potencial de ventas es significativo, la operación actual en mobiliario está generando una demanda elevada de capital de trabajo y una excesiva dependencia del factoring, impactando nuestro flujo de caja. Esto se debe principalmente a las condiciones de crédito limitadas con algunos proveedores y a la falta de profundidad en la relación con otros que podrían ofrecernos mayor estabilidad en inventario y condiciones favorables.
            </p>

            <h4 class="sub-heading">Nuestra estrategia para la categoría de mobiliario se centrará en los siguientes pilares fundamentales:</h4>
            <ul class="list-disc list-inside text-main mb-4">
                <li>
                    <strong>1. Optimización del Flujo de Caja como Prioridad Central:</strong> Corregiremos el rumbo para reducir el consumo de capital de trabajo. Esto significa gestionar activamente las condiciones de crédito con nuestros proveedores y limitar operaciones que nos obliguen a dar "vueltas" excesivas a líneas de crédito acotadas o a comprar al contado, priorizando siempre la salud de nuestro flujo de caja.
                </li>
                <li>
                    <strong>2. Consolidación y Profesionalización con Proveedores Clave:</strong> Profundizaremos y estandarizaremos la relación con nuestros socios estratégicos. Esto incluye a:
                    <ul class="list-circle list-inside ml-4 text-sm mt-2">
                        <li><strong>Acco Brands:</strong> Actor fundamental con 90 días de crédito y cupo ilimitado, proveedor de foco para Ergonomía.</li>
                        <li><strong>Full Muebles:</strong> Con 45 días de crédito y cupo ilimitado. Vigilancia en compras al contado.</li>
                        <li><strong>HP Muebles:</strong> Confirmando sus 60 días de crédito.</li>
                        <li><strong>Ofix Chile:</strong> Con sus 30 días de crédito.</li>
                        <li><strong>TokStok:</strong> Línea de crédito de $10.000.000, acotado a compras ágiles de bajo volumen (aprox. 65 sillas mensuales).</li>
                    </ul>
                </li>
                <li>
                    <strong>3. Búsqueda Activa de un Proveedor Pivote (Tipo Sodimac):</strong> Necesidad imperativa de un proveedor con amplitud de stock, flexibilidad y condiciones de crédito que complementen nuestra oferta actual. Nuestra apuesta estratégica es Sodimac.
                </li>
                <li>
                    <strong>4. Enfoque en el Mix de Productos para Maximizar el Margen:</strong> Para alcanzar nuestro margen objetivo del 20-22% en esta categoría, priorizaremos la venta de un mix de productos complementarios (ej. silla, kardex y mobiliario para elevar rentabilidad a 25%).
                </li>
            </ul>

            <p class="text-main mb-4">
                Este ajuste de rumbo no es una desviación, sino una evolución inteligente que capitaliza nuestros aprendizajes y nos permite ser fieles a nuestra filosofía de "cazar margen" y generar flujo de caja.
            </p>
            <p class="text-main italic">
                Agradezco de antemano el compromiso de cada uno en la ejecución de esta estrategia. La colaboración entre Ventas, Compras y Administración será, más que nunca, fundamental para garantizar que cada venta contribuya positivamente a nuestra estabilidad financiera y a nuestra propuesta de valor.
            </p>
            <p class="text-main text-right mt-4">
                Atentamente,<br>
                Enrique E. Varas B. | FirmaVB<br>
                Gerente General
            </p>
        </section>

        <!-- Nueva Sección: Procedimiento de Emisión de Facturas para Proveedores -->
        <section id="procedimiento_facturas" class="section-card">
            <h2 class="section-title">Procedimiento Proveedores Emisión de Facturas 2025</h2>
            <p class="text-lg leading-relaxed text-main mb-4">
                Estimado(a) Proveedor(a):
                Con el objetivo de agilizar y asegurar la correcta recepción y procesamiento de sus facturas, le solicitamos seguir el siguiente protocolo de envío de documentación para todas las compras realizadas por nuestra compañía. Este procedimiento aplica para todas las órdenes de compra emitidas por nuestra empresa.
            </p>

            <h3 class="subsection-title">1. Datos de Facturación:</h3>
            <p class="text-main mb-2">
                Es crucial que las facturas se emitan con nuestra información tributaria precisa. Consulte a su comprador y especifique claramente la condición de pago, incluyendo en el campo 801 de la factura el número de nuestra orden de compra.
            </p>

            <h3 class="subsection-title">2. Proceso de Envío de Facturas y Guías de Despacho:</h3>
            <p class="text-main mb-2">
                Una vez despachado el producto y emitida la factura, siga estos pasos:
            </p>
            <ul class="list-disc list-inside text-main mb-4">
                <li class="new-list-item">
                    **Envío de Correo Electrónico:** Envíe un correo electrónico con la siguiente estructura:
                    <ul class="list-circle list-inside ml-4 text-sm mt-2">
                        <li>Para: Facturacion y Cobranzas</li>
                        <li>Con Copia (CC): Emprendedores</li>
                        <li>Con Copia (CC): Administracion FirmaVB</li>
                        <li>Asunto del Correo: "Factura N° [Número de Factura] - OC N° [Número de Orden de Compra] - [Nombre de tu Empresa Proveedora]"</li>
                    </ul>
                </li>
                <li class="new-list-item">
                    **Adjuntos Obligatorios:**
                    <ul class="list-circle list-inside ml-4 text-sm mt-2">
                        <li>Factura Electrónica en formato XML y PDF: Asegúrese de adjuntar ambos formatos.</li>
                        <li>Para el envío del XML es necesario enviarlo a nuestra casilla del facturador electrónico: <strong class="highlight">cl.empresas@defontanadte.com</strong></li>
                        <li>Guía(s) de Despacho / Factura Recepcionada(s) Conforme: Es indispensable adjuntar la copia de la guía de despacho o factura debidamente timbrada y firmada por nuestro personal al momento de la recepción del producto. Sin este documento, no podremos procesar su pago.</li>
                    </ul>
                </li>
                <li class="new-list-item">
                    **Recepción Conforme:** Recuerde que es responsabilidad del transportista o repartidor obtener la firma y el timbre de "recepción conforme" en la guía de despacho o factura por parte de nuestro equipo.
                </li>
            </ul>

            <h3 class="subsection-title">3. Observaciones Importantes:</h3>
            <ul class="list-disc list-inside text-main mb-4">
                <li class="new-list-item">
                    **Documentación Completa:** Solo se procesarán las facturas que vengan acompañadas de la guía de despacho o factura debidamente recepcionada conforme y con los datos de nuestra empresa ingresados correctamente.
                </li>
                <li class="new-list-item">
                    **Contacto para Consultas:** En caso de dudas sobre este procedimiento, favor de contactar al área de Compras de FirmaVB.
                </li>
            </ul>
            <p class="text-lg leading-relaxed text-main mb-4">
                Agradecemos de antemano su colaboración para asegurar una gestión eficiente y oportuna de nuestros procesos de compra y pago.
            </p>
            <p class="text-main text-right mt-4">
                Saludos cordiales,<br>
                El Equipo de Compras FirmaVB<br>
                Un abrazo, Enrique E. Varas B. | FirmaVB
            </p>
        </section>

        <!-- Sección 6: Conclusión y Liderazgo (FirmaVB) -->
        <section id="conclusion_firmavb" class="section-card text-center">
            <h2 class="section-title mx-auto">6. Conclusión y Liderazgo (FirmaVB)</h2>
            <p class="text-lg mb-4 leading-relaxed text-main">
                La evolución de FirmaVB no es un cambio de rumbo, sino una maduración estratégica.
            </p>
            <p class="text-2xl font-semibold text-[#118AB2] mb-6">
                Nuestra meta no es competir donde todos compiten, sino <span class="font-bold italic">crear valor donde nadie más lo ve.</span>
            </p>
            <p class="text-xl leading-relaxed text-main">
                El <span class="font-bold text-[#118AB2]">nivel de servicio</span> es el motor que nos lleva a esos espacios únicos de rentabilidad y crecimiento sostenible.
            </p>
        </section>

    </main>

    <!-- Pie de página (Existente) -->
    <footer class="bg-[#073B4C] text-center py-6 text-[#FFD166]">
        <p class="font-semibold text-sm">&copy; <span id="currentYearSimple"></span> Holding Estratégico S.A.</p>
        <p class="text-xs mt-1 opacity-75">Plan Estratégico Simplificado (v1)</p>
        <p class="text-xs mt-1 opacity-75">FirmaVB Plan Estratégico</p>
        <p class="text-xs mt-1 opacity-75">Atentamente, Enrique E. Varas B. - Gerente General – FirmaVB</p>
    </footer>

    <script>
        document.getElementById('currentYearSimple').textContent = new Date().getFullYear();
        Chart.register(ChartDataLabels);

        // Function to highlight the current week in the Gantt chart (still present in JS for robustness)
        function highlightCurrentWeek() {
            const today = new Date();
            const currentYear = today.getFullYear();
            const currentMonth = today.getMonth(); // 0-indexed (June is 5)

            // Check if the current month is June 2025
            if (currentYear === 2025 && currentMonth === 5) { // 5 for June
                const dayOfMonth = today.getDate();

                let currentWeekColumn = 0;
                if (dayOfMonth >= 1 && dayOfMonth <= 7) {
                    currentWeekColumn = 1;
                } else if (dayOfMonth >= 8 && dayOfMonth <= 14) {
                    currentWeekColumn = 2;
                } else if (dayOfMonth >= 15 && dayOfMonth <= 21) {
                    currentWeekColumn = 3;
                } else if (dayOfMonth >= 22 && dayOfMonth <= 28) {
                    currentWeekColumn = 4;
                } else if (dayOfMonth >= 29 && dayOfMonth <= 30) {
                    currentWeekColumn = 5; // This would be the 5th column if the Gantt shows 6 weeks
                }

                if (currentWeekColumn > 0) {
                    // Get all week header elements
                    const weekHeaders = document.querySelectorAll(`.gantt-timeline-header-simplified .week-header-col-${currentWeekColumn}`);
                    if (weekHeaders.length > 0) {
                        weekHeaders[0].classList.add('current-week-highlight');
                    }
                }
            }
        }

        // Sticky Nav Scroll Active State
        const navElementSimple = document.getElementById('main-nav');
        if (navElementSimple) {
            const navLinksSimple = navElementSimple.querySelectorAll('a');
            // Select all sections that have an ID and are within the main content area
            const sectionsSimple = document.querySelectorAll('main section[id]');

            function changeNavSimple() {
                let index = sectionsSimple.length;
                // Loop backwards to find the current section in view
                while(--index >= 0 && window.scrollY + navElementSimple.offsetHeight + 10 < sectionsSimple[index].offsetTop) {}

                navLinksSimple.forEach((link) => link.classList.remove('active'));
                if (index >= 0 && navLinksSimple[index]) {
                    // Find the corresponding nav link by matching href with section ID
                    const currentSectionId = sectionsSimple[index].id;
                    const activeLink = Array.from(navLinksSimple).find(link => link.getAttribute('href') === `#${currentSectionId}`);
                    if (activeLink) {
                        activeLink.classList.add('active');
                    }
                }
            }

            if (sectionsSimple.length > 0) { // Ensure sections exist before adding listener
                changeNavSimple();
                window.addEventListener('scroll', changeNavSimple);
            }
        }

        // Call the function when the page loads
        window.addEventListener('load', highlightCurrentWeek);

        // --- OC Summary Data Loading (Still present, but section removed from HTML) ---
        // This data would typically come from a server-side process or API call
        // For this demonstration, it's hardcoded based on the Python processing of your CSV
        const ocSummaryData = {
    "top_suppliers": [
        {
            "name": "TORRE S.A.",
            "value": 11090333.0,
            "value_formatted": "$11.090.333,00"
        },
        {
            "name": "ADIOFFICE S.A.",
            "value": 2901300.0,
            "value_formatted": "$2.901.300,00"
        },
        {
            "name": "DIPISA S.A.",
            "value": 2043800.0,
            "value_formatted": "$2.043.800,00"
        },
        {
            "name": "ACCOR BRANDS CHILE S.A.",
            "value": 1699990.0,
            "value_formatted": "$1.699.990,00"
        },
        {
            "name": "PRISA S.A.",
            "value": 1600000.0,
            "value_formatted": "$1.600.000,00"
        }
    ],
    "top_institutions": [
        {
            "name": "INSTITUTO PROFESIONAL AIEP",
            "value": 12000000.0,
            "value_formatted": "$12.000.000,00"
        },
        {
            "name": "UNIVERSIDAD SAN SEBASTIAN",
            "value": 1800000.0,
            "value_formatted": "$1.800.000,00"
        },
        {
            "name": "COLEGIO ALTO LAS CONDES",
            "value": 1500000.0,
            "value_formatted": "$1.500.000,00"
        },
        {
            "name": "MUNICIPALIDAD DE LAS CONDES",
            "value": 1200000.0,
            "value_formatted": "$1.200.000,00"
        },
        {
            "name": "CLINICA ALEMANA DE SANTIAGO S.A.",
            "value": 900000.0,
            "value_formatted": "$900.000,00"
        }
    ],
    "top_products": [
        {
            "name": "RESMA PAPEL MULTIUSO",
            "value": 8000000.0,
            "value_formatted": "$8.000.000,00"
        },
        {
            "name": "CARTULINA ESPA\u00d1OLA",
            "value": 2500000.0,
            "value_formatted": "$2.500.000,00"
        },
        {
            "name": "LAPICES GRAFITO",
            "value": 1800000.0,
            "value_formatted": "$1.800.000,00"
        },
        {
            "name": "CUADERNOS UNIVERSITARIOS",
            "value": 1500000.0,
            "value_formatted": "$1.500.000,00"
        },
        {
            "name": "SILLA ERGONOMICA",
            "value": 1200000.0,
            "value_formatted": "$1.200.000,00"
        }
    ]
};


        function loadOCSummary() {
            // Check if the element exists before trying to populate it
            const topSuppliersList = document.getElementById('top-suppliers-list');
            const topInstitutionsList = document.getElementById('top-institutions-list');
            const topProductsList = document.getElementById('top-products-list');

            if (ocSummaryData && !ocSummaryData.error && topSuppliersList && topInstitutionsList && topProductsList) {
                // Populate Top Suppliers
                topSuppliersList.innerHTML = '';
                ocSummaryData.top_suppliers.forEach(item => {
                    const li = document.createElement('li');
                    li.textContent = `${item.name}: ${item.value_formatted}`;
                    topSuppliersList.appendChild(li);
                });

                // Populate Top Institutions
                topInstitutionsList.innerHTML = '';
                ocSummaryData.top_institutions.forEach(item => {
                    const li = document.createElement('li');
                    li.textContent = `${item.name}: ${item.value_formatted}`;
                    topInstitutionsList.appendChild(li);
                });

                // Populate Top Products
                topProductsList.innerHTML = '';
                ocSummaryData.top_products.forEach(item => {
                    const li = document.createElement('li');
                    li.textContent = `${item.name}: ${item.value_formatted}`;
                    topProductsList.appendChild(li);
                });
            } else if (ocSummaryData.error) {
                 // Display error message if data loading failed, checking if elements exist first
                if (topSuppliersList) topSuppliersList.innerHTML = '<li class="text-red-500">Error al cargar datos de proveedores.</li>';
                if (topInstitutionsList) topInstitutionsList.innerHTML = '<li class="text-red-500">Error al cargar datos de instituciones.</li>';
                if (topProductsList) topProductsList.innerHTML = '<li class="text-red-500">Error al cargar datos de productos.</li>';
                console.error("Error loading OC Summary Data:", ocSummaryData.error || "Unknown error");
            }
        }

        // Call the function to load OC summary when the page loads
        window.addEventListener('load', loadOCSummary);

    </script>
</body>
</html>
