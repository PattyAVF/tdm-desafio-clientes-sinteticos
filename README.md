

---

## 💡 Solución

Se diseñó un flujo completo que permite:

1. Generar datos sintéticos con Faker  
2. Introducir errores controlados (`error_rate`)  
3. Validar los datos con reglas determinísticas  
4. Clasificar errores por tipo  
5. Generar métricas de calidad  

---

## 🏗️ Arquitectura

### 🔹 Arquitectura de referencia

```text
Generación → Dataset → Validación → Métricas → Reporte
🔹 Arquitectura de solución
Google Colab
   ↓
Generación (Faker + error_rate)
   ↓
PySpark DataFrame
   ↓
Validaciones:
   - Schema
   - Domain
   - Duplicates
   - Business rules
   ↓
Resultados:
   - Dataset validado
   - Errores detectados
   - Métricas de calidad

⚙️ Tecnologías
Python
PySpark
Faker
Google Colab
```
## 🚀 Ejecución
1. Abrir en Google Colab

Ejecutar el notebook incluido en el repositorio.

2. Instalar dependencias
 ```
pip install pyspark faker pandas
```
3. Ejecutar flujo

Ejecutar las celdas del notebook en orden. El flujo realiza:

# Generación de datos sintéticos
 ```
# 1. GeneraR la lista de diccionarios
data = [generar_cliente(i) for i in range(1, NUM_REGISTROS + 1)]

# 2. CreaR el DataFrame pasando el SCHEMA como segundo argumento
df = spark.createDataFrame(data, schema=schema)
 ```
# Resumen de generación
 ```
print("DataFrame Spark creado correctamente")
print(f"Total registros generados: {df.count()}")
print(f"Total errores inyectados: {len(log_errores_inyectados)}")
 ```
# Validación determinística
 ```
print("Iniciando Validación Determinística de Datos...")

📊 Ejemplo de salida
🔹 Vista del dataset generado

Total registros generados: 400
Total errores inyectados: 4

|customer_id|tipo_identificacion|identificacion|nombre|apellido|fecha_nacimiento|email|telefono|direccion|
|-----------|-------------------|--------------|------|--------|----------------|-----|--------|----------|
|Cus001|PASAPORTE|5O1CE7B5|Pedro|Mora|17/10/1995|pedro.mora1@testmail.com|0993632280|Av. Colón N9945 y Sucre, Ambato|
|Cus002|CEDULA|1710967389|Juan|Gómez|17/06/1952|juan.gomez2@testmail.com|0975196537|Calle Bolívar N512 y Sucre, Guayaquil|
|Cus003|RUC|1718397506001|Carlos|Mora|12/09/1963|carlos.mora3@testmail.com|0908336014|Calle Bolívar N1932 y Sucre, Cuenca|
 ```
🔹 Reporte de métricas
 ```
REPORTE DE MÉTRICAS DE CALIDAD TDM

Total Registros:        400
Reglas Evaluadas:       5 (R1, R2, R3, R4, R5)
Errores Totales:        1
% Cumplimiento:         99.75%

Clasificación de Errores:
- Schema (Nulos/Tipos): 1
- Domain (Catálogos):   0
- Dup (Unicidad):       0
- Business (Lógica):    0

Muestra de Errores Detectados:

|customer_id|estado_cliente|fecha_nacimiento|
|-----------|---------------|----------------|
|Cus328     |INACTIVO       |13/11/1953      |
 ```


## 🧪 Validaciones implementadas

### ✔ Schema
- Campos obligatorios  
- Tipos de datos  

### ✔ Domain
- Formatos inválidos  
- Valores fuera de catálogo  

### ✔ Duplicates
- Registros duplicados  

### ✔ Business rules
- Reglas funcionales  

## 📂 Estructura del proyecto

```text
tdm-data-validator/
│
├── notebooks/
├── src/
├── data/
├── docs/
├── presentation/
└── README.md
```

## 🧠 Decisiones clave

- Uso de **Google Colab** para facilitar ejecución  
- Uso de **PySpark** para escalabilidad  
- Uso de **datos sintéticos** para evitar datos sensibles  
- Uso de **seed** para reproducibilidad  
- Uso de **error_rate** para simular fallos reales  
- Clasificación de errores para análisis  


## 💡 Valor del proyecto

- Mejora la calidad de datos en testing  
- Reduce errores en producción  
- Facilita auditoría y trazabilidad  


## 👤 Autor

**Patricia Valarezo**
