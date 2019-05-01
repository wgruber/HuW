

# (PART\*) Teil III: Dummy-Codierung {-}


```r
    # Field R - S302 ff
    rm(list = ls())
    graphics.off()
    if (!require("pacman")) install.packages("pacman")
    pacman::p_load(pander)
    options(digits=3)
```

# Kategorielle Prädiktoren {-}

Bei lineare Modellen ist häufig neben intervallskalierten Prädiktorvariablen auch die Verwendung von kategoriellen Variablen von Interesse. So lange der verwendete Prädiktor nur zwei Ausprägungen hat (z.B. männlich/weiblich, Ja/Nein, etc.), stellt dies auch kein Problem dar.

## Mehrstufiger kategorieller Prädiktor {-}

Während eines dreitägigen Musikfestivals wurde bei einer Anzahl freiwilliger TeilnehmerInnen der "Hygienezustand" gemessen (Variablen *day1*, *day2*, *day3*). Der Wertebereich der Messung liegt zwischen 0 und 4, mit 0 = smell like s..t, bis 4 = smell like freshly baked bread[^9]. Darüber hinaus wurden die TeilnehmerInnen über ihre jeweilige Zuordnung zu eine bestimmten, persönlich bevorzugten Musikrichtung (*music*) befragt. Bei dem Fesitval gaben die TeilnehmerInnen insgesamt vier verschiedenen Musikrichtungen an: *Metaller*, *Crusty*, *Indie*, *NMA* (= No Music Affiliation). Nach Erfassung der Daten wurde die Differenz der Hygienewerte zwischen dem letzten und dem ersten Tag des Festivals berechnet und in der Variablen *change* gespeichert:

[^9]: Daten und Beispiel aus [@Field.2017], Kapitel 7.12.1


--------------------------------------------------------------------------
 &nbsp;   ticknumb           music            day1   day2   day3   change 
-------- ---------- ------------------------ ------ ------ ------ --------
 **1**      2111            Metaller          2.65   1.35   1.61   -1.04  

 **2**      2229             Crusty           0.97   1.41   0.29   -0.68  

 **10**     2504     No Musical Affiliation   1.11   0.44   0.55   -0.56  

 **12**     2510             Crusty           0.82   0.2    0.47   -0.35  

 **14**     2515     No Musical Affiliation   1.76   1.64   1.58   -0.18  

 **21**     2549             Crusty           2.17   0.7    0.76   -1.41  
--------------------------------------------------------------------------

Offenbar liegt bei der Variablen *music* ein Faktor mit mehr als 2 Stufen (es sind 4) vor. Da die Verwendung von katetoriellen Variablen in einem linearen Modell eine Stufenanzahl von 2 voraussetzt, kann durch geschicktes Kodieren der Variablen diese Voraussetzung auch für mehrstufige Variablen erreicht werden. 

# Dummy Kodierung {-}

Man nennt diesen Vorgang auch **Dummy Kodierung**. Die Vorgehensweise ist dabei:

1. Die Anzahl der neuen (Dummy) Variablen ist die Anzahl der Stufen des Prädiktors - 1 $(N_{DummyVars} = N_{Stufen} - 1)$
2. Man legt so viele neue Variablen (Dummy-Variablen) an, wie man (im ersten Schritt) als Anzahl der Gruppen berechnet hat.
3. Wahl einer Bezugsgruppe (Baseline-Bedingung). üblicherweise die Kontrollgruppe, falls keine vorhanden wählt man am besten die Gruppe, in der die meisten Personen/Fälle vorliegen.
4. Allen Dummy-Variablen für die gewählte Baselinegruppe den Zahlenwert 0 zuweisen.
5. Der ersten Dummy-Variablen für die erste Gruppe die man gegen die Baselinegruppe vergleichen will den Wert 1 zuweisen, den restlichen Gruppen den Wert 0.
6. Wiederholung des Schrittes 5, bis alle Dummy-Variablen entsprechend codiert wurden.
7. Alle Dummy-Variablen ins Modell aufnehmen!

|               | DVar1 | DVar2 |DVar2 |
|:--------------|:-----:|:-----:|:----:|
| Crusty        |   1   |   0   |  0   |
| Indie Kid     |   0   |   1   |  0   |
| Metaller      |   0   |   0   |  1   |
| No Affliation |   0   |   0   |  0   |

Bei der linearen Modellierung in R werden kategorielle Daten im Modell automatisch Dummy-Kodiert. Will man jedoch eine spezielle Anordung der Gruppen, sollte man wissen, wie eine händische Kodierung einfach durchgeführt werden kann. Im folgenden Code werden diese Möglichkeiten dargestellt:


