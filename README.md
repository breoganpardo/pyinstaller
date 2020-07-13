# How to use pyinstaller with external libraries?
This repo is just to keep track of all steps I took to get the pyinstaller properly work with external libraries

## 1. Video to get general overview
Generally whit this video is enough:
https://www.youtube.com/watch?v=UZX5kH72Yx4

However, if you need to import external libraries (pip install list),pyinstaller will through the following error:
NameError: name '####library name####' is not defined

## 2.¿Cómo hacer para que pandas entre en pyinstaller?
### 2.1. Faltan librerías en python en consola
  Ejecuta archivo .py desde cmd
    Ejecuta tu python script desde el comand line (cmd).
    Para ello, abre el CMD, vete a la ruta donde tengas el .py. Ejecuta como "python _______.py"
    Si te sale error de que library not found o algo así, hay que installar las librerias en python con: python -m pip install pandas
    Itera hasta que todas las librerias estén instaladas.
    
### 2.2. Error-->ModuleNotFoundError: No module named 'sklearn.utils._cython_blas'
Si a pesar de haber instalado una librería (pandas por ejemplo) pyinstaller sigue sin reconocerla, toca modificar los archivos de hook_pandas o la librería que sea dentro de pyinstaller.
Vete a tu ruta de python, similar a esta:(c:/~/Python3.6/Lib/site-package/PyInstaller/hooks),
Busca hook-pandas.py
Introduce en la sección "hiddenimports" lo siguiente: 
hiddenimports = ['pandas._libs.tslibs.timedeltas','pandas._libs.tslibs.nattype','pandas._libs.tslibs.np_datetime','pandas._libs.skiplist']

Other libraries hook files modifications:
* Sklearn, Pandas, Scipy:http://datasciencefortress.blogspot.com/2018/02/creating-executables-for-machine.html
## 
