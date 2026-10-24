# Auditoría UX y propuesta de flujo/maqueta – Plan Público Lirmi (con constructor TDR en #bases)

Fecha: 2026-10-24
Alcance: solo contenido público accesible en https://plan-publico-lirmi.ailinvs.chatgpt.site (sin edición ni publicación del sitio). Basado en navegación observada el 24 oct 2026.

## 1. Inventario de secciones actuales (conservadas)

Menú lateral (grupos):

**1 · Dirección**
- Panel ejecutivo
- Alertas y renovaciones
- Sofía · consultas

**2 · Territorio**
- SLEP, comunas e instituciones
- Catastro y evidencias
- Directorio de contactos

**3 · Gestión comercial**
- Cartera comercial
- Agenda de gestión
- Actividad y seguimiento
- Licitaciones y compras públicas
- Análisis competitivo
- Competidores: análisis y compras

**4 · Propuestas**
- Cotizaciones y propuestas (#bases)
- Agente IA

**5 · Control del plan**
- Indicadores del plan
- Hitos del plan
- Objetivos del plan
- Material consolidado
- Documentación de la compañía
- Datos y actualización

Observaciones de navegabilidad (reproducibles):
- Menú lateral con 5 grupos y ~20 ítems: muchas opciones simultáneas, requiere scroll o colapsar.
- Panel ejecutivo concentra resúmenes nacionales, alertas de renovación, ranking SLEP y accesos rápidos.
- #bases (Cotizaciones y propuestas) permite buscar/seleccionar cliente por RBD/comuna y muestra catálogo de establecimientos.
- No se observó en superficie pública un constructor TDR explícito con pasos de secciones/exportación; el flujo visible es selección de cliente + preparación de propuesta.
- Acceso a datos privados (planillas Google) marcado como "Acceso privado / Solo propietario".

Bloqueo: no se pudo verificar interactividad completa del constructor TDR (si existe más allá del selector) sin autenticación o interacciones profundas no expuestas en la vista pública inicial.

## 2. Propuesta de reorganización más simple

Objetivo: menos opciones simultáneas, entradas claras, orientación y regreso sencillo. Conservar todo el contenido.

**Propuesta de menú simplificado (3 grupos principales + acceso rápido):**

1. **Hoy** (Panel ejecutivo + Alertas y renovaciones + Ranking prioritario)
2. **Territorio y cartera** (SLEP/instituciones + Catastro + Contactos + Cartera + Agenda + Seguimiento)
3. **Propuestas y control** (Cotizaciones/#bases con TDR + Licitaciones + Indicadores/Hitos/Objetivos + Material)

Accesos rápidos en Panel: Explorar territorio, Preparar propuesta (TDR), Monitorear licitaciones.

## 3. Constructor TDR dentro de #bases (flujo propuesto)

Organizar en **cuatro secciones** claras (selección → preparación → revisión → salida):

1. **Selector institucional**
   - Buscar por nombre, RBD, comuna o SLEP.
   - Mostrar datos básicos verificables (sin inventar).

2. **Preparación por secciones**
   - Secciones conservadas del contenido existente: alcance funcional, velocidad de implementación, seguridad, condiciones económicas, módulos, capacitación.
   - Selector de componentes proporcional a la selección (no mostrar todo de golpe).

3. **Vista previa antes de exportar**
   - Resumen del borrador generado.
   - Advertencia clara: "Borrador no constituye bases oficiales aprobadas".
   - Trazabilidad de fuentes usadas.

4. **Salida**
   - Exportar (PDF/Word) o copiar.
   - Proporcional a lo seleccionado.

Flujo: Selección → Preparación por secciones → Revisión previa → Salida.

## 4. Maqueta textual del flujo

```
[#bases / Cotizaciones y propuestas]
┌────────────────────────────────────────────────────────────┐
│ 1. Selector institucional                          │
│    [Buscar RBD/nombre/comuna] → Seleccionar         │
├────────────────────────────────────────────────────────────┤
│ 2. Preparación por secciones (colapsables)          │
│    □ Alcance  □ Implementación  □ Seguridad  □ Económico│
│    (mostrar solo las seleccionadas)                 │
├────────────────────────────────────────────────────────────┤
│ 3. Vista previa                                   │
│    Resumen borrador + aviso "no oficial"           │
│    [Editar] [Continuar]                             │
├────────────────────────────────────────────────────────────┤
│ 4. Salida                                         │
│    [Exportar PDF] [Copiar]                          │
└────────────────────────────────────────────────────────────┘
```

## 5. Secciones conservadas y límites

- Todo el contenido del menú actual se mantiene, reagrupado.
- Constructor TDR: propuesta de flujo sobre lo observable en #bases; no se inventan bases, requisitos ni compromisos no visibles.
- Vacío identificado: definición detallada de secciones TDR / exportación no expuesta en la superficie pública inicial.

## 6. Próximo paso

Revisión de Ailín/GPT. Si se autoriza profundizar en interacciones o se habilita más contexto público, se refina la maqueta. Sin edición del sitio ni publicación.

[Grok] 2026-10-24
