Respuesta de VISam a 1 y 15 Hz

Integrantes: Valentina Ojeda y Valentina Vasquez 
Área cerebral: VISam
Pregunta: ¿Una mayor proporción de neuronas de VISam responde a rejillas en movimiento de 15 Hz que de 1 Hz?

Descripción

Este proyecto analiza registros extracelulares de neuronas del área visual anteromedial, VISam, obtenidos mediante sondas Neuropixels en ratones despiertos. Se comparó la respuesta neuronal ante rejillas en movimiento con frecuencias temporales de 1 y 15 Hz.

El conjunto de datos contiene:

368 neuronas

5 ratones

5 761 044 potenciales de acción

Ensayos de rejillas en movimiento, rejillas estáticas, escenas naturales, película natural, destellos y actividad espontánea

Archivos

proyecto_final.ipynb: notebook con la carga, exploración, análisis y visualización de los datos.

datos.npz: conjunto de datos de VISam.

Figuras exportadas para el póster final.

Metodología

Se contaron los potenciales de acción ocurridos entre 0 y 2 segundos después del inicio de cada rejilla y se calculó la tasa de disparo en hercios. Cada neurona se comparó únicamente con los ensayos correspondientes a su ratón.

La respuesta de cada neurona se calculó con la siguiente fórmula:

Z-score = (tasa evocada promedio − tasa basal promedio) / desviación estándar de la tasa basal

La tasa basal se calculó con ensayos espontáneos de 2 segundos. Se clasificaron como respondedoras las neuronas con un Z-score mayor o igual a 2.5. Este umbral se contrastó con rasters de neuronas individuales para comprobar que identificara aumentos claros de actividad durante el estímulo.

Los intervalos de confianza se estimaron con 10 000 réplicas de bootstrap jerárquico en tres niveles: ratón, neurona y ensayo. La comparación entre 1 y 15 Hz incluyó una prueba de permutación pareada por ratón y el tamaño del efecto dz de Cohen.

Resultados principales

De las 368 neuronas analizadas, 116, equivalentes al 31.5 %, respondieron al menos a una combinación válida de rejillas en movimiento.

En la comparación asignada:

1 Hz: 14 de 368 neuronas respondedoras, 3.8 %
IC 95 %: 1.5–7.1 %

15 Hz: 26 de 368 neuronas respondedoras, 7.1 %
IC 95 %: 4.3–11.3 %

Diferencia: 3.3 puntos porcentuales a favor de 15 Hz
IC 95 %: −0.2–6.9 puntos porcentuales

Prueba de permutación: (p=0.0625)

Tamaño del efecto: (d_z=1.90)

Los cinco ratones presentaron una mayor proporción de neuronas respondedoras a 15 Hz. Sin embargo, el intervalo de confianza de la diferencia incluyó cero, por lo cual la evidencia no fue concluyente al considerar la agrupación de las neuronas por ratón. La principal limitación fue contar con solo cinco animales.

Comparación con el análisis ingenuo

También se realizó un análisis que trató las 368 neuronas como observaciones independientes:

Diferencia: 3.3 puntos porcentuales

IC 95 %: 0.3–6.2

(p=0.0283)

Este análisis produjo un intervalo artificialmente estrecho porque ignoró que varias neuronas provenían del mismo ratón. Por esta razón, la interpretación principal se basó en el análisis jerárquico.

Uso del modelo de lenguaje

Se utilizó un modelo de lenguaje para proponer y revisar código en Python, organizar las visualizaciones y aclarar conceptos estadísticos. Inicialmente, el modelo incluyó ensayos incompletos, contó 135 combinaciones de rejillas y estimó que 171 de 368 neuronas, 46.5 %, eran respondedoras. Después de revisar las variables del archivo, se excluyeron combinaciones inexistentes y se conservaron 40 condiciones reales. El resultado corregido fue de 116 de 368 neuronas, 31.5 %.

También se verificó el emparejamiento de las neuronas con los ensayos de su propio ratón y se agruparon los PSTH según la duración de cada clase de estímulo. El código y los resultados se revisaron mediante los controles indicados en la guía del proyecto.

Fuente de los datos

Los registros provienen del conjunto de datos de sondas Neuropixels del Allen Institute, descrito por Siegle et al. (2021).
