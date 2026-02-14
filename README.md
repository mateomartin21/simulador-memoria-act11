# 🧠 Simulador de Gestión de Memoria: Best Fit vs. Worst Fit

Este proyecto es una herramienta interactiva diseñada para visualizar y comparar cómo operan dos de los algoritmos de asignación de memoria más comunes en los sistemas operativos. A través de una interfaz dinámica, permite observar en tiempo real la eficiencia, fragmentación y utilización de recursos de cada método.

---

## 🚀 Instrucciones de Uso

### ¿Qué debe hacer el usuario?
1.  **Configuración Inicial:** En el panel superior, define el tamaño total de la memoria (en KB) y el número de bloques iniciales. Haz clic en **"Inicializar Memoria"**.
2.  **Carga de Procesos:** Ingresa el ID y el tamaño de los procesos que deseas simular. Al presionar **"Agregar Proceso"**, estos se enviarán a una cola de espera.
3.  **Ejecución:** Haz clic en **"Ejecutar Asignación"** para ver cómo los algoritmos procesan la cola simultáneamente.
4.  **Gestión:** Puedes limpiar la memoria manteniendo la estructura de bloques o reiniciar la simulación por completo.

### ¿Qué va a observar?
* **Representación Visual:** Los bloques con gradientes azules/verdes indican espacio libre; los bloques con gradientes rosados/amarillos indican procesos asignados.
* **Animaciones:** Los bloques parpadean (efecto *pulse*) al momento de recibir un nuevo proceso para identificar dónde se alojó.
* **Logs en tiempo real:** Una consola en la parte inferior de cada algoritmo detalla si la operación fue exitosa, fallida o si se liberó espacio.

### ¿Qué significan los resultados?
* **Utilización:** El porcentaje de la memoria total que está ocupada por procesos activos.
* **Fragmentación Externa:** Indica qué porcentaje de la memoria libre está tan dispersa que podría no ser útil para procesos grandes.
* **Bloque Libre Más Grande:** La capacidad máxima que un algoritmo puede aceptar para un solo proceso en ese instante.

---

## ⚙️ Explicación de los Algoritmos

El simulador implementa dos estrategias clásicas de búsqueda en la lista de bloques libres:

### 1. Best Fit (Mejor Ajuste)
Busca en toda la lista de bloques libres y selecciona el bloque **más pequeño** que sea lo suficientemente grande para albergar el proceso.
* **Objetivo:** Minimizar el desperdicio de espacio "sobrante" dentro de un bloque.
* **Ventaja:** Intenta preservar los bloques de memoria más grandes para procesos futuros que realmente los necesiten.

### 2. Worst Fit (Peor Ajuste)
Busca en toda la lista y selecciona el bloque **más grande** disponible para colocar el proceso.
* **Objetivo:** Dejar el residuo (espacio sobrante) lo más grande posible.
* **Lógica:** Se basa en la hipótesis de que el espacio sobrante de un bloque grande será más útil para otros procesos que los fragmentos diminutos que suele dejar el *Best Fit*.

---

## 🧠 Reflexión sobre los Resultados

Al utilizar el simulador, se hace evidente que no existe un algoritmo "perfecto". Mientras que **Best Fit** suele ser más eficiente en el aprovechamiento de la memoria a corto plazo, tiende a crear muchos huecos pequeños (fragmentación) que terminan siendo inutilizables. 

Por el contrario, **Worst Fit** intenta mantener la utilidad de los espacios sobrantes, pero puede agotar rápidamente los bloques de gran tamaño, dejando al sistema incapaz de alojar procesos robustos. La eficacia de cada uno depende directamente del flujo y tamaño de los procesos entrantes.

---

## 📚 Referencias
* Silberschatz, A., Galvin, P. B., & Gagne, G. (2018). *Operating System Concepts*. Wiley.
* Tanenbaum, A. S., & Bos, H. (2014). *Modern Operating Systems*. Pearson.
* MDN Web Docs. *JavaScript: Classes and Memory Management*.

---

## 🤖 Cláusula de Uso de IA
Se reconoce y declara el uso de herramientas de **Inteligencia Artificial** (Gemini 1.5/2.0) para las siguientes tareas:
* Generación de la lógica de gestión de memoria en JavaScript (clases `MemoryBlock` y `MemoryManager`).
* Diseño visual de la interfaz mediante CSS (Flexbox, Grid y Animaciones).
* Estructuración y redacción técnica de la documentación en este archivo README.
* Optimización del algoritmo de combinación de bloques libres (`mergeBlocks`).