```r
    # Automatisch ohne Bezeichnung der Dummyvariablen
    contrasts(DF$music) <- contr.treatment(4, base = 4)
    # Manuel mit Bezeichnung der Dummyvariablen
    crusty_v_NMA        <- c(1,0,0,0)
    indie_v_NMA         <- c(0,1,0,0)
    metal_v_NMA         <- c(0,0,1,0)
    contrasts(DF$music) <- cbind(crusty_v_NMA, indie_v_NMA, metal_v_NMA)
    pander(attr(DF$music, "contrasts"), digits = 3)
```


-----------------------------------------------------------------------
           &nbsp;             crusty_v_NMA   indie_v_NMA   metal_v_NMA 
---------------------------- -------------- ------------- -------------
         **Crusty**                1              0             0      

       **Indie Kid**               0              1             0      

        **Metaller**               0              0             1      

 **No Musical Affiliation**        0              0             0      
-----------------------------------------------------------------------

# Modelle mit kategoriellen Variablen {-}

Sind die Dummy-Variablen angelegt, kann damit auch das Modell erstellt werden. Im nachfolgenden Beispiel wird die Variable *change* durch die Dummy-Kodierten Prädiktoren modelliert. Die erste Tabelle zeigt die durchschnittlichen *change*-Werte pro Musikzugehörigkeitsgruppe.

<center>


```r
    pander(round(tapply(DF$change, DF$music, mean, na.rm = TRUE), 3))
```


--------------------------------------------------------
 Crusty   Indie Kid   Metaller   No Musical Affiliation 
-------- ----------- ---------- ------------------------
 -0.966    -0.964      -0.526            -0.554         
--------------------------------------------------------

```r
    mod_dummy_1 <- lm(change ~ music, data = DF)
    AllRes      <- summary(mod_dummy_1)
    pander(anova(mod_dummy_1), digits = 3)
```


-----------------------------------------------------------
    &nbsp;       Df    Sum Sq   Mean Sq   F value   Pr(>F) 
--------------- ----- -------- --------- --------- --------
   **music**      3     4.65     1.55      3.27     0.0237 

 **Residuals**   119    56.4     0.474      NA        NA   
-----------------------------------------------------------

Table: Analysis of Variance Table

```r
    pander(summary.lm(mod_dummy_1), digits = 3)
```


--------------------------------------------------------------------
        &nbsp;           Estimate   Std. Error   t value   Pr(>|t|) 
----------------------- ---------- ------------ --------- ----------
    **(Intercept)**       -0.554      0.0904      -6.13    1.15e-08 

 **musiccrusty_v_NMA**    -0.412      0.167       -2.46     0.0152  

 **musicindie_v_NMA**     -0.41       0.205        -2       0.0477  

 **musicmetal_v_NMA**     0.0284       0.16       0.177      0.86   
--------------------------------------------------------------------


---------------------------------------------------------------
 Observations   Residual Std. Error    $R^2$    Adjusted $R^2$ 
-------------- --------------------- --------- ----------------
     123              0.6882          0.07617      0.05288     
---------------------------------------------------------------

Table: Fitting linear model: change ~ music

</center>

Wesentliche Kennzahlen des Ergebnisses:

- $R^2 = 0.076$: d.h., dass $7.6\%$ der Variabilität in der Änderung der Hygenewerte zwischen ersten und dritten Tag (*change*) durch die Zugehörigkeit zu einer Musikgruppe erklärt werden.
- $F(3, 119) = 3.27; p = .053$ gibt an, dass die $7.6\%$ Varianzaufklärung statistisch signifikant ist. Das Modell ist also signifikant besser als kein Modell zu verwenden.
- *musiccrusty\_vs\_NMA*: Differenz zwischen der *NMA* und *crusty* Gruppe. Betrachtet man die Differenz der Mittelwerte (siehe obige Tabelle) zwischen $crusty - NMA = -.966 - (-0.554) = -0.412$, stellt man fest, dass diese Differenz dem Estimate, also dem $b$-Koeffizienten entspricht. Offenbar ist die Änderung der Hygienewerte bei *crusty* höher als bei der *NMA* $\rightarrow$ *crusties* sind größere Schweindln wie die *NMA* Leute. **Die $b$-Werte geben also die relative Änderung zur Baselinegruppe an!**
- $t = -2.46, p = .015$: tested ob die Differenz signifikant unterschiedlich zu einer Null-Differenz (kein Unterschied) in den Hygienebedingungen ist. Im vorliegenden Fall handelt es sich um eine signifikante Abnahme der Hygienewerte, wenn man von *NMA* auf *crusty* wechselt.

Die restlichen Koeffizienten sind in gleicher Weise zu interpretieren. 
