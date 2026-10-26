# Prácticas de Programación I · Universidad de las Hespérides

## Instalación breve

Necesitas Git y Python 3.12. Clona el repositorio y crea un entorno aislado:

```sh
git clone https://github.com/aprendesc/practicas_programacion_i_hesperides.git
cd practicas_programacion_i_hesperides
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m ipykernel install --prefix .venv --name practicas_programacion_i_hesperides --display-name "Python (Programación I)"
python -m jupyter lab
```

En Windows, activa el entorno con `.venv\Scripts\activate` en lugar de `source`.
En JupyterLab selecciona el kernel **Python (Programación I)** del entorno y abre un notebook de `practicas/`.

## Prácticas

Las prácticas están agrupadas por capítulos en `practicas/capitulo_*/`. La numeración de práctica mantiene el recorrido recomendado de la lista siguiente, también cuando un ejercicio integra contenidos de varios capítulos.

Completa el código iniciado. Los objetivos y pequeñas indicaciones están en cada enunciado; las referencias teóricas son opcionales. Ejecuta en orden desde la carpeta del notebook. No se incluyen comprobaciones automáticas: verifica los resultados de tu código. Una celda posterior puede fallar mientras un hueco siga sin completar.

- [01 · Valores, variables y operaciones](practicas/capitulo_07/practica_01_valores_variables_y_operaciones.ipynb)
- [02 · Colecciones y acceso a datos](practicas/capitulo_07/practica_02_colecciones_y_acceso_a_datos.ipynb)
- [03 · Estructuras condicionales](practicas/capitulo_08/practica_03_estructuras_condicionales.ipynb)
- [04 · Iteración, contadores y acumuladores](practicas/capitulo_08/practica_04_iteracion_contadores_y_acumuladores.ipynb)
- [05 · Funciones y composición](practicas/capitulo_09/practica_05_funciones_y_composicion.ipynb)
- [06 · Procesamiento de archivos de texto](practicas/capitulo_12/practica_06_procesamiento_de_archivos_de_texto.ipynb)
- [07 · Iteradores y generadores](practicas/capitulo_10/practica_07_iteradores_y_generadores.ipynb)
- [08 · Módulos y manejo de excepciones](practicas/capitulo_11/practica_08_modulos_y_manejo_de_excepciones.ipynb)
- [09 · Carga, selección y limpieza de datos con Pandas](practicas/capitulo_13/practica_09_carga_seleccion_y_limpieza_de_datos_con_pandas.ipynb)
- [10 · Combinación y agregación de datos con Pandas](practicas/capitulo_14/practica_10_combinacion_y_agregacion_de_datos_con_pandas.ipynb)

Los datos de práctica están incluidos en el repositorio. Los archivos `resultado_local.txt` y `calculos_local.py`, cuando se utilizan, se crean junto al notebook; puedes borrarlos para repetir.

## Exámenes

`examenes/` contiene únicamente `.gitkeep` para conservar la carpeta en Git. No hay exámenes publicados. Aquí aparecerán los exámenes práctico y teórico cuando se pongan a disposición.
