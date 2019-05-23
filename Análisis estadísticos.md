##Análisis estadísticos


#####1. Análisis de ordenamiento de los aislados por morfología de colonia
  - Se realiza un análisis de ordenamiento de los aislados con FactoMineR y missMDA.
  - Lo anterior utilizando una matriz de datos de morfología de las colonias.
  - Se realiza el ordenamiento de los aislados totales.
  - Se realiza un segundo ordenamiento de aislados representativos, ello dada su morfología de colonia.

######1.1 Diagramas de Venn

Se obtienen diagramas de Venn para observar los morfotipos (a nivel de morfología de colonia) y los géneros compartidos entre las comunidades cultivables aisladas de las raíces de las plantas del lugar escogido.

- Se realizan mediante:
   - Obtención de listas de géneros.
   - Morfotipos únicos.
- Lo anterior de datos a comparar y la utilización del servidor del BEG. disponible en: [Link to another page]( http://bioinformatics.psb.ugent.be/webtools/Venn/.)


######1.2 Análisis de cinéticas de crecimiento de los aislados representantes de los grupos de crecimiento

1. Con el paquete Calc de LibreOffice:
- Se calculan los promedios y desviación estándar de la absorbancia media de cada hora de las cinéticas del crecimiento de los aislados.
- Los aislados que se eligieron fueron los representantes del los grupos de crecimiento "Medio", "Rapido" y "Muy Rápido".
- Estos se grafican en R V3.3.3.

######1.3 Análisis del ensayo de inhibición de crecimiento de cepas control 

1. Se utilizan las UFC/mL calculadas en el archivo "siembra por goteo y conteo".
2. Se calculan los promedios y desviaciones estandar.
3. Lo anterior con el paquete Calc de LibreOffice.
4. Se realiza una gráfica en R v3.3.3.

######1.4 Comparación del metagenoma de la comunidad artificial con un metagenoa de una rizosfera de suelo.

El metagenoma de la comunidad cultivable artificial que se obtenga debe ser comparado con otro que crezca en condiciones similares siguiendo los pasos que se muestran a continuación:

1. Se calcula la abundancia relativa de las proteínas anotadas en el 1er nivel de clasificación de SEED  de ambos metagenomas con la  fórmula 1)
2. Se eligen 89 proteínas relacionadas con estrés por metales o relevantes en el proceso que se esté buscando.
3. Se calcula la abundancia relativa (4to nivel de SEED) de ambos metagenomas con la  fórmula 2).
4. Ambos resultados dados por ambas fórmulas se grafican en R v3.3.3.

1)  AR genes anotados = n genes de cada categoría / n genes de todos las categorías
 
2)  AR = n genes de cada categoría / n genes predichos


