Tiempos:
sinhilos.py:

1 - 5.17s
2 - 5.16s
3 - 5.17s
4 - 5.17s
5 - 5.18s
6 - 5.22s
7 - 5.17s
8 - 5.17s
9 - 5.15s
10 - 5.18s

conhilos.py:

1 - 4.02
2 - 4.02
3 - 4.04
4 - 4.03
5 - 4.03
6 - 4.01
7 - 4.01
8 - 4.02
9 - 4.02
10 - 4.02

Respuesta Pto_1A:
al principio no era muy predecible, eran las primeras veces que ejecutaba los codigos, pero ya cuando pasaron 5 veces con el mismo tiempo cambiando unas pocas sentecimas de segundos, si se volvia bastante predecible, y como analisis propio, se nota cuando una aplicacion usa hilos o no (con hilos es mas rapida debido al paralelismo de ejecucion)

Respuesta Pto_1B:
se comparo entre 3 compañeros (incluyendome) y a los 3 nos dio lo mismo en ambos programas, un promedio de 5s en "sinhilos.py" y un promedio de 4s en "conhilos.py".

Respuesta Pto_1C:
(sin descomentar) el codigo se ejecuta bien, rapido, con un promedio de 0,016Segs.
(descomentado) el codigo se siguio ejecutando bien, solo que ahora tarda mas tiempo, un promedio de 2.45segs.	
se entiende que esto ocurrio debido a que el planificador de tareas tuvo algun problema o asigno mal o a destiempo los recursos de procesamiento a los hilos del programa, por eso el race condition fue peor en una situacion que en la otra
