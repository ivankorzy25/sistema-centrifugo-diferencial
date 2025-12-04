# Análisis de Dinámica de Fluidos @ 200 RPM
## Sistema Centrífugo de Diferencial de Velocidad Angular

**Fecha:** Diciembre 2024
**Premisa:** El sistema gira a 200 RPM - dato fijo, no cuestionable
**Enfoque:** Solo dinámica de fluidos interna

---

## Parámetros Base

| Parámetro | Símbolo | Valor | Unidad |
|-----------|---------|-------|--------|
| Velocidad angular | ω | 200 RPM = 20.94 | rad/s |
| Radio interno | r₁ | 1.0 | m |
| Radio externo (PA) | r₂ | 2.0 | m |
| Densidad aceite | ρ | 870 | kg/m³ |
| Viscosidad cinemática | ν | 68×10⁻⁶ | m²/s |
| Número de CS | n | 4 | - |
| Inclinación CI | θ | 7° | - |
| Gravedad | g | 9.81 | m/s² |

---

## FASE 1: Campo Centrífugo @ 200 RPM

### 1.1 Aceleración Centrífuga

La aceleración centrífuga en función del radio:

$$a_c(r) = \omega^2 \cdot r$$

| Radio (m) | a_c (m/s²) | Equivalente en g's |
|-----------|------------|-------------------|
| 1.0 | 438.6 | 44.7 g |
| 1.5 | 657.9 | 67.1 g |
| 2.0 | 877.2 | **89.4 g** |

**El fluido en PA experimenta ~90 veces la gravedad terrestre.**

### 1.2 Presión Centrífuga

Presión diferencial desde el eje hasta radio r:

$$P(r) = \frac{1}{2}\rho\omega^2(r^2 - r_0^2)$$

Tomando r₀ = 1.0 m como referencia (P = 0):

| Radio (m) | ΔP (kPa) | ΔP (bar) |
|-----------|----------|----------|
| 1.0 | 0 | 0 |
| 1.5 | 238 | 2.38 |
| 2.0 | **572** | **5.72** |

**Presión diferencial en PA: 5.72 bar (572 kPa)**

### 1.3 Velocidad Tangencial

$$v_t = \omega \cdot r$$

| Radio (m) | v_t (m/s) | v_t (km/h) |
|-----------|-----------|------------|
| 1.0 | 20.9 | 75 |
| 1.5 | 31.4 | 113 |
| 2.0 | **41.9** | **151** |

**El fluido en PA viaja a 151 km/h tangencialmente.**

---

## FASE 2: Flujo CS → CI

### 2.1 Diferencial de Presión Disponible

En CS (girando a ω): P_CS = 572 kPa en PA
En CI (ω ≈ 0): P_CI ≈ 0 kPa (solo presión hidrostática por gravedad)

$$\Delta P = P_{CS} - P_{CI} = 572 - 0 = 572 \text{ kPa}$$

### 2.2 Velocidad del Flujo por Tobera

Usando ecuación de Bernoulli simplificada (tobera ideal):

$$v = \sqrt{\frac{2 \cdot \Delta P}{\rho}} = \sqrt{\frac{2 \times 572,000}{870}} = 36.3 \text{ m/s}$$

Con coeficiente de descarga Cd = 0.85 (tobera real):

$$v_{real} = 0.85 \times 36.3 = 30.8 \text{ m/s}$$

### 2.3 Caudal por Tobera

Asumiendo 4 toberas (una por CS), cada una con área A = 0.02 m² (equivalente a Ø 16 cm):

$$Q_{tobera} = C_d \cdot A \cdot v = 0.85 \times 0.02 \times 36.3 = 0.617 \text{ m³/s}$$

**Caudal total (4 toberas):**

$$Q_{total} = 4 \times 0.617 = 2.47 \text{ m³/s} = 2,470 \text{ L/s}$$

### 2.4 Flujo Másico

$$\dot{m} = \rho \cdot Q = 870 \times 2.47 = 2,149 \text{ kg/s}$$

### 2.5 Energía Cinética del Flujo

Energía cinética específica del fluido al salir de CS:

$$E_k = \frac{1}{2}v^2 = \frac{1}{2}(30.8)^2 = 474 \text{ J/kg}$$

Más la energía de velocidad tangencial en PA:

$$E_{tang} = \frac{1}{2}v_t^2 = \frac{1}{2}(41.9)^2 = 878 \text{ J/kg}$$

**Energía total disponible por kg de fluido:**

$$E_{total} = E_k + E_{tang} = 474 + 878 = 1,352 \text{ J/kg}$$

