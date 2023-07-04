### Real Data Example: Addiction Research



### Participants

- Mattes Grundmann
- Oya Bazer
- Jakob Zschocke

### Abstract

While Randomized Controlled Trials (RCTs) are the gold standard for causal inference, these are often not feasible in addiction research for ethical and logistic reasons; for example, when studying the impact of smoking on cancer. 
Instead, observational data from real-world settings are increasingly being used to inform clinical decisions and public health policies. This paper presents the framework for potential outcomes for causal inference and summarizes best practices in causal analysis for observational data. Among them: Matching, Inverse Probability Weighting (IPW), and Interrupted Time-Series Analysis (ITSA). 
These methods will be explained using examples from addiction research, and the resulting results will be compared.

### Explanation Matching and Inverse Treatment Probability Weighting
The methods discussed here are Matching and Inverse Probability Treatment Weighting (IPTW). Randomized experiments are generally considered the gold standard for drawing causal inferences. However, in reality, they are often difficult to conduct. Therefore, there are various methods available to handle non-randomized observational data. Two of these methods, Inverse Probability Treatment Weighting and Matching, are discussed here.

#### Matching 
The goal of matching is to establish the balance between treatment and control group, as it generally is in RTCs. Specificly, it targets similar distributions of all observed covariates in both treatment and control group. A variant of matching is one-to-one matching which matches each individual in the treatment group with an individual in the control group based on a propensity score. This score represents the probability of receiving the treatment, measured by all variables that can influence it. It is often estimated using logistic regression with pretreatment covariates. Unmatched individuals will be excluded. After matching, the Average Treatment effect among the Treated (ATT) can now be calculated using simple regression.

#### Inverse Probability Weighting (IPTW)
IPTW is a statistical technique used in observational studies to estimate the causal effect of a treatment or intervention. Its primary objective is to address potential confounding variables and (like the matching method) achieve balance between the treatment and control groups. In IPTW, propensity scores are calculated for each individual in the study population. These scores represent the probability of receiving the treatment, given a set of observed covariates, like in this case study religion or education. 
Once the propensity scores are obtained, weights are assigned to each individual based on their propensity score. These weights help balance the groups by giving more weight to individuals who are less likely to receive the treatment, and vice versa.
The weighted data is then used to estimate the causal effect of the treatment using appropriate statistical methods such as regression models or stratification techniques.

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

In conclusion, we have explored three powerful methods in causal inference which are part of the case study "Causal inference with observational data in addiction research": Matching, Inverse Probability Treatment Weighting (IPTW), and Time Series Analysis. Each of these methods offers unique approaches to address causal questions in observational data. To explain Matching and IPTW the used study investigates the causal effect of smoking on psychological distress.

We saw, that Matching is a valuable technique that aims to create comparable treatment and control groups by pairing observations based on their similarity in propensity scores. IPTW assigning weights to observations based on their propensity scores, effectively balancing treatment and control groups. So these two methods have the same goal by creating balance between treatment and control group und thereafter on that base estimating the Average Treatment Effect. 

Time Series Analysis, on the other hand, allows us to explore the dynamics and relationships among variables over time. It provides insights into the causal effects of interventions or treatments by examining how changes in one variable influence another variable in a time-dependent manner.

In summary, by employing Inverse Probability Weighting, Matching, and Time Series Analysis, researchers can enhance their ability to understand and estimate causal effects in diverse settings, contributing to evidence-based decision-making and advancing our understanding of complex phenomena.


### Current State and Call for Extension

While we have covered the basics of Matching, IPTW, and Interrupted Time-Series Analysis, there are still several avenues for further exploration and extension in this field. It is also crucial to acknowledge the inclusion of the instrumental variable method as another powerful approach in the study. Additionally, the use of Directed Acyclic Graphs (DAGs) was highlighted in the study as a graphical tool for visualizing and understanding the causal relationships between variables.
By integrating the instrumental variable method and leveraging the insights offered by DAGs, the capacity to draw reliable causal inferences can be expanded. These extensions can contribute to a more comprehensive understanding of the underlying causal mechanisms and improve the validity of causal inferences drawn from observational data in addiction research.
