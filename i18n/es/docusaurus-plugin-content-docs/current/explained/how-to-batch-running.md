---
id: batch-running
title: Cómo realizar varias simulaciones por grupos
sidebar_label: Ejecución por grupos
sidebar_position: 1
---

Cuando se buscan los parámetros físicos y geométricos adecuados, se necesita más de una simulación para evaluar y comparar los resultados y el impacto de los distintos valores de los parámetros.

Para ahorrar tiempo, puede **preparar varios casos de simulación y ejecutarlos sucesivamente durante la noche o el fin de semana**, sin necesidad de ejecutar manualmente cada simulación.

## ¿Cuándo utilizar la ejecución por grupos?

La *ejecución de varios casos en secuencia* o *ejecución sucesiva* es útil **cuando debe determinarse el impacto en los resultados de algunos parámetros físicos o geométricos como la posición del inductor, el número de devanados, la frecuencia, etc.**.

Por ejemplo, cuando se busca el perfil de endurecimiento adecuado de la pieza, **se deben probar diferentes frecuencias** para encontrar el tamaño óptimo de la zona de endurecimiento. Para ello, deben ejecutarse múltiples casos con diferentes ajustes de frecuencia para comparar los resultados. En el ejemplo de calentamiento de eje escalonado que se muestra a continuación se aprecia claramente el impacto que tienen las distintas frecuencias en los resultados.


<p align="center">

![Frequency comparement](assets/batch-running/1.png)

</p>

Para facilitar la ejecución de muchos casos diferentes, prepárelos y ejecútelos todos durante la noche o el fin de semana, y evalúe los diferentes resultados a la mañana siguiente.

## ¿Cómo configurar la ejecución por grupo?

Para ejecutar sucesivamente diferentes casos de CENOS, debe crear un archivo *.bat* en el que defina qué casos y en qué orden los desea calcular. A continuación, basta con hacer doble clic en el archivo *.bat* para iniciar los cálculos.

En este ejemplo estableceremos una ejecución sucesiva de 3 casos.

### 1. Abrir el bloc de notas

*Notepad* es un editor de código integrado en Windows. Ábralo escribiendo *Notepad* en la línea *Buscar en Windows* y pulsando *Enter*.

<p align="center">

![Frequency comparement](assets/batch-running/2.png)

</p>

### 2. Definir la secuencia

Para definir los casos que quiere ejecutar, necesita **escribir una línea de comandos para cada caso** que defina con qué ejecutarlo y dónde encontrar el archivo del caso. La estructura básica de este comando consta de 2 partes - **"ruta de CENOS "**, donde CENOS está instalado y desde donde se inicia, y **"ruta del caso "** a la carpeta del caso que desea ejecutar.

<p align="center">

![Frequency comparement](assets/batch-running/3.png)

</p>

Para encontrar **la ruta de CENOS**, haga clic con el botón derecho en el acceso directo de CENOS y seleccione **Propiedades**. La ruta de CENOS ya estará resaltada - simplemente cópiela y péguela en el bloc de notas.

<p align="center">

![Frequency comparement](assets/batch-running/4.png)

</p>

Para encontrar la **ruta del caso**, en el **explorador de archivos** vaya a la carpeta del caso y copie su dirección desde la **barra de direcciones**.

<p align="center">

![Frequency comparement](assets/batch-running/5.png)

</p>

En este ejemplo configuraremos ejecuciones sucesivas para 3 casos. Simplemente escriba el comando para cada caso en su propia línea.

:::note Nota 

Para asegurarse de que la ventana de la consola no se cierra una vez finalizados los cálculos, escriba *pause* después de las líneas de comando de los casos.

:::

:::warning Importante

Ponga ambas rutas entre comillas, de lo contrario el espaciado romperá el comando.

:::

<p align="center">

![Frequency comparement](assets/batch-running/6.png)

</p>

### 3. Guardar como archivo .bat

En *Notepad* haga clic en *Archivo -> Guardar como*. Cambie *Guardar como tipo* a *Todos los archivos (*.*)*, y guarde manualmente el archivo como **archivo por lotes** nombrándolo, por ejemplo, como ***secuencia.bat***.

<p align="center">

![Frequency comparement](assets/batch-running/7.png)

</p>

### 4. Ejecutar las simulaciones

Una vez creado el fichero **Batch**, haga doble clic sobre él para iniciar el cálculo. Se abrirá una ventana de consola desde la que se ejecutarán todos los casos definidos en el archivo *.bat*. Automáticamente se abrirá una ventana de CENOS, se calculará el caso, se guardarán los resultados, se cerrará la ventana de CENOS y se pasará a la siguiente simulación.

Cuando todas las simulaciones sean calculadas, la ventana de la consola permanecerá abierta, porque *pause* fue escrito al final de los comandos del archivo *.bat*. Esto es útil para saber que las simulaciones se han calculado correctamente.

<p align="center">

![Frequency comparement](assets/batch-running/8.png)

</p>

## Limitaciones

### Configuración de casos

Si una de las carpetas de casos definidas en el archivo *.bat* tiene una definición física incompleta, como falta de algún material, valor actual, etc., lo que significa que no se puede ejecutar, se omitirá y no se calculará.

:::note Nota

Asegúrese de que todos los casos definidos en el archivo .bat están listos para el cálculo.

:::