---

## FASE 3: Dinámica en CI

### 3.1 Frenado del Fluido

El fluido entra a CI con:
- Velocidad tangencial: ~41.9 m/s (del giro de CS)
- Velocidad radial: ~30.8 m/s (del diferencial de presión)

Las toberas tangenciales inversas redirigen el chorro para:
1. Frenar CI (mantenerla a ω ≈ 0)
2. Disipar la velocidad tangencial del fluido

**Energía disipada en frenado:**

$$E_{frenado} = \frac{1}{2}v_t^2 = 878 \text{ J/kg}$$

Esta energía se usa para mantener CI quieta y se convierte en calor/turbulencia.

### 3.2 Flujo Radial por Gravedad

Con CI inclinada 7° hacia el centro y ω_CI ≈ 0:

**Componente de gravedad en dirección radial:**

$$a_{radial} = g \cdot \sin(7°) = 9.81 \times 0.122 = 1.20 \text{ m/s²}$$

**Velocidad de flujo en canal inclinado (flujo laminar en película):**

Para un canal de ancho w = 0.35 m y profundidad h = 0.12 m:

Usando Manning para canal abierto:
- n = 0.015 (superficie lisa)
- Pendiente S = tan(7°) = 0.123
- Radio hidráulico R = A/P = (0.35×0.12)/(0.35+2×0.12) = 0.071 m

$$v = \frac{1}{n}R^{2/3}S^{1/2} = \frac{1}{0.015}(0.071)^{0.667}(0.123)^{0.5} = 4.0 \text{ m/s}$$

**Caudal por canal (8 canales radiales en CI):**

$$Q_{canal} = v \cdot A = 4.0 \times (0.35 \times 0.12) = 0.168 \text{ m³/s}$$

$$Q_{CI,total} = 8 \times 0.168 = 1.34 \text{ m³/s}$$

### 3.3 Verificación de Balance

| Flujo | Caudal (m³/s) | Caudal (L/s) |
|-------|---------------|--------------|
| Entrada CS→CI | 2.47 | 2,470 |
| Salida CI (gravedad) | 1.34 | 1,340 |
| **Déficit** | **1.13** | **1,130** |

**⚠️ PROBLEMA: El flujo por gravedad en CI es insuficiente**

### 3.4 Solución: Aumentar Capacidad de CI

Para equilibrar el flujo, necesitamos:

**Opción A: Más canales**
- 8 canales → 15 canales
- Q = 15 × 0.168 = 2.52 m³/s ✓

**Opción B: Canales más grandes**
- Aumentar sección a 0.50 m × 0.15 m
- Q = 8 × 4.0 × 0.075 = 2.4 m³/s ✓

**Opción C: Mayor inclinación**
- Aumentar a 10°: v = 4.8 m/s
- Q = 8 × 4.8 × 0.042 = 1.61 m³/s (insuficiente solo)

**Recomendación: Opción A + C combinadas**
- 12 canales de 0.40 m × 0.12 m
- Inclinación 10°
- Q = 12 × 4.8 × 0.048 = 2.76 m³/s ✓

---

## FASE 4: Retorno CI → CS

### 4.1 Mecanismo de Succión

En el centro de CI (r ≈ 1.0 m), el fluido debe entrar a CS.

CS gira a ω, creando un vórtice cerca del eje. La presión en el centro del vórtice es menor que en la periferia.

**Presión en el eje de CS:**

Si el fluido en CS forma un vórtice forzado:

$$P_{eje} = P_{PA} - \frac{1}{2}\rho\omega^2(r_{PA}^2 - r_{eje}^2)$$

$$P_{eje} = 572 - \frac{1}{2}(870)(20.94)^2(4 - 1) = 572 - 572 = 0 \text{ kPa}$$

En realidad, puede ser **negativa** (succión) si hay aire en el centro.

### 4.2 Efecto Venturi en la Entrada

Si diseñamos una entrada tipo Venturi en CS:

- Flujo principal en CS pasa por constricción
- Crea zona de baja presión
- Succiona fluido desde CI

**Caudal de succión (diseño Venturi):**

Con diferencial de 50 kPa y área de entrada 0.03 m²:

$$Q_{succion} = C_d \cdot A \cdot \sqrt{\frac{2\Delta P}{\rho}} = 0.9 \times 0.03 \times \sqrt{\frac{2 \times 50,000}{870}}$$

$$Q_{succion} = 0.9 \times 0.03 \times 10.7 = 0.29 \text{ m³/s por entrada}$$

**Total (4 entradas):**

