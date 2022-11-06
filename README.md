# PF0953 Programación en R 2022-II

## Apuntes técnicos

### Ambiente conda

Se creó un ambiente conda con los paquetes de R utilizados en el curso. Antes, se había creado el ambiente `pf0953-2022-ii`, pero se produjeron problemas de compatibilidad al cargar el paquete `sf`.

```
Error: package or namespace load failed for ‘sf’ in dyn.load(file, DLLpath = DLLpath, ...):
 unable to load shared object '/home/mfvargas/miniconda3/envs/pf0953-2022-ii-b/lib/R/library/sf/libs/sf.so':
  /lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.30' not found (required by /home/mfvargas/miniconda3/envs/pf0953-2022-ii-b/lib/R/library/sf/libs/../../../../libgdal.so.31)
```

Parece que el error se corrige al instalar `sf=1.0_6` (que instala a su vez una versión menor de `libgdal`). Se creó el ambiente `pf0953-2022-ii-b` para implementar este cambio.


```shell
conda update conda
conda create -n pf0953-2022-ii-b
conda activate pf0953-2022-ii-b
conda config --env --add channels conda-forge
conda config --env --set channel_priority strict

conda install -c conda-forge mamba

mamba install r-base r-essentials r-ggplot2 r-ggthemes r-hrbrthemes r-plotly r-dt r-sf=1.0_6 r-rmapshaper r-terra r-raster r-rgdal r-leaflet r-leaflet.providers r-leaflet.extras r-leaflet.minicharts r-leafem r-palmerpenguins r-gapminder
```
