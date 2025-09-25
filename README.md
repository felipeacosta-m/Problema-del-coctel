<img width="621" height="935" alt="image" src="https://github.com/user-attachments/assets/df476334-7efa-4217-b923-a58dd21d3479" /># Problema-del-coctel
## Descripción del proyecto

El proyecto consiste en recrear el problema de la “fiesta de cóctel”, que aborda el desafío de aislar la voz de una persona en un entorno donde múltiples fuentes sonoras se encuentran activas simultáneamente. Para ello, se instalará un arreglo de tres micrófonos en una sala de laboratorio, estratégicamente distribuidos para captar combinaciones diferentes de las señales generadas por tres participantes, cada uno emitiendo una frase distinta desde posiciones y orientaciones fijas.

Las señales adquiridas serán registradas y sometidas a un análisis temporal y espectral utilizando herramientas como la Transformada Discreta de Fourier (DFT) y la Transformada Rápida de Fourier (FFT), con el fin de identificar las características principales de cada fuente sonora. Posteriormente, se aplicarán técnicas de separación de fuentes, tales como Análisis de Componentes Independientes (ICA) y Beamforming, para extraer la señal de interés de entre las mezclas capturadas.

Finalmente, se evaluará el desempeño del proceso de separación comparando la señal aislada con la señal original, utilizando métricas de calidad como la relación señal/ruido (SNR) para cuantificar la efectividad de la solución propuesta.

##Procedimiento utilizado
Se realizo el cálculo de SNR (Signal to Noise Ratio) de cada una de las señales de audio en las cuales se obtuvieron los siguientes datos
SNR de Audio-Silva.wav: 16.55 dB
SNR de Audio-Felipe.wav: 16.13 dB
SNR de Audio-3.wav: 18.70 dB
Normalmente cuando el SNR de una señal es mayor a 10 dB se entiende que la señal es aceptable y cuando están por encima de 20 dB es una señal con muy buena calidad
Por lo que podemos analizar de los resultados obtenidos que el audio de majo cuenta con SNR más alto, es decir, con una mejor calidad y por otro lado los audios de Melany y Santi son bastante similares pero con un valor menor a la anterior, lo cual indica que contiene un poco más de ruido . 

## Métodos de separación de fuentes
LA separación de fuentes de audio es una técnica de procesamiento de señales que se usa para separar y aislar diferentes sonidos, como puede ser la voz. En otras palabras, es el proceso de extracción de señales de sonido individuales de una mezcla de varias señales en una grabación de audio.
Existen diferentes métodos de separación de fuentes, entre ellos:
### Análisis de Componentes Independientes (ICA)
Consiste en un método estadístico para separar una señal en varios subcomponentes, esto con el propósito de estimar componentes independientes. Es un modelo lineal que supone que las variables observadas son una mezcla lineal de variables desconocidas no gaussianas. 
Para realizar este análisis se representan las señales como una combinación lineal, se aplica un modelo matemático para encontrar una transformación para la independencia de las señales y por ultimo se obtiene una señal aislada similar a la original.
### Beamforming 
Es una técnica de formación de haces (forma espacial de filtrado y usada para distinguir una señal objetivo y el ruido de fondo) encargada de dirigir una señal inalámbrica a una dirección concreta, evitando que se disperse en varias direcciones. Este método mejora el SNR de la señal deseada y atenúa el ruido de otras direcciones. 
Para realizar este método, se utilizan varios micrófonos en una configuración especifica, se aplican pesos a las señales captadas para alinearla en la dirección deseada y por último, se suma la señal alineada para cancelar el ruido de otras direcciones.  
Existen otros métodos para aislamiento de señales de interés como:
*Filtrado Adaptativo: minimizar el error entre la señal deseada y la interferencia
*Transformada de Fourier de Corto tiempo: analiza y filtra señales en el dominio de la frecuencia y espacio

### Diferencias entre ICA y Beamforming
## ICA
Funciona como mezclas de señales de diferentes fuentes, separa señales superpuestas independientes y opera en el dominio estadístico y matemático
##Beamforming
Se enfoca en una dirección específica mediante manipulación de micrófonos, funciona con señales espaciales y opera en el dominio espacial.

