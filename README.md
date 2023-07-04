### Real Data Example: Addiction Research



### Participants

- Mattes Grundmann
- Oya Bazer
- Jakob Zschocke

### Abstract

While Randomized Controlled Trials (RCTs) are the gold standard for causal inference, these are often not feasible in addiction research for ethical and logistic reasons; for example, when studying the impact of smoking on cancer. 
Instead, observational data from real-world settings are increasingly being used to inform clinical decisions and public health policies. This paper presents the framework for potential outcomes for causal inference and summarizes best practices in causal analysis for observational data. Among them: Matching, Inverse Probability Weighting (IPW), and Interrupted Time-Series Analysis (ITSA). 
These methods will be explained using examples from addiction research, and the resulting results will be compared.

### Background
### Explanation Matching and Inverse Probability Weighting
Die hier behandelten Methoden sind das Matching & Inverse Probability Weighting. Grundsätzlich sind Randomisierte Experimente der Goldstandard um kausale Rückschlüsse ziehen zu können. Doch diese sind in der Realität häufig schwierig durchführbar. Nun gibt es verschiedene Methoden, um mit nicht randomisierten observationellen Daten umzugehen. Zwei dieser Methoden werden hier behandelt: Inverse Probability Weighting und Matching. 
#### Matching 
Ziel des Matchings ist es, ein Gleichgewicht zwischen der Behandlungs- und der Kontrollgruppe herzustellen, so wie es in RCTs grundsätzlich vorhanden ist. Dieses Gleichgewicht bedeutet konkret, dass die Verteilungen aller beobachteten Kovariaten in beiden Gruppen ähnlich sind. Eine Variante des Matchings ist das One-to-one Matching. Diese Methode stellt jedem Individuum der Treatment Gruppe ein passendes Individuum der Kontrollgruppe gegenüber. Dies geschieht anhand eines Propensity Scores. Dieser stellt die Wahrscheinlichkeit dar, das Treatment zu bekommen, gemessen an allen Variablen, die darauf Einfluss nehmen können. In der Case Study stellt das Rauchen beispielhaft das Treatment dar. Die beiden Gruppen "Raucher" und "nicht-Raucher" unterscheiden sich jedoch verschiedener Variablen, z.B. des Schulabschlusses. Durch das Matching wurde jeder Person ein Individuum mit einem ähnlichen Propensity Score gegenüber gestellt. Unmatched Individuen wurden ausgeschlossen. Die beiden Gruppen weisen nun deutliche geringere Unterschiede in den einzelnen Variablen wie z.B. Schulabschluss auf. Nachdem das Matching erfolgreich war, kann nun mittels der einfachen Regression, der "Average Treatment Effect of the Treated" berechnet werden.  

#### Inverse Probability Weighting (IPTW)
Auch beim IPTW ist es das Ziel, ein Gleichgewicht zwischen der Treatment und Kontrollgruppe herzustellen. Hierzu werden verschiedene Gewichtungen verwendet. Dabei werden gewichtete Daten als eine Art imaginäre Population verstanden, bei der der einzige Unterschied zwischen den Gruppen darin besteht, ob das Treatment erhalten wurde oder nicht. Das Gewicht für Individuen der Treatment Gruppe ist die Inverse ihrer Propensity Scores, also 1 geteilt durch den Propensity Score. Das Gewicht für Individuen der Kontrollgruppe berechnet sich dagegen aus der Inverse von 1 minus des Propensity Scores. Diese Gewichte werden als unstabilisierte Gewichte bezeichnet. Der Grund dafür ist, wenn ein Individuum eine geringe Wahrscheinlichkeit hat, ein Treatment zu bekommen, am Ende das Treatment aber bekommt führt dies dazu, dass dieses Individuum ein hohes Gewicht hat und somit die Varianz des geschätzten Kausalen Effekts wesentlich erhöht. In der hier behandelten Studie wurde das IPTW anhand des Beispiels "Rauchen und psychologische Störung" illustriert. Dies hat gezeigt, dass das IPTW zu einer deutlichen Verbesserung des Gleichgewichts zwischen den Gruppen geführt hat. Der kausale Effekt des Treatments kann nun geschätzt werden. 

![](figures/Matching_IPW.png)

