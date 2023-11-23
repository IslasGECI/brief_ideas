Probamos dos maneras de calcular un estadístico proveniente de diferentes distribuciones.
La intención es saber si existe diferencia entre los estadísticos.

Generamos cinco distribuciones normales de tamaño 2,000 con diferentes medias y la misma desviación estándar.
En el primer método generamos 2,000 réplicas del promedio tomando un elemento sin reemplazo de cada distribución.
En el otro método concatenamos las distribuciones originales en una nueva meta distribución e hicimos un bootstrap tradicional.
Con bootstrap tradicional nos referimos a cada muestra bootstrap conserva el tamaño original y que la distribución bootstrap es de 2,000 elementos.

Con el primer método calculamos una distribución de 2,000 réplicas del promedio.
En el segundo ejemplo generamos una distribución bootstrap del promedio de la meta distribución.
El promedio de las distribuciones de ambos métodos son iguales.
La desviación estándar del primer método es mayor a la del segundo método.

La desviación del ejemplo 1 incrementa debido a que disminuimos el número de elementos con el que calculamos las réplicas.


## Referencias
- [`resample_clt_example`](https://github.com/IslasGECI/resample_clt_example)
