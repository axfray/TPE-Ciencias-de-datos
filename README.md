# Trabajo Práctico Especial — Fundamentos de la Ciencia de Datos (2026)

## CKD-NHANES 2021-2023: enfermedad renal crónica por estadios

**Grupo 39:** Simón Campos Madarieta · Axel Ferreyra · Joaquín Fromm

Análisis exploratorio, limpieza de los datos y validación de seis hipótesis sobre el conjunto CKD-NHANES 2021-2023.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `TPE_CKD_NHANES_GRUPO39.ipynb` | Notebook con todo el análisis, organizada en secciones |
| `CKD_NHANES_2021_2023.csv` | Archivo de datos |
| `Informe_TPE_CKD_NHANES_GRUPO39.pdf` | Informe con los hallazgos y las conclusiones |
| `requirements.txt` | Librerías y versiones exactas del ambiente de PIP |
| `README.md` | Este archivo |

## Requisitos

- **Python 3.13**, la versión con la que se generó el ambiente. También funciona con Python 3.12.
- **pip**, que viene incluido con Python.
- **Un entorno para abrir notebooks de Jupyter.** La forma recomendada es **Visual Studio Code** con las extensiones **Python** y **Jupyter** de Microsoft. Como alternativa, **JupyterLab**, que se instala junto con las librerías del paso 4.
- Conexión a internet solo para instalar las librerías. La ejecución de la notebook no la necesita.

## Instalación

### 1. Descargar el repositorio

Clonarlo con git:

```
git clone <URL de este repositorio>
```

O descargarlo como ZIP desde GitHub (botón *Code* → *Download ZIP*) y descomprimirlo.

Todos los comandos siguientes se ejecutan en una terminal **posicionada en la carpeta del repositorio**: la que contiene la notebook, el CSV y el `requirements.txt`.

- **Con VS Code:** abrir la carpeta con *File* → *Open Folder...* y abrir la terminal integrada con *Terminal* → *New Terminal*. La terminal ya queda posicionada en la carpeta del repositorio. En Windows, elegir el Símbolo del sistema desde la flecha junto al botón **+** del panel de la terminal → *Command Prompt*.
- **Sin VS Code:** abrir una terminal del sistema y posicionarse en la carpeta del repositorio.

### 2. Crear el ambiente virtual

```
python -m venv venv
```

Se crea una carpeta llamada `venv` dentro del repositorio. En ella se instalan las librerías, aisladas de las del resto del sistema.

### 3. Activar el ambiente virtual

En **Windows**, desde el Símbolo del sistema (cmd):

```
venv\Scripts\activate
```

En **Linux o macOS**:

```
source venv/bin/activate
```

Si se activó correctamente, la línea de la terminal empieza con `(venv)`.

### 4. Instalar las librerías

Con el ambiente activado:

```
pip install -r requirements.txt
```

Instala la versión exacta de cada librería que usa la notebook (pandas, numpy, matplotlib, seaborn, scipy, statsmodels y scikit-learn), además de `ipykernel`, que permite ejecutar la notebook con el Python del ambiente, y de JupyterLab. Si terminó bien, la última línea empieza con `Successfully installed`.

## Ejecución

### Opción A: Visual Studio Code (recomendada)

1. **Abrir la notebook.** Con la carpeta del repositorio abierta en VS Code, abrir `TPE_CKD_NHANES_GRUPO39.ipynb` desde el explorador de archivos de la izquierda. Si VS Code sugiere instalar las extensiones Python o Jupyter, aceptar.
2. **Elegir el kernel.** Hacer clic en *Select Kernel*, arriba a la derecha de la notebook → *Python Environments...* → el ambiente `venv` (aparece como `venv (Python 3.13...)` o con la ruta a la carpeta `venv`). Si VS Code ya lo eligió solo, arriba a la derecha se ve `venv`.
3. **Ejecutar.** Hacer clic en *Run All*, en la barra superior de la notebook.