## Transformada Rápida de Fourier (FFT)
Es un método distinto de medición de audio, en donde se descompone una señal en sus componentes espectrales individuales y este proporciona información sobre su composición, este método es utilizado para análisis de errores, control de calidad y manejo de las condiciones del audio.  Este algoritmo calcula la Transformada Discreta de Fourier (DFT) la cual es una herramienta fundamental en el procesamiento de señales para convertir una señal en el dominio del tiempo al dominio de la frecuencia. 
La transformada Discreta de Fourier analiza todas las frecuencias discretas y proporciona una representación espectral de la señal y está dada por la siguiente ecuación:

![image](https://github.com/felipeacosta-m/Problema-del-coctel/blob/f525a99f91de679c0a9343b931044e83ae6b76a6/DiscretaFourier.png)

La FFT es una algoritmo que reduce la complejidad computacional para que el calculo de la DFT sea aún más rápido. 
Para este laboratorio se tomaron las audio grabados y se hallo la Transformada Rapida de Fourier y se obtuvieron las siguientes graficas

![image](https://github.com/felipeacosta-m/Problema-del-coctel/blob/40202e6a2c1c288008d0bd477be5dd8eff4d8ba1/Graficas%20audios.png)

En estas tres gráficas se observa la representación de cada señal de audio en el dominio del tiempo. En el eje x se muestra el tiempo en segundos (aproximadamente 0 a 36 s) y en el eje y se representa la amplitud de la señal en voltios.

Se evidencia que las tres señales presentan secciones de silencio o baja amplitud (ruido de fondo) al inicio y entre algunos intervalos de la grabación, seguidas de segmentos donde la amplitud aumenta de forma significativa, lo que corresponde a la presencia de voz.

Audio 1: muestra una amplitud moderada y un patrón de habla intermitente, con pausas entre frases y mayor estabilidad en la envolvente de la señal.

Audio 2: presenta la mayor amplitud pico a pico de las tres señales, lo que indica que su energía es más alta. Esto puede corresponder a una voz más fuerte o a mayor presencia de ruido.

Audio 3: tiene una amplitud intermedia, con una señal más uniforme y menos picos extremos que el audio 2, lo que sugiere menor distorsión o saturación.

![image](https://github.com/felipeacosta-m/Problema-del-coctel/blob/40202e6a2c1c288008d0bd477be5dd8eff4d8ba1/Graficas%20fourier.png)

En estas gráficas se muestra el resultado de aplicar la Transformada Rápida de Fourier (FFT) a cada una de las señales de audio. La FFT permite transformar la señal del dominio del tiempo al dominio de la frecuencia, facilitando la identificación de qué frecuencias están presentes en cada señal y con qué magnitud.

En el eje x se representan las frecuencias desde 0 hasta 8000 Hz (mitad de la frecuencia de muestreo de 16 kHz), mientras que el eje y muestra la magnitud de la transformada, la cual es un indicador de la energía de cada componente de frecuencia.

En las tres gráficas se observa un claro predominio de energía en frecuencias bajas, especialmente en el rango de 0 a 1000 Hz, lo cual es característico de la voz humana ya que la mayoría de su energía se concentra en este rango. La energía disminuye rápidamente conforme aumentan las frecuencias, lo que sugiere que el contenido de altas frecuencias es reducido.

![image](https://github.com/felipeacosta-m/Problema-del-coctel/blob/40202e6a2c1c288008d0bd477be5dd8eff4d8ba1/Graficas%20densidad%20espectral.png)

Por último, estas gráficas muestran la densidad espectral de potencia de los tres audios originales. Analizandolas generalmente, se puede estimar cómo se distribuye la energía de la señal a lo largo de las frecuencias, proporcionando una vista más suave y menos ruidosa que la FFT directa. En el eje x (escala logarítmica) se representan las frecuencias de 10 Hz a 10 kHz, mientras que en el eje y se muestra la densidad de potencia (energía por unidad de frecuencia). En las tres señales se observa un comportamiento general, picos entre 200Hz y 1000 Hz, rangos usuales para las voces, la energía es mucho mayor en bajas frecuencias, disminuyendo de manera abrupta después de 1 kHz, lo cual indica que el contenido útil de la señal se en la zona inicial, pero, se observa que en frecuaencias altas, la energíe es minima, por lo tanto, el ruido no domina el espectro y las señales son principalmente voz.



