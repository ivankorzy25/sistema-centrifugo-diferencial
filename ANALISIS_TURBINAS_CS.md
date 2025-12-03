# Análisis de Turbinas Individuales por CS
## Sistema Centrífugo de Diferencial de Velocidad Angular

**Fecha:** Diciembre 2024
**Objetivo:** Determinar la turbina óptima para cada CS

---

## Contexto: Independencia de Cada CS

Cada una de las 4 cámaras superiores (CS1, CS2, CS3, CS4) funciona como una **unidad de generación independiente**.

```
                    Vista superior del sistema

                         CS₁
                    ┌────⚡────┐
                    │ Turbina │
                    │  Eje ↑  │
                    └────┬────┘
                         │
         CS₄ ────────────┼──────────── CS₂
    ┌────⚡────┐          │         ┌────⚡────┐
    │ Turbina │    ══════╪══════   │ Turbina │
    │  Eje ↑  │      CI (ω≈0)      │  Eje ↑  │
    └────┬────┘    ══════╪══════   └────┬────┘
         │               │              │
                         │
                    ┌────┴────┐
                    │ Turbina │
                    │  Eje ↑  │
                    └────⚡────┘
                         CS₃

    ⚡ = Turbina con eje vertical independiente
```

---

## Parámetros de Flujo por CS

### A 100 RPM (Caso de referencia)

| Parámetro | Valor por CS |
|-----------|--------------|
| Caudal Q | 0.24 m³/s (240 L/s) |
| Flujo másico ṁ | 209 kg/s |
| ΔP disponible | 128,000 Pa (1.28 bar) |
| Cabeza equivalente H | 13.1 m (de aceite) |
| Velocidad tangencial entrada | 20.9 m/s (en r=2m) |
| Velocidad tangencial salida | ~0 m/s (hacia CI) |

### Velocidad específica (Ns)

La velocidad específica determina el tipo de turbina óptimo:

$$N_s = \frac{n \sqrt{Q}}{H^{3/4}}$$

Donde:
- n = velocidad de rotación de la turbina (a determinar)
- Q = caudal (0.24 m³/s)
- H = cabeza (13.1 m)

Si la turbina gira a 1000 RPM:
$$N_s = \frac{1000 \times \sqrt{0.24}}{13.1^{3/4}} = \frac{1000 \times 0.49}{7.0} \approx 70$$

**Ns ≈ 70 → Zona de turbinas Francis o de flujo mixto**

---

## Análisis del Flujo en CS

### Geometría del flujo

```
    Vista en corte de una CS (radial desde eje hacia PA)

    Eje                                                    PA (r=2m)
     │                                                        │
     │◄─────────────────── 1 metro ──────────────────────────►│
     │                                                        │
     ├────────────────────────────────────────────────────────┤ TS
     │                                                        │
     │     Fluido en CS rotando a ω                          │
     │     ───────────────────────────►                      │
     │     v_tangencial = ω × r                              │  25cm
     │                                                        │
     │                              ┌──────────┐              │
     │                              │ TURBINA  │◄── Aquí      │
     │                              │    ⚡    │              │
     ├──────────────────────────────┴────┬─────┴──────────────┤ TI
     │            CI (ω ≈ 0)             │ apertura           │
     └───────────────────────────────────┴────────────────────┘ S

    El fluido entra a la turbina con alta velocidad tangencial
    y sale hacia CI con velocidad casi cero
```

### Energía disponible por unidad de masa

La energía que la turbina puede extraer es la **diferencia de energía cinética rotacional**:

$$E_{disponible} = \frac{1}{2}v_{in}^2 - \frac{1}{2}v_{out}^2$$

Con v_in = 20.9 m/s y v_out ≈ 0:
$$E_{disponible} = \frac{1}{2}(20.9)^2 = 218 \text{ J/kg}$$

**Potencia por CS:**
$$P = \dot{m} \times E = 209 \text{ kg/s} \times 218 \text{ J/kg} = 45.6 \text{ kW}$$

Con eficiencia de turbina 85%:
$$P_{eje} = 45.6 \times 0.85 = \textbf{38.7 kW por CS}$$

---

## Tipos de Turbina Candidatos

### 1. Turbina de Flujo Cruzado (Banki-Mitchell)