### Opción B: JupyterLab

1. **Abrir JupyterLab.** En la terminal, con el ambiente activado:

   ```
   jupyter-lab
   ```

   JupyterLab se abre en el navegador. Desde el panel de archivos de la izquierda, abrir `TPE_CKD_NHANES_GRUPO39.ipynb`.
2. **Ejecutar.** En el menú *Run*, elegir *Run All Cells*.
3. **Cerrar.** Al terminar, cerrar JupyterLab con `Ctrl + C` en la terminal y confirmar.

### Resultado esperado (en las dos opciones)

- La celda que verifica el archivo de datos muestra: `El archivo CKD_NHANES_2021_2023.csv está disponible`.
- Al terminar, todas las celdas de código tienen su número de ejecución y ninguna muestra un mensaje de error.
- La ejecución genera en la misma carpeta el archivo `preprocessed_dataset_v1.pkl`, una copia del dataset limpio (sección 2.15). No forma parte del repositorio: se vuelve a generar en cada ejecución.

### Al terminar

Desactivar el ambiente en la terminal:

```
deactivate
```

La instalación se hace una sola vez. Para volver a ejecutar la notebook:
- en VS Code, alcanza con abrir la carpeta y la notebook, porque el kernel elegido queda guardado;
- en JupyterLab, hay que repetir la activación (paso 3) y la opción B.

## Problemas frecuentes

- **No se reconoce el comando `python`.** En Linux y macOS suele llamarse `python3`, y en Windows puede usarse `py`. En ese caso, el paso 2 queda `python3 -m venv venv` o `py -m venv venv`.
- **Hay varias versiones de Python instaladas.** Se puede elegir la versión al crear el ambiente: `python3.13 -m venv venv` en Linux y macOS, o `py -3.13 -m venv venv` en Windows.
- **En Debian o Ubuntu, el paso 2 informa que falta `ensurepip`.** Hay que instalar el módulo de ambientes virtuales del sistema: `sudo apt install python3-venv`.
- **En Windows, PowerShell no permite activar el ambiente.** Usar el Símbolo del sistema (cmd), como en el paso 3. En VS Code se elige desde la flecha junto al botón **+** del panel de la terminal → *Command Prompt*.
- **La línea de la terminal no empieza con `(venv)`.** El ambiente no está activado, y las librerías se instalarían fuera de él. Activarlo (paso 3) antes de instalar.
- **VS Code no muestra el ambiente `venv` en la lista de kernels.** Elegir *Select Another Kernel...* → *Python Environments...* y, si no aparece, recargar la ventana (*Developer: Reload Window* desde la paleta de comandos, `Ctrl + Shift + P`). El ambiente tiene que estar creado dentro de la carpeta abierta en VS Code.
- **VS Code ofrece instalar `ipykernel` al ejecutar.** El kernel elegido no es el del ambiente `venv`, que ya lo trae instalado. Volver al paso 2 de la opción A y elegir `venv`.
- **La notebook no encuentra el archivo de datos.** `CKD_NHANES_2021_2023.csv` tiene que estar en la misma carpeta que la notebook y con ese nombre exacto. La celda de verificación lista los archivos de la carpeta para revisarlo.
- **Otro editor compatible con notebooks.** También se puede usar, eligiendo como kernel el intérprete de Python de la carpeta `venv`.

## Versiones

El archivo `requirements.txt` se generó con `pip freeze` a partir de un ambiente con Python 3.13, y fija la versión exacta de cada librería y de sus dependencias. Instalar exactamente esas versiones asegura que los resultados coincidan con los del informe.

| Librería | Versión |
|---|---|
| pandas | 2.2.3 |
| numpy | 2.4.6 |
| matplotlib | 3.10.0 |
| seaborn | 0.13.2 |
| scipy | 1.16.3 |
| statsmodels | 0.15.0 |
| scikit-learn | 1.6.1 |
| ipykernel | 6.17.1 |
| jupyterlab | 4.6.6 |
