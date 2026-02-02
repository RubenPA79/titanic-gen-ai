# 📊 Informe Detallado de Resultados: Titanic GenAI

Este documento detalla los hallazgos técnicos y las métricas obtenidas tras la ejecución del pipeline de análisis.

## 1. Archivos Generados (Listos para Descarga)

Al clonar este repositorio, encontrarás los siguientes archivos en la carpeta principal:

| Archivo | Descripción | Uso |
| :--- | :--- | :--- |
| `interactive_eda.html` | **Gráfico Interactivo**. Muestra clústeres de pasajeros por Edad, Precio y Supervivencia. | **Abrir en navegador web**. Permite hacer zoom y ver detalles al pasar el mouse. |
| `titanic_clean.csv` | Dataset con imputación inteligente de edad. | Usar para entrenar modelos base sin ruido de nulos. |
| `titanic_features.csv` | Dataset final con ingeniería de variables ("Family Survival"). | Usar para modelos avanzados (Random Forest, XGBoost). |

---

## 2. Hallazgo Clave: "Family Survival Rate"

Nuestra hipótesis fue que **la supervivencia no era individual, sino grupal**.

### Evidencia en los Datos
Al agrupar pasajeros por `Apellido` y `Ticket`, descubrimos patrones extremos:
*   **Grupos de Alta Supervivencia:** Familias enteras en 1ª y 2ª clase donde si sobrevivía uno, sobrevivían casi todos (mujeres y niños primero, pero con el grupo).
*   **La Tragedia de los Sage:** La familia Sage (11 miembros, 3ª clase) pereció por completo. Nuestro modelo, al ver que un miembro tenía una tasa de supervivencia familiar de 0, predijo correctamente la muerte de los otros 10, algo que un modelo simple basado solo en "Edad" o "Sexo" podría fallar.

---

## 3. Explicabilidad del Modelo (SHAP)

El gráfico SHAP (generado en el Notebook 3) revela la importancia de las variables para el modelo Random Forest:

1.  **`Family_Survival_Rate`**: Es consistentemente la variable **más importante**.
    *   *Valor Alto (+1)* → Empuja fuertemente la predicción hacia **Sobrevivir**.
    *   *Valor Bajo (0)* → Empuja fuertemente hacia **No Sobrevivir**.
2.  **`Sex` y `Pclass`**: Siguen siendo vitales, pero la tasa familiar captura matices que estas variables solas pierden.
3.  **`Age`**: Gracias a nuestra imputación inteligente por títulos (Master, Dr, etc.), la edad se volvió una variable más limpia y predictiva, diferenciando claramente a "niños" (Masters) de adultos.

---

## 4. Conclusión Técnica

El uso de **Ingeniería de Variables Orientada a Grupos** mejoró la capacidad del modelo para detectar casos difíciles. Mientras los modelos tradicionales ven "pasajeros aislados", nuestro enfoque ve "redes familiares", lo cual es una representación mucho más fiel de la realidad histórica del Titanic.

**Recomendación:** Descarga `interactive_eda.html` y ábrelo en tu navegador para explorar visualmente estos grupos.