$$Q_{retorno} = 4 \times 0.29 = 1.16 \text{ m³/s}$$

### 4.3 Balance Final de Flujo

| Componente | Caudal (m³/s) |
|------------|---------------|
| Salida CS→CI (por presión) | 2.47 |
| Tránsito en CI (por gravedad) | 2.76 (optimizado) |
| Retorno CI→CS (por succión) | 1.16 |

**⚠️ El retorno es el cuello de botella**

### 4.4 Solución: Sistema Auto-Regulado

El sistema se auto-regula: si el retorno es menor que la salida, el nivel en CI sube, aumentando la presión hidrostática y reduciendo el diferencial efectivo.

**Punto de equilibrio:**

El caudal real será limitado por el retorno:

$$Q_{equilibrio} \approx 1.2 \text{ m³/s}$$

Esto es aproximadamente el 50% del caudal máximo teórico.

---

## FASE 5: Potencia Extraíble

### 5.1 Con Caudal de Equilibrio

Usando Q = 1.2 m³/s (limitado por retorno):

**Potencia hidráulica total:**

$$P_{hidraulica} = \Delta P \cdot Q = 572,000 \times 1.2 = 686 \text{ kW}$$

### 5.2 Distribución de Energía

| Destino | Energía (J/kg) | Potencia (kW) | % |
|---------|----------------|---------------|---|
| Disponible en PA | 1,352 | 686 | 100% |
| Frenado CI (disipado) | 878 | 446 | 65% |
| **Extraíble por turbinas** | **474** | **240** | **35%** |

### 5.3 Potencia Neta de Turbinas

Con eficiencia de turbina η = 85%:

$$P_{turbinas} = 240 \times 0.85 = 204 \text{ kW}$$

**Por cada CS (4 turbinas):**

$$P_{por CS} = \frac{204}{4} = 51 \text{ kW}$$

### 5.4 Resumen de Potencia @ 200 RPM

```
╔════════════════════════════════════════════════════════════╗
║  POTENCIA EXTRAÍBLE @ 200 RPM                              ║
╠════════════════════════════════════════════════════════════╣
║                                                            ║
║  Caudal de equilibrio:     1,200 L/s                       ║
║  Potencia hidráulica:      686 kW                          ║
║  Pérdidas en frenado CI:   446 kW (65%)                    ║
║  Potencia disponible:      240 kW (35%)                    ║
║  Eficiencia turbinas:      85%                             ║
║                                                            ║
║  POTENCIA NETA:            204 kW                          ║
║  Por turbina (×4):         51 kW cada una                  ║
║                                                            ║
╚════════════════════════════════════════════════════════════╝
```

---

## Comparación con 100 RPM

| Parámetro | 100 RPM | 200 RPM | Factor |
|-----------|---------|---------|--------|
| ω (rad/s) | 10.47 | 20.94 | 2× |
| ΔP (kPa) | 143 | 572 | 4× |
| v_tobera (m/s) | 18.1 | 36.3 | 2× |
| Q (m³/s) | 0.6 | 1.2 | 2× |
| P_hidráulica (kW) | 86 | 686 | 8× |
| P_neta (kW) | 29 | 204 | 7× |

**La potencia escala aproximadamente con ω³**

---

## Conclusiones del Análisis de Dinámica de Fluidos

### Hallazgos Principales

1. **Campo centrífugo intenso:** 90 g's en PA, 5.7 bar de presión diferencial

2. **Flujo alto pero limitado:** El caudal teórico es 2.47 m³/s, pero el retorno CI→CS limita a ~1.2 m³/s

3. **Pérdidas significativas en CI:** 65% de la energía se disipa en el frenado tangencial

4. **Potencia extraíble:** ~204 kW netos a 200 RPM (51 kW por turbina)

### Puntos Críticos de Diseño

1. **Retorno CI→CS:** Es el cuello de botella. Optimizar el sistema Venturi/vórtice.

2. **Frenado en CI:** Considerar recuperar parte de la energía de frenado.

3. **Canales en CI:** Deben ser suficientes para transportar el caudal por gravedad.

4. **Cavitación:** A 200 RPM, la presión en el eje puede ser negativa. Requiere presurización.

### Siguientes Pasos

1. [ ] Optimizar diseño de entradas Venturi para aumentar retorno
2. [ ] Evaluar recuperación de energía de frenado en CI
3. [ ] Análisis de cavitación y presurización
4. [ ] Diseño detallado de turbinas de 51 kW

---

*Análisis de dinámica de fluidos - Sistema girando a 200 RPM como dato fijo*
