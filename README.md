# Practico 3


## Ejercicio 1
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


## Ejercicio 2:

 ### Inciso A)

#intente hacerlo con un link hacia el archivo, no pude, agradeceria una aclaracion del proceso en un futuro

#include <pthread.h>
#include <stdio.h>
#include <stdlib.h>
#define NUMBER_OF_THREADS 2
#define CANTIDAD_INICIAL_HAMBURGUESAS 20
int cantidad_restante_hamburguesas = CANTIDAD_INICIAL_HAMBURGUESAS;
int turno = 0;


void *comer_hamburguesa(void *tid)
{
	while (1 == 1)
	{ 
		while(turno!=(int)tid);
    // INICIO DE LA ZONA CRÍTICA
		if (cantidad_restante_hamburguesas > 0)
		{
			printf("Hola! soy el hilo(comensal) %d , me voy a comer una hamburguesa ! ya que todavia queda/n %d \n", (int) tid, cantidad_restante_hamburguesas);
			cantidad_restante_hamburguesas--; // me como una hamburguesa
			turno = (turno + 1)% NUMBER_OF_THREADS;
		}
		else
		{
			printf("SE TERMINARON LAS HAMBURGUESAS :( \n");

			pthread_exit(NULL); // forzar terminacion del hilo
			
		}
    // SALIDA DE LA ZONA CRÍTICA   
	turno = (turno + 1)% NUMBER_OF_THREADS;
	}
}

int main(int argc, char *argv[])
{
	pthread_t threads[NUMBER_OF_THREADS];
	int status, i, ret;
	for (int i = 0; i < NUMBER_OF_THREADS; i++)
	{
		printf("Hola!, soy el hilo principal. Estoy creando el hilo %d \n", i);
		status = pthread_create(&threads[i], NULL, comer_hamburguesa, (void *)i);
		if (status != 0)
		{
			printf("Algo salio mal, al crear el hilo recibi el codigo de error %d \n", status);
			exit(-1);
		}
	}

	for (i = 0; i < NUMBER_OF_THREADS; i++)
	{
		void *retval;
		ret = pthread_join(threads[i], &retval); // espero por la terminacion de los hilos que cree
	}
	pthread_exit(NULL); // como los hilos que cree ya terminaron de ejecutarse, termino yo tambien.
}
 
 
 
 
 ### Inciso B)

![Captura de pantalla 2024-05-13 201320](https://github.com/Nicky066/ASO2024TPs/assets/166407614/ab7175d9-f7c0-4c60-bcbc-81486b38be42) 
