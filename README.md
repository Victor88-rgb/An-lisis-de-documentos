# Validador Inteligente de Documentos de Venta con IA

**Autor:** Víctor Sandoval Gómez  
**Curso:** Inteligencia Artificial (Generación de Prompts)  
**Comisión:** 84185

---

## 📄 Resumen del Proyecto

Este proyecto demuestra cómo automatizar la validación de documentos de venta utilizando un modelo de lenguaje avanzado (Google Gemini). El sistema compara de forma inteligente los datos de una oferta comercial (documento de texto) con los datos registrados en un sistema CRM (formato JSON), identificando cualquier discrepancia de manera instantánea y generando un reporte estructurado.

El objetivo principal es resolver un cuello de botella operativo común: la revisión manual de documentos, que es lenta, costosa y propensa a errores humanos.

## 🎯 El Problema a Resolver

En el sector de ventas, la coherencia entre los datos del CRM y los documentos finales (ofertas, contratos) es crucial. El proceso manual de verificación presenta varios desafíos:

-   **Ineficiencia Operativa:** Consume horas de trabajo que podrían dedicarse a tareas de mayor valor.
-   **Riesgo de Error Humano:** Un simple error de tipeo en un precio, RUT o número de serie puede generar pérdidas financieras y dañar la relación con el cliente.
-   **Lentitud en el Ciclo de Venta:** Los retrasos en la validación alargan el tiempo de respuesta al cliente, arriesgando la pérdida de la oportunidad de negocio.

## 💡 La Solución Propuesta

Se desarrolló un script en Python dentro de un entorno de Google Colab que implementa un sistema de **Procesamiento Inteligente de Documentos (IDP)**.

El flujo de trabajo es el siguiente:

1.  **Entrada de Datos:** El sistema recibe dos fuentes de información:
    -   **Datos del CRM:** Un objeto JSON con la información que se considera "la fuente de la verdad".
    -   **Documento de Oferta:** El texto plano del documento que necesita ser verificado.

2.  **Procesamiento con IA:** Se utiliza un **único y eficiente prompt** enviado a la API de Google Gemini. Este prompt instruye al modelo para que:
    -   Extraiga las entidades relevantes del documento de texto.
    -   Compare cada valor extraído con su correspondiente en los datos del CRM.
    -   Genere un reporte de validación completo.

3.  **Salida Estructurada:** El sistema devuelve un **reporte en formato JSON** que detalla, campo por campo, si los valores coinciden o no, mostrando el valor esperado (CRM) y el valor encontrado (documento). Esta salida es predecible y fácil de integrar en otros sistemas (ej. enviar una notificación por correo).

## ✨ Características Principales

-   **Automatización Total:** Elimina la necesidad de revisión manual.
-   **Alta Precisión:** Aprovecha la capacidad de los LLMs para comprender texto no estructurado y extraer información con exactitud.
-   **Salida Estructurada (JSON):** Garantiza una respuesta consistente y legible por máquina, lista para ser procesada.
-   **Eficiencia de Costos:** La validación completa se realiza con **una sola llamada a la API**, optimizando el uso de recursos.
-   **Fácil Implementación:** Desarrollado como una POC en un notebook de Google Colab, demostrando la viabilidad de la solución con herramientas accesibles.

## 🛠️ Tecnologías y Herramientas

-   **Lenguaje:** Python 3
-   **Entorno:** Google Colab (Jupyter Notebook)
-   **Modelo de IA:** Google Gemini 1.5 Pro
-   **Librerías Principales:** `google-generativeai`, `json`

## 🧠 Técnicas de Prompt Engineering Aplicadas

La efectividad de la solución reside en un prompt cuidadosamente diseñado (**Fast Prompting**) que utiliza las siguientes técnicas:

-   **Role-Playing:** Se le asigna a la IA el rol de "auditor de documentos extremadamente meticuloso" para contextualizar la tarea y mejorar la calidad de la respuesta.
-   **Structured Output (JSON):** Se le exige a la IA que la salida sea **únicamente** un JSON bien formado. Esta es la técnica más importante, ya que hace que la respuesta sea directamente procesable por el código, eliminando la necesidad de análisis de texto (parsing) y reduciendo la fragilidad del sistema.
-   **Chain of Thought (Implícito):** El prompt guía al modelo a seguir una secuencia lógica de pasos (leer, extraer, comparar, reportar), lo que mejora la fiabilidad del razonamiento para obtener un resultado preciso.

## 🚀 Cómo Ejecutar el Proyecto

1.  **Clonar el Repositorio:**
    ```bash
    git clone https://github.com/tu-usuario/tu-repositorio.git
    ```
2.  **Abrir en Google Colab:** Sube el archivo `.ipynb` a tu Google Colab.
3.  **Configurar la API Key:**
    -   En el panel izquierdo de Colab, haz clic en el icono de la llave (🔑 "Secretos").
    -   Crea un nuevo secreto con el nombre `GEMINI_API_KEY`.
    -   Pega tu clave de API de Google Gemini en el campo del valor.
4.  **Ejecutar las Celdas:** Ejecuta todas las celdas del notebook en orden. El script instalará las dependencias, cargará los datos de ejemplo y mostrará el reporte de validación final en la salida.
