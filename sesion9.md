<!-- No borrar o modificar -->
[Inicio](./index.md)

## Sesión 9 


<!-- Su documentación aquí -->

## Actividad: Ejercicio de limpieza de datos con Pandas

```
import pandas as pd
import streamlit as st
import matplotlib.pyplot as plt 
data = pd.read_csv('ventas_vehiculos .csv')

st.header("Tabla antes de la limpieza de datos")
data
#datos vacios
data = data.dropna()

#datos atipicos
#plt.hist(data["Kilometraje"])
#st.pyplot()

#plt.boxplot(data["Kilometraje"])
#st.pyplot()

#data.plot.scatter(x="Estado", y="Kilometraje")
#st.pyplot()

data = data[~((data["Kilometraje"] > 100.000) & (data["Estado"] == "Nuevo"))]
data = data[data["Año"]>2000]

#datos duplicados
duplicates = data[data.duplicated(keep=False)]
#st.write(duplicates)

#formato de datos

#st.write(data.dtypes)
data["Fecha"] = pd.to_datetime(data["Fecha"])
#st.write(data.dtypes)

st.header("Tabla despues de la limpieza de datos")
data
```

**DOCUMENTACIÓN DE ERRORES ENCONTRADOS EN EL DATASET**

**Valores vacíos:**
Se identificaron los siguientes valores vacios
| id_registros | Columna_vacía |
|--|--|
|2|Precio|
|20|Precio|
|34|Precio|
|50|Precio|
|200|Precio|
|234|Precio|
|345|Precio|
|342|Precio|
|67|Color|
|209|Color|


**Valores atípicos:**

Para la atipicidad, me basé en un principio en el kilometraje, notando una tendencia que entre vehículos tanto nuevos como viejos, existe una atipicidad en los kilometrajes:![info1](https://firebasestorage.googleapis.com/v0/b/produccion-fotografica-512c5.appspot.com/o/infoAti1.png?alt=media&token=607b2f17-c6ff-4bd8-b145-4915ccb4488e&_gl=1*1fc51o5*_ga*MTIxMjg0MzYwOS4xNjg0Nzg5MTk2*_ga_CW55HF8NVT*MTY5NjU1NTMwNS4yMS4xLjE2OTY1NTUzNDYuMTkuMC4w)
Sin embargo, atendiendo a que es normal en un vehículo usado un kilometraje superior a 100.000km, no lo es para un vehículo usado (aclarando que bajo ese criterio deberían eliminarse todos los vehículos nuevos por tener un kilometraje alto, pero no se hará para efectos de tener más registros que filtrar con las otras funciones) por ende, solo se filtraran los vehículos nuevos que superen dicho kilometraje.

Otro criterio utilizado fue el de eliminar vehículos cuyo año de lanzamiento fuero inferior a los 2000, pues como apunta esta tabla: 

![info2](https://firebasestorage.googleapis.com/v0/b/produccion-fotografica-512c5.appspot.com/o/infoAti2.png?alt=media&token=19e6d377-3f42-40f2-a323-1d2aa2304ae9&_gl=1*2r32e9*_ga*MTIxMjg0MzYwOS4xNjg0Nzg5MTk2*_ga_CW55HF8NVT*MTY5NjU1NTMwNS4yMS4xLjE2OTY1NTUzNTguNy4wLjA.)

Existe atipicidad en ese rango de años en relación a los otros vehículos
![info3](https://firebasestorage.googleapis.com/v0/b/produccion-fotografica-512c5.appspot.com/o/infoAti3.png?alt=media&token=4fcd614e-edd6-4fa3-a374-3782af8bdcf1&_gl=1*17h5z7a*_ga*MTIxMjg0MzYwOS4xNjg0Nzg5MTk2*_ga_CW55HF8NVT*MTY5NjU1NTMwNS4yMS4xLjE2OTY1NTUzNjcuNTkuMC4w)

Es a partir de ese año donde se encuentra la mayoría de los carros tanto nuevos como usados.


**Valores repetidos:**
Al aplicar la función validadora de registros repetidos, se puede verificar que no existen registros de dicha naturaleza:
![enter image description here](https://firebasestorage.googleapis.com/v0/b/produccion-fotografica-512c5.appspot.com/o/infoRep.png?alt=media&token=cf1dc8e6-43ae-4778-84dc-f474f6f38679&_gl=1*1tdnifw*_ga*MTIxMjg0MzYwOS4xNjg0Nzg5MTk2*_ga_CW55HF8NVT*MTY5NjU1NTMwNS4yMS4xLjE2OTY1NTUzNzYuNTAuMC4w)


**Formato de valores:**
Respecto al formato de los valores, se detecta que el campo de fecha, su formato no es de tipo date, sino object:

![enter image description here](https://firebasestorage.googleapis.com/v0/b/produccion-fotografica-512c5.appspot.com/o/infoFormat.png?alt=media&token=340010ac-4df0-4097-b1ae-9375e0be9b50&_gl=1*lro8hj*_ga*MTIxMjg0MzYwOS4xNjg0Nzg5MTk2*_ga_CW55HF8NVT*MTY5NjU1NTMwNS4yMS4xLjE2OTY1NTUzNzEuNTUuMC4w)

Por ende, se aplicará la corrección correspondiente. En los demás campos se consideran que el tipo de datos es el adecuado.




