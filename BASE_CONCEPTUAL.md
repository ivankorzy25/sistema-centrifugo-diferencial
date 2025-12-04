# Sistema Centrífugo de Diferencial de Velocidad Angular
## Base Conceptual - Separación de Sistemas Independientes

**Versión:** 2.0
**Fecha:** Diciembre 2024
**Estado:** Base para continuación de análisis

---

## Principio Fundamental: Dos Sistemas Independientes

Este documento establece la separación conceptual entre dos sistemas que operan de manera **completamente independiente** entre sí.

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   SISTEMA A                         SISTEMA B                       │
│   Motor de Rotación                 Dinámica Interna                │
│                                                                     │
│   ┌─────────────┐                  ┌─────────────────────────┐      │
│   │             │                  │  CS (ω)    ══►  CI (≈0) │      │
│   │    MOTOR    │───mantiene ω───►│                         │      │
│   │             │                  │  CI (≈0)   ══►  CS (ω)  │      │
│   └─────────────┘                  └─────────────────────────┘      │
│         │                                    │                      │
│         ▼                                    ▼                      │
│   Solo compensa:                    Opera con su propia             │
│   - Fricción rodamientos            energía del diferencial         │
│   - Resistencia del aire            de velocidad angular            │
│                                                                     │
│   ════════════════════════════════════════════════════════════      │
│              NO HAY CONEXIÓN ENERGÉTICA ENTRE A Y B                 │
│   ════════════════════════════════════════════════════════════      │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## SISTEMA A: Mantenimiento de Giro (PMGI)

### Definición

**PMGI (Potencia de Mantenimiento de Giro Independiente):** Potencia que el motor externo debe suministrar para mantener la masa giratoria a velocidad angular constante ω.

### Características

| Aspecto | Descripción |
|---------|-------------|
| Función | Mantener ω constante |
| Compensa | Fricción + resistencia del aire |
| No compensa | Nada de lo que ocurre dentro |
| Analogía | Motor del tren |

### Ecuación

$$P_{PMGI} = \tau_{fricción} \cdot \omega + P_{aire}$$

Donde:
- τ_fricción = torque de fricción en rodamientos principales
- P_aire = potencia disipada por resistencia aerodinámica

### Lo que PMGI NO incluye

- ❌ Movimiento del fluido interno
- ❌ Transferencia de fluido entre cámaras
- ❌ Potencia extraída por turbinas internas
- ❌ Cualquier dinámica dentro del recinto giratorio

### Analogía del Tren (Definitiva)

```
┌─────────────────────────────────────────────────────────────────┐
│                         TREN EN MOVIMIENTO                       │
│                              (ω)                                 │
│  ┌─────────────────────────────────────────────────────────────┐│
│  │                                                             ││
│  │   🏃 Persona corriendo    🌊 Agua en botella    ⚡ Generador ││
│  │       dentro                  agitándose          interno   ││
│  │                                                             ││
│  │   Nada de esto afecta al motor del tren                     ││
│  │                                                             ││
│  └─────────────────────────────────────────────────────────────┘│
│                              │                                   │
│                              ▼                                   │
│                    Motor del tren solo ve:                       │
│                    - Fricción de ruedas                          │
│                    - Resistencia del viento                      │
└─────────────────────────────────────────────────────────────────┘
```

---

## SISTEMA B: Dinámica Interna del Recinto Giratorio

### Definición

Todo lo que ocurre dentro de la masa giratoria, incluyendo:
- Flujo de fluido entre cámaras
- Diferencial de velocidad angular (CS a ω, CI a ≈0)
- Extracción de potencia
- Todas las físicas del sistema centrífugo

### Fuente de Energía

La energía del Sistema B proviene del **diferencial de velocidad angular**, NO del motor externo.

```
┌─────────────────────────────────────────────────────────────────┐
│                     FLUJO DE ENERGÍA INTERNO                     │
│                                                                  │
│   Fluido en CS (ω)                     Fluido en CI (≈0)         │
│   ┌──────────────┐                     ┌──────────────┐          │
│   │ Alto momento │ ══════════════════► │ Bajo momento │          │
│   │   angular    │    Libera energía   │   angular    │          │
│   │  L = m·ω·r²  │         ↓           │    L ≈ 0     │          │
│   └──────────────┘    ┌────────┐       └──────────────┘          │
│                       │TURBINA │                                 │
│                       │  ⚡    │                                 │
│                       └────────┘                                 │
│                            │                                     │
│                            ▼                                     │
│                    Potencia extraída                             │
│                                                                  │
│   ════════════════════════════════════════════════════════════   │
│   Esta energía viene del DIFERENCIAL, no del motor externo       │
│   ════════════════════════════════════════════════════════════   │
└─────────────────────────────────────────────────────────────────┘
```

### Analogía Hidroeléctrica

El Sistema B funciona como una **represa hidroeléctrica dentro del tren**:

