Análisis filogenético comparativo de la familia de transportadores HAK/KUP/KT en plantas
En este repositirio se busca dilusidar la historia de divergencia de la familia de transportadores de potasio esto mediante tres especies basándonos únicamente en secuencias proteicas encontradas en el NCBI ya que en trabajos anteriores se ha realizado con secuencias de ADN y lo que se busca en encontrar una relacion desde otro punto de vista


---------------------------------------------------------------------------------Introducción---------------------------------------------------------------------------------------------

Los transportadores de potasio de la familia HAK/KUP/KT constituyen una familia génica ampliamente distribuida en plantas. Estos transportadores están relacionados principalmente con la adquisición y distribución de K⁺, particularmente bajo condiciones de baja disponibilidad del ion. La familia también recibe las denominaciones HAK, KT o KUP debido a la relación evolutiva entre los transportadores HAK de alta afinidad y las permeasas KUP descritas inicialmente en otros organismos.

Los genes ortólogos son genes que se relacionan mediante un evento de especiación, mientras que los genes parálogos son genes cuya relación se origina por una duplicación génica. En una reconciliación entre árbol génico y árbol de especies, los nodos internos pueden clasificarse como eventos de especiación o duplicación; esta clasificación permite inferir las relaciones de ortología y paralogía entre los genes.

Gomez-Porras et al. (2012) realizaron un análisis filogenético de diferentes familias de transportadores de K⁺ en plantas terrestres, incluyendo Arabidopsis thaliana, Oryza sativa, Physcomitrella patens, Populus trichocarpa y Selaginella moellendorffii. Para la familia HAK/KUP/KT identificaron 13 genes en A. thaliana, 27 en arroz, 22 en P. trichocarpa, 18 en P. patens y 11 en S. moellendorffii. Su análisis permitió reconocer seis grupos principales de transportadores HAK y proponer eventos de duplicación y pérdida génica durante la evolución de las plantas terrestres.

En el presente análisis se realizó una reconstrucción filogenética comparativa utilizando secuencias proteicas de HAK/KUP/KT de A. thaliana, Oryza sativa y Physcomitrium patens. El objetivo fue reproducir de manera simplificada el flujo de análisis filogenético utilizado para estudiar esta familia y posteriormente interpretar las relaciones entre las proteinas expresadas.

Descarga y selección de las secuencias FASTA

El primer paso consistió en obtener las secuencias proteicas correspondientes a miembros de la familia HAK/KUP/KT las cuales fueron obtenidas directamente del NCBI en formato .fasta.

Para Arabidopsis thaliana se utilizaron los 13 miembros descritos por Gomez-Porras et al. (2012), correspondientes a:

KT1
KT2
KUP3
KUP4
HAK5
KT5-KT12

Para Oryza sativa se incorporaron múltiples miembros de la familia HAK

HAK1-HAK23

mientras que para Physcomitrium patens se incorporaron los miembros disponibles en el conjunto de secuencias utilizado para este análisis.

HAK1-HAK4

El conjunto final utilizado para construir el árbol contiene 40 secuencias representantes de tres linajes evolutivos diferentes: una angiosperma dicotiledónea (13 A. thaliana), una angiosperma monocotiledónea (23 O. sativa) y una briofita (4 P. patens) con intención de ver como se pudieron dispersar a través del tiempo estas proteínas.

------------------------------------------------------------------------Agrupación    de las secuencias--------------------------------------------------------------------------------------

se agruparon todas las secuencias en una sola global para asi procesar de mejor manera la información y que con un solo archivo se corriera el alineamiento. 
satguni@lko:~/taller_cd$ cat *.fasta > archivo_combinado.fasta 
satguni@lko:~/taller_cd$ mv archivo_combinado.fasta K_transporters.fasta

------------------------------------------------------------------------Alineamiento de aminoácidos---------------------------------------------------------------------------------------

Una vez obtenidas las secuencias FASTA, se realizó un alineamiento múltiple de las proteínas utilizando MAFFT.

El propósito del alineamiento es establecer correspondencias entre posiciones homólogas de las diferentes proteínas. En otras palabras, cada columna del alineamiento representa una posición que puede ser comparada evolutivamente entre los diferentes miembros de la familia.

Este paso es fundamental porque los métodos filogenéticos basados en caracteres, como Maximum Likelihood, utilizan las diferencias observadas posición por posición para estimar las relaciones evolutivas entre las secuencias.

MAFFT es una herramienta ampliamente utilizada para el alineamiento múltiple de secuencias de proteínas y nucleótidos. Su versión 7 incorpora diferentes estrategias para realizar alineamientos múltiples y mejorar la eficiencia y precisión del proceso.

El resultado de este procedimiento fue el archivo:

KTransporter_alineado.fasta

Este archivo corresponde al alineamiento utilizado posteriormente como entrada para IQ-TREE.

Es importante diferenciar las secuencias originales del alineamiento. Las proteínas originales pueden presentar longitudes diferentes; sin embargo, después del alineamiento todas las secuencias deben ocupar el mismo número de posiciones 850, incorporándose espacios o gaps (-) cuando sea necesario para representar inserciones o deleciones.

Por lo tanto, el alineamiento constituye la matriz de caracteres sobre la cual posteriormente se estimó la filogenia.
satguni@lko:~/taller_cd$ mafft --auto KTransporter_alineado_limpio.fasta > KTransporter_alineado.fasta
outputhat23=16
treein = 0
compacttree = 0
stacksize: 8192 kb
rescale = 1
All-to-all alignment.
tbfast-pair (aa) Version 7.525
alg=L, model=BLOSUM62, 2.00, -0.10, +0.10, noshift, amax=0.0
0 thread(s)

outputhat23=16
Loading 'hat3.seed' ...
done.
Writing hat3 for iterative refinement
rescale = 1
Gap Penalty = -1.53, +0.00, +0.00
tbutree = 1, compacttree = 0
Constructing a UPGMA tree ...
   30 / 40
