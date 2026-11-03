# Project Map

```text
Repositorios
├── Upstream: aprendesc/practicas_programacion_i_hesperides   (https://github.com/aprendesc/practicas_programacion_i_hesperides.git; solo lectura de configuración, no se hace fetch ni push)
│   └── develop
└── Downstream: aprendesc/practicas_programacion_i_hesperides
    ├── develop                  [A: rama del mapa, = a4b4940 al escribirlo]
    └── (sin rama de issue)      [B: no aplicable; la rama de issue feature/87 es de W2]
```

Repositorio base `hesperides/docs/asignatura_programacion_i/08_practicas/practicas_programacion_i_hesperides`. Mapa documental: este repositorio no es una aplicación con `main`, sino material de clase en Jupyter; sus mecánicas son las cinco cosas que se hacen con él. Entradas y salidas de disco y red proceden de README, `.gitignore`, `scripts/promote-to-upstream` y `publication.py`; no se ha ejecutado ninguna.

## Contexto

Este repositorio es el cuaderno de prácticas de Programación I de la Universidad de las Hespérides. El README presenta diez prácticas que van de valores y colecciones a iteradores, módulos, excepciones, procesamiento de archivos de texto y datos tabulares con Pandas. Son huecos por completar y se ejecutan en orden desde la carpeta del notebook.

Cada práctica tiene dos caras. La **edición del alumno** es la que se versiona y se publica: enunciados con huecos y datos de práctica. La **edición del profesor** (soluciones, guion, constructores) vive en `profesor/`, que `.gitignore` excluye, para que nunca se publique por accidente. Los exámenes aún no existen: `examenes/` conserva la carpeta con un `.gitkeep`. Por último, `scripts/promote-to-upstream` prepara en local una rama sin las rutas privadas de metodología para una contribución a upstream, y no hace push.

---

## Storage

Rutas relativas a la raíz del repositorio. «Versionado» significa seguido por Git en `develop`; «ignorado» significa excluido por `.gitignore`.

```text
Storage
└── Local · practicas_programacion_i_hesperides/
    ├── practicas/capitulo_*/        [versionado] 18 notebooks practica_NN_*.ipynb + datos/
    ├── examenes/.gitkeep            [versionado] sin exámenes publicados
    ├── requirements.txt · README.md [versionado] entorno e instrucciones
    ├── scripts/promote-to-upstream  [versionado] preparación de contribución a upstream
    ├── context/{issues,sessions}/   [versionado] contratos y resúmenes; context/project-map.md es este documento
    ├── .githooks/                   [versionado] salvaguardas del clon
    ├── profesor/                    [ignorado, solo local]
    │   └── practicas/capitulo_07..14/ + calculos_local.py + resultado_local.txt
    ├── .venv/                       [ignorado, generado por Entorno]
    └── publish/<rama>               [rama Git local, generada por Promoción; no es carpeta]
```

Entorno crea `.venv/` y el kernel; las prácticas leen de `practicas/` y escriben solo copias locales del alumno; la edición del profesor escribe en `profesor/`; Promoción solo crea una rama local `publish/<rama>`.

---

## Diff

Sin diff. El mapa describe `develop` en downstream `aprendesc/practicas_programacion_i_hesperides`; no hay una rama de issue contra la que compararlo. La rama `feature/87-practicas-notebook-todas-las-asignaturas` pertenece a W2 y su diff se calculará en el delta de esa rama.

## Mapa global

Las **cinco mecánicas** del repositorio, cada una un comando o acción independiente. Ninguna se encadena automáticamente con la anterior.