| Represa Convencional | Sistema Centrífugo |
|---------------------|-------------------|
| Gravedad crea diferencial de altura | Rotación crea diferencial de ω |
| Agua cae de altura alta a baja | Fluido pasa de ω alto a ω bajo |
| Turbina extrae energía de la caída | Turbina extrae energía del frenado |
| No afecta a la gravedad | No afecta al motor de rotación |

---

## Geometría del Sistema

### Dimensiones Base

| Parámetro | Valor |
|-----------|-------|
| Radio interno (r₁) | 1.0 m |
| Radio externo (r₂) | 2.0 m |
| Altura total | 0.50 m |
| Altura TI (techo intermedio) | 0.25 m |

### Componentes

```
Vista en corte radial (desde el eje hacia PA):

        Eje                                              PA (r=2m)
         │                                                  │
         │◄────────────── 1 metro ──────────────────────────►│
         │                                                  │
    0.50m├─────────────────────TS────────────────────────────┤
         │                    CS                            │
         │         (gira con estructura a ω)                │
    0.25m├────────TI──────────┐   ┌─────────────────────────┤
         │                    │   │ ← Apertura 10cm         │
         │         CI         │   │                         │
         │  (bandeja flotante │   │                         │
         │   sobre rodamientos│   │                         │
         │   ω_CI ≈ 0)        │   │                         │
    0.00m├────────────────────S───┴─────────────────────────┤
         │                                                  │
      r=1m                                               r=2m
```

### Nomenclatura Establecida

| Símbolo | Nombre | Descripción |
|---------|--------|-------------|
| S | Suelo | Base del recipiente |
| TI | Techo Intermedio | División entre CI y CS (altura 25cm) |
| TS | Techo Superior | Tope del recipiente (altura 50cm) |
| PA | Pared de Análisis | Pared externa (r = 2m) |
| CI | Cámara Inferior | Bajo TI, bandeja flotante, ω ≈ 0 |
| CS | Cámara Superior | Sobre TI, gira con estructura a ω |
| AI | Aceite Inicial | Fluido de trabajo |

---

## Configuración Física de CI

### Implementación Recomendada: Bandeja sobre Rodamientos

CI es una bandeja independiente que:
- Está **dentro** del sistema giratorio (no anclada al suelo)
- Monta sobre rodamientos de baja fricción
- Puede girar libremente respecto a la estructura
- **INCLINADA HACIA EL CENTRO** (dato fundamental)
- Se mantiene a ω_CI ≈ 0 mediante:
  - Toberas tangenciales inversas (frenado principal)
  - Baffles radiales (evitan rotación del fluido)
  - Ruedas motorizadas con control activo (corrección fina)

### Inclinación de CI - Principio Fundamental

```
Vista en corte radial de CI (inclinada):

    Borde (PA)                                    Centro (eje)
    r = 2m                                        r = 1m
       │                                             │
       │  ╲                                          │
       │    ╲   Aceite fluye por GRAVEDAD            │
       │      ╲  (no hay centrífuga, ω_CI ≈ 0)       │
       │        ╲                                    │
       │          ╲  ────────────────────►           │
       │            ╲     dirección del flujo        │
       │              ╲                              │
       │                ╲                            │
       │                  ╲  ← Inclinación ~2-5°     │
       └────────────────────╲────────────────────────┘
                              Punto más bajo
                              (salida a CS)
```

**Por qué funciona:**
- CI está a ω_CI ≈ 0, por lo tanto NO hay fuerza centrífuga significativa
- La única fuerza que actúa sobre el aceite en CI es la GRAVEDAD
- Con CI inclinada hacia el centro, la gravedad lleva el aceite al centro
- El aceite "cae" naturalmente hacia la salida (zona de succión a CS)

**Cálculo de la pendiente necesaria:**

Para superar la viscosidad del aceite y mantener flujo:
- Ángulo mínimo: ~1-2° (flujo lento)
- Ángulo óptimo: ~3-5° (flujo fluido)
- Ángulo máximo: ~10° (límite estructural)

Con inclinación de 3° y radio de 1m:
- Desnivel: Δh = 1m × tan(3°) = 5.2 cm
- Presión hidrostática: ΔP = ρgh = 870 × 9.8 × 0.052 = 443 Pa

Esta presión es suficiente para mantener el flujo radial en CI.

```
Vista superior de CI:

                    Entrada desde CS
                         ↓
              ┌──────────○──────────┐
             /    ║            ║    \
            /     ║    ════    ║     \    ════ = Baffles radiales
           │      ║    ════    ║      │
  Entrada →○ ═════╬════════════╬═════ ○← Entrada
           │      ║    ════    ║      │         (4 entradas desde 4 CS)
            \     ║    ════    ║     /
             \    ║            ║    /
              └──────────○──────────┘
                         ↑
                   Salida al centro
                   (hacia CS por succión)
```

### Por qué CI NO puede estar fija al suelo

Si CI estuviera anclada al suelo:
- El fluido debería "subir al tren" (acelerarse de 0 a ω) al entrar a CS
- El fluido debería "bajar del tren" (frenarse de ω a 0) al entrar a CI
- El motor debería compensar estos cambios de momento angular
- **Esto violaría PMGI** - el motor vería lo que pasa dentro

