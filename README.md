
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

        /* Estilos para la tabla Gantt */
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
            background-color: #06D6A0; /* Caribbean Green */
            border-radius: 0.25rem;
            opacity: 0.9;
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
                <a href="#gantt_simple">Gantt Holding</a>
                <a href="#kpis_simple">KPIs Holding</a>
                <a href="#introduccion_firmavb">Introducción FirmaVB</a>
                <a href="#fundamentos_firmavb">Fundamentos FirmaVB</a>
                <a href="#categorias_firmavb">Categorías FirmaVB</a>
                <a href="#nivel_servicio_firmavb">Servicio FirmaVB</a>
                <a href="#acciones_clave_firmavb">Acciones FirmaVB</a>
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

        <!-- Sección: Carta Gantt Simplificada (Actualizada) -->
        <section id="gantt_simple" class="mb-8 content-card">
            <h2 class="section-heading">Carta Gantt Simplificada (Próximas 6 Semanas) (Holding)</h2>
            <div class="gantt-simplified overflow-x-auto p-2">
                <div class="gantt-timeline-header-simplified">
                    <div class="gantt-task-name-simplified gantt-header-simplified">Actividad / Semana</div>
                    {[...Array(6)].map((_, i) => `<div class="gantt-header-simplified">Semana ${i+1}</div>`).join('')}
                </div>

                {[
                    { name: 'Análisis Clientes', start: 1, span: 2, color: '#06D6A0' }, // Semanas 1-2
                    { name: 'Optimización Robot', start: 1, span: 3, color: '#FFD166'}, // Semanas 1-3
                    { name: 'Capacitación Equipo', start: 2, span: 1, color: '#06D6A0' }, // Semana 2 (visual separation from week 1 tasks)
                    { name: 'Revisión Carteras', start: 3, span: 1, color: '#06D6A0' }, // Semana 3
                    { name: 'Implement. Estrategias', start: 3, span: 4, color: '#118AB2' }, // Semanas 3-6
                    { name: 'Seguimiento KPIs', start: 4, span: 3, color: 'rgba(255,209,102,0.6)'}, // Semanas 4-6 (starts slightly after Implement. Estrategias)
                    { name: 'Implementación ERP', start: 1, span: 6, color: '#FF6B6B' } // Semanas 1-6 (long-term project)
                ].map(task => `
                    <div class="gantt-row-simplified">
                        <div class="gantt-task-name-simplified" title="${task.name}">${task.name}</div>
                        <div class="gantt-bar-container-simplified" style="--start-col: ${Math.floor(task.start) + 1}; --span-col: ${task.span};">
                            <div class="gantt-bar-simplified" style="background-color: ${task.color};"></div>
                        </div>
                    </div>
                `).join('')}
            </div>
            <p class="text-xs text-gray-500 mt-2 text-center">Nota: Cada columna representa una semana. Las barras indican duración estimada.</p>
        </section>

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
                            <td>Torre, Dipisa, Acco Brands, Prisa (pivote)</td>
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
                    <p class="text-gray-700 text-main">Foco en las categorías definidas y en productos con márgenes saludables.</p>
                </div>
                <div class="bg-yellow-50-custom p-6 rounded-lg shadow-sm">
                    <h3 class="subsection-title text-yellow-700-custom">Compras</h3>
                    <p class="text-gray-700 text-main">Consolidar proveedores, estandarizar condiciones y negociar líneas de crédito efectivas.</p>
                </div>
                <div class="bg-red-50-custom p-6 rounded-lg shadow-sm">
                    <h3 class="subsection-title text-red-700-custom">Administración y Finanzas</h3>
                    <p class="text-gray-700 text-main">Priorizar a clientes que sí pagan. Minimizar uso de <i>factoring</i>. Control estricto de flujo de caja.</p>
                </div>
                <div class="bg-purple-50-custom p-6 rounded-lg shadow-sm">
                    <h3 class="subsection-title text-purple-700-custom">Postventa y Logística</h3>
                    <p class="text-gray-700 text-main">Garantizar un nivel de servicio excepcional en cada entrega y postventa institucional.</p>
                </div>
            </div>
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
    </script>
</body>
</html>
