# Calculadora de dosis por gramaje (medicamentos sin prescripción)

Este proyecto implementa una calculadora de dosis basada en el peso del paciente, la posología (mg/kg/día) y la presentación del medicamento. Además, integra registro y consulta de medicinas, ordenamientos y búsquedas por gramaje.

## Flujo de uso (ejemplo real)

Ejemplo 1: Augmentine “125” suspensión (125/31.25 mg/5 ml)

Peso del paciente: 8 kg

Posología deseada: 40 mg/kg/día

Presentación: Suspensión

Dosis al día = 8 kg × 40 mg/kg/día = 320 mg/día

Frecuencia: 3 dosis/día (cada 8 h)

Concentración: 125 mg/5 ml → 25 mg/ml

Dosis por toma = 320 mg / 3 = 106.67 mg

Volumen por toma = 106.67 mg ÷ 25 mg/ml ≈ 4.28 ml cada 8 horas

Además, el sistema permite registrar medicamentos y ver listados por orden alfabético o por gramaje.

## Estructuras y módulos principales

Lista doblemente enlazada para registrar medicinas (alta, baja, consulta rápida a head y acceso a tail).

Ordenamiento (Merge Sort) para organizar medicinas por nombre (asc/desc).

Árbol binario de búsqueda (BST) para indexar por gramaje y localizar rápidamente mismas o similares concentraciones.

I/O: lectura/escritura desde/ hacia medicinas.csv.

En el código se incluyen funciones como: agregaMedicina, eliminaMedicina, obtenGramaje, ordenaMedicinasAsc/Desc, obtenPorGramaje, medicinasMismoGramaje, etc. (ver medicinas.h y reportes.h).

## Formato de datos

medicinas.csv

Nombre, mg
Ibuprofeno, 200
Ibuprofeno, 400
Paracetamol, 300

## Cálculos implementados

Dosis diaria (mg/día): peso_kg * posologia_mg_kg_dia

Dosis por toma (mg): mg_dia / dosis_por_dia

Volumen por toma (ml): mg_por_toma / (mg_por_ml), donde mg_por_ml = mg_en_envase / ml_en_envase

## Criterios SICT
SICT0302B — Toma decisiones

Estructura lineal seleccionada: Lista doblemente enlazada

Motivo: permite insertar siempre en O(1) al inicio (última medicina registrada accesible con rapidez), recorrer en ambos sentidos y, si se requiere, acceder a la primera añadida (tail).

Complejidad típica:

Búsqueda por valor: O(n) (recorrido y comparación).

Inserción en head: O(1).

Eliminación por valor: O(n) (búsqueda + unlink en O(1)).

Algoritmo de ordenamiento: Merge Sort (sobre lista)

Motivo: Es estable, tiene O(n log n) en el mejor/promedio/peor caso, y funciona muy bien sobre listas enlazadas (no requiere acceso aleatorio).

Uso: ordenar por nombre ascendente y descendente.

Árbol adecuado: BST por gramaje

Motivo: facilita búsquedas por valor (encontrar gramaje exacto o cercano) y listar por rangos.

Complejidad (BST no balanceado):

Inserción / búsqueda: promedio O(log n), peor O(n) (si se degrada).

En este problema la entrada suele venir desordenada, reduciendo la probabilidad de degeneración.

SICT0301B — Evalúa los componentes

Casos de prueba (archivo pruebas.cpp):

Lista doblemente enlazada:

Inserción en head, eliminación por valor, búsqueda.

Ordenamiento:

Merge Sort por nombre (asc/desc), verifica orden y estabilidad en empates.

Árbol (BST) por gramaje:

Inserción en BST, búsqueda exacta y por “mismo gramaje”, recorrido in-order.

Análisis de complejidad

Lista doblemente enlazada

Acceso por valor: O(n)

Inserción en head: O(1)

Eliminación por valor (buscar + unlink): O(n)

Ordenamiento (Merge Sort en lista)

Tiempo: O(n log n) en todos los casos

Espacio: O(log n) por recursión

Estable: Sí

BST por gramaje

Construcción (n inserciones): promedio O(n log n), peor O(n²)

Búsqueda/Inserción individual: promedio O(log n), peor O(n)

I/O

Lectura CSV: O(n)

Escritura CSV: O(n)

## SICT0303B — Implementa acciones científicas

Consultas útiles:

Búsqueda de medicinas por nombre (lista).

Reportes ordenados por nombre (asc/desc).

Consultas al BST: obtener por gramaje o listar con mismo gramaje.

Lectura de archivos: carga medicinas.csv al inicio.

Escritura de archivos: los nuevos registros se persisten en medicinas.csv para no recapturar cada ejecución.

## Interfaz (menú sugerido)

Registrar nueva medicina

Eliminar medicina

Buscar por nombre

Reporte ordenado (nombre asc/desc, Merge Sort)

Consultas por gramaje (BST)

Guardar cambios en medicinas.csv

Salir