```text
LVL LOW · REPOSITORIO DOCUMENTAL
Pruebas: sin pruebas funcionales (context/tests/ no existe)

Entorno · README «Instalación breve»
+------------+     +-----------------------+     +----------------------+     +----------------------+
| (1) Clonar | --> | (2) Instalar en .venv | --> | (3) Registrar kernel | --> | (4) Abrir JupyterLab |
+------------+     +-----------------------+     +----------------------+     +----------------------+

1 <- red: repositorio downstream
2 <- red: paquetes Python
2 -> disco: .venv/
3 -> disco: kernel Jupyter

Prácticas · practicas/capitulo_*
+---------------------+     +----------------------+     +--------------------------+
| (1) Abrir enunciado | --> | (2) Completar huecos | --> | (3) Ejecutar y verificar |
+---------------------+     +----------------------+     +--------------------------+

1 <- disco: notebook de práctica y datos
3 -> disco: notebook completado del alumno

Edición del profesor · profesor/ (ignorado)
+-------------------------+     +----------------------------------+
| (1) Preparar soluciones | --> | (2) Guardar edición del profesor |
+-------------------------+     +----------------------------------+

1 <- disco: enunciados de practicas/capitulo_07..14
2 -> disco: soluciones en profesor/practicas/capitulo_07..14 (solo local)

Exámenes · examenes/
+----------------------------------+
| (1) Reservar carpeta de exámenes |
+----------------------------------+

1 -> disco: examenes/.gitkeep

Promoción a upstream · scripts/promote-to-upstream
+----------------------------------+     +----------------------------+     +--------------------------+
| (1) Leer develop y rama upstream | --> | (2) Retirar rutas privadas | --> | (3) Crear publish/<rama> |
+----------------------------------+     +----------------------------+     +--------------------------+

1 <- disco: develop y rama upstream de seguimiento
3 -> disco: rama local publish/<rama>
```

Las líneas bajo cada diagrama usan el número de la caja: `n ->` es una salida y `n <-` una entrada; `disco` y `red` indican el tipo de intercambio. Solo Entorno usa red. El orden natural es Entorno, Prácticas, Edición del profesor y Promoción; los exámenes están reservados pero vacíos.

## Mecánicas principales

### Entorno · README «Instalación breve»

Prepara una instalación aislada: clona el repositorio, crea `.venv/` con Python 3.12, instala `requirements.txt`, registra un kernel de Jupyter con el nombre que verá el alumno y abre JupyterLab. Aislar el entorno evita mezclar las dependencias de la práctica con las del sistema; el coste es una instalación por repositorio (dependencias mínimas).

```text
LVL LOW
Entrada: README.md · «Instalación breve»
Prueba: sin prueba funcional (context/tests/ no existe)
Configuración
└── Entorno de ejecución
    ├── requirements.txt = jupyterlab>=4,<5 · pandas>=2.2,<4
    ├── python = sin .python-version
    └── kernel = Python (Programación I)

+------------------------+     +----------------------------+     +----------------------+     +----------------------+
| (1) Clonar repositorio | --> | (2) Crear .venv e instalar | --> | (3) Registrar kernel | --> | (4) Abrir JupyterLab |
+------------------------+     +----------------------------+     +----------------------+     +----------------------+

1 <- red: repositorio downstream (git clone)
2 <- red: paquetes de requirements.txt
2 -> disco: entorno .venv/
3 -> disco: kernel Jupyter dentro de .venv/
```

---

### Prácticas · `practicas/capitulo_*/`

El alumno abre un notebook, completa los huecos y ejecuta las celdas en orden desde la carpeta del notebook. No hay comprobaciones automáticas: el propio alumno verifica sus resultados, y una celda posterior puede fallar mientras un hueco siga sin completar. La numeración `practica_NN` sigue el recorrido recomendado del README, no el orden de las carpetas de capítulo.

