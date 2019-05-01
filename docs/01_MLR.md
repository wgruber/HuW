

# (PART\*) Teil I: Wiederholung Modellbildung I {-}



# Variabilität {-}

Bevor wir uns mit einzelnen Techniken und Verfahren der linearen Modellbildung auseinandersetzen, soll in einem kurzen Exkurs eines der grundlegensten Prinzipien der statistischen Modellbildung wiederholt und diskutiert werden - die *Varianz* von beobachten Werten.

Eigentlich ist es die Variabilität von Merkmalen, die statistische Methoden für die Erklärung von Effekten überhaupt erst auf den Plan ruft. Würden Merkmale wie z.B. Leistung einer Person, Persönlichkeitsmerkmale, Wetter, Produktionsgenauigkeit etc. nicht schwanken/variieren, würden wir heute nicht in diesem Raum sitzen und uns mit statistischen Ideen beschäftigen.

Der Begriff Variabilität ist für uns so alltäglich, dass wir ganz selbstverständlich damit umgehen. Doch was steckt wirklich dahinter? Wie können wir Sie nutzen um komplexere Eigenschaften einer Sache oder eines unerklärlichen Phenomäns auf die Spur zu kommen? 

Betrachten wir zunächst einmal ein sehr einfaches Beispiel. Im nachfolgenden Graphen sind (sehr vereinfacht) mehrere Möglichkeiten dargestellt, wie eine Person mitsamt Hund sich entlang einer Straße bewegt.

<center>

![**Abbildung 1**: Gassi gehen mit Blindenhund. Die blaue Linie beschreibt den Weg des Hundehalters, die Orange den des Hindes. Die Grüne Line ist die Referenzlinie, von welcher aus der Abstand zur jeweiligen Position (Hund und Mensch) zu sechs Beobachtungszeitpunkten gemessen wurde.](Images/GassiPositiveKorrelation.JPG){ width=25% }

</center>

Die Daten der Messungen sind in folgender Tabelle gegeben:

