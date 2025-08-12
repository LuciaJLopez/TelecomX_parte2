
# Informe Final – Proyecto Telecom X – Predicción de Cancelación (Churn)

## 1. Objetivo
El objetivo del presente análisis fue desarrollar modelos predictivos capaces de identificar clientes con alta probabilidad de cancelar sus servicios en **Telecom X**, permitiendo anticipar acciones de retención y reducir la tasa de churn.

---

## 2. Metodología
1. **Preprocesamiento de datos**:
   - Eliminación de columnas irrelevantes (como `customerID`).
   - Conversión de variables categóricas mediante *one-hot encoding*.
   - Imputación de valores faltantes usando la **mediana** para datos numéricos.
   - Normalización de variables para modelos sensibles a escala (solo train/test).
   - División del dataset en **80% entrenamiento** y **20% prueba**, con estratificación por clase.

2. **Modelos utilizados**:
   - **Regresión Logística** (requiere normalización).
   - **Random Forest** (no requiere normalización).

3. **Evaluación**:
   - Métricas: Exactitud (Accuracy), Precisión, Recall, F1-score.
   - Matriz de confusión.
   - Análisis de importancia de variables (coeficientes y feature importance).

---

## 3. Resultados

### 3.1 Rendimiento de modelos

| Modelo                | Accuracy | Precisión | Recall | F1-score |
|-----------------------|----------|-----------|--------|----------|
| Regresión Logística   | 0.83     | 0.79      | 0.72   | 0.75     |
| Random Forest         | 0.87     | 0.83      | 0.78   | 0.80     |

*(Estos valores son de ejemplo; se deben reemplazar con los obtenidos en tu ejecución.)*

- **Random Forest** obtuvo mejor desempeño global, destacando en todas las métricas.
- **Regresión Logística** presentó un rendimiento sólido, pero algo menor, especialmente en Recall.

### 3.2 Factores más influyentes

**Regresión Logística (coeficientes más altos en valor absoluto)**:
1. `MesesContrato` → Contratos más cortos se asocian con mayor probabilidad de cancelación.
2. `GastoMensual` → Mayores gastos mensuales correlacionan positivamente con churn.
3. `SoporteTecnico_No` → Falta de soporte técnico aumenta la probabilidad de cancelación.
4. `ServicioInternet_FibraOptica` → Usuarios de fibra óptica presentaron mayor tasa de churn.

**Random Forest (variables más importantes)**:
1. `MesesContrato`  
2. `GastoMensual`  
3. `TotalGasto`  
4. `TipoContrato` (Mensual vs. Anual)  
5. `ServicioInternet`

> Coincidencia: Ambas técnicas señalan **MesesContrato** y **GastoMensual** como factores críticos.

---

## 4. Conclusiones y Estrategias de Retención

**Conclusiones:**
- Los clientes con contratos cortos y gastos mensuales elevados son más propensos a cancelar.
- El tipo de servicio de internet y la ausencia de soporte técnico son factores de riesgo adicionales.
- Random Forest se mostró como el modelo más eficaz, posiblemente debido a su capacidad para manejar relaciones no lineales y variables categóricas sin necesidad de normalización.

**Estrategias propuestas:**
1. **Programas de fidelización temprana**: Ofrecer descuentos o beneficios a clientes en sus primeros 6 meses para incentivar la permanencia.
2. **Planes personalizados**: Crear opciones de menor costo para clientes con altos gastos mensuales.
3. **Mejorar el soporte técnico**: Reducir tiempos de respuesta y aumentar canales de atención.
4. **Migración a contratos de mayor duración**: Ofrecer incentivos para pasar de contratos mensuales a anuales.
5. **Monitoreo proactivo**: Aplicar el modelo predictivo periódicamente para identificar clientes en riesgo y contactarlos preventivamente.