```text
LVL LOW
Entrada: practicas/capitulo_*/practica_NN_*.ipynb (18 notebooks versionados)
Prueba: sin prueba funcional (context/tests/ no existe)
Configuración
└── Notebook de práctica
    └── sin parámetros: el alumno completa huecos y ejecuta en orden

+---------------------+     +----------------------+     +--------------------------+
| (1) Abrir enunciado | --> | (2) Completar huecos | --> | (3) Ejecutar y verificar |
+---------------------+     +----------------------+     +--------------------------+

1 <- disco: notebook de práctica y practicas/capitulo_{00_base_python,12,13,14}/datos/
2 -> disco: notebook completado (copia del alumno)
3 -> disco: resultados locales (resultado_local.txt, calculos_local.py)
```

---

### Edición del profesor · `profesor/`

El profesor guarda aquí, fuera de Git, las soluciones de las prácticas de los capítulos 07 a 14. `profesor/` está en `.gitignore`. A diferencia de las otras dos prácticas, no hay constructores ni validadores: la preparación es manual. Junto a las soluciones hay residuos locales (`calculos_local.py`, `resultado_local.txt`).

```text
LVL LOW
Entrada: Script: sin scripts: profesor/ contiene solo soluciones y residuos locales
Prueba: sin prueba funcional (context/tests/ no existe); sin validación ejecutada
Configuración
└── profesor/practicas/
    └── capitulo_07..14/   (soluciones por capítulo)

+-------------------------+     +----------------------------------+
| (1) Preparar soluciones | --> | (2) Guardar edición del profesor |
+-------------------------+     +----------------------------------+

1 <- disco: enunciados de practicas/capitulo_07..14
2 -> disco: soluciones en profesor/practicas/capitulo_07..14 (solo local)
```

---

### Exámenes · `examenes/`

Carpeta reservada para el examen práctico y el teórico. Hoy solo contiene `.gitkeep` para que Git conserve la carpeta; no hay exámenes publicados.

```text
LVL LOW
Entrada: examenes/ (carpeta reservada)
Prueba: sin prueba funcional (context/tests/ no existe)
Configuración
└── examenes/
    └── .gitkeep = única entrada versionada

+----------------------------------+
| (1) Reservar carpeta de exámenes |
+----------------------------------+

1 -> disco: examenes/.gitkeep
```

---

### Promoción a upstream · `scripts/promote-to-upstream`

Prepara una contribución a upstream sin tocar la copia de trabajo: toma un commit confirmado (por defecto `develop`) y la rama de seguimiento de una rama upstream que ya existe, retira las rutas privadas de metodología y sus menciones en los `.gitignore`, y crea localmente `publish/<rama>`. No hace fetch, push ni checkout, y no sobrescribe una rama `publish/` existente; revisar esa rama y publicarla, si procede, requiere autorización explícita aparte. El hook `pre-push` comprueba después que el árbol propuesto no contenga rutas privadas.

```text
LVL LOW
Entrada: scripts/promote-to-upstream <rama-upstream-existente> [fuente=develop]
Prueba: sin prueba funcional (context/tests/ no existe)
Configuración
└── .githooks/clone-hooks/publication.py prepare
    ├── fuente = develop (por defecto)
    └── rutas privadas = context, .githooks, .claude, .codex, skills, AGENTS.md, SKILL.md…

+----------------------------------+     +----------------------------+     +--------------------------+
| (1) Leer develop y rama upstream | --> | (2) Retirar rutas privadas | --> | (3) Crear publish/<rama> |
+----------------------------------+     +----------------------------+     +--------------------------+

1 <- disco: commit fuente y rama upstream de seguimiento (sin fetch)
3 -> disco: rama local publish/<rama> (sin push ni checkout)
```

---

## Anomalías y límites

- Sin pruebas funcionales: `context/tests/` no existe y no se han ejecutado notebooks, constructores ni validadores. El mapa describe lo que dicen los archivos, no un comportamiento observado.
- `practicas/` versiona 18 notebooks pero el README lista 10: los de `capitulo_00_base_python` y `capitulo_01..05` (8 notebooks) comparten nombre con las prácticas de Fundamentos de Python y no figuran en el README. No se ha comparado su contenido; queda para decidir con el usuario si pertenecen aquí.
