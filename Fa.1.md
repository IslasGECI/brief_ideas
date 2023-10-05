## Introducción
Generamos cinco distribuciones normales de tamaño 2000 con diferentes medias y la misma desviación estándar.
## Ejemplo 1
Promediamos tomando sin reemplazo un elemento de cada distribución.
De esta manera obtenemos una distribución de 2000 promedios.
## Ejemplo 2
Concatenamos las cinco distribuciones en una sola meta-distribución de tamaño 10000.
Hacemos remuestreo bootstrap tradicional, conservando el tamaño de la meta-distribución.
Con este procedimiento generamos 2000 réplicas bootstrap del promedio.
## Conclusión
El promedio de la distribución del ejemplo 1 y de las réplicas del ejemplo 2 son iguales.
La desviación estándar de la distribución en el ejemplo 1 es mayor a la de las réplicas del ejemplo 2.
Al disminuir el tamaño de las muestras bootstrap en el ejemplo 2, incrementamos su desviación estándar.
## Referencias
[resample_clt_example](https://github.com/IslasGECI/resample_clt_example)
