
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
conda create -n dsTeamClikauto --file base_req.txt python=3.9 #crea un enviroment que compartiremos todos PROCURA SIEMPRE TRABAJAR EN ÉL
conda activate dsTamClikauto # Activa el enviroment que creaste en la linea anterior
jupyter-lab # run jupyter lab and fun
conda deactivate #desactiva tu enviroment como buena practica
conda list -e > GFB_req.txt
```



conda install scikit-learn-intelex -c intel # instala las actualizaciones para que scikit-learn sea menos lento
