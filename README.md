Cada columna del comando D, muestra los rangos de memoria gaurdadas desde la direccion de 0DAB los grupos de datos hexadecimales, y los puntos son datos no imprimibles de ASCII por su valor


El comando D es el que nos muestra el resultado sin modificar nada, nos permite tener una verificacion segura de la operacion de E, invocar E300 no es seguro porque ese comando es suceptible a cualquier input entonces si no se tiene cuidado puede cambiar espacio de memoria, mientras que F no muestra resultados sino que es el que rellena informacion en cierto rango que sobrescribiria lo anterior, y el comando D es el que garantiza solo la lectura de los datos asi que no genera problemas de sobrescritura de datos


El direccionamiento de memoria de MOV AX [0300] requiere un ciclo mas porque necesita ubicar la direccion de 0300 y extraer el dato que esta en esa direccion en vez de ser solamente un dato sencillo, y en un escenario de direccionamiento directo seria mejor cuando los datos sean dinamicos o cambiables sin constantes porque permite leer cuanto cambian en tiempo de ejecucion y finalmente al ejecutra U con el rango que cada combinacion es que los codigos hexadecimales son traudcibles del binario y ver que se cambio la direccionamiento de A

Iteración Instrucción EjecutadaAX despuésCX despuésIP siguiente LOOP salta
Pre-bucle MOV AX, 0000 0000 Previo 0103 -
Pre-bucleMOV CX, 0004 0000 0004 0106 -
1ADD AX, 0002 0002 0004 0109 -
1LOOP 0106 0002 0003 0106 Si
2 ADD AX, 0002 0004 0003 0109 -
2 LOOP 0106 0004 0002 0106 si
3 ADD AX, 0002 0006 0002 0109 -
3 LOOP 0106 0006 0001 0106 Sí
4 ADD AX, 0002 0008 0001 0109 -
4 LOOP 0106 0008 0000 010B No
Fin INT 20 0008 0000 Terminado -


el recomendable es el del loop del paso 6 porque esta mas optimizado por los bytes del codigo, porque se codifica en solo E2 FB, en vez del otro que requiere 3 bytes, en cambio el DEC/JNZ se puede utilizar para situaciones mas complejas o cuando no se necesite salir del loop por contador sino por alguna condicion logica, y al usar el comando U podemos ver que en el primero inicia con 0100 a 010B osea 12 bytes mas el INT 20, mientras que el otro va desde 0200 al 020D, que son 14 Bytes.

TABLA DEC/JNZ

IteraciónInstrucción EjecutadaAX despuésCX despuésIP siguiente condicion jnz
MOV AX, 0000 0000 Previo 0203 -
Inicialización MOV CX, 0004 0000 0004 0206 -
1 ADD AX, 0002 0002 0004 0209 -
1 DEC CX 0002 0003 020A -
1 JNZ 0206 0002 0003 0206 si (ZF = 0, CX ≠ 0)
2ADD AX, 0002 0004 0003 0209 -
2DEC CX 0004 0002 020A -
2JNZ 0206 0004 0002 0206 Sí (ZF = 0, CX ≠ 0)
3ADD AX, 0002 0006 0002 0209 -
3DEC CX 0006 0001 020A -
3JNZ 0206 0006 0001 0206 Sí (ZF = 0, CX ≠ 0)
4ADD AX, 0002 0008 0001 0209 -
4DEC CX 0008 0000 020A - (Se activa ZF = 1)
4JNZ 0206 0008 0000 020C No (ZF = 1, CX = 0)
Fin INT 20 0008 0000 Terminado -


el comando G 20C es mas practico que G porque elimina el paso a paso y muestra el resultado luego de la operacion y no tener que pulsar T todas las veces necesarias para completarlo aunque se pierde la informacion entre paso y paso, y solamente fue necesario lo de los T para crear las tablas y solo t lo ofrece porque es un salto de paso a paso para ver que ocurre en cada iteracion, y al terminar con G 20C podemos usar el R para ver como termino y el estado actual del AX 