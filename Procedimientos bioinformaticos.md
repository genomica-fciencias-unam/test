##Procedimientos bioinformaticos 

Primero se realiza un control de calidad con el programa Fastx v 36.06 que remueve regiones de baja calidad y secuencias de adaptadores.

#### 1. Análisis de amplicones

- 1.1 Ensamblado de amplicones
  - Las lecturas MiSeq crudas se ensamblan.
  - Lo anterior utilizando PandaSeq.
  - Parámetros a seguir:
   - _minoverlap -o_ de 15
   - _maxoverlap_ -o_ como default
   - _threeshold -t_ de 0.95.
  - Dependiendo del tamaño esperado de los amplicones se realiza un filtrado de la longitud.

- 1.2 Asignación taxonómica
  - Con CD-HIT v4.6 se realiza el agrupamiento de secuencias.
  - Se usa CD-HIT-EST con un umbral de indentidad de las secuencias de 0.97.
  - Con QIIME se realiza la asignación taxonómica.
  - Se realizan aliniamientos locales.
  - Se contrastan con la base de datos GreenGenes.
  - Se genera una tabla de OTUs.
  - El formato de la tabla (_biom_)se convierte a un archivo tabular.
  - Se calcula la abundancia relativa a nivel de género.


####2. Análisis metagenómicos

- 2.1  Ensamblado de metagenoma
  - Las lecturas HiSeq crudas se ensamblan.
  - Lo anterior utilizando velvet.
  - Con velveth se crea un grafo de los datos con _kmers_ de tamaño 21.
  - Con velvetg se llamó a los _contigs_.
  - Lo anterior con:
   - Una cobertura esperada de 2
   - Una longitud de las lecturas insertadas de 350 pb.

- 2.2 Asignación taxonómica
  - Con SSU-ALIGN v0.1.1 se realiza un alineamiento estructural de las secuencias de la subunidad pequeña del rRNA de las secuencias crudas del metagenoma.
  - Con SSU-BUILT se construye un modelo truncado de la región amplificada.
  - Se realiza un segundo alineamiento estructural de las secuencias de la subunidad pequeña del rRNA de las secuencias crudas del metagenoma utilizado en dicho modelo.
  - Se realiza un alineamiento local BLAST de las secuencias obtenidas en el paso 1.
  - Se utilizan como base los datos del archivo de secuencias de OTUs representativos del microbioma cultivable.
  - Se utilizan las secuencias obtenidas del paso 1 + las secuencias alineadas al modelo de la región deseada + las secuencias alineadas con BLAST.
  - Las secuencias anteriores se probaron contra las secuencias de OTUs.
  - Se realiza una asignación taxonómica en QIIME.
  - Finalmemente con KRAKEN se asignaron etiquetas taxonómicas a los _contigs_ del ensamble del metagenoma.
  - Se obtiene la lista de géneros asignados para cada uno de los 4 procedimientos.
  - Se obtiene una lista de especies asignadas para el último procedimiento.

######2.3  Predicción de genes y anotación de genes

1. Se utiliza PRODIGAL v2.6.2 para predecir genes del metagenoma.
2. Parámetro -p: _single_ para un solo genoma
3. Parámetro -p: _meta_ para un metagenoma.
4. Se realiza la anotación de genes utilizando 3 bases de datos:
* KEGG *
* eggNOG 4.5.1 *
* SEED *

######Consideraciones

1. Mediante el servidor Ghost Koala utilizando KEGG se descarga un archivo tabular con los (_KEGG Orthology_) anotados.
2. Mediante el programa eggNOG 4.5.1 con la base de datos del mismo nombre, se obtiene una tabla con los _Cluster Orthologous Groups_ asignados.
3. Mediante M5NR utilizando SEED se obtiene una tabla con los tres niveles de subsistemas de SEED.


######2.4  Reclutamiento de fragmentos

1. Se utiliza una base de datos no redundante de las secuencias representativas de los pangenomas de cada especie bacteriana.
2. El genoma de cada especie bacteriana debe de estar completamente secuenciado y disponible en el NCBI.
3. Se realiza un alineamiento con NUCmer * de los _contigs_ del metagenoma con la base de datos obtenida en el paso anterior.
4. Se realiza el filtrado de calidad de los alineamiento con delta-filter * .
5. Se recuperan los alineamientos con más de 80% de indentidad.
6. Los reclutamientos se grafican con mummerplot.

