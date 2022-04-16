
# Why another Set up ?

##### Dado el estado en el que estamos:

La propuesta de este set up es: que **TODOS compartamos el mismo ambiente de trabajo LOCAL**, sin herramientas de AWS u otro cloud provider, solo utilizando herramientas open source como Git, Anaconda, Python y otros lenguajes (que puedan surgir en un task o proyecto relacionado a ciencia de datos).

Aprovechando que ya se tiene GitHub y que nos gusta pues … aprovechémoslo.

###### Sobre las herramientas a utilizar

* Al usar Git y GitHub cada quien puede contribuir de manera asíncrona al proyecto sin impactar el trabajo de los demás.

* Con [Gitflow](https://jeffkreeftmeijer.com/git-flow/) el uso de las ramas es más sencillo.
  * Además de nos permite distinguir entre lo que ya está listo para ser presentado a negocio y en un futuro puede ser usado como producción por medio de la rama `main`.
  * El research que se lleve a cabo podemos llevarlo en la rama `develop`.
     * Los análisis y task que se lleven a cabo de manera individual pueden usar los tags de `feature` si son de research o bien de `hotfix` si se trata de arreglar un error en el **código** o la **data** no de metodología.
   Por ejemplo si se tiene la idea de usar 2 algoritmos para clasificar podemos dividir la tarea en dos task un `feature/algoritmo1` y `feature/algoritmo2`. De esta manera dos personas diferentes pueden abordar y **documentar** la tarea sin interrumpirse y lograr el objetivo.
   Esto además fomenta la colaboración entre pares, aquí Chuy es el master y el nos puede enseñar más de esto como prácticas de pair programing.

* Usamos [Anaconda](https://en.wikipedia.org/wiki/Anaconda_(Python_distribution)) por 4 razones:

  * Es un estándar en la industria. Por lo que *medio* podemos confiar en su soporte en el largo plazo.
  * Incluye por defecto [Conda](https://en.wikipedia.org/wiki/Conda_(package_manager)).
**Esto es la médula espinal del Set up**
Con el podemos tener cada quien su propio environment y cuando alguien logre un avance o instale una librería complicada nos comparte el contenido de su environment y todos lo podemos recrear y aumentar a nuestro environment.

  * Su propia distribución de paquetes de R y Python nos ahorra MUCHOS dolores de cabeza para no perder tiempo en checar compatibilidad entre versiones de lenguajes y librerías (como en R) o e.g. en el caso de Python esos issues llegan a nivel de incompatibilidad de librerías a nivel versión 2.1.X

  * Al instalarlo *solicito* se encarga de configurar las librerías de intel y de la tarjeta gráfica (NVIDIA) que tengamos optimizadas para ML y AI. Solo hay que prestar atención a la instalación.




#### Install Git

You can get and install Git for you OS [here](https://git-scm.com/downloads) an folow the instructions:
   * If you want to get started quickly with Git, maybe you should start by watching the 4 videos on section [git-scm.com/videos.](https://git-scm.com/videos)
   * If you like Git and want to dig deeper, the [Pro Git](https://git-scm.com/book/en/v2) book is great. because it is concise and [open access](https://en.wikipedia.org/wiki/Open_access).

#### Install Gitflow

Después de leer sobre [Gitflow](https://jeffkreeftmeijer.com/git-flow/) notaras que al final de la referencia se encuentra una liga a un [repo](https://github.com/nvie/gitflow/wiki/Installation), del mismo autor de GitFlow!, sobre como instalarlo dependiendo de tu OS. Sigue las instrucciones correspondientes a tu OS. La mayoría, Linux & MAC es una sola línea de código y en Windows viene ya con Git.

#### Install Anaconda

1. Go to Anaconda [Documentation](https://docs.anaconda.com/anaconda/install/#installation) installation section and select and follow the steps for you OS.

   Pon atención a las salidas de la instalación por ejemplo en mi caso en Windows 11 una sección del log fue:

   ```bash
   DEBUG menuinst_win32:create(325): Shortcut cmd is  C:\Users\joser\anaconda3\pythonw.exe, args are ['C:\\Users\\joser\\anaconda3\\cwp.py', 'C:\\Users\\joser\\anaconda3', 'C:\\Users\\joser\\anaconda3\\pythonw.exe', 'C:\\Users\\joser\\anaconda3\\Scripts\\spyder-script.py']
   DEBUG menuinst_win32:create(325): Shortcut cmd is C:\Users\joser\anaconda3\python.exe, args are ['C:\\Users\\joser\\anaconda3\\cwp.py', 'C:\\Users\\joser\\anaconda3', 'C:\\Users\\joser\\anaconda3\\python.exe', 'C:\\Users\\joser\\anaconda3\\Scripts\\spyder-script.py', '--reset']
       Windows 64-bit packages of scikit-learn can be accelerated using scikit-learn-intelex.
       More details are available here: https://intel.github.io/scikit-learn-intelex

       For example:

           $ conda install scikit-learn-intelex
           $ python -m sklearnex my_application.py


   done
   Delete file: C:\Users\joser\anaconda3\pkgs\env.txt
   Output folder: C:\Users\joser\anaconda3\conda-meta
   Extract: history
   Creating Anaconda3 menus...
   .
   .
   .
   Completed
   ```
2. Abre una terminal y notaras que la frase `(base)` aparece a la derecha de tu path
![](1.png)
Ahora en la terminal sigue las siguientes líneas

   ```bash
   conda config --set auto_activate_base False ## para desactivar la autoactivación del enviroment ‘base’
   conda env list # lista los enviroments y sus rutas
   conda activate base
   # si tienes un procesador intel ejecuta lo siguiente
   conda install scikit-learn-intelex -c intel # instala las actualizaciones para que scikit-learn sea menos lento
   conda list -e > base_req.txt   #exporta los packages del enviroment 'base'
   conda deactivate #desactiva tu enviroment como buena practica
   conda create -n dsTeamClikauto --file base_req.txt python=3.9 #crea un enviroment que compartiremos todos PROCURA SIEMPRE TRABAJAR EN ÉL
   conda activate dsTamClikauto # Activa el enviroment que creaste en la linea anterior
   jupyter-lab # run jupyter lab and fun
   conda deactivate #desactiva tu enviroment como buena practica
   ```


