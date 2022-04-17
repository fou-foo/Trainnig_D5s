
En VM Ubuntu 20.
```bash
conda activate GFB
conda list -e > GFB_req.txt
```

En Windows 11

```bash
conda env list # lista los enviroments y sus rutas
conda activate base
# si tienes un procesador intel ejecuta lo siguiente
conda install scikit-learn-intelex -c intel # instala las actualizaciones para que scikit-learn sea menos lento
conda list -e > base_req.txt   #exporta los packages del enviroment 'base'
conda deactivate #desactiva tu enviroment como buena practica
conda create -n GFB --file base_req.txt python=3.9 #crea un enviroment que compartiremos todos PROCURA SIEMPRE TRABAJAR EN ÉL
conda install -c conda-forge matplotlib-base #ajustes manuales

conda install scikit-learn-intelex -c intel

conda activate GFB # Activa el enviroment que creaste en la linea anterior
jupyter-lab # run jupyter lab and fun
conda install --file GFB_req.txt # TUVE QUE AGREGAR EL CANAL DE CONDA-FORGE A MANO CON LA UI
conda deactivate #desactiva tu enviroment como buena practica
conda list -e > GFB_req.txt
```



conda install scikit-learn-intelex -c intel # instala las actualizaciones para que scikit-learn sea menos lento