```
    Vista frontal              Vista lateral

       ┌─────────┐            Entrada tangencial
       │ ░░░░░░░ │                  ↓
       │ ░     ░ │            ┌─────────────┐
       │ ░     ░ │            │ ╲   ╱ ╲   ╱ │
    ───┼─░─────░─┼───         │  ╲ ╱   ╲ ╱  │
       │ ░     ░ │            │   ╳     ╳   │ → Eje
       │ ░     ░ │            │  ╱ ╲   ╱ ╲  │
       │ ░░░░░░░ │            │ ╱   ╲ ╱   ╲ │
       └─────────┘            └─────────────┘
           ↓                        ↓
        Salida                   Salida
```

| Aspecto | Evaluación |
|---------|------------|
| Rango Ns | 20-200 ✓ |
| Eficiencia | 75-85% |
| Simplicidad | Alta ✓ |
| Mantenimiento | Bajo ✓ |
| Adaptación al flujo tangencial | Excelente ✓ |
| Tamaño | Compacto ✓ |

**Ventajas para este sistema:**
- Acepta entrada tangencial directamente
- Funciona bien con variaciones de caudal
- Diseño simple y robusto
- El flujo cruza el rotor dos veces (doble extracción)

**Dimensiones estimadas:**
- Diámetro: 25-30 cm
- Ancho: 20-25 cm
- Peso: 15-25 kg

---

### 2. Turbina Francis (Flujo Mixto)

```
    Vista en corte

         Entrada espiral
              ↓
        ╔═══════════╗
       ╔╝           ╚╗
      ╔╝   ┌─────┐   ╚╗
      ║    │     │    ║
      ║    │  ●──┼────║──→ Eje
      ║    │     │    ║
      ╚╗   └─────┘   ╔╝
       ╚╗           ╔╝
        ╚═══════════╝
              ↓
           Salida axial
```

| Aspecto | Evaluación |
|---------|------------|
| Rango Ns | 60-400 ✓ |
| Eficiencia | 90-95% ✓✓ |
| Simplicidad | Media |
| Mantenimiento | Medio |
| Adaptación al flujo tangencial | Buena |
| Tamaño | Medio |

**Ventajas:**
- Máxima eficiencia
- Diseño probado en hidroeléctricas
- Buen rango de operación

**Desventajas:**
- Más compleja de fabricar
- Requiere carcasa espiral
- Mayor costo

**Dimensiones estimadas:**
- Diámetro runner: 20-25 cm
- Con carcasa: 40-50 cm
- Peso: 30-50 kg

---

### 3. Turbina de Reacción Radial (Diseño Personalizado)

```
    Vista superior (dentro de CS)

                PA (r=2m)
                   │
    ───────────────┼───────────────
                   │
         ╔═════════╧═════════╗
         ║  ↙ ↙ ↙ ↙ ↙ ↙ ↙   ║ ← Álabes curvos
         ║ ╱───────────────╲ ║   capturan momento
         ║│                 │║   angular
         ║│       ●         │║ ← Eje vertical
         ║│                 │║
         ║ ╲───────────────╱ ║
         ║   ↘ ↘ ↘ ↘ ↘ ↘   ║
         ╚═══════════════════╝
                   │
                   ↓
              Hacia CI
```

| Aspecto | Evaluación |
|---------|------------|
| Eficiencia | 80-88% |
| Simplicidad | Alta ✓ |
| Adaptación | Óptima ✓✓ |
| Fabricación | Media |
| Integración | Perfecta ✓✓ |

**Concepto:**
- Diseñada específicamente para este sistema
- Los álabes capturan el momento angular del fluido
- Salida hacia abajo (a CI)
- Eje vertical hacia arriba

**Ventajas:**
- Integración perfecta con la geometría
- Sin necesidad de carcasa espiral externa
- Aprovecha directamente el flujo tangencial de CS

---

## Recomendación: Turbina de Reacción Radial Personalizada

### Justificación

Para este sistema específico, una **turbina de reacción radial con salida axial** es la opción óptima porque:

1. **Geometría natural:** El fluido ya viene con velocidad tangencial (ω × r)
2. **Integración:** Se instala directamente en la apertura CS→CI
3. **Eje vertical:** Simplifica la transmisión de potencia
4. **Compacta:** Cabe en el espacio disponible (25 cm de altura)

