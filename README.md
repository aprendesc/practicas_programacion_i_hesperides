# Prácticas de Programación I · Universidad de las Hespérides

## Instalación breve

Necesitas Python 3.12. Desde la raíz del repositorio crea un entorno aislado:

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyter lab
```

En Windows, activa el entorno con `.venv\Scripts\activate` en lugar de `source`.
En JupyterLab selecciona el kernel **Python 3** del entorno y abre un notebook de `workshop/tareas/`.
Si ya tienes otro entorno, puedes usar un nombre de carpeta diferente en el primer comando y activarlo.

## Prácticas

Las prácticas están agrupadas por capítulos en `workshop/tareas/capitulo_*/`. La numeración de práctica mantiene el recorrido recomendado de la lista siguiente, también cuando un ejercicio integra contenidos de varios capítulos.

Completa el código iniciado. Los objetivos y pequeñas indicaciones están en cada enunciado; las referencias teóricas son opcionales. Ejecuta en orden desde la carpeta del notebook. No se incluyen comprobaciones automáticas: verifica los resultados de tu código. Una celda posterior puede fallar mientras un hueco siga sin completar.

- [01 · Valores, variables y operaciones](workshop/tareas/capitulo_07/practica_01_valores_variables_y_operaciones.ipynb)
- [02 · Colecciones y acceso a datos](workshop/tareas/capitulo_07/practica_02_colecciones_y_acceso_a_datos.ipynb)
- [03 · Condiciones y decisiones](workshop/tareas/capitulo_08/practica_03_condiciones_y_decisiones.ipynb)
- [04 · Bucles, contadores y acumuladores](workshop/tareas/capitulo_08/practica_04_bucles_contadores_y_acumuladores.ipynb)
- [05 · Funciones pequeñas y composición](workshop/tareas/capitulo_09/practica_05_funciones_pequenas_y_composicion.ipynb)
- [06 · Leer, calcular y guardar](workshop/tareas/capitulo_12/practica_06_leer_calcular_y_guardar.ipynb)
- [07 · Iteradores y generadores](workshop/tareas/capitulo_10/practica_07_iteradores_y_generadores.ipynb)
- [08 · Módulos y errores concretos](workshop/tareas/capitulo_11/practica_08_modulos_y_errores_concretos.ipynb)
- [09 · Primeros pasos con Pandas](workshop/tareas/capitulo_13/practica_09_primeros_pasos_con_pandas.ipynb)
- [10 · Relacionar y resumir tablas](workshop/tareas/capitulo_14/practica_10_relacionar_y_resumir_tablas.ipynb)

Los datos de práctica están incluidos y son pequeños. Los archivos `resultado_local.txt` y `calculos_local.py`, cuando se utilizan, se crean junto al notebook; puedes borrarlos para repetir.

## Exámenes

`workshop/examenes/practico/` y `workshop/examenes/teorico/` contienen los exámenes cuando se ponen a disposición. De momento no hay exámenes publicados en estas carpetas; `.gitkeep` conserva su estructura en Git.

## Otros materiales

Las clases síncronas existentes, cuando las haya, permanecen en `workshop/clases_sincronas/`. No se han reconstruido como parte de estas prácticas.
