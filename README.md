
# 🚀 Generador de Datos Sintéticos - Unidad de Entornos No Productivos

Este proyecto automatiza la creación de datasets de clientes bajo un contrato de datos explícito (YAML).

## 🏗️ Arquitectura de la Solución
- **Gobernanza**: Uso de `contract.yaml` para definir reglas de negocio.
- **Procesamiento**: Motor en **PySpark** para generación escalable.
- **Calidad**: Validador determinístico con reporte de métricas (Schema, Domain, Dup, Business).

## 🛠️ Instrucciones de Ejecución
1. Instalar dependencias: `pip install pyspark pyyaml`
2. Cargar el archivo `contract.yaml`.
3. Ejecutar el notebook para generar los archivos `CSV` y `JSON`.

## 🧪 Reproducibilidad
Para obtener resultados consistentes y trazables, se utiliza el **Seed 42**.
