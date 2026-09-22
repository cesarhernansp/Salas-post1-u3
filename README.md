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