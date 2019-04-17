Este tutorial tiene como propósito hacer el set-up inicial para empezar a desarrollar modelos machine learning en el increíble lenguaje **R**.

Empecemos!

<img src="https://blog.datascienceheroes.com/content/images/2019/04/cat_coding.gif" width="200px">


## Instalando R


Pueden ir a la página principal: https://cran.r-project.org, o bien alos atajos debajo. 
Los llevará a la última versión de **R**: 3.5.3 (abril 2019):

### Windows

http://mirror.fcaglp.unlp.edu.ar/CRAN/bin/windows/base/R-3.5.3-win.exe

En algunos casos será necesario instalar Rtools, el que trae programas para compilar como el gcc. Si sos desarrollador/a problablemente ya lo tengas.

Rtools lo bajan de: https://cran.r-project.org/bin/windows/Rtools/Rtools34.exe

Al instalar tengan la precaución de setear la opcion del PATH como figura en la imagen:

<img src="https://blog.datascienceheroes.com/content/images/2019/04/instalar_rtools.png" width="400px">

Mas información de Rtools acá: https://github.com/stan-dev/rstan/wiki/Install-Rtools-for-Windows

### MacOS

http://mirror.fcaglp.unlp.edu.ar/CRAN/bin/macosx/R-3.5.3.pkg

### Linux

http://mirror.fcaglp.unlp.edu.ar/CRAN/ (elijan su distribución)


## Instalando RStudio

Es el entorno de desarrollo de R.

Vamos a: https://www.rstudio.com/products/rstudio/download/#download

Buscamos e instalamos la versión compatible con nuestro sistema operativo:

<img src="https://blog.datascienceheroes.com/content/images/2019/04/rstudio_distributions.png" width="700px">


## Instalando los paquetes (librerías) de R

Esto es dependiente de lo que se necesite hacer, pero daré los que uso normalmente.

Tengan en cuenta que si ya tenian R instalado, e instalan una version nueva, entonces necesitaran instalar todos los paquetes de nuevo.

Abren RStudio, y si todo fue bien, tienen que ver algo como esto:

A continuación copian y pegan la siguiente línea de código para instalar los paquetes en la consola (donde esta el cursor), apretan enter y esperan unos minutos…

`libs_para_instalar=c( "tidyverse","Hmisc", "funModeling","reshape2" ,"caret", "data.table","lubridate", "zoo", "knitr","infotheo","RColorBrewer","minerva", "roxygen2","Lock5Data", "shiny", "scales","corrplot","feather", "gridExtra", "xgboost", "gbm", "randomForest", "devtools")`

`install.packages(libs_para_instalar)`

<img src="https://blog.datascienceheroes.com/content/images/2019/04/instalar_librerias_R.gif">


Si les aparece el mensaje: _"Do you want to install from sources the package which needs compilation? (Yes/no/cancel)"_ Escriban: `Yes`

Si les aparece que para instalar el paquete 'X' se necesita el paquete 'Y'. Instalen 'Y' y luego repitan el proceso.

<img src="https://blog.datascienceheroes.com/content/images/2019/04/pajarito_yes.gif" width="300px">


**Listo!**

## Verificando todos los paquetes instalados

Ejecuten la siguiente línea, que comparará los paquetes instalados con los que figuraban en la lista `libs_para_instalar`:

`libs_para_instalar[!(libs_para_instalar %in% installed.packages()[,"Package"])]`

Si todo salió bien no deberían ver reportado ningún paquete: 

<img src="https://blog.datascienceheroes.com/content/images/2019/04/mensaje_inst_ok.png" width="650px">

Nota: `character(0)` = todo salió ok

## Errores durante la instalación

1) 

**Revisen que no haya ningún error en la instalación al terminar.**

Si lo hay, intenten reinstalar ese paquete solamente. Si no funciona -> Google (los errores pueden ser variados, sobretodo si tienen windows).

Si siguen con el problema, pueden preguntarlo en español en: **datosenR.org**

Si tuvieron un error en la instalación de un paquete, todos los paquetes siguientes en la lista no fueron instalados. Pueden probar el volver a correr el `install.packages`, solamente con los paquetes en cuestión.

2) 

Si ya tienen la distribución de R de Microsoft, MRAN (https://mran.microsoft.com); es muy problable que los paquetes que instalen no estén a la última versión que en CRAN.

¿Qué es CRAN? Es la red global de servidores oficiales de R donde están los paquetes y el programa R en cuestión. Cada vez que hacen `install.packages` los va a buscar ahí. 

Les recomiendo que igualmente instalen R desde CRAN (como lo indicado anteriormente).

3) 
Como resolver el warning: _["package 'xxx' is not available (for R version x.y.z)?](https://stackoverflow.com/questions/25721884/how-should-i-deal-with-package-xxx-is-not-available-for-r-version-x-y-z-wa)_


## Haciendo algunas pruebas

Copien y ejecuten esto en R, crearan unos gráficos y creando un modelo predictivo, así de fácil!



```r
library(randomForest) 
library(tidyverse) 
library(funModeling) 

randomForest(mtcars, formula = wt ~ qsec)

select(mtcars, cyl, hp) %>% arrange(cyl) %>% top_n(5)

ggplot(mtcars, aes(cyl)) + geom_histogram()

plot_num(mtcars)
```

<img src="https://blog.datascienceheroes.com/content/images/2019/04/probando_R.gif">

<br>

Fin 🎉

---


Si quieren seguir practicando ciencia de datos, los/las invito a leer: https://librovivodecienciadedatos.ai 📗

<img src="https://librovivodecienciadedatos.ai/introduction/libro-vivo-de-ciencia-de-datos.png" alt="Libro Vivo de Ciencia de Datos" width="200px">

_Happy coding!_ 🚀


[Twitter](https://twitter.com/pabloc_ds) y [Linkedin](https://www.linkedin.com/in/pcasas/).