#### Instrumental Variable Method

Sowohl das Matching, als auch die IPTW-Methode können zwar zur Prüfung des Confoundings von gemessenen Kovariaten genutzt werden, gehen aber davon aus, dass kein ungemessenes Confounding existiert. Diese Annahme ist nicht überprüfbar und wird sehr wahrscheinlich verletzt, da nicht alle Störvariablen gemessen und in Matching- und Gewichtungsverfahren aufgenommen werden könnnen. Um das ungemessene Confounding zu kontrollieren, wurde die Instrumental Variable Method eingeführt:
Bei dieser Methode wird eine Intrumentalvariable gesucht, welche (i) einen direkten kausalen Effekt auf das Treatment hat, (ii) keinen direkten kausalen Effekt auf das Ergebnis hat und (iii) das Ergebnis nicht durch andere Variablen als das Treatment beinflusst. Dies wird durch die folgende Grafik veranschaulicht. 

![](figures/Instrumentalvariable.png)

Die Methode zur Bestimmmung eines kausalen Effektes funktioniert nach dem folgenden Prinzip: 
Ist eine Instrumentalvariable identifiziert worden, kann über eine Regression (kleinste Quadrate Methode) für jeden Induviduum die counfounding freie Ausprägung des Treatments geschätzt werden, auf Basis derer durch eine weitere Regression der kausale Effekt auf das Ergebnis geschätzt werden kann. Das Ausfindigmachen einer Instrumentalvariable stellt die größte Schwierigkeit dieser Methode dar. 

#### Interrupted Time-Series Analysis

Unter Verwendung von Daten aus wiederholten Beobachtungen eines Ergebnisses wird in einer unterbrochenen Zeitreihenanalyse (ITSA) die Entwicklung des Ergebnisses vor und nach der Intervention.
Dies kann konzeptualisiert werden auf der Grundlage des kontrafaktischen Rahmens als Vergleich dessen was ohne die Intervention geschehen wäre (ein kontrafaktisches Szenario) mit dem, was nach einer Intervention beobachtet wurde. 
Eine Kontrollreihe, bei der die Intervention nicht durchgeführt wird, kann um die kausale Schlussfolgerung zu verstärken.

Es ist auch wichtig, dass eine vergleichbare Kontrollreihe aus einer Population ausgewählt wird, die derjenigen, die der Intervention ausgesetzt ist, möglichst ähnlich ist
mit Ausnahme der Tatsache, dass die eine die Intervention erhält und eine nicht. Die Kontrollreihe kann beispielsweise von einem anderen Ort mit ähnlichen Bevölkerungsmerkmalen stammen, oder sie kann aus dem historischen Trend in derselben Population stammen.

Eine unterbrochene Zeitreihenanalyse mit Kontrolle basiert häufig auf das Regressionsmodell:

Y<sub>t</sub> = &beta;<sub>0</sub> + &beta;<sub>1</sub>(time) + &beta;<sub>2</sub>(post intervention) + &beta;<sub>3</sub>(post intervention &times; time)  + &beta;<sub>4</sub>(group) + &beta;<sub>5</sub>(group &times; time) + &beta;<sub>6</sub>(group &times; post intervention) + &beta;<sub>7</sub>(time &times; post intervention &times; group) + &epsilon;<sub>t</sub>

![](figures/InterruptedTimeSeriesAnalysis.png)

### Results & Interpretation


### Current State and Call for Extension

- [ ] Briefly summarize the state of your data product as of the end of the course
- [ ] Briefly summarize what could be added or improved in the future


## Organization of the Repo

We'd recommend you to organize your repo as follows.

* Include figures (`.jpg`, `.png`, ...) in a subdirectory called `figures/`, see [this example](figures/logo.png)
* Include data files (`.csv`, `.rda`, ...) in a subdirectory called `data/`, see [this example](data/experiment_data_counterfactual.rda)
* Include your R code (`.R` files) in a subdirectory called `R`, see [this example](R/my_function.R)
* In case you use quarto for your data product, include your `.qmd` files here, see [this example](demo_repo.qmd)

These basic recommendations are intended to give you a bit structure. You can deviate from them as you like but please make sure others should be able to understand what you did.
