<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Infografía: Análisis Estratégico del Mercado y Foco en Cliente del Holding (v2)</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <!-- 
        Resumen del Plan de Narrativa y Estructura (v2):
        La infografía presentará el análisis estratégico del mercado interno y el enfoque en el cliente de "Holding Estratégico S.A.", basado en el informe 'estrategia_foco_clientes_presentacion_v1' y 'estrategia_rentabilidad_caja_v2'.
        Secciones:
        1. Título Principal.
        2. Contexto del Holding y Desafíos (Datos Reales).
        3. Objetivos Estratégicos del Holding.
        4. Metodología de Segmentación de Clientes.
        5. Hallazgos Clave: Radiografía del Portafolio (Márgenes reales de empresas, gráficos de distribución y Venta/Margen como "Modelo Ilustrativo").
        6. Estrategias Clave por Segmento de Clientes (Matriz y Acciones Detalladas).
        7. Plan de Trabajo Detallado (Actividades, Responsables, Plazos).
        8. Carta Gantt Visual del Plan de Trabajo.
        9. Indicadores Clave de Desempeño (KPIs).
        10. Impacto Esperado y Próximos Pasos.

        Confirmación de Ausencia de SVG y Mermaid JS:
        NI Mermaid JS NI SVG fueron utilizados en la generación de esta infografía. 
        Todas las visualizaciones son generadas mediante Chart.js (Canvas) o HTML/CSS con Tailwind.
    -->
    <!-- 
        Selección de Visualizaciones (Resumen v2):
        - Contexto (Pérdida, Márgenes Reales): Single Big Number (HTML/Tailwind). Goal: Inform. No SVG.
        - Objetivos Estratégicos: Lista con iconos (HTML/Tailwind Unicode). Goal: Inform. No SVG.
        - Metodología Segmentación: Flow Chart (HTML/CSS/Tailwind). Goal: Organize. No SVG.
        - Hallazgos Clave (Márgenes Empresas Reales): Bar Chart (Chart.js). Goal: Compare. No SVG.
        - Hallazgos Clave (Distribución Clientes, Venta/Margen - Modelo Ilustrativo): Donut Chart, Grouped Bar Chart (Chart.js). Goal: Compare, Inform. No SVG.
        - Matriz Estratégica: HTML Table (Tailwind). Goal: Organize. No SVG.
        - Plan de Trabajo: HTML Table (Tailwind). Goal: Organize. No SVG.
        - Carta Gantt: HTML/CSS con Tailwind (simulación visual). Goal: Organize. No SVG.
        - KPIs: Lista con iconos (HTML/Tailwind Unicode). Goal: Inform. No SVG.
        - Impacto Esperado: Single Big Number (HTML/Tailwind). Goal: Inform. No SVG.

        Paleta de Colores Seleccionada: "Energetic & Playful"
        - Coral: #FF6B6B
        - Sunglow Yellow: #FFD166
        - Caribbean Green: #06D6A0
        - Blue Munsell: #118AB2
        - Midnight Green (Dark Blue): #073B4C
    -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #F3F4F6; /* Tailwind gray-100 */
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px; 
            margin-left: auto;
            margin-right: auto;
            height: 300px; 
            max-height: 400px;
        }
        @media (min-width: 768px) { /* md breakpoint */
            .chart-container {
                height: 350px;
            }
        }
        @media (min-width: 1024px) { /* lg breakpoint */
            .chart-container {
                height: 400px;
            }
        }
        .stat-card {
            background-color: white;
            border-radius: 0.5rem; /* rounded-lg */
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06); /* shadow-md */
            padding: 1.5rem; /* p-6 */
            margin-bottom: 1.5rem; /* mb-6 */
            color: #073B4C; /* Midnight Green */
        }
        .stat-title {
            font-size: 1.125rem; /* text-lg */
            font-weight: 600; /* font-semibold */
            color: #118AB2; /* Blue Munsell */
            margin-bottom: 0.5rem;
        }
        .stat-value {
            font-size: 2.25rem; /* text-4xl */
            font-weight: 700; /* font-bold */
            color: #06D6A0; /* Caribbean Green */
        }
        .section-title {
            font-size: 1.875rem; /* text-3xl */
            font-weight: 700;
            color: #073B4C; /* Midnight Green */
            margin-bottom: 1rem;
            padding-bottom: 0.5rem;
            border-bottom: 2px solid #06D6A0; /* Caribbean Green */
        }
        .card-title {
            font-size: 1.5rem; /* text-2xl */
            font-weight: 600; /* font-semibold */
            color: #118AB2; /* Blue Munsell */
            margin-bottom:1rem;
        }
        .text-content {
            font-size: 1rem; /* text-base */
            line-height: 1.6;
            color: #374151; /* Tailwind gray-700 */
        }
        .flowchart-step {
            background-color: #FFD166; /* Sunglow Yellow */
            color: #073B4C;
            padding: 1rem;
            border-radius: 0.5rem;
            text-align: center;
            font-weight: 600;
            box-shadow: 0 2px 4px rgba(0,0,0,0.1);
            min-height: 80px;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .flowchart-arrow {
            font-size: 2rem;
            color: #118AB2; /* Blue Munsell */
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .kpi-list li {
            background-color: #E0F2FE; /* Tailwind sky-100 like */
            padding: 0.75rem;
            border-radius: 0.375rem; /* rounded-md */
            margin-bottom: 0.5rem;
            display: flex;
            align-items: center;
            color: #073B4C;
        }
        .kpi-list li::before {
            content: '📊';
            margin-right: 0.75rem;
            font-size: 1.25rem;
        }
        #sticky-nav {
            position: sticky;
            top: 0;
            z-index: 50;
            background-color: rgba(7, 59, 76, 0.9); 
            backdrop-filter: blur(5px);
            padding: 0.5rem 0;
            box-shadow: 0 2px 4px rgba(0,0,0,0.2);
        }
        #sticky-nav a {
            color: #FFD166; 
            padding: 0.5rem 1rem;
            margin: 0 0.25rem;
            border-radius: 0.375rem;
            font-weight: 600;
            transition: background-color 0.3s ease, color 0.3s ease;
        }
        #sticky-nav a:hover, #sticky-nav a.active {
            background-color: #FFD166; 
            color: #073B4C; 
        }
        .gantt-chart {
            display: flex;
            flex-direction: column;
            gap: 0.5rem;
            font-size: 0.875rem;
        }
        .gantt-row {
            display: grid;
            grid-template-columns: 150px repeat(6, 1fr); /* Task name + 6 time units (e.g. weeks/months) */
            align-items: center;
            gap: 0.25rem;
            padding: 0.25rem 0;
            border-bottom: 1px solid #E5E7EB; /* gray-200 */
        }
        .gantt-task-name {
            font-weight: 600;
            padding-right: 0.5rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }
        .gantt-bar-container {
            position: relative;
            height: 20px; /* Altura de la barra */
        }
        .gantt-bar {
            position: absolute;
            height: 100%;
            background-color: #06D6A0; /* Caribbean Green */
            border-radius: 0.25rem;
            opacity: 0.8;
        }
        .gantt-milestone {
            position: absolute;
            width: 20px; /* Ancho del hito */
            height: 20px; /* Altura del hito */
            background-color: #FF6B6B; /* Coral */
            border-radius: 50%; /* Círculo */
            transform: translateX(-50%); /* Centrar el hito */
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            color: white;
            font-size: 0.75rem;
        }
        .gantt-header {
            font-weight: bold;
            text-align: center;
            color: #073B4C;
            padding-bottom: 0.5rem;
        }

    </style>
