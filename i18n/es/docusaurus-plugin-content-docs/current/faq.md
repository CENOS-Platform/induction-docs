---
id: faq
title: Preguntas frecuentes
sidebar_label: Preguntas frecuentes
sidebar_position: 8
---

### ¿Puede simularse en CENOS un enfriamiento por pulverización que sigue al inductor en un sistema de endurecimiento por inducción de barrido?

La zona de enfriamiento en movimiento puede definirse mediante expresiones. Lea más [**aquí**](/physics/field-expressions#moving-spray-cooling).

### ¿Cómo definir correctamente los devanados de la bobina en un caso con simetría?

En casos de simetría 2D o 3D es necesario definir cada mitad o sección de bobinado por separado en la configuración de la física. Si agrupa todos los devanados en un grupo, la corriente establecida en este grupo se distribuirá sobre todos los devanados y producirá resultados incorrectos.

### ¿Qué hacer con la interfaz inductor-aire?

La interfaz inductor-aire sólo debe definirse si está interesado en el análisis térmico del inductor. De lo contrario, no es necesario definirla por separado.

### ¿Es necesario identificar el centro hueco del inductor como *Aire* en la sección de física?

Si usted está construyendo la simulación del inductor con el canal de enfriamiento en 2D o 3D, usted necesita incluir el canal de enfriamiento al grupo *Air* para el cálculo correcto del campo EM.

### ¿Qué hacer con la interfaz concentrador-aire?

La interfaz concentrador-aire necesita una definición separada sólo cuando el análisis térmico se realiza en concentradores. Si calcula el calentamiento en concentradores, consulte el artículo de documentación sobre el cálculo térmico de concentradores de flujo.

### ¿Se puede simplificar la bobina asimétrica a un plano 2D?

La simulación del calentamiento por inducción puede simplificarse a 2D sólo para geometrías axial-simétricas. Si la colocación de su inductor o concentrador no es axial-simétrica, la simplificación 2D de dicha geometría no proporcionará resultados que puedan representar la geometría completa.

### ¿Qué significa prioridad de malla?

La prioridad de malla es el orden en el que se calculan las submallas. Si dos submallas (inductor y concentrador) tienen una superficie común, una submalla se calculará primero, y la otra se basará parcialmente en la primera submalla. Se calcularán primero las submallas que estén en la parte superior de la lista, y deberá dar prioridad a las submallas con mayor importancia (inductor > concentrador).

### Después de volver a abrir Shaper, la geometría no está allí y dice "Part_1 (not loaded)". ¿Cómo acceder a esta geometría?

La geometría todavía está allí, simplemente no se carga. Haga clic derecho en *Part_1 (not loaded)* y haga clic en *Activate*. Entonces debería poder acceder a todo lo que ha creado en *Part_1*.

### Al usar el paso de tiempo *Adaptativo*, se producen saltos hacia arriba y hacia abajo en el tamaño del paso de tiempo. ¿Cuál podría ser la razón de ésto?

Si utiliza el paso de tiempo *Adaptativo*, CENOS ajusta automáticamente el tamaño del paso de tiempo. En los puntos en los que el calentamiento es más rápido, crea pasos temporales más pequeños, pero cuando el calentamiento no es tan dinámico, los pasos temporales se crean más grandes para ahorrar tiempo de cálculo. Este comportamiento puede crear saltos hacia arriba y hacia abajo en el tamaño del paso de tiempo. Si quiere deshacerse de estos saltos, necesita establecer un paso de tiempo constante lo suficientemente pequeño para una buena resolución de cada parte del calentamiento, ya que no puede ajustar los parámetros del paso de tiempo *Adaptativo*.

### ¿Qué significa "ERROR: Elements found with aspect ratio > 10000"?

Al exportar la malla a CENOS, a veces se produce un error sobre la relación de aspecto. Significa que la malla se ha creado correctamente, pero contiene elementos muy largos y estrechos que pueden afectar a los resultados de la simulación. Si es así, debe averiguar dónde se encuentran estos elementos y cambiar el enfoque de mallado en ese dominio. Puede encontrar más información en el artículo de documentación sobre [**Aspect Ratio**](/meshing/aspect-ratio).

### ¿Puedo introducir corriente RMS como entrada?

En CENOS sólo puede utilizarse la amplitud de la corriente como entrada de corriente. Si conoce el valor de corriente RMS, debe multiplicarlo por √2 para obtener el valor de la amplitud.

### ¿Cómo guardar resultados personalizados en ParaView?

Puede guardar sus resultados personalizados como un archivo de estado en *ParaView*. El archivo de estado guardará su estado actual de resultados (con filtros, gráficos, enfoques de visualización personalizados, etc.), y podrá cargarlo más tarde y acceder a sus resultados personalizados. Para guardar el archivo de estado, en *ParaView* haga clic en *File → Save State…*. Cuando abra ParaView la próxima vez, sus resultados personalizados se abrirán automáticamente.

### ¿Cómo ajustar el sentido de la corriente que circula por la bobina?

Si desea cambiar la dirección de la corriente en un devanado específico, debe añadir el signo menos "-" antes del valor de la corriente.