### Diseño Propuesto

```
    Corte vertical de la turbina

              Eje de salida
                  ↑
                  │
            ┌─────┴─────┐ ← Sello/rodamiento
            │           │
    ════════╪═══════════╪════════ TS
            │  ┌─────┐  │
     Fluido │  │ ╲ ╱ │  │ Fluido
     CS →→→ │  │  ●  │  │ →→→ CS
     (ω)    │  │ ╱ ╲ │  │ (ω)
            │  └──┬──┘  │
    ════════╪═════╧═════╪════════ TI
            │     ↓     │
            │   A CI    │
            │  (ω ≈ 0)  │
            └───────────┘

    El rotor tiene álabes que:
    - Capturan la velocidad tangencial
    - Redirigen el flujo hacia abajo
    - Transfieren torque al eje
```

### Especificaciones por CS

| Parámetro | Valor |
|-----------|-------|
| Diámetro del rotor | 25-30 cm |
| Número de álabes | 8-12 |
| Ángulo de entrada | 15-25° |
| Ángulo de salida | 80-90° (casi axial) |
| Velocidad de giro | 1000-1500 RPM |
| Potencia nominal | 38 kW |
| Torque en eje | 240-360 N·m |
| Eficiencia esperada | 82-88% |

### Perfil de Álabe

```
    Vista del álabe (desplegado)

    Entrada (borde externo)     Salida (centro)
              │                       │
              ▼                       ▼
         ┌────────────────────────────┐
         │    ╲                       │
         │      ╲                     │
         │        ╲                   │ ← Curvatura
         │          ╲                 │   progresiva
         │            ╲               │
         │              ──────────────│
         └────────────────────────────┘

    El fluido entra tangencialmente y sale casi axial
```

---

## Transmisión de Potencia

### Configuración del Eje

```
    Vista del conjunto turbina-eje

                    Acople/Generador
                         ↑
                    ┌────┴────┐
                    │ ═══════ │ ← Rodamiento superior
                    │    ║    │
                    │    ║    │ ← Eje (acero inox)
                    │    ║    │    Ø 40-50 mm
    ════════════════╪════╬════╪════════════════ TS
                    │    ║    │
                    │ ┌──╨──┐ │
                    │ │ROTOR│ │ ← Turbina
                    │ └──┬──┘ │
    ════════════════╪════╧════╪════════════════ TI
                    │ ═══════ │ ← Rodamiento inferior
                    │         │    (sellado)
                    └─────────┘
                         │
                         ↓
                    Flujo a CI
```

### Opciones de Aprovechamiento

#### Opción A: Generador Eléctrico Directo

```
    ┌───────────────┐
    │   Generador   │ ← Montado sobre estructura giratoria
    │   38 kW       │
    └───────┬───────┘
            │ Cables por slip ring
            ↓
    ════════════════════
       Estructura fija
```

| Aspecto | Especificación |
|---------|----------------|
| Tipo | Generador síncrono o PMG |
| Potencia | 40 kW nominal |
| Voltaje | 400V trifásico |
| RPM | 1000-1500 |
| Peso | 80-120 kg |
| Transmisión | Slip ring de potencia |

#### Opción B: Eje Mecánico Directo

```
                    Carga mecánica externa
                           ↑
    ┌──────────────────────┼──────────────────────┐
    │                      │                      │ Estructura
    │                 ┌────┴────┐                 │ fija
    │                 │ Junta   │                 │
    │                 │ rotativa│                 │
    │                 └────┬────┘                 │
    └──────────────────────┼──────────────────────┘
                           │
    ═══════════════════════╪═══════════════════════
                           │
                      ┌────┴────┐
                      │   Eje   │ Estructura
                      │ turbina │ giratoria
                      └─────────┘
```

**Problema:** Requiere junta rotativa compleja (el eje gira a ω_turbina mientras todo el sistema gira a ω_sistema).

**Velocidad relativa del eje respecto a estructura fija:**
- ω_eje_absoluto = ω_sistema + ω_turbina
- A 100 RPM sistema + 1200 RPM turbina = 1300 RPM absolutos

#### Opción C: Bomba Hidráulica (Recomendada)

