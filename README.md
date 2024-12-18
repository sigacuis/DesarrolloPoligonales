# Cálculo del espesor real de las capas mediante el método de poligonales usando Python

## Descripción del repositorio
Este es un código de Python que resuelve el cálculo del espesor real de las capas mediante el uso de funciones matemáticas cuyos atributos de entrada son los datos tomados en campo, los cuales comúnmente están representados por bases de datos en archivos excel que pueden ser cargados y visualizados en este lenguaje de programación mediante el uso de la librería Pandas.

# Datos de entrada: 

- DistSegmento: Longitud del segmento A-B 
- Azi_Segmento: Azimut segmento A-B
- Dip_Segmento: Inclinación segmento A-B
- Az_rumbo_bedding: Azimut de rumbo de las capas 
- Az_buz_bedding: Azimut de buzamiento de las capas
- dip_bedding: Buzamiento de las capas

# Datos de salida:
- espesor: Columna donde se guardan los espesores reales calculados en metros

<p align="center">
<img src="https://github.com/Anagabrielamantilla/DesarrolloPoligonales/blob/main/Img0.png" width="800">
</p>

###### Funciones creadas

- az2carto(azi): donde el argumento de entrada <b>azi</b> es el ángulo en azimut (en grados, 0 - 360). Esta es una función que convierte los datos de azimut del rumbo en ángulos euclidianos

```
out =  az2carto(azi)
```
- cal_thick(L,I,a,b,f): donde los argumentos de entrada son <b>L</b> (longitud del segmento), <b>I</b> (buzamiento de la capa), <b>a</b> (azimut de rumbo de las capas), <b>b</b> (azimut de buzamiento de las capas), <b>f</b> (azimut de rumbo del segmento)

```
out =  cal_thick(L,I,a,b,f)
```
Las variables de entrada están definidas de la siguiente forma:

```
I=I*np.pi/180
a=az2carto(a)*np.pi/180
b=az2carto(b)*np.pi/180
f=az2carto(f)*np.pi/180
```
El cálculo de las variables aparentes está dado por:

```
omega=np.arctan(np.tan(I)*np.sin(abs(a-f)))*180/np.pi #ángulo de dirección aparente
E=np.sin(omega*np.pi/180)*L #espesor aparente
```
El cálculo de las variables reales está dado por:

```
L2=abs(np.cos((f-b))*L) #longitud proyectada en la misma dirección del buzamiento
E2=np.sin(I)*L2 #espesor real
```
Para obtener la documentación sobre las variables de entrada que requiere la función puedes ejecutar la siguiente celda:

```
help(cal_thick)
```

## Ejemplo en Colab 

En este Colab está un ejemplo completo del uso de las funciones y el proceso automático para aplicarlas en un archivo de excel. Para abrirlo de click en el siguiente ícono: 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1xms3EEhLpyYVl7YiIcuiTqt-IsWStdxS#scrollTo=ZwSqdcHlWbe9)

El espesor real puede ser calculado ingresando los datos tomados en campo segmento por segmento, así como se muestra en la primera parte del código. Pero, también mediante el uso de la función <b>cal_thick</b> que calcula los espesores de manera automática para todos los segmentos ingresados en la tabla excel. Para esto se recomienda nombrar las variables de la misma forma que se encuentra en el Colab. 

###### Exportar el resultado a un excel 
Los espesores reales de todos los segmentos se guardan automáticamente en una nueva columna denominada <b>espesor</b>. El archivo resultante puede ser exportado nuevamente en un archivo .csv, el cual puede visualizarse en excel con todos los datos de la poligonal desarrollada. El archivo exportado podrá descargarse desplegando el panel izquierdo donde se visualizará una carpeta llamada <b>DesarrolloPoligonales</b> y dentro de la cual se encontrará el archivo que contiene los espesores reales con extensión .csv

<p align="center">
<img src="https://github.com/Anagabrielamantilla/DesarrolloPoligonales/blob/main/Img2.jpg" width="400">
</p>

## Usarlo en el disco local

Para usar en el disco local, se debe descargar la carpeta y usar alguna de las siguientes opciones:
- Para los usuarios de Jupyter-notebook: Usar el ejemplo presentado en el archivo <b>poligonal.ipynb</b>. 
- Para los usuarios de spyder u otro IDE:  Usar el ejemplo presentado en el archivo <b>poligonal.py</b>. 

## ¿Cómo colaborar con el proyecto ? 

Ayúdame difundiendo. Envíame más ejemplos para hacer diferentes test. Encuentra errores y repórtalos en un issue en GitHub.

> Contáctanos


Ana Mantilla: anagmd2019@gmail.com </br> <a href="https://www.linkedin.com/in/ana-gabriela-mantilla-24377a21a/">
  <img src="https://cdn-icons-png.flaticon.com/512/174/174857.png" alt="HTML tutorial" style="width:30px;height:30px;">
</a> </br> 
Paul Goyes:   goyes.yesid@gmail.com </br> <a href="https://www.linkedin.com/in/paul-goyes-0212b810/">
  <img src="https://cdn-icons-png.flaticon.com/512/174/174857.png" alt="HTML tutorial" style="width:30px;height:30px;">
</a>

## ¿Cómo citar? 

Mantilla, A y Goyes, P (2024). Anagabrielamantilla/DesarrolloPoligonales: DesarrolloPoligonales (poligonales). Zenodo.
https://doi.org/10.5281/zenodo.10995259
