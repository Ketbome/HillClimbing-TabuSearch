# Gestión de aterrizaje de UAVs

Este proyecto tiene como objetivo la gestión eficiente de aterrizaje y descarga de minerales en colonias espaciales utilizando UAVs (Unmanned Autonomous Vehicles) en el año 2535.

## Descripción del problema

En el año 2535, la humanidad ha logrado crear artificialmente atmósferas, lo que ha permitido establecer colonias espaciales en varios lugares. Cada una de estas colonias requiere la recolección de diferentes tipos de minerales para construir infraestructura adicional y garantizar la supervivencia. Como jefe general de la autonomía de las colonias IO, Europa, Deimos y Titán, es tu responsabilidad asignar tiempos de aterrizaje a los UAVs para coordinar la recolección de recursos.

A continuación, se presentan algunas consideraciones importantes:

- Existirán un conjunto D de UAVs. Cada UAV tendrá un tiempo más temprano de ater-
  rizaje Ek , más tarde de aterrizaje Lk y uno preferente Pk (Ek ≤ Pk ≤ Lk ) ∀k = 1, ..., D.
  Existirá un tiempo de separación mı́nimo τij entre el UAV i y un UAV j con i ̸= j (por
  la diferencia de tamaño entre ellos). Lo anterior implica, por ejemplo, que si el tiempo
  del primer UAV es Ti y del segundo Tj , con Ti < Tj , entonces Tj ≥ Ti + τij .

- Por cada unidad sobre (bajo) el tiempo preferente Pk se penalizará en 1 el costo. El
  objetivo del problema es minimizar dicho costo.

- Considere que cada archivo es un caso de prueba distinto.

El archivo a leer tiene el siguiente formato:
Numero de UAVs
P a r a c a d a UAV i ( i = , 1 . . . , D ) :
T . mas temprano de a terrizaje , T. preferente ,
T . mas tarde de a terrizaje ( todo en la misma linea )
Para cada UAV j ( j = 1 , . . . , D ) :
Tiempo de separacionre querido despues que i aterrice para que j aterrice
Hice un greedy determinista y uno estocastico que me da una solucion pero quiero mejorarla, necesito hacer un hill climbing que busque mejoras en la soluciones
Las soluciones esán hechas en python donde se tiene un greedy determinista y uno estocástico y a partir de ellos se aplica hill climbing alguna mejora y mejor mejora, también tabu search

## Algoritmos implementados

En este proyecto, se han implementado tres algoritmos para abordar el problema de asignación de tiempos de aterrizaje de los UAVs:

1. Greedy determinista: Este algoritmo selecciona los tiempos de aterrizaje de los UAVs en orden ascendente según su preferencia. No tiene en cuenta las restricciones de tiempo de separación ni las penalizaciones asociadas. Proporciona una solución rápida pero no necesariamente óptima.

2. Greedy estocástico: Este algoritmo selecciona los tiempos de aterrizaje de los UAVs de forma aleatoria, teniendo en cuenta las restricciones de tiempo de separación. Este si bien no mejora las soluciones del determinista, se utiliza para llegar a otras soluciones locales que pueden mejorar con los otros algoritmos.

3. Hill Climbing: Este algoritmo de búsqueda local busca mejorar la solución obtenida por los algoritmos greedy. Comienza con una solución inicial y realiza cambios locales en busca de una solución mejor. Si encuentra una mejora, continúa explorando en esa dirección. Sin embargo, puede quedar atrapado en óptimos locales y no garantiza la solución óptima global. Se utiliza un algoritmo de alguna mejora y mejor mejora.

4. Tabu Search: Algoritmo de exploración y explotación, para este caso la exploración se basa en buscar sectores cercanos a la solución principal, sacada por orden de tiempos preferenciales y hacer un swap entre vecinos, de manera que la solución no se repita, normalmente el algoritmo de Tabu Search en este caso debería ir guardando las modificaciones y que no se repitan dentro de un tiempo de manera de no bloquear la modificación. Por consiguiente se comienza a explotar en este caso se utilizó Hill Climbing para la explotación del espacio de solución encontrado.

## Cómo ejecutar los algoritmos

Para ejecutar los algoritmos, sigue estos pasos:

- Asegúrate de tener Python instalado en tu sistema.
- Clona este repositorio o descarga los archivos fuente.
- Ejecuta el archivo principal, `read.py`, utilizando el intérprete de Python.
- Sigue las instrucciones proporcionadas por el programa para seleccionar el algoritmo y el archivo de entrada.
- Utiliza el comando `python3 read.py t2_Titan.txt`
- El programa mostrará la solución obtenida y los costos asociados.