```
    ┌─────────────────────┐
    │   Bomba hidráulica  │ ← Montada sobre estructura giratoria
    │   pequeña (40 kW)   │
    └──────────┬──────────┘
               │
         ┌─────┴─────┐
         │ Aceite HP │ ← Líneas hidráulicas
         │ ═══════►  │   por junta rotativa
         │ ◄═══════  │   (menor complejidad que
         │ Retorno   │    slip ring de potencia)
         └─────┬─────┘
               │
    ═══════════╪═══════════
               │
         Motor hidráulico
         fijo al suelo
```

| Aspecto | Especificación |
|---------|----------------|
| Bomba | Pistones axiales, 40 kW |
| Presión | 200-250 bar |
| Caudal | 100-120 L/min |
| Motor externo | Hidráulico de igual capacidad |
| Junta rotativa | Hidráulica (2 puertos) |
| Eficiencia total | 85-90% |

**Ventajas:**
- Junta rotativa hidráulica más simple que slip ring de potencia
- Flexibilidad de ubicación del motor receptor
- Puede acumularse energía (acumulador hidráulico)
- Tecnología probada

---

## Potencia Total del Sistema

### 4 Turbinas Independientes

| RPM Sistema | P/turbina | P total (4×) |
|-------------|-----------|--------------|
| 50 | 4.8 kW | 19.2 kW |
| 100 | 38 kW | **152 kW** |
| 150 | 129 kW | 516 kW |
| 200 | 306 kW | 1,224 kW |

### Comparación con Análisis Anterior

El análisis anterior estimaba ~12 kW neto por CS a 100 RPM, pero usaba una extracción del 45% de la energía del flujo.

El nuevo cálculo considera:
- Extracción del 100% de la energía cinética diferencial
- Eficiencia de turbina 85%
- **Resultado: 38 kW por CS** (vs 12 kW anterior)

La diferencia está en que antes se asumía dejar 55% de energía en el flujo para mantener circulación. Con el diseño correcto de turbina (reacción, no impulso), se puede extraer casi toda la energía cinética diferencial y el flujo continúa por presión.

---

## Diagrama de Integración Final

```
                            Generador/Bomba CS₁
                                   ↑
                              ┌────┴────┐
                              │  Eje ↑  │
    ┌─────────────────────────┴─────────┴─────────────────────────┐
    │                         │ TURBINA │                         │
    │      CS₁                └────┬────┘                         │
    │      (ω)                     │                              │
    ├─────────────────────────TI───┴───TI─────────────────────────┤
    │                              ↓                              │
    │                         ┌─────────┐                         │
    │                         │   CI    │                         │
    │      ┌──────────────────┤ (ω≈0)   ├──────────────────┐      │
    │      │                  │ Bandeja │                  │      │
    │      │                  │ flotante│                  │      │
    │      ↓                  └────┬────┘                  ↓      │
    │ ┌─────────┐                  │                  ┌─────────┐ │
    │ │TURBINA  │                  │                  │ TURBINA │ │
    │ │  CS₄    │                  │                  │  CS₂    │ │
    │ └────┬────┘                  │                  └────┬────┘ │
    │      │                       │                       │      │
    │      ↓                       ↓                       ↓      │
    └──────┴───────────────────────┴───────────────────────┴──────┘
           │                       │                       │
        Eje CS₄               Succión              Eje CS₂
                            (a CS por eje)
```

---

## Resumen Ejecutivo

| Aspecto | Especificación |
|---------|----------------|
| Tipo de turbina | Reacción radial con salida axial |
| Cantidad | 4 unidades (una por CS) |
| Potencia por unidad | 38 kW @ 100 RPM |
| Potencia total | 152 kW @ 100 RPM |
| Diámetro rotor | 25-30 cm |
| RPM turbina | 1000-1500 |
| Transmisión | Bomba hidráulica (recomendada) |
| Eje | Vertical, Ø 40-50 mm, acero inox |

---

## Próximos Pasos

1. [ ] Diseño detallado de perfil de álabes
2. [ ] Simulación CFD del flujo en turbina
3. [ ] Selección de rodamientos y sellos
4. [ ] Diseño del sistema hidráulico de transmisión
5. [ ] Análisis de vibraciones y balanceo
6. [ ] Prototipo a escala reducida

---

*Análisis de turbinas v1.0 - Sistema independiente por CS*