done.

Progressive alignment ...
STEP    27 /39
Reallocating..done. *alloclen = 2776
STEP    39 /39
done.
tbfast (aa) Version 7.525
alg=A, model=BLOSUM62, 1.53, -0.00, -0.00, noshift, amax=0.0
1 thread(s)

minimumweight = 0.000010
autosubalignment = 0.000000
nthread = 0
randomseed = 0
blosum 62 / kimura 200
poffset = 0
niter = 16
sueff_global = 0.100000
nadd = 16
Loading 'hat3' ... done.
rescale = 1

   30 / 40
Segment   1/  1    1-1111
STEP 009-009-0  identical.
Oscillating.

done
dvtditr (aa) Version 7.525
alg=A, model=BLOSUM62, 1.53, -0.00, -0.00, noshift, amax=0.0
0 thread(s)


Strategy:
 L-INS-i (Probably most accurate, very slow)
 Iterative refinement method (<16) with LOCAL pairwise alignment information

If unsure which option to use, try 'mafft --auto input > output'.
For more information, see 'mafft --help', 'mafft --man' and the mafft page.

The default gap scoring scheme has been changed in version 7.110 (2013 Oct).
It tends to insert more gaps into gap-rich regions than previous versions.
To disable this change, add the --leavegappyregion option.

------------------------------------------------------------------------Selección del modelo evolutivo------------------------------------------------------------------------------------

Después del alineamiento se realizó la selección del modelo de evolución de proteínas utilizando IQ-TREE 2 y su herramienta ModelFinder.

El análisis se ejecutó inicialmente mediante:

iqtree2 -s KTransporter_alineado.fasta -m MFP

El modelo seleccionado de acuerdo con el criterio BIC fue:

LG+F+R5

La selección de modelos es importante porque una filogenia de Maximum Likelihood no solamente depende de las diferencias observadas entre las secuencias, sino también de un modelo matemático que describa cómo pueden producirse los cambios de aminoácidos a lo largo de la evolución.

La matriz LG corresponde a un modelo empírico de sustitución de aminoácidos desarrollado a partir de conjuntos de datos de proteínas. El componente +F indica que se utilizaron las frecuencias observadas de aminoácidos en el conjunto de datos. Finalmente, +R5 representa una distribución FreeRate con cinco categorías para modelar la heterogeneidad de las tasas evolutivas entre los sitios del alineamiento.

Por lo tanto, el modelo LG+F+R5 permite considerar simultáneamente:

que algunos cambios de aminoácidos son más probables que otros;
las frecuencias específicas de los aminoácidos observadas en el conjunto de datos; y
que diferentes posiciones de las proteínas pueden evolucionar a diferentes velocidades.

La selección de un modelo apropiado es un componente importante de la inferencia filogenética porque los modelos de sustitución describen probabilísticamente la evolución de las secuencias y permiten calcular la probabilidad de observar los datos bajo diferentes hipótesis evolutivas.

IQ-TREE integra ModelFinder para realizar esta selección de manera automatizada y comparar múltiples modelos mediante criterios estadísticos de información.

satguni@lko:~/taller_cd$ iqtree2 -s KTransporter_alineado.fasta -m MFP
IQ-TREE multicore version 2.0.7 for Linux 64-bit built Nov 30 2024
Developed by Bui Quang Minh, Nguyen Lam Tung, Olga Chernomor,
Heiko Schmidt, Dominik Schrempf, Michael Woodhams.