Con CI flotante dentro del sistema:
- El fluido nunca "sube ni baja del tren"
- Las transferencias de momento angular son internas
- El motor no se entera de nada
- **PMGI se mantiene independiente**

---

## Física del Diferencial de Velocidad Angular

### Presión Centrífuga

En un fluido rotando a velocidad angular ω:

$$P(r) = P_0 + \frac{1}{2}\rho\omega^2(r^2 - r_0^2)$$

### Diferencial de Presión CS vs CI

| Cámara | ω | Presión en PA (r=2m) |
|--------|---|---------------------|
| CS | ω | P_CS = ½ρω²r² = **alta** |
| CI | ≈0 | P_CI ≈ P_atmosférica = **baja** |

Este diferencial impulsa el flujo de CS hacia CI.

### Ciclo de Flujo

```
1. CS(PA) ──────► CI(entrada)     Por presión diferencial
   [ω, alta P]    [≈0, baja P]    Fluido pierde momento angular
                                   → Energía disponible para turbina

2. CI ──────────► CI(centro)      Por gravedad (CI inclinada al centro)
   [entrada]      [salida]        Fluido fluye radialmente

3. CI(centro) ──► CS(eje)         Por succión (Venturi + centrífuga)
   [≈0]           [ω bajo]        Fluido entra a CS cerca del eje

4. CS(eje) ─────► CS(PA)          Por centrífuga
   [ω, r pequeño] [ω, r grande]   Fluido se acelera, gana momento angular
                                   (sin costo - es pseudo-fuerza)

5. Ciclo se repite
```

---

## Extracción de Potencia

### Fuente de la Energía Extraíble

Cuando el fluido pasa de CS a CI:
- **Antes:** L = m·ω·r² (momento angular alto, en CS a radio grande)
- **Después:** L ≈ 0 (momento angular casi cero, en CI)

Esta pérdida de momento angular = **energía cinética rotacional liberada**.

Cuando el fluido vuelve de CI a CS:
- Entra cerca del eje (r pequeño)
- L_ganado = m·ω·r_eje² << L_perdido

**Balance:** Energía neta disponible = ½m·ω²·(r_PA² - r_eje²)

### Potencia Disponible

$$P_{disponible} = \frac{1}{2}\rho Q \omega^2 (r_{PA}^2 - r_{eje}^2)$$

A 100 RPM (ω = 10.47 rad/s), con Q = 0.96 m³/s:

| Parámetro | Valor |
|-----------|-------|
| P_hidráulica | ~123 kW |
| P_extraíble (45%) | ~55 kW |
| P_neta (η=85%) | ~47 kW |

### Ubicación de Extracción

4 turbinas, una por cada CS, ubicadas cerca de PA antes de la tobera a CI.

```
         CS₁                    CS₂
    ┌────⚡────┐            ┌────⚡────┐
    │  turbina │            │  turbina │
    └────┬─────┘            └────┬─────┘
         │                       │
         ▼                       ▼
    ═════════════════════════════════════
                    CI
    ═════════════════════════════════════
         ▲                       ▲
         │                       │
    ┌────┴─────┐            ┌────┴─────┐
    │  turbina │            │  turbina │
    └────⚡────┘            └────⚡────┘
         CS₃                    CS₄
```

---

## Resumen de Independencia

### Sistema A (PMGI)
- **Qué es:** Motor externo manteniendo ω
- **Qué compensa:** Fricción + aire
- **Qué no ve:** Todo lo interno
- **Energía:** Suministrada externamente

### Sistema B (Dinámica Interna)
- **Qué es:** Flujo y extracción dentro del recinto
- **Motor:** No lo afecta
- **Fuente de energía:** Diferencial ω_CS vs ω_CI
- **Analogía:** Represa hidroeléctrica dentro del tren

### Conexión entre sistemas

```
                    ┌─────────────┐
                    │   NINGUNA   │
                    └─────────────┘
```

El Sistema A mantiene la rotación.
El Sistema B aprovecha que existe rotación para crear un diferencial interno.
Ninguno afecta al otro energéticamente.

---

## Próximos Pasos para Análisis

Este documento sirve como base para continuar el análisis con la separación conceptual clara. Temas pendientes:

1. [ ] Cálculos detallados de flujo por fase del ciclo
2. [ ] Diseño de toberas inversas óptimas
3. [ ] Especificaciones de turbinas por CS
4. [ ] Sistema de control de estabilización de CI
5. [ ] Análisis de arranque y parada
6. [ ] Escenarios de falla y seguridad
7. [ ] Prototipo a escala reducida

---

## Referencias del Proyecto

- [DOCUMENTACION_TECNICA.md](./DOCUMENTACION_TECNICA.md) - Documentación completa
- [HISTORIAL_CONVERSACION.md](./HISTORIAL_CONVERSACION.md) - Historial de desarrollo
- [GitHub Repository](https://github.com/ivankorzy25/sistema-centrifugo-diferencial)

---

*Base conceptual v2.0 - Sistemas A y B claramente separados*
