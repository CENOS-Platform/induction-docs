---
id: fluxtrol-heating
title: Cómo configurar el cálculo térmico de los concentradores de flujo
sidebar_label: Calefacción de concentradores de flujo
sidebar_position: 11
---

El sistema de calentamiento por inducción más básico consta sólo de dos partes: la pieza de trabajo y el inductor. Los sistemas más avanzados incorporan concentradores de flujo, que ayudan a concentrar el campo magnético y mejoran la economía del sistema.

Cuando se introducen concentradores de flujo en la simulación, deben conocerse parámetros adicionales a partir de los resultados, como **la pérdida de potencia y el calentamiento de los concentradores**.

En este artículo **aprenderemos a configurar la definición térmica del concetrador de flujo** para el cálculo del calentamiento y las pérdidas.

<p align="center">

![Concentrators](assets/fluxtrol-heating/0.png)

</p>

## Habilitar cálculo térmico

Para calcular el *Análisis Térmico* de los concentradores de flujo, es necesario **habilitar este tipo de análisis** en la configuración de física bajo el dominio del concentrador.

<p align="center">

![Concentrators](assets/fluxtrol-heating/1.png)

</p>

## Añadir propiedades del material

Para el análisis adicional es necesario definir las propiedades térmicas y los parámetros para las pérdidas.

### Propiedades térmicas

Defina *Conductividad Térmica* y *Capacidad Térmica* de la misma manera que para otros dominios, como la pieza de trabajo.

<p align="center">

![Concentrators](assets/fluxtrol-heating/2.png)

</p>

### Pérdidas de potencia

Para calcular la pérdida de potencia en concentradores de flujo, marque la casilla *Use power losses in non-conducting material*. Introduzca *Amplitud para la pérdida de potencia*, *Exponente de frecuencia* y *Exponente de campo magnético*.

<p align="center">

![Concentrators](assets/fluxtrol-heating/3.png)

</p>

## Definir las condiciones de contorno

Para el *Análisis térmico* es necesario **crear un grupo de superficies para la interfaz concentrador-aire**, y **definir el intercambio de calor** en esta superficie.

<p align="center">

![Concentrators](assets/fluxtrol-heating/4.png)

</p>

Si el concentrador está en contacto con el inductor (tienen una superficie común), **necesita crear un grupo separado para la superficie concentrador-inductor**. Defínalo con *Temperatura fija* o *Flujo de calor*.

Para el análisis EM defina cada uno de estos grupos como *Interfaz*.