Host:    lko (AVX2, FMA3, 2 GB RAM)
Command: iqtree2 -s K+Transporter_alineado.fasta -m MFP
Seed:    437577 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Sun Sep 20 17:33:48 2026
Kernel:  AVX+FMA - 1 threads (8 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 8 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file K+Transporter_alineado.fasta ... Fasta format detected
Alignment most likely contains protein sequences
Alignment has 40 sequences with 1051 columns, 987 distinct patterns
758 parsimony-informative, 155 singleton sites, 138 constant sites
                         Gap/Ambiguity  Composition  p-value
   1  OAO99080.1                25.31%    passed     23.26%
   2  AEC08341.1                32.25%    passed     26.41%
   3  OAP19081.1                33.30%    passed     71.66%
   4  OAP07151.1                24.64%    passed     99.77%
   5  sp|O80739.2|POT12_ARATH   21.31%    passed     85.35%
   6  AEC09846.1                24.45%    passed     92.61%
   7  sp|Q8LPL8.1|POT13_ARATH   18.65%    passed     48.35%
   8  AEE35043.1                25.59%    passed     87.59%
   9  OAO89587.1                30.64%    passed     92.91%
  10  OAO90979.1                25.69%    passed     97.56%
  11  OAO97961.1                23.31%    passed     41.98%
  12  OAP05278.1                24.93%    passed     99.52%
  13  NP_194095.2               26.26%    passed     64.84%
  14  NP_001389294.1            24.64%    passed     88.81%
  15  NP_001408583.1            19.79%    failed      3.87%
  16  sp|Q7XLC6.4|HAK11_ORYSJ   24.74%    passed     89.66%
  17  sp|Q8VXB1.1|HAK12_ORYSJ   24.55%    passed     64.07%
  18  sp|Q652J4.1|HAK13_ORYSJ   25.98%    passed      8.39%
  19  NP_001409095.1            18.27%    passed     11.45%
  20  NP_001406780.1            17.51%    passed     22.73%
  21  NP_001405276.1            22.84%    passed     69.92%
  22  sp|Q67UC7.2|HAK17_ORYSJ   32.73%    passed     89.96%
  23  sp|Q653B6.1|HAK18_ORYSJ   24.55%    passed     91.28%
  24  NP_001403557.1            29.40%    passed     41.44%
  25  NP_001395901.1            25.50%    passed     85.80%
  26  NP_001403558.1            28.92%    passed     53.44%
  27  sp|Q75G84.1|HAK21_ORYSJ   23.98%    passed     23.99%
  28  NP_001408882.1            18.17%    failed      0.00%
  29  NP_001409675.1            16.56%    passed     25.10%
  30  NP_001388412.1            23.12%    passed      8.64%
  31  NP_001409522.1            33.68%    passed     77.99%
  32  NP_001395942.1            25.69%    passed     28.61%
  33  NP_001396050.1            28.83%    passed     53.78%
  34  sp|Q8H3P9.3|HAK7_ORYSJ    22.84%    passed     99.68%
  35  sp|Q8VXB5.2|HAK8_ORYSJ    24.55%    passed     82.77%
  36  NP_001409217.1            25.02%    passed     84.83%
  37  CAM90409.1                21.79%    passed     98.77%
  38  CAM90410.1                21.50%    passed     44.18%
  39  CAM90411.1                21.98%    passed     73.85%
  40  CAM88968.1                22.07%    passed     49.08%
****  TOTAL                     24.64%  2 sequences failed composition chi2 test (p-value<5%; df=19)


Create initial parsimony tree by phylogenetic likelihood library (PLL)... 0.030 seconds
Perform fast likelihood tree search using LG+I+G model...
Estimate model parameters (epsilon = 5.000)
Perform nearest neighbor interchange...
Estimate model parameters (epsilon = 1.000)
1. Initial log-likelihood: -41031.581
Optimal log-likelihood: -41031.168
Proportion of invariable sites: 0.030
Gamma shape alpha: 1.048
Parameters optimization took 1 rounds (0.897 sec)
Time for fast ML tree search: 4.358 seconds

NOTE: ModelFinder requires 62 MB RAM!
ModelFinder will test up to 546 protein models (sample size: 1051) ...
 No. Model         -LnL         df  AIC          AICc         BIC
  1  LG            43109.259    77  86372.518    86384.863    86754.245
  2  LG+I          42793.899    78  85743.798    85756.477    86130.483
  3  LG+G4         41042.622    78  82241.245    82253.924    82627.929
  4  LG+I+G4       41031.066    79  82220.131    82233.149    82611.773
  5  LG+R2         41336.961    79  82831.921    82844.939    83223.563
  6  LG+R3         41108.504    81  82379.009    82392.718    82780.566
  7  LG+R4         41014.607    83  82195.215    82209.635    82606.687
  8  LG+R5         40997.077    85  82164.153    82179.304    82585.541


  9  LG+R6         40991.806    87  82157.611    82173.512    82588.914
 21  LG+F+R5       40876.739    104 81961.478    81984.564    82477.057
 22  LG+F+R6       40874.876    106 81961.752    81985.781    82487.246
 34  WAG+R5        41162.872    85  82495.745    82510.895    82917.132
 35  WAG+R6        41152.649    87  82479.299    82495.199    82910.601
 47  WAG+F+R5      41016.292    104 82240.584    82263.670    82756.163
 48  WAG+F+R6      41015.597    106 82243.194    82267.223    82768.688
 60  JTT+R5        41012.341    85  82194.682    82209.832    82616.069
 61  JTT+R6        40999.816    87  82173.633    82189.533    82604.935
 73  JTT+F+R5      40936.649    104 82081.299    82104.386    82596.879
 74  JTT+F+R6      40932.233    106 82076.467    82100.496    82601.962
 86  JTTDCMut+R5   41024.770    85  82219.539    82234.690    82640.927
 87  JTTDCMut+R6   41012.130    87  82198.260    82214.160    82629.562
 99  JTTDCMut+F+R5 40943.825    104 82095.650    82118.737    82611.230
100  JTTDCMut+F+R6 40939.481    106 82090.961    82114.991    82616.456
112  DCMut+R5      41541.613    85  83253.225    83268.376    83674.613
113  DCMut+R6      41534.966    87  83243.932    83259.832    83675.234
125  DCMut+F+R5    41224.026    104 82656.052    82679.139    83171.632
126  DCMut+F+R6    41220.125    106 82652.250    82676.279    83177.744
138  VT+R5         41226.158    85  82622.316    82637.466    83043.703
139  VT+R6         41222.725    87  82619.450    82635.350    83050.752
151  VT+F+R5       41108.284    104 82424.568    82447.655    82940.148
152  VT+F+R6       41104.643    106 82421.285    82445.315    82946.780
164  PMB+R5        41478.710    85  83127.419    83142.570    83548.807
165  PMB+R6        41474.247    87  83122.494    83138.394    83553.796
177  PMB+F+R5      41498.107    104 83204.214    83227.301    83719.794

178  PMB+F+R6      41497.452    106 83206.905    83230.935    83732.400
190  Blosum62+R5   41516.351    85  83202.702    83217.852    83624.089
191  Blosum62+R6   41510.137    87  83194.273    83210.174    83625.575
203  Blosum62+F+R5 41476.614    104 83161.228    83184.314    83676.807
204  Blosum62+F+R6 41471.796    106 83155.593    83179.622    83681.087
216  Dayhoff+R5    41538.224    85  83246.449    83261.599    83667.836
217  Dayhoff+R6    41531.556    87  83237.112    83253.012    83668.414
229  Dayhoff+F+R5  41220.474    104 82648.947    82672.034    83164.527
230  Dayhoff+F+R6  41216.540    106 82645.081    82669.111    83170.576
242  mtREV+R5      43015.393    85  86200.786    86215.936    86622.173
243  mtREV+R6      43008.983    87  86191.965    86207.865    86623.267
255  mtREV+F+R5    41613.863    104 83435.727    83458.814    83951.307
256  mtREV+F+R6    41606.675    106 83425.351    83449.380    83950.845
268  mtART+R5      43133.439    85  86436.878    86452.028    86858.265
269  mtART+R6      43123.725    87  86421.449    86437.349    86852.751
281  mtART+F+R5    42108.402    104 84424.804    84447.891    84940.384
282  mtART+F+R6    42100.772    106 84413.544    84437.574    84939.039
294  mtZOA+R5      42109.496    85  84388.992    84404.142    84810.379
295  mtZOA+R6      42102.416    87  84378.832    84394.732    84810.134
307  mtZOA+F+R5    41469.268    104 83146.537    83169.623    83662.116
308  mtZOA+F+R6    41459.172    106 83130.344    83154.374    83655.839
320  mtMet+R5      42665.877    85  85501.754    85516.904    85923.141
321  mtMet+R6      42656.237    87  85486.475    85502.375    85917.777
333  mtMet+F+R5    41352.368    104 82912.737    82935.824    83428.317



334  mtMet+F+R6    41343.102    106 82898.205    82922.235    83423.700
346  mtVer+R5      43103.359    85  86376.719    86391.869    86798.106
347  mtVer+R6      43090.618    87  86355.237    86371.137    86786.539
359  mtVer+F+R5    41790.076    104 83788.151    83811.238    84303.731
360  mtVer+F+R6    41777.599    106 83767.198    83791.228    84292.693
372  mtInv+R5      42870.929    85  85911.857    85927.008    86333.245
373  mtInv+R6      42862.883    87  85899.766    85915.667    86331.069
385  mtInv+F+R5    41168.631    104 82545.261    82568.348    83060.841
386  mtInv+F+R6    41160.564    106 82533.128    82557.158    83058.623
398  mtMAM+R5      43671.885    85  87513.771    87528.921    87935.158
399  mtMAM+R6      43657.612    87  87489.223    87505.124    87920.526
411  mtMAM+F+R5    42355.547    104 84919.094    84942.181    85434.674
412  mtMAM+F+R6    42340.197    106 84892.394    84916.423    85417.889
424  HIVb+R5       41748.512    85  83667.023    83682.173    84088.410
425  HIVb+R6       41738.296    87  83650.591    83666.491    84081.893
437  HIVb+F+R5     41470.442    104 83148.883    83171.970    83664.463
438  HIVb+F+R6     41462.269    106 83136.538    83160.568    83662.033
450  HIVw+R5       43465.869    85  87101.738    87116.889    87523.126
451  HIVw+R6       43451.936    87  87077.871    87093.771    87509.173
463  HIVw+F+R5     42608.739    104 85425.478    85448.564    85941.057
464  HIVw+F+R6     42595.312    106 85402.625    85426.654    85928.119
476  FLU+R5        41774.293    85  83718.585    83733.735    84139.973
477  FLU+R6        41766.410    87  83706.820    83722.720    84138.122
489  FLU+F+R5      41512.656    104 83233.313    83256.399    83748.892
490  FLU+F+R6      41505.423    106 83222.845    83246.875    83748.340
502  rtREV+R5      41706.803    85  83583.605    83598.755    84004.992
503  rtREV+R6      41701.311    87  83576.622    83592.522    84007.924
515  rtREV+F+R5    41252.145    104 82712.290    82735.377    83227.870
516  rtREV+F+R6    41250.478    106 82712.955    82736.985    83238.450
528  cpREV+R5      41306.893    85  82783.786    82798.936    83205.173
529  cpREV+R6      41300.858    87  82775.716    82791.616    83207.018
541  cpREV+F+R5    41156.768    104 82521.537    82544.623    83037.116
542  cpREV+F+R6    41152.144    106 82516.287    82540.317    83041.782
Akaike Information Criterion:           LG+F+R5
Corrected Akaike Information Criterion: LG+F+R5
Bayesian Information Criterion:         LG+F+R5
Best-fit model: LG+F+R5 chosen according to BIC

All model information printed to K+Transporter_alineado.fasta.model.gz
CPU time for ModelFinder: 1781.868 seconds (0h:29m:41s)
Wall-clock time for ModelFinder: 1785.072 seconds (0h:29m:45s)

NOTE: 31 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
1. Initial log-likelihood: -40876.739
Optimal log-likelihood: -40876.714
Site proportion and rates:  (0.142,0.069) (0.282,0.282) (0.216,0.731) (0.259,1.535) (0.102,3.491)
Parameters optimization took 1 rounds (1.920 sec)
Computing ML distances based on estimated model parameters... 0.335 sec
Computing BIONJ tree...
0.002 seconds
Log-likelihood of BIONJ tree: -40909.310
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 2.206 second
Computing log-likelihood of 98 initial trees ... 17.588 seconds
Current best score: -40876.714

Do NNI search on 20 best initial trees
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -40876.702
Estimate model parameters (epsilon = 0.100)
   BETTER TREE FOUND at iteration 2: -40867.106


Iteration 10 / LogL: -40876.811 / Time: 0h:0m:53s
Iteration 20 / LogL: -40872.215 / Time: 0h:1m:21s
Finish initializing candidate tree set (4)
Current best tree score: -40867.106 / CPU time: 77.753
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Estimate model parameters (epsilon = 0.100)
UPDATE BEST LOG-LIKELIHOOD: -40865.309
Iteration 30 / LogL: -40877.820 / Time: 0h:1m:58s (0h:4m:55s left)
Iteration 40 / LogL: -40877.696 / Time: 0h:2m:30s (0h:3m:59s left)
Iteration 50 / LogL: -40866.230 / Time: 0h:3m:4s (0h:3m:15s left)
Iteration 60 / LogL: -40876.761 / Time: 0h:3m:34s (0h:2m:32s left)
Iteration 70 / LogL: -40877.733 / Time: 0h:4m:7s (0h:1m:54s left)
Iteration 80 / LogL: -40867.461 / Time: 0h:4m:37s (0h:1m:17s left)
Iteration 90 / LogL: -40865.391 / Time: 0h:5m:17s (0h:0m:42s left)

Iteration 100 / LogL: -40876.744 / Time: 0h:5m:47s (0h:0m:7s left)
TREE SEARCH COMPLETED AFTER 103 ITERATIONS / Time: 0h:5m:57s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -40865.309
2. Current log-likelihood: -40865.296
Optimal log-likelihood: -40865.287
Site proportion and rates:  (0.135,0.065) (0.283,0.275) (0.217,0.715) (0.263,1.520) (0.103,3.487)
Parameters optimization took 2 rounds (3.775 sec)
BEST SCORE FOUND : -40865.287
Total tree length: 22.575

Total number of iterations: 103
CPU time used for tree search: 352.226 sec (0h:5m:52s)
Wall-clock time used for tree search: 353.640 sec (0h:5m:53s)
Total CPU time used: 360.126 sec (0h:6m:0s)
Total wall-clock time used: 361.564 sec (0h:6m:1s)

Analysis results written to:
  IQ-TREE report:                K+Transporter_alineado.fasta.iqtree
  Maximum-likelihood tree:       K+Transporter_alineado.fasta.treefile
  Likelihood distances:          K+Transporter_alineado.fasta.mldist
  Screen log file:               K+Transporter_alineado.fasta.log



----------------------------------------------------------Reconstrucción filogenética mediante Maximum Likelihood-------------------------------------------------------------------------

Una vez seleccionado el modelo LG+F+R5 se reconstruyó el árbol filogenético utilizando el método de Maximum Likelihood (ML).
La inferencia se realizó mediante IQ-TREE 2 utilizando 1000 réplicas de Ultrafast Bootstrap (UFBoot).

El análisis permitió obtener el árbol:

K_Transporter_tree.treefile

La metodología de Maximum Likelihood busca el árbol que maximiza la probabilidad de observar el alineamiento de aminoácidos bajo el modelo evolutivo seleccionado. IQ-TREE utiliza una estrategia eficiente de búsqueda del espacio de árboles y permite estimar simultáneamente las relaciones filogenéticas y los soportes de las ramas.

El UFBoot se utilizó para evaluar la estabilidad de los clados obtenidos. En este análisis se realizaron 1000 réplicas, valor recomendado por la documentación de IQ-TREE para este procedimiento.

Los valores mostrados sobre las ramas del árbol corresponden a los valores de soporte UFBoot. De acuerdo con la documentación de IQ-TREE, para árboles de un solo gen se recomienda considerar especialmente confiables las ramas con UFBoot ≥95%. Por esta razón, en la interpretación se dio mayor importancia a los clados con valores de 95–100 y se interpretaron con mayor precaución aquellos con valores inferiores.

satguni@lko:~/taller_cd$ iqtree2 -s KTransporter_MAFFT.fasta -st AA -m LG+F+R5 -B 1000 -pre K_Transporters_tree
IQ-TREE multicore version 2.0.7 for Linux 64-bit built Nov 30 2024
Developed by Bui Quang Minh, Nguyen Lam Tung, Olga Chernomor,
Heiko Schmidt, Dominik Schrempf, Michael Woodhams.

Host:    lko (AVX2, FMA3, 2 GB RAM)
Command: iqtree2 -s KTransporter_MAFFT.fasta -st AA -m LG+F+R5 -B 1000 -pre K_Transporters_tree
Seed:    173996 (Using SPRNG - Scalable Parallel Random Number Generator)
Time:    Sun Sep 27 18:32:00 2026
Kernel:  AVX+FMA - 1 threads (8 CPU cores detected)

HINT: Use -nt option to specify number of threads because your CPU has 8 cores!
HINT: -nt AUTO will automatically determine the best number of threads to use.

Reading alignment file KTransporter_MAFFT.fasta ... Fasta format detected
Alignment most likely contains protein sequences
Alignment has 39 sequences with 1051 columns, 986 distinct patterns
757 parsimony-informative, 155 singleton sites, 139 constant sites
             Gap/Ambiguity  Composition  p-value
   1  HAK5_ARATH    25.31%    passed     20.39%
   2  KT1_ARATH     32.25%    passed     24.74%
   3  KT9_ARATH     33.30%    passed     71.87%
   4  KT10_ARATH    24.64%    passed     99.74%
   5  KT12_ARATH    21.31%    passed     85.39%
   6  KT2_ARATH     24.45%    passed     92.31%
   7  KT5_ARATH     18.65%    passed     45.42%
   8  KT6_ARATH     25.59%    passed     85.93%
   9  KT7_ARATH     30.64%    passed     92.19%
  10  KT8_ARATH     25.69%    passed     97.07%
  11  KUP3_ARATH    24.93%    passed     99.54%
  12  KUP4_ARATH    26.26%    passed     64.10%
  13  HAK1_ORYSA    24.64%    passed     90.37%
  14  HAK10_ORYSA   19.79%    failed      4.34%
  15  HAK11_ORYSA   24.74%    passed     87.51%
  16  HAK12_ORYSA   24.55%    passed     59.13%
  17  HAK13_ORYSA   25.98%    passed      8.61%
  18  HAK14_ORYSA   18.27%    passed     12.23%
  19  HAK15_ORYSA   17.51%    passed     23.06%
  20  HAK16_ORYSA   22.84%    passed     68.75%
  21  HAK17_ORYSA   32.73%    passed     90.60%
  22  HAK18_ORYSA   24.55%    passed     90.33%
  23  HAK19_ORYSA   29.40%    passed     44.02%
  24  HAK2_ORYSA    25.50%    passed     86.38%
  25  HAK20_ORYSA   28.92%    passed     55.45%
  26  HAK21_ORYSA   23.98%    passed     21.59%
  27  HAK22_ORYSA   18.17%    failed      0.00%
  28  HAK23_ORYSA   16.56%    passed     27.27%
  29  HAK3_ORYSA    23.12%    passed      9.92%
  30  HAK4_ORYSA    33.68%    passed     79.22%
  31  HAK5_ORYSA    25.69%    passed     26.14%
  32  HAK6_ORYSA    28.83%    passed     57.57%
  33  HAK7_ORYSA    22.84%    passed     99.74%
  34  HAK8_ORYSA    24.55%    passed     83.06%
  35  HAK9_ORYSA    25.02%    passed     85.24%
  36  HAK1_PHYPA    21.79%    passed     98.81%
  37  HAK2_PHYPA    21.50%    passed     44.73%
  38  HAK3_PHYPA    21.98%    passed     72.11%
  39  HAK4_PHYPA    22.07%    passed     47.94%
****  TOTAL         24.67%  2 sequences failed composition chi2 test (p-value<5%; df=19)

Create initial parsimony tree by phylogenetic likelihood library (PLL)... 0.063 seconds
Generating 1000 samples for ultrafast bootstrap (seed: 173996)...

NOTE: 34 MB RAM (0 GB) is required!
Estimate model parameters (epsilon = 0.100)
1. Initial log-likelihood: -40750.141
2. Current log-likelihood: -40045.578
3. Current log-likelihood: -40023.721
4. Current log-likelihood: -40016.501
5. Current log-likelihood: -40013.422
6. Current log-likelihood: -40012.258
7. Current log-likelihood: -40011.805
8. Current log-likelihood: -40011.607
Optimal log-likelihood: -40011.519
Site proportion and rates:  (0.123,0.059) (0.279,0.264) (0.212,0.679) (0.280,1.477) (0.106,3.410)
Parameters optimization took 8 rounds (16.260 sec)
Computing ML distances based on estimated model parameters... 0.318 sec
Computing BIONJ tree...
0.014 seconds
Log-likelihood of BIONJ tree: -40015.948
--------------------------------------------------------------------
|             INITIALIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Generating 98 parsimony trees... 1.683 second
Computing log-likelihood of 98 initial trees ... 16.894 seconds
Current best score: -40011.519

Do NNI search on 20 best initial trees
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 1: -39997.122
Estimate model parameters (epsilon = 0.100)
BETTER TREE FOUND at iteration 2: -39986.161
Iteration 10 / LogL: -39997.931 / Time: 0h:1m:3s
^[
Iteration 20 / LogL: -39989.519 / Time: 0h:1m:34s
Finish initializing candidate tree set (4)
Current best tree score: -39986.161 / CPU time: 76.229
Number of iterations: 20
--------------------------------------------------------------------
|               OPTIMIZING CANDIDATE TREE SET                      |
--------------------------------------------------------------------
Estimate model parameters (epsilon = 0.100)
UPDATE BEST LOG-LIKELIHOOD: -39985.212
Iteration 30 / LogL: -39987.477 / Time: 0h:2m:14s (0h:5m:34s left)
Iteration 40 / LogL: -39998.878 / Time: 0h:2m:41s (0h:4m:15s left)
Iteration 50 / LogL: -39986.353 / Time: 0h:3m:9s (0h:3m:20s left)
Log-likelihood cutoff on original alignment: -40030.603
Iteration 60 / LogL: -39987.548 / Time: 0h:3m:36s (0h:2m:34s left)
Iteration 70 / LogL: -39986.249 / Time: 0h:4m:6s (0h:1m:54s left)
Iteration 80 / LogL: -39987.175 / Time: 0h:4m:37s (0h:1m:17s left)
Iteration 90 / LogL: -39997.194 / Time: 0h:5m:3s (0h:0m:40s left)
Iteration 100 / LogL: -39985.432 / Time: 0h:5m:32s (0h:0m:6s left)
Log-likelihood cutoff on original alignment: -40030.603
NOTE: Bootstrap correlation coefficient of split occurrence frequencies: 1.000
TREE SEARCH COMPLETED AFTER 103 ITERATIONS / Time: 0h:5m:40s

--------------------------------------------------------------------
|                    FINALIZING TREE SEARCH                        |
--------------------------------------------------------------------
Performs final model parameters optimization
Estimate model parameters (epsilon = 0.010)
1. Initial log-likelihood: -39985.212
Optimal log-likelihood: -39985.211
Site proportion and rates:  (0.126,0.061) (0.286,0.271) (0.217,0.708) (0.275,1.525) (0.096,3.566)
Parameters optimization took 1 rounds (0.796 sec)
BEST SCORE FOUND : -39985.211
Creating bootstrap support values...
Split supports printed to NEXUS file K_Transporters_tree.splits.nex
Total tree length: 22.021

Total number of iterations: 103
CPU time used for tree search: 320.866 sec (0h:5m:20s)
Wall-clock time used for tree search: 322.262 sec (0h:5m:22s)
Total CPU time used: 340.116 sec (0h:5m:40s)
Total wall-clock time used: 342.031 sec (0h:5m:42s)

Computing bootstrap consensus tree...
Reading input file K_Transporters_tree.splits.nex...
39 taxa and 119 splits.
Consensus tree written to K_Transporters_tree.contree
Reading input trees file K_Transporters_tree.contree
Log-likelihood of consensus tree: -39985.211

Analysis results written to:
  IQ-TREE report:                K_Transporters_tree.iqtree
  Maximum-likelihood tree:       K_Transporters_tree.treefile
  Likelihood distances:          K_Transporters_tree.mldist

Ultrafast bootstrap approximation results written to:
  Split support values:          K_Transporters_tree.splits.nex
  Consensus tree:                K_Transporters_tree.contree
  Screen log file:               K_Transporters_tree.log

---------------------------------------------------------------------------------Resultados de la filogenia------------------------------------------------------------------------------

El árbol obtenido muestra que los miembros de los transportadores de k no se distribuyen aleatoriamente, sino que forman diferentes agrupaciones o clados con distintos niveles de soporte.

Una característica importante es que existen clados que contienen genes de diferentes especies y otros que contienen múltiples genes pertenecientes a una misma especie.

Esta distribución es relevante porque puede proporcionar evidencia de diferentes procesos evolutivos:

divergencia por especiación;
duplicación de genes;
expansión de familias génicas;
pérdida de genes;
y posterior divergencia funcional de copias duplicadas.

Sin embargo, debe tenerse en cuenta que el árbol obtenido es un árbol proteico y no un árbol de especies. Por lo tanto, la identificación definitiva de eventos de duplicación y la asignación formal de ortología requieren comparar el árbol obtenido con un árbol de especies mediante un procedimiento de reconciliación. La reconciliación permite distinguir nodos asociados a especiación de aquellos asociados a duplicación (He et.al 2012)

se encintraron Relaciones entre genes de Arabidopsis y arroz uno de los patrones observados corresponde al agrupamiento:

KT1_ARATH + HAK13_ORYSA 

con un soporte UFBoot de 86% el hecho de que los genes de dos especies diferentes se encuentren en el mismo clado es compatible con una relación de homología derivada de un ancestro común. Sin embargo, debido a que el soporte es inferior a 95% , esta relación debe describirse como compatible con ortología, y no como una demostración definitiva.

Otro grupo corresponde a:
KUP3_ARATH + HAK3_ORYSA con soporte de 73%.

Por el contrario, el clado que incluye:

KT2_ARATH + HAK8_ORYSA + HAK9_ORYSA presenta valores de soporte elevados, incluyendo un nodo de 100% para HAK8 y HAK9 y un soporte de 100% para el agrupamiento superior.
Este patrón indica una relación evolutiva estrecha entre estos genes y constituye una evidencia más robusta de que estas secuencias pertenecen al mismo linaje filogenético.

Uno de los patrones más claros del árbol corresponde a:
KT9_ARATH + KT10_ARATH con un soporte UFBoot de 100%.
Ambos genes pertenecen a A. thaliana y forman un clado muy bien soportado. Debido a que se trata de dos copias diferentes dentro de la misma especie, este patrón es compatible con una relación de paralogía, es decir, genes relacionados por un evento de duplicación génica.De manera similar:

KT6_ARATH + KT8_ARATH forman un clado con 98% de soporte.
La presencia de dos genes de la misma especie dentro de un clado altamente soportado también es compatible con una relación de paralogía.

Finalmente:
KT5_ARATH + KT7_ARATH presentan un soporte de 98%, constituyendo otro par de genes estrechamente relacionados dentro de Arabidopsis.

Estos resultados muestran que la familia HAK/KUP/KT contiene múltiples copias dentro de A. thaliana, lo que indica que la evolución de esta familia no puede explicarse únicamente por eventos de especiación. También han ocurrido procesos de duplicación génica.

El árbol muestra varios grupos que contienen múltiples genes de O. sativa.

HAK11_ORYSA + HAK12_ORYSA + HAK18_ORYSA
HAK11 y HAK12 presentan un soporte de 100%; el agrupamiento con HAK18 presenta 99%.

Este patrón constituye una evidencia fuerte de que estos tres genes pertenecen a un mismo linaje de la familia HAK/KUP/KT y es compatible con una expansión génica dentro del linaje de arroz.

También se observa:

HAK19_ORYSA + HAK20_ORYSA con soporte de 100%.

Otro grupo está constituido por:

HAK16_ORYSA + HAK21_ORYSA + HAK22_ORYSA con soportes de 100% en los principales nodos que unen estas secuencias. Finalmente, HAK14 y HAK15 forman un clado con 94%, que posteriormente se agrupa con KT5 y KT7 de Arabidopsis con un soporte de 100%.
Estos patrones son compatibles con la existencia de múltiples duplicaciones y expansiones independientes dentro del linaje de arroz.

Un resultado particularmente interesante es el siguiente agrupamiento:

KT5_ARATH + KT7_ARATH con 98% de soporte, y: HAK14_ORYSA + HAK15_ORYSA con 94% de soporte. Estos dos grupos se encuentran posteriormente unidos por un nodo con 100% de soporte.
Esto indica que las cuatro secuencias pertenecen a un linaje filogenético bien definido.

La interpretación más prudente es que el patrón es compatible con una historia evolutiva en la que existieron procesos de duplicación asociados a estos linajes.(He et.al 2012) 
Sin embargo, el árbol por sí solo no permite establecer con certeza si las duplicaciones ocurrieron antes o después de la divergencia entre monocotiledóneas y dicotiledóneas.


Los genes de Physcomitrium patens disponibles en el conjunto analizado presentan también una agrupación interesante.

HAK2_PHYPA + HAK3_PHYPA forman un clado con 89% de soporte. Posteriormente, este grupo se agrupa con; HAK4_PHYPA con un soporte de 100%. Este patrón es compatible con una expansión del linaje HAK dentro de Physcomitrium.


En el árbol, HAK5_ARATH aparece como una rama terminal separada del resto del conjunto. Sin embargo, es importante no interpretar directamente esta posición como evidencia de que HAK5 sea necesariamente el linaje ancestral o el primero en divergir.

El árbol utilizado es un árbol proteico y la posición de la raíz no fue establecida mediante un grupo externo. Por lo tanto, la posición de HAK5 en el extremo del árbol debe interpretarse como una relación topológica del árbol no enraizado y no como evidencia de que HAK5 sea ancestral. No obstante, HAK5 es un miembro particularmente interesante de la familia. Gomez-Porras et al. ubicaron HAK5 de Arabidopsis dentro del Grupo I de transportadores HAK y señalaron que HAK5, junto con determinados HAK de arroz y P. patens, presenta evidencia funcional como transportador de K⁺ de alta afinidad.


En el presente árbol, los pares KT9–KT10, KT6–KT8 y KT5–KT7 de Arabidopsis constituyen candidatos fuertes a relaciones de paralogía debido a que son copias diferentes de una misma especie y presentan soportes de 100%, 98% y 98%, respectivamente.
Por otro lado, agrupamientos entre genes de Arabidopsis y arroz pueden ser compatibles con relaciones de ortología.

Los resultados obtenidos son consistentes con la conclusión general de Gomez-Porras et al. (2012) de que la familia HAK/KUP/KT presenta una historia evolutiva compleja caracterizada por múltiples duplicaciones y expansiones génicas.

El estudio original identificó seis grupos principales de transportadores HAK en plantas terrestres, denominados Groups I–VI. Los autores propusieron que el ancestro común más reciente de las plantas terrestres poseía dos transportadores HAK. Uno habría dado origen al actual Group II, mientras que el otro habría experimentado varias duplicaciones antes del origen de las plantas vasculares. Algunas de estas copias se perdieron en el linaje de las plantas vasculares, mientras que contribuyeron a las amplificaciones específicas observadas en P. patens.

En el presente análisis se utilizó una estrategia moderna basada en IQ-TREE 2, que integra ModelFinder para la selección del modelo y UFBoot para evaluar el soporte de las ramas.
Por lo tanto, aunque las herramientas computacionales son diferentes, ambos análisis siguen el mismo principio general:
alineamiento → selección de modelo → Maximum Likelihood → evaluación del soporte → interpretación evolutiva.

El árbol obtenido se adjunto en formato newick y ademas se visualizo en peartree de donde se extrajo la imagen completa que se utilizo para este analisis.

 -------------------------------------------------------------------------------Limitaciones del análisis---------------------------------------------------------------------------------
 
Existen varias limitaciones que deben considerarse antes de realizar conclusiones evolutivas definitivas.
 un árbol génico por sí solo no permite determinar de manera definitiva la historia completa de duplicaciones y pérdidas. Para realizar esta inferencia de forma más rigurosa sería necesario construir o utilizar un árbol de especies y realizar una reconciliación árbol génico–árbol de especies.
ademas de que, algunos nodos del árbol presentan valores UFBoot inferiores a 95%. De acuerdo con la documentación de IQ-TREE, los valores ≥95% son aquellos sobre los que se recomienda comenzar a confiar para un árbol de un solo gen. Por tanto, los nodos con soportes de 44%, 51%, 73%, 76%, 80%, 83%, 86% y 89% deben interpretarse con mayor precaución que aquellos con 95–100%.

----------------------------------------------------------------------------------------Conclusión-------------------------------------------------------------------------------------

El análisis filogenético de la familia HAK/KUP/KT permitió identificar una estructura evolutiva compleja caracterizada por la presencia de múltiples linajes y por agrupamientos de genes procedentes de diferentes especies.

El alineamiento de las proteínas mediante MAFFT permitió establecer posiciones homólogas entre las secuencias. Posteriormente, IQ-TREE seleccionó mediante ModelFinder el modelo LG+F+R5 según el criterio BIC. Bajo este modelo se reconstruyó un árbol mediante Maximum Likelihood y se evaluó el soporte de sus ramas utilizando 1000 réplicas de UFBoot.

El árbol mostró varios clados con soporte elevado. Entre los patrones más destacados se encuentran los pares KT9–KT10, KT6–KT8 y KT5–KT7 de Arabidopsis, que presentan valores de soporte de 100%, 98% y 98%, respectivamente, y son compatibles con relaciones de paralogía. También se observaron agrupamientos de múltiples genes de arroz, como HAK11–HAK12–HAK18, HAK16–HAK21–HAK22 y HAK19–HAK20, que sugieren expansiones de la familia HAK dentro del linaje de O. sativa.

En Physcomitrium se identificó un agrupamiento formado por HAK2, HAK3 y HAK4, con soportes de 89–100%, compatible con una expansión del linaje HAK. 

En conjunto, los resultados apoyan la idea de que la diversidad actual de los transportadores HAK/KUP/KT es producto tanto de la divergencia entre especies como de múltiples eventos de duplicación génica. Las relaciones de ortología pueden proponerse para determinados clados que incluyen genes de diferentes especies, mientras que los agrupamientos de múltiples copias dentro de una misma especie constituyen candidatos a relaciones de paralogía.

No obstante, la identificación definitiva de eventos de duplicación, especiación y pérdida requiere una reconciliación formal entre el árbol génico y el árbol de especies. Por ello, las interpretaciones realizadas en este trabajo deben considerarse inferencias filogenéticas compatibles con los datos, y no reconstrucciones definitivas de toda la historia evolutiva de la familia.

En términos generales, el análisis confirma que los transportadores HAK/KUP/KT constituyen una familia génica antigua y diversificada, cuya evolución en plantas terrestres ha estado acompañada por múltiples procesos de duplicación, pérdida y especialización de linajes, en concordancia con el modelo evolutivo propuesto previamente para esta familia.

-----------------------------------------------------------------------------------Referencias--------------------------------------------------------------------------------------------

Gomez-Porras, J. L., Riaño-Pachón, D. M., Benito, B., Haro, R., Sklodowski, K., Rodríguez-Navarro, A., & Dreyer, I. (2012). Phylogenetic Analysis of K⁺ Transporters in Bryophytes, Lycophytes, and Flowering Plants Indicates a Specialization of Vascular Plants. Frontiers in Plant Science, 3, 167. DOI: 10.3389/fpls.2012.00167.

He C, Cui K, Duan A, Zeng Y, Zhang J. Genome-wide and molecular evolution analysis of the Poplar KT/HAK/KUP potassium transporter gene family. Ecol Evol. 2012 Aug;2(8):1996-2004. doi: 10.1002/ece3.299. Epub 2012 Jul 19. PMID: 22957200; PMCID: PMC3434002.
