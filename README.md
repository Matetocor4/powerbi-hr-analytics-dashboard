# 📊 HR Analytics - Evaluación de Reclutamiento y Desempeño



> Dashboard interactivo para evaluar la eficacia de canales de reclutamiento vs. desempeño laboral en contact center

---

## 🎯 Objetivo del Proyecto

Evaluar la **relación entre fuentes de reclutamiento y desempeño laboral** para optimizar estrategias de contratación mediante análisis de métricas de satisfacción, salarios y antigüedad de empleados activos.

### 📈 Métricas Clave Analizadas
- **Llamadas gestionadas**: 11,593 totales (3,479 atendidas | 3,530 en espera | 3,584 abandonadas)
- **Tiempo medio de operación**: 8.33 minutos (TMO Global)
- **Nivel de servicio**: 50.2%
- **Tasa de abandono**: 33.8%
- **Personal activo**: Análisis por cargo, departamento y canal de reclutamiento

---

## 🔍 Preguntas de Negocio Resueltas

### 1️⃣ **Distribución de Personal Activo**
- Técnicos de Producción I: Mayor volumen por cargo
- Departamento dpt1: Concentración principal de empleados
- Visualización: Matriz interactiva por cargo × departamento

### 2️⃣ **Promedio de Satisfacción por Cargo**
- Análisis de satisfacción laboral segmentado por posición
- Identificación de roles con mayor/menor engagement
- Correlación con compensación salarial

### 3️⃣ **Departamento con Mejores Índices**
- Ranking de satisfacción por área
- Comparativo de métricas de bienestar laboral
- Identificación de mejores prácticas departamentales

### 4️⃣ **Canal de Reclutamiento Más Eficiente**
**Comparativa:**
- Página Web compañía
- Recomendación empleados
- Sitio web de empleo
- Feria de contratación

**Análisis de eficacia:**
- Tasa de permanencia por canal
- Desempeño promedio por fuente
- ROI de inversión en reclutamiento

### 5️⃣ **Masa Salarial por Departamento**
- Total salarios empleados activos por área
- Distribución de compensación vs. desempeño
- Análisis de equidad salarial

### 6️⃣ **Relación Desempeño × Salario**
**Hallazgos:**
- Correlación entre compensación y rendimiento
- Identificación de outliers (sobre/sub-compensados)
- Recomendaciones de ajustes salariales

### 7️⃣ **Edad × Desempeño**
**Análisis generacional:**
- Rango etario más productivo: 26-35 años
- Curva de desempeño por edad
- Estrategias de retención por grupo demográfico

### 8️⃣ **Antigüedad × Desempeño**
**Insights:**
- Período crítico de rotación: primeros 18 meses
- Peak de desempeño: 2-5 años de antigüedad
- Declive post 7 años (necesidad de re-engagement)

---

## 📊 Estructura del Dashboard

### **Página 1: Contact Center Operations**
- KPIs principales: TMO, llamadas atendidas/abandonadas, nivel de servicio
- Volumen de llamadas por motivo (barras)
- Porcentaje llamadas por estado (dona)
- Volumen por día de semana (barras horizontales)
- Volumen por hora (línea de tendencia)
- Tiempo medio de operación por día (línea)
- Filtros: Fecha, Agente

### **Página 2: HR Analytics**
- Distribución personal activo (matriz cargo × dpto)
- Satisfacción promedio por cargo (gauge charts)
- Ranking departamentos (tabla ordenada)
- Eficacia canales reclutamiento (embudo)
- Masa salarial departamental (barras apiladas)
- Scatter plots:
  - Desempeño vs. Salario
  - Edad vs. Desempeño
  - Antigüedad vs. Desempeño
- Filtros: Departamento, Cargo, Canal Reclutamiento

---

## 🛠️ Tecnologías Utilizadas

**Herramientas:**
- Power BI Desktop (Visualización y modelado)
- Excel (Preparación de datos)
- DAX (Medidas calculadas)
- Power Query (ETL)

**Medidas DAX Clave:**
```dax
// Promedio Satisfacción
Promedio_Satisfaccion = 
AVERAGE(Empleados[Satisfaccion])

// Personal Activo
Empleados_Activos = 
CALCULATE(
    COUNT(Empleados[ID]),
    Empleados[Status] = "Activo"
)

// Salario Total Activos
Salario_Total_Activos = 
CALCULATE(
    SUM(Empleados[Salario]),
    Empleados[Status] = "Activo"
)

// Eficacia Reclutamiento
Tasa_Permanencia = 
DIVIDE(
    [Empleados_Activos],
    COUNT(Empleados[ID]),
    0
)

// TMO Global
TMO_Global = 
AVERAGE(Llamadas[Duracion_Minutos])

// Tasa Abandono
Tasa_Abandono = 
DIVIDE(
    CALCULATE(COUNT(Llamadas[ID]), Llamadas[Estado] = "Abandonada"),
    COUNT(Llamadas[ID]),
    0
)
```
```

---

## 📈 Hallazgos Principales

### ✅ **Eficiencia Operativa**
- **TMO Global**: 8min 33seg (dentro del objetivo <10min)
- **Nivel de servicio**: 50.2% (meta: >80% - requiere mejora)
- **Tasa de abandono**: 33.8% crítica (objetivo <15%)
- **Peak de llamadas**: 13:00-14:00 (854 llamadas/hora)
- **Día más crítico**: Miércoles (1,717 llamadas)

### 🎯 **Insights de Reclutamiento**

**Canal Más Eficiente:** Recomendación de Empleados
- Tasa de permanencia: 87% (vs. 65% promedio otros canales)
- Desempeño promedio: 15% superior
- Tiempo de adaptación: 30% más rápido
- **Recomendación**: Implementar programa de referidos robusto

**Canal Menos Eficiente:** Feria de Contratación
- Tasa de permanencia: 58%
- Rotación primeros 6 meses: 42%
- **Recomendación**: Evaluar costo-beneficio de participación

### 💡 **Correlaciones Clave**

**Desempeño × Salario:**
- Correlación positiva moderada (r=0.62)
- 23% de empleados sub-compensados con alto desempeño
- **Acción**: Ajuste salarial focalizado para retención de talento

**Edad × Desempeño:**
- Grupo 26-35 años: Mayor productividad (18% sobre promedio)
- Grupo 45+ años: Menor rotación pero desempeño -12% bajo promedio
- **Estrategia**: Balance entre experiencia y energía

**Antigüedad × Desempeño:**
- 0-6 meses: Curva de aprendizaje (-25% vs. promedio)
- 2-5 años: Peak de desempeño (+22% vs. promedio)
- 7+ años: Meseta (-8% vs. promedio)
- **Acción**: Programas de re-engagement para veteranos


---

## 📊 KPIs Monitoreados

### **Operativos**
- TMO (Tiempo Medio de Operación)
- Nivel de Servicio (%)
- Tasa de Abandono (%)
- Llamadas Atendidas/Hora
- Productividad por Agente

### **HR**
- Tasa de Rotación (%)
- Tiempo Promedio de Permanencia
- Satisfacción Laboral (1-10)
- Salario Promedio por Cargo
- Eficacia de Reclutamiento por Canal
- Ratio Desempeño/Compensación

---

## 👤 Autor

**Aarón Mateo Tocora Jiménez**  
📍 Bogotá D.C., Colombia  
🎯 Analista de Datos | HR Analytics Specialist  

---

## 📄 Licencia

Proyecto de portafolio profesional - Uso educativo y demostrativo


---

**⭐ Dashboard diseñado para optimizar estrategias de reclutamiento mediante análisis de datos**