<!--html_preserve--><div id="htmlwidget-5fee2d4b2735b33679dd" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-5fee2d4b2735b33679dd">{"x":{"filter":"none","data":[["1","2","3","4","5","6"],[4,5,2,3,2,3],[3,4,1,2,0,2],[0.83,1.83,-1.17,-0.17,-1.17,-0.17],[1,2,-1,0,-2,0],[0.83,3.66,1.17,0,2.34,0],[0.71,1.56,-1,-0.15,-1,-0.15],[0.71,1.42,-0.71,0,-1.42,0],[0.5,2.22,0.71,0,1.42,0]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>Mensch<\/th>\n      <th>Hund<\/th>\n      <th>MenschD<\/th>\n      <th>HundD<\/th>\n      <th>KP<\/th>\n      <th>ZMensch<\/th>\n      <th>ZHund<\/th>\n      <th>ZKP<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"className":"dt-right","targets":[1,2,3,4,5,6,7,8]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"rowCallback":"function(row, data) {\nDTWidget.formatRound(this, row, data, 3, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 4, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 5, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 6, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 7, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 8, 1, 3, ',', '.');\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script><!--/html_preserve-->

In obiger Tabelle zeigt die Spalte *MenschD* die Differenz jeder Beobachtung zu Mittelwert aller Beobachtungen (für *HundD* gilt dasselbe, eben für die Variable Hund). Die Spalte *KP* zeigt das Kreuzprodukt, also $KP = MenschD \cdot HundD$. Die Spalten *ZMensch* und *ZHund*, sowie die *ZKP* entsprechen den z-Transformierten beobachteten Werten ($z_i^M = (M_i - \bar{M}) / sd(M)$ und $z_i^H = (H_i - \bar{H}) / sd(H)$).


Statistische Kennwerte für obige Daten (Mittelwert, Varianz und Standardabweichung) sind in folgender Tabelle dargestellt:

<!--html_preserve--><div id="htmlwidget-d3f6111bb0fa499aa1bf" style="width:100%;height:auto;" class="datatables html-widget"></div>
<script type="application/json" data-for="htmlwidget-d3f6111bb0fa499aa1bf">{"x":{"filter":"none","data":[["Mean","Var","SD"],[3.16666666666667,1.36666666666667,1.16904519445001],[2,2,1.4142135623731],[-0.00333333333333326,1.36666666666667,1.16904519445001],[0,2,1.4142135623731],[1.33333333333333,2.05246666666667,1.43264324472866],[-0.00499999999999999,0.99651,0.998253474824906],[0,1.0082,1.0040916292849],[0.808333333333333,0.755696666666667,0.869308154032083]],"container":"<table class=\"display\">\n  <thead>\n    <tr>\n      <th> <\/th>\n      <th>Mensch<\/th>\n      <th>Hund<\/th>\n      <th>MenschD<\/th>\n      <th>HundD<\/th>\n      <th>KP<\/th>\n      <th>ZMensch<\/th>\n      <th>ZHund<\/th>\n      <th>ZKP<\/th>\n    <\/tr>\n  <\/thead>\n<\/table>","options":{"columnDefs":[{"className":"dt-right","targets":[1,2,3,4,5,6,7,8]},{"orderable":false,"targets":0}],"order":[],"autoWidth":false,"orderClasses":false,"rowCallback":"function(row, data) {\nDTWidget.formatRound(this, row, data, 1, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 2, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 3, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 4, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 5, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 6, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 7, 1, 3, ',', '.');\nDTWidget.formatRound(this, row, data, 8, 1, 3, ',', '.');\n}"}},"evals":["options.rowCallback"],"jsHooks":[]}</script><!--/html_preserve-->

Wenn also ein Hund jeder Bewegung der Person folgt und dabei auch stets denselben Abstand hält, sind deren beobachteten Pfade zwar örtlich gesehen unterschiedlich, aber die Varianz des einen erklärt voll und ganz die Varianz des anderen Pfades. Mit anderen Worten, die beiden Pfade zeigen eine perfekte Kovariation. Formal wird diese *Kovariation* als *durchschnittliche Summe der Kreuzprodukte* ermittelt, also (M = Mensch, H = Hund):

<center>

$cov(M, H) = \frac{\sum_{i=1}^{6} (M_i - \bar{M}) \cdot (H_i - \bar{H})}{N-1}$

</center>

Setzt man die Beispieldaten in diese Berechnungsvorschrift ein, erhält man für die Summe der Kreuzprodukte 8. Die Kovarianz der beobachteten Werte ist (als durchschnittliche Kreuzproduktsumme) somit $cov(M,H) =$ 1.6. Die Korrelation berechnet sich dann ganz einfach zu:

<center>

$r(M, H) = \frac{cov(M,H)}{s_M \cdot s_H}$

</center>

Im vorliegenden Beispiel ergibt sich eine Korrelation $r(M,H) =$ 1 (also eine positive und perfekte Korrelation).

Der Korrelationskoeffizient hat gegebüber der Kovarianz den Vorteil, dass er durch die Normierung über die Standardabweichungen:

1. einen (einheitenlosen) Wertebereich zwischen $r \in [-1, 1]$ aufweist und damit vergleichbar mit anderen Korrelationswerten wird.
2. Als praktische **Effektgröße** interpretiert werden kann. 
3. Das Quadrat des Korrelationskoeffizienten ($r^2$) Auskunft über die aufgeklärte Varianz gibt. Dieses Maß spielt eine wesentliche Bedeutung sowohl bei der Korrelationsanalyse, als auch bei der multiplen Regression und anderen Verfahren. Häufig findet man die Bezeichnung **Determinationskoeffizient**.

Letztere Eigenschaft sei nochmals anhand des verwendeten Beispiels verdeutlicht:

> Im Fall einer perfekten Kovarianz (also 100% Übereinstimmung der Bewegungen von Mensch und Hund), braucht man nur mehr die Bewegung einer Variablen zu wissen (z.B. die des Menschen), um die Bewegungen des Hundes zu bestimmen (erklären). Somit erklärt die Variabilität des Menschen zu 100 % die Variabilität der Bewegungen des Hundes.

Die Beziehung zwischen zwei (intervallskallierten) Variablen lässt sich am besten mit einem Streudiagramm darstellen:

<center>

<img src="01_MLR_files/figure-html/Gassi_Pos_Korr_Scatter-1.png" width="288" />

</center>

Die folgende Abbildung zeigt ein weiteres Mensch-Hund Beispiel:

<center>

![**Abbildung 2**: in diesem Beispiel scheint es sich um eine Hund zu handeln, der bestmöglich das Gegenteil vom Menschen macht. Bestmöglich dahingehen, dass er nicht nur in die genau entgegengesetzte Richtung ausweicht, sondern dabei auch auf den genauen Abstand der Abweichung achtet.](Images/GassiNegativeKorrelation.JPG){ width=25% }

</center>

In diesem Fall ist die Korrelation auch perfekt, nur eben in die entgegengesetzte Richtung, was zur Folge hat, dass diese Korrelation den Wert $r(M,H) = -1$ zeigt. 

<center>

<img src="01_MLR_files/figure-html/Gassi_Neg_Korr_Scatter-1.png" width="288" />

</center>

Interessant und der Praxis am ehesten entsprechend, sind jedoch Fälle, in denen zwei Variablen nur teilweise Gemeinsamkeiten aufweisen. Im folgenden Beispiel wäre 

<center>

![**Abbildung 3**: Hund und Mensch bewegen sich zum Teil unabhängig, zum Teil aber auch synchron. Dies entspricht dann einer Kovarianz, bzw. Korrelation die irgendwo zwischen $r \in [-1, 1]$ angesiedelt ist (im Beispiel ist $r(M,H) = 0.5$.](Images/GassiBeliebigeKorrelation.JPG){ width=25% }

<img src="01_MLR_files/figure-html/Gassi_Teilweis_Korr_Scatter-1.png" width="288" />

</center>

Die Korrelation liegt in diesem Beispiel bei $r(M,H) = $ 0.5. Daraus lässt sich auch nochmals eine sehr wichtige Erkenntnis bezüglich der geteilten Varianz der beiden Variablen festhalten:

> Bei einer Korrelation von $r(x,y) = 0.5$ entspricht der Determinationskoeffizient $r^2(x,y) = 0.25$. In Prozent ausgedrückt, werden als 25% der Variabilität einer Variablen (z.B. Hund) durch die Variable Mensch erklärt. In welchen Abschnitten der Daten diese gemeinsame Variablität auftritt, lässt sich durch den $r$ nicht bestimmen.

Diese Feststellung führt uns aber zu einer weiteren Betrachtung von Variablitäten: 

<center>

![**Abbildung 4**: Hund und Mensch scheinen sich wieder synchron, aber in gegenseitiger Richtung zu bewegen. Man würde also eine negative und hohe Korrelation erwarten. Interressant ist jedoch die Beobachtung, dass ein Versatz der Beobachtungen um eine Einheit zu einem hohen positiven Zusammenhang führen würde!](Images/GassiAutokorrKorrelation.JPG){ width=25% }

</center>

Würde man davon ausgehen, dass sich der Mensch und Hund bei jedem Messzeitpunkt (1 bis 6) jeweils auf der gleichen Höhe befunden haben, dann wird man eine hohe **negative Korrelation** erhalten. Nimmt man jedoch an, dass der Mensch zum Messzeitpunkt (MZP) 1, der Hund aber bereits auf MZP 2 war, dann verschiebt sich die Spur des Hundes einfach um einen MZP nach oben! Korreliert man nun diese beiden Beobachtungen, würde sich eine nahezu perfekte **positive Korrelation** ergeben!

> Durch schrittweises Verschieben der Werte einer Variablen um eine Einheit ($\tau_i$) mit anschließender Berechnung der Korrelationskoeffizienten (r_{\tau_i}(x,y)), erhält man in Abhängigkeit von der Anzahl der Verschiebungen ($i \in [0, N-1]$) maximal $N$ neue Korrelatinskoeffizienten. Man bezeichnet diese Art der Korrelationsberechnung als **Kreuzkorrelation**.



Für das Beispiel ergibt sich eine normale Korrelation von $r(M,H)=$ -1. Die Korrelationen berechnet nach dem Versatzprinzip ergeben folgendes Bild:

<center>

<img src="01_MLR_files/figure-html/Gassi_Kreuz_Korr_Plot-1.png" width="480" />

</center>

Die Verschiebung $\tau$ wurde in diesem Beispiel mit $i = 4$ angegeben, d.h. es wurden die Werte der Variablen Hund um jeweils vier Schritte nach links und vier Schritte nach rechts verschoben. Bei jeder Verschiebung wurde die Korrelation berechnet (im Graphen ist die Verschiebung mit *Lag* auf der x-Achse angegeben). Auf der y-Achse wird der entsprechende Korrelationskoeffient angezeigt.

<center>


-----------------
 Tau   CrossCorr 
----- -----------
 -4     -0.4253  

 -3      0.431   

 -2     -0.3678  

 -1     0.6609   

  0       -1     

  1     0.6609   

  2     -0.3678  

  3      0.431   

  4     -0.4253  
-----------------

</center>

Die Werte der Tabelle zeigen nochmals den krassen Wechsel der Korrelation zwischen den Werte $\tau = 0$ (also keiner Verschiebung) und $\tau = 1$. Werden die Werte um nur einen Beobachtungspunkt verschoben, ändert sich die Korrelation von einer perfekt negativen, zu einer sehr hohen positiven Korrelation!

Eine weitere wichtige Eigenschaft die mit Hilfe dieser Vorgehensweise geprüft werden kann, ist die der sogenannten **Autokorrelation**. Diese funktioniert im Prinzip wie die eben beschriebene Kreuzkorrelation, mit dem Unterschied, dass eine Variable mit verschobenen "Eigenversionen" korreliert wird. Folgendes Beispiel zeigt das Ergebnis für die Variable Mensch unseres Beispiels:

<center>

<img src="01_MLR_files/figure-html/Gassi_Auto_Korr_Plot-1.png" width="480" />

</center>

Die Verschiebung $\tau$ wurde in diesem Beispiel mit $i = 4$ angegeben, d.h. es wurden die Werte der Variablen Mensch um schrittweise in eine Richtung verschoben. Bei jeder Verschiebung wurde die Korrelation berechnet (im Graphen ist die Verschiebung mit *Lag* auf der x-Achse angegeben). Auf der y-Achse wird der entsprechende Korrelationskoeffient angezeigt.

<center>


-----------------
 Tau   CrossCorr 
----- -----------
  0        1     

  1     -0.6609  

  2     0.3678   

  3     -0.431   

  4     0.4253   
-----------------

</center>

Die perfekte positive Korrelation bei einer Verschiebung um den Wert $\tau = 0$ ist bei der Autokorrelation trivial, da es sich ja um einen direkten Vergleich der Variablen mit sich selbst handelt. Bei Lag = 1 wird jedoch ersichtlich, dass sich die Korrelation ändert (auf $r = -0.66$), springt dann wieder auf $r = +0.37$ usw.

Es ist zu beachten, dass dieser Datensatz nur zu Demonstrationszwecken erzeugt wurde. Eine inhaltliche Interpretation wäre im gegebenen Fall nicht angebracht.

Nichts desto trotz sollte durch diese Beispiel gezeigt werden, dass sowohl die Kreuzkorrelation als auch die Autokorrelation vor allem in der Zeitreihenanalyse (und damit auch bei Längsschnittstudien) wichtige Erkenntnisse über die betrachteten Variablen liefern können. Vor allem kann eine vorliegende **Autokorrelation** bei der MLR zu beträchtlichen Einschränkungen der Gültigkeit einen Modells beitragen. Bei den MLR-Methoden werden wir noch über Möglichkeiten sprechen, bei MLR auf statitische Signifikanz einer Autokorrelation zu prüfen (Stichwort: Durbin-Watson).

# Korrelationen {-}

Korrelationen sind ein Maß für den statistischen Zusammenhang zwischen zwei Datensätzen. Unabhängige Variablen sind daher stets unkorreliert. Korrelation impliziert daher auch stochastische Abhängigkeit - ohne jedoch auf kausale Zusammenhänge schließen zu können. Bei der Berechnung einer Korrelation wird die lineare Abhängigkeit zwischen zwei Variablen quantifiziert.

Korrelationen werden i.A. der *deskriptiven Statistik* zugeordnet. Durch eine Reihe von Verfahren, wie z.B. partielle Korrelation, multiple Korrelation oder Faktorenanalyse, kann die einfache Korrelation zweier Variablen auf Beziehungen zwischen zwei Variablen unter Berücksichtigung des Einflusses weiterer Variablen werden. 

Korrelationen sind ein unverzichtbares Werkzeug für viele Forschungsgebiete und stehen häufig am Beginn jeder weiteren Datenanalyse, wie z.B.:

* multiple Regression
* Faktorenanalyse
* Clusteranalyse
* Mediator- und Moderator-Analyse

Die Berechnung einer Korrelation ist für sich gesehen an keine Voraussetzungen gebunden. Hingegen fordern eine sinnvolle Interpretationen der berechneten Kennwerte und vor allem die statistischen Tests von Korrelationskoeffizienten folgende inhaltliche und formale Überlegungen[^1]:

[^1]: [die Abbildungen wurden der Website Matheguru entnommen](https://matheguru.com/stochastik/korrelation-korrelationskoeffizient.html){target="_blank"}


* **Skalenniveau**: der Korrelationskoeffizient liefert zuverlässige Ergebnisse wenn die Variablen mindestens intervallskaliert sind oder für dichotome Daten[^2].

[^2]: dieser Spezialfall ist unter biserialer, bzw. punktbiserialer Korrelation bekannt.

* **Endliche Varianz (und Kovarianz)**: bei Erhöhung des Stichprobenumfangs darf sich die Variabilität nicht immer weiter erhöhen, sondern sollte sich stabilisieren. Bei Variablen, die bivariat normalverteilt sind, ist diese Voraussetzung automatisch gegeben. Der Korrelationskoeffizient ist damit auch gleichzeitig der *Maximum-Likelyhood Schäzter* des Korrelationskoeffizienten in der Grundgesamtheit (asymptotisch *erwartungstreu* und *effizient*).

<center>

![**Abbildung 5**: Endliche Varianz](Images/EndlicheVarianz.JPG){ width=40% }

</center>


* **Linearität**: die Korrelation ist ein Maß für **lineare Abhängigkeit**. Abweichungen der Daten von dieser Linearitätsannahme führen zu einer mehr oder weniger starken Verzerrung des Korrelationskoeffizienten, wie in den nachfolgenden Beispielen gezeigt wird:

<center>

![**Abbildung 6**: Linearität und Korrelation](Images/Linearitaet.JPG){ width=60% }

</center>

Vor allem zur Prüfung der Signifikanz einer Korrelation sollem man weitere Voraussetzungen überprüfen:

* **Normalverteilung**: Korrelation berechnen sich aus dem Kreuzprodukt von z-standardisierten Werten zweier Variablen. Für diese Berechnung wird der Mittelwert als zentraler Kennwert verwendet, welcher nur dann ein "sinnvoller" Kennwert für die Daten ist, wenn diese zumindest symmetrisch und im besten Fall normalverteilt sind.

* *Homoskedastizität*: bedeutet unterschiedliche Streuung innerhalb einer Datenmessung. Die exogene und die endogene Variable[^3] sind nicht mehr identisch verteilt, d.h. sie ändern ihre Variablität mit zu/abnehmenden Werten einer Variablen. Das hat zur Folge hat, dass die KQ[^4]-Schätzer nicht mehr effizient sind und der Standardfehler der Koeffizienten verzerrt und nicht konsistent wird.


[^3]: eine *exogene* Variable ist eine erklärende Variable, die mit der Störgröße unkorreliert ist (sogenannte Exogenität).Eine *endogene* erklärende Variable in einem multiplen Regressionsmodell ist eine erklärende Variable, die entweder aufgrund einer ausgelassenen Variablen, eines Messfehlers oder wegen Simulatanität mit der Störgröße korreliert ist (sogenannte Endogenität).

[^4]: KQ steht für kleinste Quadrate (auch MLS - Minimum Least Square, oder OLS - Ordinary Least Square) und ist eine einfache Schätzung über minimierte quadradische Abstände der Residuen (Fehler) zu einem Modell (Mittelwert, Gerade, etc.)

<center>

![**Abbildung 7**: Variablität(einschränkung) und Korrelation](Images/Variabilitaet.JPG){ width=30% }

</center>


* **KEINE Ausreißer**: der Korrelationskoeffizient ist nicht robust gegenüber Ausreißern. Dies bedeutet, dass Ausreißer den Korrelationskoeffizienten sowohl künstlich erhöhen als auch künstlich senken können.

<center>

![**Abbildung 8**: Einfluss von Ausreißer bei linearer Modellbildung](Images/Ausreisser.JPG){ width=30% }

</center>

* **KEINE Kluster**: es kann vorkommen, dass zwei oder mehr Gruppen eine Korrelation zeigen, die eigentlich getrennt untersucht werden müssten. Dieses Problem wird oft auch mittels **partieller Korrelation** umgangen, bei der mögliche Drittvariablen statistisch konstant gehalten werden.

<center>

![**Abbildung 9**: Kluster und deren Auswirkung bei linearer Modellierung](Images/Cluster.JPG){ width=30% }

</center>


## Partial und Semipartialkorrelation {-}


## Korrelationstechniken {-}
# (PART\*) Teil II: Multiple lineare Regression {-}

# WarmUp MLR {-}

Die multiple lineare Regressionsanalyse (MLR) untersucht, welchen Beitrag mehrere Variablen (Prädiktoren, unabhängige-, exogene Variablen) gemeinsam, aber auch spezifisch zur Vorhersage einer interessierenden anderen Variablen (Kriterium,  abhängige-, endogene Variable) leisten.


```r
  # DF_6 <- read.spss("Daten/Buehner2017/Regression_bsp_6.sav", 
  #                   use.value.labels=TRUE, 
  #                   to.data.frame=TRUE, 
  #                   use.missings = TRUE)
  # bsp6 <- lm(bdi_ges ~ fie_nsb + fie_abk,
  #            data = DF_6)
  # 
  # pander(summary(bsp6))
  # 
  # pander(confint(bsp6, level=0.95))
  # 
  # library(lm.beta)
  # pander(lm.beta(bsp6))
  # 
  # 
  # bsp6b <- lm(scale(bdi_ges, center=T, scale=T) ~ scale(fie_nsb, center=T, scale=T) + scale(fie_abk, center=T, scale =T), data=DF_6)
  # pander(summary(bsp6b))
  
  album <- read_delim("Daten/Album Sales 2.dat", 
                              "\t", escape_double = FALSE, trim_ws = TRUE)
```

```
## Parsed with column specification:
## cols(
##   adverts = col_double(),
##   sales = col_double(),
##   airplay = col_double(),
##   attract = col_double()
## )
```

```r
  # View top few rows of goggles data set
  # from Discovering Statistics Using R
  # Single block example
  blk1 <- lm(sales ~ adverts + airplay, data=album)
  AAA <- apa.reg.table(blk1, table.number = 1)
  
  pander(AAA[["table_body"]])
```


--------------------------------------------------------------------
  Predictor       b         b_95%_CI      beta   beta_95%_CI    sr2 
------------- --------- ---------------- ------ -------------- -----
 (Intercept)   41.12**   [22.72, 59.53]                             

   adverts     0.09**     [0.07, 0.10]    0.52   [0.44, 0.61]   .27 

   airplay     3.59**     [3.02, 4.15]    0.55   [0.46, 0.63]   .29 

                                                                    

                                                                    

                                                                    
--------------------------------------------------------------------

Table: Table continues below

 
--------------------------------------
 sr2_95%_CI     r           Fit       
------------ ------- -----------------
                                      

 [.18, .36]   .58**                   

 [.20, .38]   .60**                   

                        R2 = .629**   

                      95% CI[.55,.69] 

                                      
--------------------------------------

```r
  # # apa.reg.table(blk1,filename="exRegTable.doc")
  # # Two block example, more than two blocks can be used
  # blk1 <- lm(sales ~ adverts, data=album)
  # blk2 <- lm(sales ~ adverts + airplay + attract, data=album)
  # apa.reg.table(blk1,blk2,filename="exRegBlocksTable.doc")
  # # Interaction product-term test with blocks
  # blk1 <- lm(sales ~ adverts + airplay, data=album)
  # blk2 <- lm(sales ~ adverts + airplay + I(adverts * airplay), data=album)
  # apa.reg.table(blk1,blk2,filename="exInteraction1.doc")
  # # Interaction product-term test with blocks and additional product terms
  # blk1<-lm(sales ~ adverts + airplay, data=album)
  # blk2<-lm(sales ~ adverts + airplay + I(adverts*adverts) + I(airplay*airplay), data=album)
  # blk3<-lm(sales~adverts+airplay+I(adverts*adverts)+I(airplay*airplay)+I(adverts*airplay),data=album)
  # apa.reg.table(blk1,blk2,blk3,filename="exInteraction2.doc")
  # #Interaction product-term test with single regression (i.e., semi-partial correlation focus)
  # blk1 <- lm(sales ~ adverts + airplay + I(adverts * airplay), data=album)
  # apa.reg.table(blk1,filename="exInteraction3.doc")
```

# Kategorielle Variablen {-}

# Mediatior-Analyse {-}

Eine häufig verwendete Form der linearen Modellierung findet man in der Theorieentwicklung und Theorieprüfung. Eine dieser Modellansätze ist bekannt als *Mediatior-Analyse*. Bei dieser Form der Analyse wird untersucht, inwieweit eine Beziehung zwischen zwei Merkmalen über ein drittes Merkmal erklärt werden kann, bzw. überhaupt erst zustande kommt. Folgendes Beispiel soll die Bedeutung eines Mediators verdeutlichen.

> Der Zusammenhang zwischen *Konzentration* $X$ (UV) und der *Intelligenz* $Y$ (AV) soll genauer untersucht werden. Auch wenn es zwischen diesen Merkmalen einen mehr oder weniger starken/schwachen Zusammenhang geben sollte, ist es es naheliegend anzunehmen, dass zumindest ein weiteres Merkmal diese Beziehung wesentlich beeinflusst. Der Literatur ist zu entnehmen, dass die exekutive Funktion *Koordination* sowohl hinsichtlich der Konzentration als auch der Intelligenz eine wichtige Rolle spielt. Es soll daher die Hypothese geprüft werden, dass dieses Merkmal den Zusammenhang zwischen Konzentration und Intelligenz vermittelt - also mediiert. Mittels einer Mediatior-Analyse sollte daher diese Theorie geprüft werden. Wir bezeichnen das Merkmal Koordination mit $M$.

Es gibt nun drei Ansätze den Effekt eines Mediatiors zu prüfen:

  1. Causal Steps Approach (CSA) 
  2. Test of Joined Siginificance (TJS)
  3. Difference in Coefficient Methods (DCM)

Die Empfehlungen der Literatur können wie folgt zusammengefasst werden: Es sollte die Product of Coefficient Methode (PCM)  mit Bootstrap  in Kombination mit dem als Test of Joined Significance (TJS)  beschriebenen Vorgehen durchgeführt werden. Dabei sollte immer die Interpretation von unstandardisierten Regressionsgewichten (Rucker et al., 2011) erfolgen sowie die Reliabilitätsschätzung des Mediators über 0.90  liegen (vgl. Hoyle & Robinson, 2004). Es wird empfohlen, die Stichprobe so groß wie möglich zu wählen und insbesondere auf Suppressionseffekte zu achten.

Folgende Abbildung stellt den eben dargestellten Sachverhalt nochmals graphisch dar:

<!-- <center> -->

<!-- ![**Abbildung 10**: Konzeptuelles Mediator-Modell](Images/MediatorModell.JPG){ width=100% } -->

<!-- </center> -->

## Fallbeispiel 1 {-}

> Lambert (2012) hat in seiner Studie festgestellt, dass der Konsum von pornographische Material (consumption) die Treue in einer Beziehung (infidelity) negative beeinflusst. In seiner Hypothese ging er aber auch davon aus, dass eine weitere Variable, nämlich der Einsatz mit der jemand versucht eine partnerschaftliche Beziehung (commitment) aufrecht zu erhalten, einen esentlichen Einfluss auf die Beziehung zwischen consumption und infidelity ausübt. Er vermutet, dass commitment als Mediator wirkt.

## Fallbeispiel 2 {-}

In einer Fragebogenstudie wurden Daten über negative Selbstbewertung, Abhängigkeitskognitionen und Depressivität erhoben. Die Selbstbewertung und Abhängigkeitskognition wurde mit dem Fragebogen Irrationaler Einstellungen (FIE-NSB und FIE-ABK) von [@Klages] gemessen, die Depressivität (BDI-GES) mit dem Beck-Depressions-Inventar von [@Hautzinger].

### Causal Mediation Analysis 


```r
  options(digits = 2)
  
  DF_6 <- read.spss("Daten/Buehner2017/Regression_bsp_6.sav", 
                                use.value.labels=TRUE, 
                                to.data.frame=TRUE, 
                                use.missings = TRUE)
```

```
## re-encoding from UTF-8
```

```r
  set.seed(2014)
  med.fit1 <- lm(fie_nsb ~ fie_abk,           data = DF_6)
  med.fit2 <- lm(bdi_ges ~ fie_abk + fie_nsb, data = DF_6)
  med.out  <- mediate(med.fit1, med.fit2, 
                      treat="fie_abk", 
                      mediator="fie_nsb", 
                      boot=TRUE, 
                      sims=100)
  summary(med.out)
```

```
## 
## Causal Mediation Analysis 
## 
## Nonparametric Bootstrap Confidence Intervals with the Percentile Method
## 
##                Estimate 95% CI Lower 95% CI Upper p-value    
## ACME              0.391        0.291         0.53  <2e-16 ***
## ADE               0.114       -0.046         0.26    0.26    
## Total Effect      0.505        0.364         0.64  <2e-16 ***
## Prop. Mediated    0.775        0.557         1.10  <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Sample Size Used: 191 
## 
## 
## Simulations: 100
```


### Lavaan Mediation Analysis 

Das Paket *Lavaan* wurde eigentlich für Pfad- und Strukturgleichungsmodelle entwickelt, aber es lassen sich damit auch Mediationsanalysen durchführen. Folgende Vorteile bieten sich durch die Verwendung dieses Paketes:

  1. Es können robuste Schätzverfahren wie *Maximum Likelihood*, oder *Robuste Maximum Likelihood* und Bootstrapverfahren kombiniert werden.
  2. Regressionsmodelle können schnell erweitert werden, bzw. latent abzubilden.
  


```r
  medModel <- '
  #Direkter Effekt
  bdi_ges~c*fie_abk
  #Mediator
  fie_nsb~a*fie_abk
  bdi_ges~b*fie_nsb
  # indirekter Effect (a*b)
  ab := a*b
  # Totaler Effekt
  total := c + (a*b)
  '
  fit <- sem(model = medModel, data = DF_6, estimator="ML", se="boot", bootstrap=100)
  
  summary(fit, fit.measures=TRUE, standardized=TRUE)
```

```
## lavaan 0.6-3 ended normally after 12 iterations
## 
##   Optimization method                           NLMINB
##   Number of free parameters                          5
## 
##   Number of observations                           191
## 
##   Estimator                                         ML
##   Model Fit Test Statistic                       0.000
##   Degrees of freedom                                 0
##   Minimum Function Value               0.0000000000000
## 
## Model test baseline model:
## 
##   Minimum Function Test Statistic              176.345
##   Degrees of freedom                                 3
##   P-value                                        0.000
## 
## User model versus baseline model:
## 
##   Comparative Fit Index (CFI)                    1.000
##   Tucker-Lewis Index (TLI)                       1.000
## 
## Loglikelihood and Information Criteria:
## 
##   Loglikelihood user model (H0)              -1353.544
##   Loglikelihood unrestricted model (H1)      -1353.544
## 
##   Number of free parameters                          5
##   Akaike (AIC)                                2717.088
##   Bayesian (BIC)                              2733.349
##   Sample-size adjusted Bayesian (BIC)         2717.511
## 
## Root Mean Square Error of Approximation:
## 
##   RMSEA                                          0.000
##   90 Percent Confidence Interval          0.000  0.000
##   P-value RMSEA <= 0.05                             NA
## 
## Standardized Root Mean Square Residual:
## 
##   SRMR                                           0.000
## 
## Parameter Estimates:
## 
##   Standard Errors                            Bootstrap
##   Number of requested bootstrap draws              100
##   Number of successful bootstrap draws             100
## 
## Regressions:
##                    Estimate  Std.Err  z-value  P(>|z|)   Std.lv  Std.all
##   bdi_ges ~                                                             
##     fie_abk    (c)    0.114    0.081    1.397    0.162    0.114    0.083
##   fie_nsb ~                                                             
##     fie_abk    (a)    0.507    0.073    6.952    0.000    0.507    0.420
##   bdi_ges ~                                                             
##     fie_nsb    (b)    0.771    0.077   10.033    0.000    0.771    0.681
## 
## Variances:
##                    Estimate  Std.Err  z-value  P(>|z|)   Std.lv  Std.all
##    .bdi_ges          60.722    5.384   11.278    0.000   60.722    0.482
##    .fie_nsb          80.736    8.632    9.353    0.000   80.736    0.823
## 
## Defined Parameters:
##                    Estimate  Std.Err  z-value  P(>|z|)   Std.lv  Std.all
##     ab                0.391    0.071    5.510    0.000    0.391    0.286
##     total             0.505    0.079    6.368    0.000    0.505    0.369
```

```r
  parameterEstimates(fit, boot.ci.type = "bca.simple")
```

```
## Warning in norm.inter(t, adj.alpha): extreme order statistics used as
## endpoints
```

```
##       lhs op     rhs label   est    se    z pvalue ci.lower ci.upper
## 1 bdi_ges  ~ fie_abk     c  0.11 0.081  1.4   0.16   -0.028     0.26
## 2 fie_nsb  ~ fie_abk     a  0.51 0.073  7.0   0.00    0.377     0.66
## 3 bdi_ges  ~ fie_nsb     b  0.77 0.077 10.0   0.00    0.622     0.92
## 4 bdi_ges ~~ bdi_ges       60.72 5.384 11.3   0.00   52.171    72.14
## 5 fie_nsb ~~ fie_nsb       80.74 8.632  9.4   0.00   64.436   100.93
## 6 fie_abk ~~ fie_abk       67.24 0.000   NA     NA   67.243    67.24
## 7      ab :=     a*b    ab  0.39 0.071  5.5   0.00    0.283     0.57
## 8   total := c+(a*b) total  0.50 0.079  6.4   0.00    0.362     0.68
```

```r
  # inspect( fit, "rsquare" )  
```


# Moderator-Analyse {-}

Eine andere Form der Modellierung zur Theorientwicklung und Prüfung ist die *Moderatior-Analyse*.