</head>
<body class="text-gray-800">

    <nav id="sticky-nav" class="hidden md:block">
        <div class="container mx-auto px-4">
            <div class="flex justify-center items-center flex-wrap">
                <a href="#contexto">Contexto</a>
                <a href="#objetivos">Objetivos</a>
                <a href="#metodologia">Metodología</a>
                <a href="#hallazgos">Hallazgos</a>
                <a href="#estrategias">Estrategias</a>
                <a href="#plan_trabajo">Plan Trabajo</a>
                <a href="#gantt">Gantt</a>
                <a href="#kpis">KPIs</a>
                <a href="#impacto">Impacto</a>
            </div>
        </div>
    </nav>

    <header class="bg-gradient-to-r from-[#118AB2] to-[#06D6A0] py-12 text-white text-center">
        <div class="container mx-auto px-4">
            <h1 class="text-4xl md:text-5xl font-bold mb-4">Análisis Estratégico del Mercado y Foco en Cliente</h1>
            <p class="text-xl md:text-2xl font-light">Holding Estratégico S.A. - Visión 2025 (v2)</p>
        </div>
    </header>

    <main class="container mx-auto px-4 py-8">

        <section id="contexto" class="mb-12">
            <h2 class="section-title text-center">Contexto y Desafíos del Mercado Interno</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                El Holding enfrenta un entorno desafiante que requiere una reestructuración estratégica. La rentabilidad actual, basada en datos de Ene-Abr 2025, y la presión sobre el flujo de caja son preocupaciones centrales, demandando un enfoque más inteligente y selectivo en nuestras operaciones y relaciones comerciales.
            </p>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="stat-card text-center">
                    <h3 class="stat-title">Resultado Operacional Estimado</h3>
                    <p class="stat-value text-[#FF6B6B]">- $7.6M</p>
                    <p class="text-sm text-gray-500">(Diagnóstico Ene-Abr 2025)</p>
                </div>
                <div class="stat-card text-center">
                    <h3 class="stat-title">Margen Bruto Promedio Holding</h3>
                    <p class="stat-value text-[#FF6B6B]">13.31%</p>
                    <p class="text-sm text-gray-500">Meta mínima: 18%</p>
                </div>
                <div class="stat-card text-center md:col-span-2 lg:col-span-1">
                    <h3 class="stat-title">Principales Desafíos Adicionales</h3>
                    <ul class="text-left text-content list-disc list-inside mt-2 space-y-1">
                        <li>Presión sobre Flujo de Caja (alta dependencia del factoring).</li>
                        <li>Ciclos de cobro extensos.</li>
                        <li>Gestión de Inventario ("embarrada en bodega").</li>
                        <li>Márgenes insuficientes en empresas clave (Cloudbook 13.02%, Mercado Público 10.29%). Grumpy destaca con 22.39%.</li>
                    </ul>
                </div>
            </div>
        </section>

        <section id="objetivos" class="mb-12 stat-card">
            <h2 class="section-title text-center">Objetivos Estratégicos (Próximos 6-12 Meses)</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                Para revertir la situación actual y construir un futuro sostenible, hemos definido objetivos claros y medibles. El foco en clientes rentables y buenos pagadores es esencial para alcanzar estas metas.
            </p>
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6 text-center">
                <div class="p-4 bg-[#E0F2FE] rounded-lg shadow">
                    <div class="text-4xl mb-2">🎯</div>
                    <h3 class="font-semibold text-lg text-[#073B4C]">Rentabilidad</h3>
                    <p class="text-[#118AB2]">Margen Bruto Consolidado: <strong>18% mínimo</strong></p>
                </div>
                <div class="p-4 bg-[#E0F2FE] rounded-lg shadow">
                    <div class="text-4xl mb-2">📈</div>
                    <h3 class="font-semibold text-lg text-[#073B4C]">Resultado Operacional</h3>
                    <p class="text-[#118AB2]">Punto de equilibrio en 6 meses, utilidad en 12 meses.</p>
                </div>
                <div class="p-4 bg-[#E0F2FE] rounded-lg shadow">
                    <div class="text-4xl mb-2">💰</div>
                    <h3 class="font-semibold text-lg text-[#073B4C]">Flujo de Caja</h3>
                    <p class="text-[#118AB2]">Reducir dependencia factoring: <strong>30-40%</strong></p>
                </div>
                <div class="p-4 bg-[#E0F2FE] rounded-lg shadow">
                     <div class="text-4xl mb-2">📦</div>
                    <h3 class="font-semibold text-lg text-[#073B4C]">Inventario</h3>
                    <p class="text-[#118AB2]">Control en nuevo ERP (6m), Reducir sobrante <strong>70%</strong> (9m).</p>
                </div>
                <div class="p-4 bg-[#E0F2FE] rounded-lg shadow sm:col-span-2 lg:col-span-1">
                    <div class="text-4xl mb-2">🤖</div>
                    <h3 class="font-semibold text-lg text-[#073B4C]">Robot Postulaciones</h3>
                    <p class="text-[#118AB2]">Rentabilidad neta positiva en 6-9 meses.</p>
                </div>
            </div>
        </section>

        <section id="metodologia" class="mb-12">
            <h2 class="section-title text-center">Entendiendo Nuestro "Mercado" de Clientes</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                Para dirigir nuestros esfuerzos eficazmente, implementamos un proceso de análisis y segmentación que nos permite identificar y priorizar a nuestros clientes estratégicos.
            </p>
            <div class="bg-white p-6 rounded-lg shadow-md">
                <h3 class="card-title text-center">Proceso de Análisis y Segmentación de Clientes</h3>
                <div class="grid grid-cols-1 md:grid-cols-7 items-center gap-4 text-sm md:text-base">
                    <div class="flowchart-step md:col-span-2">1. Análisis de Margen Bruto por Cliente y Categoría</div>
                    <div class="flowchart-arrow hidden md:block">➡️</div>
                    <div class="flowchart-step md:col-span-2">2. Análisis de Comportamiento de Pago (Info. Juanita)</div>
                     <div class="flowchart-arrow md:hidden text-center text-3xl transform rotate-90">⬇️</div>
                    <div class="flowchart-arrow hidden md:block">➡️</div>
                     <div class="flowchart-step md:col-span-2 md:mt-0 mt-4">3. Cruce de Datos: Matriz Margen vs. Condición de Pago</div>
                     <div class="flowchart-arrow md:hidden text-center text-3xl transform rotate-90">⬇️</div>
                </div>
                 <div class="grid grid-cols-1 md:grid-cols-7 items-center gap-4 text-sm md:text-base mt-4 md:mt-0">
                    <div class="md:col-start-4 flowchart-arrow hidden md:block transform rotate-90">⬇️</div>
                 </div>
                <div class="grid grid-cols-1 md:grid-cols-7 items-center gap-4 text-sm md:text-base mt-0 md:mt-4">
                     <div class="md:col-start-3 md:col-span-3 flowchart-step">4. Definición de Segmentos Estratégicos y Planes de Acción</div>
                </div>
            </div>
        </section>

        <section id="hallazgos" class="mb-12">
            <h2 class="section-title text-center">Hallazgos Clave: Radiografía de Nuestro Portafolio</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                El análisis revela patrones importantes en nuestro portafolio de clientes. Los márgenes de las empresas del holding son datos concretos, mientras que la distribución de clientes y su impacto en ventas/margen se presentan como un modelo ilustrativo del análisis a profundizar.
            </p>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                 <div class="stat-card md:col-span-2">
                    <h3 class="card-title text-center">Márgenes Brutos (%) Reales por Empresas del Holding y Metas</h3>
                    <p class="text-content mb-4 text-sm text-center">Comparativa de márgenes observados en las empresas del holding y la meta estratégica.</p>
                    <div class="chart-container h-[350px] md:h-[400px] max-w-3xl">
                        <canvas id="margenesEmpresasChart"></canvas>
                    </div>
                     <p class="text-xs text-gray-500 mt-2 text-center">Nota: Se requiere análisis detallado para obtener márgenes consolidados por categoría de producto (Art. Oficina, Mobiliario, Desechables). Papelería Prisa (Cloudbook) presenta desafíos con márgenes del 4-9%. Mobiliario Humano tiene una meta >25%.</p>
                </div>
                <div class="stat-card">
                    <h3 class="card-title text-center">Distribución de Clientes por Segmento Estratégico (Modelo Ilustrativo)</h3>
                    <p class="text-content mb-4 text-sm text-center">Este gráfico ilustra cómo se podrían distribuir los clientes una vez completado el análisis detallado según la matriz de priorización. Los porcentajes son ejemplificativos.</p>
                    <div class="chart-container h-[350px] md:h-[400px]">
                        <canvas id="distribucionClientesChart"></canvas>
                    </div>
                </div>
                <div class="stat-card">
                    <h3 class="card-title text-center">Impacto Venta vs. Margen por Segmento (Modelo Ilustrativo)</h3>
                     <p class="text-content mb-4 text-sm text-center">Comparativa ilustrativa del posible aporte a ventas y margen de diferentes grupos de clientes. Cifras ejemplificativas pendientes de análisis detallado.</p>
                    <div class="chart-container h-[350px] md:h-[400px]">
                        <canvas id="ventaMargenChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <section id="estrategias" class="mb-12 stat-card">
            <h2 class="section-title text-center">Estrategias Clave por Segmento de Clientes</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                Basados en la matriz de Margen Bruto vs. Condición de Pago, definimos estrategias específicas para optimizar la rentabilidad y el flujo de caja.
            </p>
            <div class="overflow-x-auto">
                <table class="min-w-full bg-white border border-[#118AB2]">
                    <thead class="bg-[#073B4C] text-white">
                        <tr>
                            <th class="py-3 px-4 border-b border-r border-gray-600">Margen Bruto / Condición de Pago</th>
                            <th class="py-3 px-4 border-b border-r border-gray-600 text-[#06D6A0]">Buen Pagador</th>
                            <th class="py-3 px-4 border-b border-r border-gray-600 text-[#FFD166]">Pagador Promedio</th>
                            <th class="py-3 px-4 border-b border-gray-600 text-[#FF6B6B]">Mal Pagador</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr class="text-center">
                            <td class="py-3 px-4 border-b border-r font-semibold bg-[#E0F2FE]">Alto Margen</td>
                            <td class="py-3 px-4 border-b border-r bg-green-100 text-green-800">⭐ **FOCO PRIORITARIO 1:** Maximizar y Fidelizar. Cross/Up-selling, contratos.</td>
                            <td class="py-3 px-4 border-b border-r bg-yellow-100 text-yellow-800">**FOCO PRIORITARIO 2:** Mejorar Pago. Incentivos pronto pago.</td>
                            <td class="py-3 px-4 border-b bg-red-100 text-red-800">**EVALUAR RIESGO/BENEFICIO:** Negociar pago anticipado. ¿Compensa?</td>
                        </tr>
                        <tr class="text-center">
                            <td class="py-3 px-4 border-b border-r font-semibold bg-[#E0F2FE]">Margen Medio</td>
                            <td class="py-3 px-4 border-b border-r bg-green-50 text-green-700">**FOCO SECUNDARIO:** Incrementar Margen. Optimizar mix, costos.</td>
                            <td class="py-3 px-4 border-b border-r bg-yellow-50 text-yellow-700">**MANTENER Y OPTIMIZAR:** Mejorar ambos gradualmente.</td>
                            <td class="py-3 px-4 border-b bg-red-50 text-red-700">**ALERTA MÁXIMA:** Mejorar pago URGENTE, luego margen. Alto riesgo.</td>
                        </tr>
                        <tr class="text-center">
                            <td class="py-3 px-4 border-r font-semibold bg-[#E0F2FE]">Bajo Margen</td>
                            <td class="py-3 px-4 border-r bg-orange-100 text-orange-800">**OPTIMIZAR MARGEN URGENTE:** Renegociar. Si no, reevaluar.</td>
                            <td class="py-3 px-4 border-r bg-gray-100 text-gray-700">**BAJA PRIORIDAD / DESCONTINUAR GRADUAL**</td>
                            <td class="py-3 px-4 bg-red-200 text-red-900">🚫 **NO TRABAJAR / PLAN DE SALIDA:** Drenaje de recursos.</td>
                        </tr>
                    </tbody>
                </table>
            </div>
             <p class="text-content mt-6">
                <strong>Acciones Transversales Clave:</strong>
                <ul class="list-disc pl-5 mt-2 text-sm space-y-1">
                    <li><strong>Equipo Comercial (Mary, Paz, Erick, Tomás):</strong> Aplicar estrategias segmentadas, identificar oportunidades de cross/up-selling en clientes foco, mejorar condiciones de pago negociadas, y retroalimentar sobre la efectividad de las estrategias.</li>
                    <li><strong>Operaciones (Jorge L.):</strong> Optimizar costos de entrega y logística, asegurar gestión de inventario eficiente para soportar y priorizar las necesidades de los clientes estratégicos.</li>
                    <li><strong>Finanzas (Mauricio R., Juanita):</strong> Seguimiento proactivo de pagos, gestión de riesgo crediticio por segmento, análisis continuo del costo de factoring y su impacto en la rentabilidad neta por cliente.</li>
                    <li><strong>Liderazgo (Enrique V.):</strong> Impulsar el cambio cultural hacia la rentabilidad, supervisar la implementación del plan, y tomar decisiones estratégicas en casos complejos de clientes.</li>
                </ul>
            </p>
        </section>

        <section id="plan_trabajo" class="mb-12 stat-card">
            <h2 class="section-title text-center">Plan de Trabajo Detallado</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                La implementación de esta estrategia requiere un plan de acción coordinado con actividades, responsables y plazos definidos.
            </p>
            <div class="overflow-x-auto">
                <table class="min-w-full bg-white border border-[#118AB2] text-sm">
                    <thead class="bg-[#073B4C] text-white">
                        <tr>
                            <th class="py-2 px-3 border-b border-r border-gray-600 text-left">Actividad</th>
                            <th class="py-2 px-3 border-b border-r border-gray-600 text-left">Responsable(s)</th>
                            <th class="py-2 px-3 border-b border-gray-600 text-left">Plazo Límite</th>
                        </tr>
                    </thead>
                    <tbody class="text-[#374151]">
                        <tr>
                            <td class="py-2 px-3 border-b border-r">1. Finalización Análisis Detallado de Rentabilidad por Cliente y Categoría</td>
                            <td class="py-2 px-3 border-b border-r">Enrique V., Mauricio R., Apoyo Equipo Comercial</td>
                            <td class="py-2 px-3 border-b">Próximas 2 semanas (hasta ~14 Junio)</td>
                        </tr>
                        <tr>
                            <td class="py-2 px-3 border-b border-r">2. Integración Datos de Condiciones de Pago por Cliente</td>
                            <td class="py-2 px-3 border-b border-r">Juanita, Mauricio R.</td>
                            <td class="py-2 px-3 border-b">Próximas 2 semanas (hasta ~14 Junio)</td>
                        </tr>
                        <tr>
                            <td class="py-2 px-3 border-b border-r">3. Definición Final de Segmentos de Clientes y Listados</td>
                            <td class="py-2 px-3 border-b border-r">Enrique V., Mauricio R.</td>
                            <td class="py-2 px-3 border-b">Hasta 21 Junio</td>
                        </tr>
                        <tr>
                            <td class="py-2 px-3 border-b border-r">4. Capacitación Detallada al Equipo Comercial sobre Segmentos y Estrategias</td>
                            <td class="py-2 px-3 border-b border-r">Enrique V.</td>
                            <td class="py-2 px-3 border-b">Semana del 24 Junio</td>
                        </tr>
                        <tr>
                            <td class="py-2 px-3 border-b border-r">5. Revisión Individual de Carteras por Ejecutivo y Ajuste de Foco</td>
                            <td class="py-2 px-3 border-b border-r">Mary, Paz, Erick, Tomás con Enrique V.</td>
                            <td class="py-2 px-3 border-b">Hasta 5 Julio</td>
                        </tr>
                        <tr>
                            <td class="py-2 px-3 border-b border-r">6. Implementación Continua de Estrategias por Segmento</td>
                            <td class="py-2 px-3 border-b border-r">Equipo Comercial</td>
                            <td class="py-2 px-3 border-b">Continuo desde Julio</td>
                        </tr>
                        <tr>
                            <td class="py-2 px-3 border-b border-r">7. Seguimiento Mensual de KPIs y Ajustes Estratégicos</td>
                            <td class="py-2 px-3 border-b border-r">Enrique V., Mauricio R., Jorge L., Líderes Comerciales</td>
                            <td class="py-2 px-3 border-b">Mensual (1ª revisión fines de Julio)</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <section id="gantt" class="mb-12 stat-card">
            <h2 class="section-title text-center">Carta Gantt Visual del Plan de Trabajo</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                Cronograma visual simplificado de las principales actividades y sus duraciones estimadas para los próximos meses.
            </p>
            <div class="gantt-chart overflow-x-auto p-2 bg-gray-50 rounded">
                <div class="gantt-row gantt-header">
                    <div class="gantt-task-name">Actividad / Mes</div>
                    <div>Junio Sem 1-2</div>
                    <div>Junio Sem 3</div>
                    <div>Junio Sem 4</div>
                    <div>Julio Sem 1-2</div>
                    <div>Julio Sem 3-4</div>
                    <div>Agosto+</div>
                </div>
                
                <div class="gantt-row">
                    <div class="gantt-task-name">1-2. Análisis Rentab. y Pagos</div>
                    <div class="gantt-bar-container" style="grid-column: 2 / span 1;"> <div class="gantt-bar" style="width: 100%;"></div> </div>
                </div>
                <div class="gantt-row">
                    <div class="gantt-task-name">3. Definición Segmentos</div>
                    <div class="gantt-bar-container" style="grid-column: 3 / span 1;"> <div class="gantt-bar" style="width: 100%;"></div> </div>
                     <div class="gantt-bar-container" style="grid-column: 3 / span 1;"> <div class="gantt-milestone" style="left: 95%;" title="Hito: Fin Análisis">FA</div> </div>
                </div>
                <div class="gantt-row">
                    <div class="gantt-task-name">4. Capacitación Equipo</div>
                    <div class="gantt-bar-container" style="grid-column: 4 / span 1;"> <div class="gantt-bar" style="width: 100%;"></div> </div>
                    <div class="gantt-bar-container" style="grid-column: 4 / span 1;"> <div class="gantt-milestone" style="left: 95%;" title="Hito: Capacitación">C</div> </div>
                </div>
                <div class="gantt-row">
                    <div class="gantt-task-name">5. Revisión Carteras Indiv.</div>
                    <div class="gantt-bar-container" style="grid-column: 5 / span 1;"> <div class="gantt-bar" style="width: 100%;"></div> </div>
                </div>
                <div class="gantt-row">
                    <div class="gantt-task-name">6. Implementación Estrategias</div>
                    <div class="gantt-bar-container" style="grid-column: 5 / span 3;"> <div class="gantt-bar" style="width: 100%; background-color: #118AB2;"></div> </div>
                </div>
                <div class="gantt-row">
                    <div class="gantt-task-name">7. Seguimiento KPIs</div>
                     <div class="gantt-bar-container" style="grid-column: 6 / span 1;"> <div class="gantt-milestone" style="left: 95%; background-color: #FFD166; color: #073B4C;" title="Hito: 1ª Revisión KPIs">R1</div> </div>
                    <div class="gantt-bar-container" style="grid-column: 6 / span 2;"> <div class="gantt-bar" style="width: 100%; background-color: #118AB2; opacity:0.5;"></div> </div>
                </div>
            </div>
            <p class="text-xs text-gray-500 mt-2 text-center">Nota: FA = Fin Análisis, C = Capacitación, R1 = 1ª Revisión KPIs. Las barras indican duración estimada.</p>
        </section>

        <section id="kpis" class="mb-12 stat-card">
            <h2 class="section-title text-center">Indicadores Clave de Desempeño (KPIs)</h2>
            <p class="text-content text-center mb-8 max-w-3xl mx-auto">
                El seguimiento riguroso de estos indicadores nos permitirá medir el progreso y realizar ajustes oportunos a nuestra estrategia.
            </p>
            <ul class="kpi-list grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-2">
                <li>Margen Bruto Promedio por Cliente (general y por segmento).</li>
                <li>% de Ventas y Margen provenientes de cada segmento de la matriz.</li>
                <li>Número de Clientes migrados entre segmentos.</li>
                <li>Días Promedio de Cobro (DSO), general y por segmento.</li>
                <li>% de Cartera Vencida, general y por segmento.</li>
                <li>Rentabilidad Neta del Robot de Postulaciones.</li>
                <li>"Margen Neto Real" por operación en Mobiliario.</li>
                <li>Reducción de costos de factoring asociados a clientes de alto riesgo.</li>
            </ul>
        </section>
        
        <section id="impacto" class="mb-12 text-center">
            <h2 class="section-title">Impacto Esperado y Próximos Pasos</h2>
            <p class="text-content mb-8 max-w-3xl mx-auto">
                Con la implementación de esta estrategia de foco en el cliente, anticipamos una mejora significativa en la rentabilidad y solidez financiera del Holding.
            </p>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-6 mb-8">
                 <div class="stat-card">
                    <h3 class="stat-title">Mejora Margen Bruto</h3>
                    <p class="stat-value">🎯 18%+</p>
                </div>
                <div class="stat-card">
                    <h3 class="stat-title">Salud Financiera</h3>
                    <p class="stat-value">💪 Estable</p>
                </div>
                <div class="stat-card">
                    <h3 class="stat-title">Eficiencia Operativa</h3>
                    <p class="stat-value">⚙️ Optimizada</p>
                </div>
            </div>
            <div class="bg-white p-6 rounded-lg shadow-md">
                <h3 class="card-title">Próximos Pasos Clave (Post-Implementación Inicial):</h3>
                <ul class="text-left text-content list-decimal list-inside space-y-2 max-w-xl mx-auto">
                    <li>Establecimiento de metas individuales para el Equipo Comercial alineadas a estos objetivos.</li>
                    <li>Sesiones de feedback continuo con el Equipo Comercial sobre la aplicación de estrategias.</li>
                    <li>Revisión trimestral de la segmentación de clientes y efectividad de las estrategias.</li>
                    <li>Ajustes al plan de incentivos del Equipo Comercial para reforzar el foco en rentabilidad y buenos pagadores.</li>
                </ul>
                <p class="mt-6 font-semibold text-[#073B4C]">¡Juntos construiremos un holding más fuerte y rentable!</p>
            </div>
        </section>

    </main>

    <footer class="bg-[#073B4C] text-center py-6 text-[#FFD166]">
        <p>&copy; <span id="currentYear"></span> Holding Estratégico S.A. Todos los derechos reservados.</p>
        <p class="text-xs mt-1">Infografía generada como herramienta de análisis estratégico (v2).</p>
    </footer>

    <script>
        document.getElementById('currentYear').textContent = new Date().getFullYear();

        function wrapLabels(labels, maxWidth) {
            return labels.map(label => {
                if (typeof label === 'string' && label.length > maxWidth) {
                    const words = label.split(' ');
                    const lines = [];
                    let currentLine = '';
                    words.forEach(word => {
                        if ((currentLine + word).length > maxWidth && currentLine.length > 0) {
                            lines.push(currentLine.trim());
                            currentLine = word + ' ';
                        } else {
                            currentLine += word + ' ';
                        }
                    });
                    lines.push(currentLine.trim());
                    return lines;
                }
                return label;
            });
        }
        
        const tooltipTitleCallback = (tooltipItems) => {
            const item = tooltipItems[0];
            let label = item.chart.data.labels[item.dataIndex];
            if (Array.isArray(label)) {
                return label.join(' ');
            }
            return label;
        };

        const commonChartOptions = {
            responsive: true,
            maintainAspectRatio: false,
            plugins: {
                tooltip: {
                    callbacks: {
                        title: tooltipTitleCallback
                    }
                },
                legend: {
                    labels: {
                        color: '#073B4C', 
                         font: {
                            size: 12
                        }
                    }
                }
            },
            scales: {
                y: {
                    beginAtZero: true,
                    ticks: { color: '#073B4C', font: { size: 10 } },
                    grid: { color: '#D1D5DB' }
                },
                x: {
                    ticks: { color: '#073B4C', font: { size: 10 } },
                    grid: { display: false }
                }
            }
        };
        
        // Datos Reales y Simulados para Gráficos
        // 1. Márgenes por Empresa Chart (Bar) - DATOS REALES
        const margenesEmpresasCtx = document.getElementById('margenesEmpresasChart').getContext('2d');
        new Chart(margenesEmpresasCtx, {
            type: 'bar',
            data: {
                labels: wrapLabels([
                    'Cloudbook', 
                    'Grumpy', 
                    'Mercado Público SPA', 
                    'Promedio Holding (Actual)',
                    'Meta Margen Holding'
                ], 16),
                datasets: [{
                    label: 'Margen Bruto (%)',
                    data: [13.02, 22.39, 10.29, 13.31, 18.00],
                     backgroundColor: [
                        '#FFD166', '#06D6A0', '#FF6B6B', '#118AB2', '#32CD32'
                    ],
                    borderColor: '#073B4C',
                    borderWidth: 1
                }]
            },
            options: {
                ...commonChartOptions,
                scales: {
                    ...commonChartOptions.scales,
                    y: {
                        ...commonChartOptions.scales.y,
                        ticks: {
                            ...commonChartOptions.scales.y.ticks,
                            callback: function(value) { return value.toFixed(2) + '%' }
                        }
                    }
                },
                plugins: {
                     ...commonChartOptions.plugins,
                    legend: { display: false } 
                }
            }
        });

        // 2. Distribución de Clientes Chart (Donut) - MODELO ILUSTRATIVO
        const distribucionClientesCtx = document.getElementById('distribucionClientesChart').getContext('2d');
        new Chart(distribucionClientesCtx, {
            type: 'doughnut',
            data: {
                labels: wrapLabels([
                    'Foco Prioritario 1 (Alto Margen, Buen Pagador)', 
                    'Foco Prioritario 2 (Alto Margen, Pagador Promedio)', 
                    'Evaluar Riesgo (Alto Margen, Mal Pagador)',
                    'Foco Secundario (Margen Medio, Buen Pagador)',
                    'Mantener/Optimizar (Margen Medio, Pagador Promedio)',
                    'Alerta Máxima (Margen Medio, Mal Pagador)',
                    'Optimizar Urgente (Bajo Margen, Buen Pagador)',
                    'Baja Prioridad (Bajo Margen, Pagador Promedio)',
                    'No Trabajar (Bajo Margen, Mal Pagador)'
                ], 20), 
                datasets: [{
                    label: '% de Clientes (Ilustrativo)',
                    data: [15, 10, 5, 30, 15, 10, 5, 5, 5], // Suma 100 - Ajustado para ilustración
                    backgroundColor: ['#06D6A0', '#3CB371', '#2E8B57', '#FFD166', '#F0E68C', '#FFA07A', '#FF6B6B', '#CD5C5C', '#A52A2A'],
                    borderColor: '#FFFFFF',
                    borderWidth: 2
                }]
            },
            options: {
                ...commonChartOptions,
                plugins: {
                    ...commonChartOptions.plugins,
                    legend: { 
                        position: 'bottom',
                        labels: { ...commonChartOptions.plugins.legend.labels, font: {size: 9} } 
                    },
                    title: {
                        display: true,
                        text: 'Modelo Ilustrativo - Porcentajes Ejemplificativos',
                        color: '#FF6B6B',
                        font: { size: 10 }
                    }
                },
                scales: { x: { display: false }, y: { display: false } } 
            }
        });

        // 3. Venta vs Margen Chart (Grouped Bar) - MODELO ILUSTRATIVO
        const ventaMargenCtx = document.getElementById('ventaMargenChart').getContext('2d');
        new Chart(ventaMargenCtx, {
            type: 'bar',
            data: {
                labels: wrapLabels(['Foco Prioritario 1', 'Margen Medio (Bueno/Promedio)', 'Bajo Margen / Mal Pagador'], 16),
                datasets: [
                    {
                        label: '% del Total de Ventas (Ilustrativo)',
                        data: [35, 40, 25], // Ajustado para ilustración
                        backgroundColor: '#118AB2', 
                        borderColor: '#073B4C',
                        borderWidth: 1
                    },
                    {
                        label: '% del Total de Margen Bruto (Ilustrativo)',
                        data: [55, 30, 15], // Ajustado para ilustración
                        backgroundColor: '#06D6A0', 
                        borderColor: '#049F80',
                        borderWidth: 1
                    }
                ]
            },
            options: {
                ...commonChartOptions,
                 plugins: {
                    ...commonChartOptions.plugins,
                    title: {
                        display: true,
                        text: 'Modelo Ilustrativo - Porcentajes Ejemplificativos',
                        color: '#FF6B6B',
                        font: { size: 10 }
                    }
                }
            }
        });


        // Sticky Nav Scroll Active State
        const navLinks = document.querySelectorAll('#sticky-nav a');
        const sections = document.querySelectorAll('main section[id]');

        function changeNav() {
            let index = sections.length;
            while(--index && window.scrollY + 100 < sections[index].offsetTop) {} 
            
            navLinks.forEach((link) => link.classList.remove('active'));
            if (index >= 0 && navLinks[index]) { 
               navLinks[index].classList.add('active');
            }
        }

        if (document.getElementById('sticky-nav')) { 
            changeNav(); 
            window.addEventListener('scroll', changeNav);
        }

    </script>
</body>
</html>
