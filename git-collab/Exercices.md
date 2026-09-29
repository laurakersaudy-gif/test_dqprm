# DQPRM

## Exercices de mise en pratique en Python

#### Albertine Dubois - albertine.dubois@cea.fr, Ludovic Ferrer - Ludovic.Ferrer@ico.unicancer.fr & Marion Savanier - marion.savanier@cea.fr

Version 2026


---

## Exercice 1 - Calcul automatique de l'IMC d'un individu

Ecrire une fonction qui calcule l'indice de masse corporelle (IMC) d'un(e) patient(e) donné(e)

* La fonction nécessitera 2 paramètres en entrée, le poids (en $kg$) et la taille (en $m$), et renverra la valeur de l'IMC en sortie
* Suivant la valeur d'IMC, la fonction devra également fournir une interprétation du résultat (maigreur, IMC normal, surpoids, obésité, obésité massive)
* Tester la fonction avec différents couples de valeurs poids/taille

**Rappel :**

<img width=400 src='./data/imc.gif'>

---


```python
def indice_de_masse_corporelle(m,s):
    imc = m / (s*s) # Indiquer la formule pour calculer l'IMC.
    print("IMC = {:0.1f}".format(imc))
    if imc <= 18.5:
        print("Valeur d'IMC indiquant une maigreur")
    elif 18.5 < imc <= 24.9 :
        print("Valeur d'IMC normal")
    elif 24.9 < imc <= 29.9 :
        print("Valeur d'IMC indiquant un surpoids")
    elif 29.9 < imc <= 40 :
        print("Valeur d'IMC indiquant un obésité")
    else :
        print("Valeur d'IMC indiquant une obésité massive")
    return imc

imc = indice_de_masse_corporelle(65,1.72)

```

    IMC = 22.0
    Valeur d'IMC normal


## Exercice 2 - Suivi glycémie
-----------

**Question 1.** Lire avec la bibliothèque Pandas le fichier `glycemie.csv` contenu dans le dossier `data` (attention au séparateur décimal : . ou , ?)

**Question 2.** Tracer sur un même graphique, dont vous fixerez les dimensions, les courbes de la variation au cours du temps de la glycémie de ce patient pour chacun des points de mesure renseigné par colonne

**Question 3.** Indiquer le nom des axes et la légende


```python
import pandas as pd

df = pd.read_csv("data/glycemie.csv").dropna(axis=1)
df

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>A jeun</th>
      <th>Avant déj.</th>
      <th>Avant dîner</th>
      <th>Coucher</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>mardi 01 juin</td>
      <td>1.18</td>
      <td>2.36</td>
      <td>2.36</td>
      <td>1.58</td>
    </tr>
    <tr>
      <th>1</th>
      <td>mardi 02 juin</td>
      <td>1.25</td>
      <td>2.56</td>
      <td>2.31</td>
      <td>2.35</td>
    </tr>
    <tr>
      <th>2</th>
      <td>mardi 03 juin</td>
      <td>1.24</td>
      <td>2.89</td>
      <td>2.30</td>
      <td>2.45</td>
    </tr>
    <tr>
      <th>3</th>
      <td>mardi 04 juin</td>
      <td>1.32</td>
      <td>3.01</td>
      <td>2.58</td>
      <td>2.35</td>
    </tr>
    <tr>
      <th>4</th>
      <td>mardi 05 juin</td>
      <td>1.04</td>
      <td>3.05</td>
      <td>1.65</td>
      <td>2.36</td>
    </tr>
    <tr>
      <th>5</th>
      <td>mardi 06 juin</td>
      <td>1.09</td>
      <td>3.65</td>
      <td>1.74</td>
      <td>2.35</td>
    </tr>
    <tr>
      <th>6</th>
      <td>mardi 07 juin</td>
      <td>0.98</td>
      <td>2.58</td>
      <td>1.25</td>
      <td>2.14</td>
    </tr>
    <tr>
      <th>7</th>
      <td>mardi 08 juin</td>
      <td>1.25</td>
      <td>2.14</td>
      <td>1.36</td>
      <td>1.25</td>
    </tr>
    <tr>
      <th>8</th>
      <td>mardi 09 juin</td>
      <td>1.39</td>
      <td>1.98</td>
      <td>1.63</td>
      <td>1.58</td>
    </tr>
    <tr>
      <th>9</th>
      <td>mardi 10 juin</td>
      <td>1.87</td>
      <td>1.51</td>
      <td>1.95</td>
      <td>1.85</td>
    </tr>
    <tr>
      <th>10</th>
      <td>mardi 11 juin</td>
      <td>0.96</td>
      <td>1.65</td>
      <td>1.25</td>
      <td>1.47</td>
    </tr>
    <tr>
      <th>11</th>
      <td>mardi 12 juin</td>
      <td>1.11</td>
      <td>1.58</td>
      <td>1.35</td>
      <td>1.74</td>
    </tr>
    <tr>
      <th>12</th>
      <td>mardi 13 juin</td>
      <td>1.08</td>
      <td>2.01</td>
      <td>1.68</td>
      <td>1.98</td>
    </tr>
    <tr>
      <th>13</th>
      <td>mardi 14 juin</td>
      <td>1.56</td>
      <td>2.32</td>
      <td>1.86</td>
      <td>1.89</td>
    </tr>
    <tr>
      <th>14</th>
      <td>mardi 15 juin</td>
      <td>1.25</td>
      <td>1.56</td>
      <td>1.47</td>
      <td>1.35</td>
    </tr>
  </tbody>
</table>
</div>




```python
import matplotlib.pyplot as plt

plt.figure(figsize=(12, 5))

for time in df.columns[1:]:
    if 'AUCUN' not in time:
        plt.scatter(df.index, df[time], label=str(time))

plt.xticks(rotation=45)
plt.ylabel('Glycémie (g/l)', size=14)
plt.xlabel('Date', size=14)
plt.legend()

plt.show()
```


    
![png](Exercices_files/Exercices_5_0.png)
    


## Exercice 3 - Dosimétrie
-----------

### Contexte
**Radioembolisation** dans le traitement d'un cancer hépatique à l'aide de **microsphères de verre** marquées à l'$^{90}Y$.

Planification de l'activité à administrer à l'aide d'une acquisition tomographique réalisée au $^{99m}Tc$-MAA

- Déterminer l'activité d'$^{90}Y$ pour délivrer une dose absorbée limite de 120 Gy au lobe hépatique contenant la tumeur
- Déterminer la dose absorbée à la tumeur

Pour illustrer le propos de l'impact de la dosimétrie prévisionnelle dans le traitement des hépatocarcinome, voir [ici](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4731431/#!po=84.5455).

### Modéle de partionnement

[Ho et al.](https://www.ncbi.nlm.nih.gov/pubmed/8753684) ont défini un modèle de calcul basée sur la connaissance de **la répartition de l'activité** dans le foie après la perfusion des microsphères radioactives. Le calcul de la dose absorbée aux  volumes d'intérêt est estimée par la méthologie du *MIRD*.

L'activité perfusée dans le foie se répartie dans lui-même et les poumons s'il existe un *shunt* entre ce premier et ces derniers.

- L'activité dans les poumons est estimée par $A_L = A_{inj.} \times \frac{L}{100}$
    - L pourcentage de shunt pulmonaire
- L'activité dans le foie comprenant la partie saine ($A_N$) et tumorale ($A_T$) est estimée par $A_N+A_T = A_{inj.} (1-\frac{L}{100})$
- Le rapport tumeur/foie sain $r=\frac{\frac{A_T}{m_T}}{\frac{A_N}{m_N}}$ peut être estimé à partir des pseudo-concentrations d'activité mesurées par la segmentation dans la tumeur et le foie sain. A l'aide de l'équation précédente, on peut ensuite exprimer les activités dans le foie sain ($A_N$) et dans la tumeur ($A_T$) en fonction de ce rapport et de $A_{inj.}$.

### Rappels

#### Equation du MIRD

$$ \bar{D}_{k \leftarrow h} = \sum_{h} \tilde{A}_{h} \times S_{k \leftarrow h} $$

où $\tilde{A}_{h}$ est l'activité cumulée dans la source i.e: le **nombre total de désintégration dans la source h** et $S_{k \leftarrow h}$ **le facteur S** liant la source h à la cible k.

#### Equation simplifiée
Dans le cas la cas d'une **radioembolisation**,
- toute l'activité injectée est piègée dans le foie (si pas de *shunt pulmonaire*)
- seule la décroissance physique du radionucléide intervient (pas d'élimination biologique du traceur).

Cela simplifie le calcul

$$\bar{D}_{foie} = A(0)_{foie} \times \frac{T_{phys.}}{ln\,2} \times S_{foie \leftarrow foie}$$

Dans le cas où on utilise un radionucléide qui émet **uniquement des émissions $\beta^-$**, la dernière équation est équivalente à :

$$ \bar{D}_{foie} = A(0)_{foie} \times \frac{T_{phys.} \times \Delta}{ln\,2\times m_{foie}}$$

où $\Delta$ représente **l'énergie totale émise par transition** et $m_{foie}$ la masse du foie.

En réorganisant les équations, on obtient l'activité à injecter pour une dose absorbée déterminée

$$ A(0)_{foie} = \frac{\bar{D}_{foie} \times m_{foie} \times ln\,2}{T_{phys.}\times \Delta}$$

Dans le cadre d'un traitement par radioembolisation avec des µ-sphères de verre, on souhaite délivrer une dose absorbée de 120 Gy dans **l'ensemble du foie perfusé**.

**Question 1.** Lire avec Pandas le fichier `Table.csv` contenu dans le dossier `data` qui contient les valeurs des différents volumes d'intérêt ainsi que les activités dans ces volumes (attention au format du séparateur de colonnes). La première colonne sera utilisée comme index des lignes.

**Question 2.** Ajouter une colonne au tableau avec les masses des différents volumes d'intérêt (on prendra comme valeur de masse volumique $\rho=1.03\ g/cm^3$)

**Question 3.** Déterminer l'activité à injecter dans le lobe droit pour atteindre cette dose absorbée limite en utilisant l'équation simplifiée du MIRD

**Question 4.** Déterminer la dose absorbée à la tumeur pour cette activité injectée

NB. Il n'y a pas eu de shunt pulmonaire identifié durant cette procédure

Données :
* Période de l'yttrium 90 : 64,05 $heures$
* Energie totale émise par transition : 0.9336 $\frac{MeV}{Bq.s}$
* On considère que les tissus hépatiques et la tumeur ont une masse volumique égale à 1.03 $\frac{g}{cm^3}$


```python
import pandas as pd

df1 = pd.read_csv("data/Table.csv",sep='\t').set_index('Segment')
# df1

```


```python
df1['Masse [g]'] = df1['Volume [cm3]'] * 1.03
df1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Number of voxels [voxels]</th>
      <th>Volume [mm3]</th>
      <th>Volume [cm3]</th>
      <th>Minimum</th>
      <th>Maximum</th>
      <th>Mean</th>
      <th>Median</th>
      <th>Standard Deviation</th>
      <th>Masse [g]</th>
    </tr>
    <tr>
      <th>Segment</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>foie_total</th>
      <td>13024</td>
      <td>1124660.00</td>
      <td>1124.66000</td>
      <td>1</td>
      <td>8735</td>
      <td>1153.240</td>
      <td>1146</td>
      <td>941.664</td>
      <td>1158.399800</td>
    </tr>
    <tr>
      <th>tum_dome_CT</th>
      <td>125</td>
      <td>10794.20</td>
      <td>10.79420</td>
      <td>1651</td>
      <td>8735</td>
      <td>3923.500</td>
      <td>3629</td>
      <td>1466.790</td>
      <td>11.118026</td>
    </tr>
    <tr>
      <th>lobe_droit</th>
      <td>9375</td>
      <td>809562.00</td>
      <td>809.56200</td>
      <td>31</td>
      <td>8735</td>
      <td>1526.330</td>
      <td>1384</td>
      <td>847.588</td>
      <td>833.848860</td>
    </tr>
    <tr>
      <th>tum_dome_SPECT</th>
      <td>114</td>
      <td>9844.27</td>
      <td>9.84427</td>
      <td>4163</td>
      <td>8735</td>
      <td>5341.220</td>
      <td>5034</td>
      <td>980.795</td>
      <td>10.139598</td>
    </tr>
    <tr>
      <th>lobe_gauche</th>
      <td>3653</td>
      <td>315448.00</td>
      <td>315.44800</td>
      <td>1</td>
      <td>1955</td>
      <td>195.493</td>
      <td>117</td>
      <td>207.995</td>
      <td>324.911440</td>
    </tr>
  </tbody>
</table>
</div>




```python
m_foie_lobe_d = df1.loc['lobe_droit', 'Masse [g]']
print(m_foie_lobe_d)

```

    833.8488600000001



```python
import numpy as np

delta_Mev_per_Bq_s = 0.9336
T_y90_s = 64.05 *3600
dose_foie_limite_Gy = 120
num = dose_foie_limite_Gy * m_foie_lobe_d * np.log(2)
denom = T_y90_s * delta_Mev_per_Bq_s * 1000 *1.6 *1e-4
act_1 = num/denom
print(f"L'activité à injecter est de {act_1:.2f} GBq pour atteindre {dose_foie_limite_Gy} Gy au lobe droit.")
```

    L'activité à injecter est de 2.01 GBq pour atteindre 120 Gy au lobe droit.


D'après le modèle de partitionnement, on doit estimer le  rapport de concentration entre la tumeur et le foie perfusé,


```python
ratio_tum_lobe = df1.loc['tum_dome_SPECT','Mean'] / df1.loc['lobe_droit','Mean']
print(f"Le rapport des concentrations est estimé à {ratio_tum_lobe:.2f}")
```

    Le rapport des concentrations est estimé à 3.50


Dans le cas d'**absence de shunt pulmonaire**, les équations du modèle de partionnement deviennent:

$$
\begin{align}
A_T  &= r \times A_N \frac{m_T}{m_N}\\
A_N  &= \frac{A_{inj.}}{(1 + r \times \frac{m_T}{m_N})}
\end{align}
$$


```python
m_tum =  df1.loc['tum_dome_SPECT','Masse [g]']
A_n = act_1 / (1 + ratio_tum_lobe * (m_tum/m_foie_lobe_d))
A_t = ratio_tum_lobe * A_n * m_tum/m_foie_lobe_d
print(f'Les activités dans le foie perfusé et la tumeur sont {A_n*1000:.2f} et {A_t*1000:.2f} MBq respectivement.')
```

    Les activités dans le foie perfusé et la tumeur sont 1931.50 et 82.19 MBq respectivement.


On peut alors estimer la dose à la tumeur


```python
dose_t = A_t * 1e9 * T_y90_s * delta_Mev_per_Bq_s *1.6e-13 / (m_tum * 1e-3 * np.log(2))
print(f'La dose à la tumeur est {dose_t:.2f} Gy')

```

    La dose à la tumeur est 402.79 Gy


## Exercice 4 - Analyse des données enregistrées avec un oxymètre de pouls
-----------

L’oxymètre permet de mesurer la quantité d’oxygène dont le sang est saturé. Cette mesure permet de surveiller l’état des patients sujets à des troubles respiratoires ou souffrant d’affections de l’appareil respiratoire.

Le principe utilisé pour le fonctionnement des oxymètres de pouls est basé sur la capacité d’absorption du sang des lumières rouge et infrarouge, selon leur saturation en oxygène. Le calcul du taux de saturation sanguin en oxygène noté SpO2 est basé sur le rapport entre la CHbO2 sur la CHb, respectivement concentration sanguine en oxyhémoglobine et concentration totale d’hémoglobine dans le sang.

$$ SpO_2=\frac{CHbO_2}{Chb} $$

Lorsque l'hémoglobine capte l’oxygène au niveau des poumons, il se transforme en oxyhémoglobine et se colore en rouge vif et lorsque cet oxygène est libéré au niveau des tissus, il se transforme en désoxyhémoglobine. Ces deux types d’hémoglobines possèdent un taux d’absorption différent de la lumière rouge et de la lumière infrarouge. L’oxyhémoglobine absorbe mieux la lumière infrarouge et la désoxyhémoglobine absorbe mieux la lumière rouge.

Le principe d’absorbance va permettre de déterminer le taux de saturation en oxygène d’un milieu. En effet, la quantité de lumière absorbée par un milieu est proportionnelle à sa concentration en une espèce chimique donnée, selon la loi de Beer-lambert. Le capteur qui se place à l’extrémité du doigt est équipé d’un émetteur et d’un récepteur de lumière.

L’émetteur permet l’émission d’une lumière infrarouge et d’une lumière rouge grâce à deux Led. La lumière rouge a une longueur d’onde de 660 nm, la lumière infrarouge a une longueur d’onde de 950 nm. Ces deux lumières vont traverser la peau et vont être captées par un récepteur, constitué une photodiode, qui va les quantifier.

<center><figure>
<img src="./data/fonctionnement-oxymetre.jpg">
</figure></center>

Un calcul sur la quantité de lumière absorbée va permettre de déterminer la saturation sanguine en oxygène. La saturation du sang (SpO2), s’exprime en pourcentage et va permettre d’avoir une estimation de l’état d’un patient. La valeur normale est située entre 90 % et 100 %. L’oxymètre va en outre permettre de mesurer la fréquence cardiaque, par la mesure de la variation des différents flux de sang au niveau des extrémités.

Un oxymètre de pouls affiche 3 données : la **SpO2**, la **fréquence cardiaque** (fréquence de pulsation du pouls par minute) et la **courbe de l’onde du pouls**.

<center><figure>
<img src="./data/oxypleth.jpg">
</figure></center>

**Question 1.** Lire avec la bibliothèque Pandas le fichier `data_oxypleth.csv` contenu dans le dossier `data`. Déterminer le nombre de lignes et de colonnes ainsi que le nombre total d'éléments contenus dans ce fichier

**Question 2.**  Tracer côte à côte la courbe de l'onde du pouls correspondante et celle obtenue pour les 300 premières données du fichier uniquement

**Question 3.** Utiliser la fonction `print(*my_dataframe,sep=",")` pour lister les éléments contenus dans votre dataframe

Les données acquises par cet oxymètre de pouls ont été enregistrées de la façon suivante :

    * Les données (normalisées, valeurs comprises entre 0 et 100) se succèdent les unes à la suite des autres
    * A intervalle régulier, un élément de valeur 254 est stocké. Il s'agit d'un élément sans signification physiologique dont la valeur correspond en réalité à une étiquette (signal tag)
    * A ce signal tag + 1, la valeur de saturation calculée par l'oxymètre est enregistrée
    * A ce signal tag + 2, la valeur de fréquence cardiaque calculée par l'oxymètre est enregistrée

Exemple :

```python
...
29  : donnée  
254 : valeur signal tag t0, pas de signification physiologique donc de donnée correspondante
98  : t0+1 --> valeur de saturation (%)
84  : t0+2 --> valeur de la fréquence cardiaque (bpm)
21  : donnée  
15  : donnée  
12  : donnée    
26  : donnée  
...
```

**Question 4.** Nettoyer les données en retirant les éléments qui ne correspondent pas au signal de l'onde de pouls. Les valeurs de saturation et de fréquence cardiaque seront isolées et sauvegardées dans deux autres variables

**Question 5.** Tracer sur une même figure les 6 courbes suivantes :

* Données complètes de l'oxypleth (paramètres d'affichage par défaut)
* Données nettoyées (paramètres d'affichage par défaut)
* Données nettoyées réduites aux 300 premières valeurs (courbe de couleur verte)
* Valeurs de fréquence cardiaque seules (points de couleur bleu)
* Valeurs de saturation seules (points de couleur rouge)
* Valeurs de fréquence cardiaque et de saturation sur un même graphique (axe des ordonnées entre 0 et 120)
  


```python
import pandas as pd

df2 = pd.read_csv('data/data_oxypleth.csv')
df2
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>data</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>71</td>
    </tr>
    <tr>
      <th>1</th>
      <td>70</td>
    </tr>
    <tr>
      <th>2</th>
      <td>254</td>
    </tr>
    <tr>
      <th>3</th>
      <td>98</td>
    </tr>
    <tr>
      <th>4</th>
      <td>81</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
    </tr>
    <tr>
      <th>3291</th>
      <td>87</td>
    </tr>
    <tr>
      <th>3292</th>
      <td>76</td>
    </tr>
    <tr>
      <th>3293</th>
      <td>68</td>
    </tr>
    <tr>
      <th>3294</th>
      <td>65</td>
    </tr>
    <tr>
      <th>3295</th>
      <td>66</td>
    </tr>
  </tbody>
</table>
<p>3296 rows × 1 columns</p>
</div>




```python
rows, columns = df2.shape
print("Dataset comprenant {0} ligne(s) et {1} colonne(s)".format(rows, columns))
print("Nombre total d'éléments :", df2.size)
```

    Dataset comprenant 3296 ligne(s) et 1 colonne(s)
    Nombre total d'éléments : 3296



```python
def clean(df_):
    # Indices des balises 254
    idx = df_.index[df_["data"] == 254]
    idx_sat = idx + 1
    idx_fc = idx + 2

    # Extraction de la saturation et de la fréquence cardiaque
    sat = df_.loc[idx_sat, "data"].copy()
    fc = df_.loc[idx_fc, "data"].copy()

    # Suppression des balises, saturations et fréquences cardiaques
    indices_a_supprimer = idx.union(idx_sat).union(idx_fc)
    df_cleaned = df_.drop(index=indices_a_supprimer)

    return df_cleaned, sat, fc


df2_cleaned, sat, fc = clean(df2)

# display(df2_cleaned)
# display(sat)
```


```python
import pandas as pd
import matplotlib.pyplot as plt

# Conservation des 300 premières valeurs
df2_crop = df2.iloc[:300].copy()

fig, axes = plt.subplots(1, 2, figsize=(15, 5))

# Données complètes
axes[0].plot(df2.index, df2["data"])
axes[0].set_title("DataFrame original (données complètes)")
axes[0].set_xlabel("Index")
axes[0].set_ylabel("Valeur")
axes[0].grid(True, alpha=0.3)

# 300 premières valeurs
axes[1].plot(df2_crop.index, df2_crop["data"], color="orange")
axes[1].set_title("DataFrame réduit (300 premières valeurs)")
axes[1].set_xlabel("Index")
axes[1].set_ylabel("Valeur")
axes[1].grid(True, alpha=0.3)

fig.suptitle("Comparaison des données", fontsize=16)
plt.tight_layout()
plt.show()
```


    
![png](Exercices_files/Exercices_21_0.png)
    



```python
print(*df2_crop['data'],sep=",") # permet d'afficher la liste des valeurs
```

    71,70,254,98,81,61,47,39,32,25,20,17,17,17,18,18,18,17,17,17,17,17,17,17,17,18,18,19,19,20,22,27,35,45,56,65,254,98,81,70,72,71,68,64,59,52,44,36,30,24,21,20,19,19,20,19,19,19,18,18,17,17,17,17,18,18,18,18,18,19,22,29,39,51,60,67,70,71,69,65,59,53,45,38,30,24,20,18,17,254,96,83,17,16,16,15,14,14,13,13,13,13,14,14,15,16,17,18,19,21,26,34,46,59,69,74,76,75,71,66,59,51,44,35,28,21,17,16,16,17,18,19,19,18,18,17,16,16,16,16,17,18,254,96,83,18,18,18,18,19,21,27,38,53,65,72,73,72,68,64,59,52,45,37,31,23,18,15,15,16,17,17,17,16,16,15,15,16,16,18,19,20,20,19,18,18,19,24,32,46,60,70,73,72,68,254,97,84,64,59,54,48,41,32,25,18,13,12,12,13,14,16,16,16,16,16,16,15,15,15,15,16,16,16,17,22,32,45,60,70,73,72,67,61,55,50,43,36,28,21,15,12,12,13,14,16,17,17,254,98,84,17,17,17,17,17,18,18,18,19,19,20,22,29,41,57,72,80,82,79,73,67,61,54,47,39,32,24,17,13,12,12,13,14,15,15,15,15,15,15,15,16,16,16,16,17,17,18,22,31



```python
import numpy as np

data = df2['data'].to_numpy()

# Liste des indices des différents signal tags
tagindex = np.where(data == 254)[0]

print("List of tag index values:", tagindex)
# Check if for the first tag index value, the signal value is indeed 254
print("Valeur du premier signal tag :", data[tagindex[0]])

# Define a set of empty lists to store the clinically useful information
sat_arr = []
fc_arr = []
data_arr = data.copy()
valuestoremove = []

```

    List of tag index values: [   2   36   89  142  195  248  301  354  407  460  513  566  619  672
      725  778  831  884  937  990 1043 1096 1149 1202 1255 1308 1361 1414
     1467 1520 1573 1626 1679 1732 1785 1838 1891 1944 1997 2050 2103 2156
     2209 2262 2315 2368 2421 2474 2527 2580 2633 2686 2739 2792 2845 2898
     2951 3004 3057 3110 3163 3216 3269]
    Valeur du premier signal tag : 254



```python
for i in range(tagindex.size):
    # Valeur de saturation située juste après le signal tag
    sat_arr.append(data[tagindex[i] + 1])
    # Valeur de fréquence cardiaque située deux places après le signal tag
    fc_arr.append(data[tagindex[i] + 2])
    # Indices du tag, de la saturation et de la fréquence cardiaque
    valuestoremove.extend([tagindex[i], tagindex[i] + 1, tagindex[i] + 2])

# Suppression des valeurs qui ne correspondent pas à l'onde de pouls
data_arr = np.delete(data_arr, valuestoremove)
sat_arr = np.array(sat_arr)
fc_arr = np.array(fc_arr)

print("Nombre de données de l'onde de pouls :", data_arr.size)
print("Nombre de valeurs de saturation :", sat_arr.size)
print("Nombre de valeurs de fréquence cardiaque :", fc_arr.size)
```

    Nombre de données de l'onde de pouls : 3107
    Nombre de valeurs de saturation : 63
    Nombre de valeurs de fréquence cardiaque : 63



```python
fig, axes = plt.subplots(3, 2, figsize=(15, 13))

# 1. Données complètes
axes[0, 0].plot(data)
axes[0, 0].set_title("Données complètes de l'oxymètre")

# 2. Données nettoyées
axes[0, 1].plot(data_arr)
axes[0, 1].set_title("Onde de pouls nettoyée")

# 3. Les 300 premières données nettoyées
axes[1, 0].plot(data_arr[:300], color='green')
axes[1, 0].set_title("Onde de pouls nettoyée (300 premières valeurs)")

# 4. Fréquence cardiaque
axes[1, 1].plot(fc_arr, 'bo')
axes[1, 1].set_title("Fréquence cardiaque")
axes[1, 1].set_ylabel('Fréquence (bpm)')

# 5. Saturation en oxygène
axes[2, 0].plot(sat_arr, 'ro')
axes[2, 0].set_title("Saturation en oxygène")
axes[2, 0].set_ylabel('SpO2 (%)')

# 6. Fréquence cardiaque et saturation
axes[2, 1].plot(fc_arr, 'bo', label='Fréquence cardiaque')
axes[2, 1].plot(sat_arr, 'ro', label='Saturation')
axes[2, 1].set_title("Fréquence cardiaque et saturation")
axes[2, 1].set_ylim(0, 120)
axes[2, 1].legend()

for ax in axes.flat:
    ax.set_xlabel('Index')

plt.tight_layout()
plt.show()
```


    
![png](Exercices_files/Exercices_25_0.png)
    


## Exercice 5
-----------

On considère que l'âge moyen des étudiants inscrits au DQPRM est de 26 ans.

Après avoir affiché les données sous forme d'un box-plot, vérifier à partir du fichier `ages_DQPRM.csv` dans le dossier `data` que c'est bien le cas pour votre promo.


```python
import pandas as pd

df3 = pd.read_csv('data/ages_DQPRM.csv')
df3.columns = ['Étudiant', 'Age']
df3
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Étudiant</th>
      <th>Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>29</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>25</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>24</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>29</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>26</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>27</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>27</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>32</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>26</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>25</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>22</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>27</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>24</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>26</td>
    </tr>
    <tr>
      <th>15</th>
      <td>15</td>
      <td>24</td>
    </tr>
    <tr>
      <th>16</th>
      <td>16</td>
      <td>27</td>
    </tr>
    <tr>
      <th>17</th>
      <td>17</td>
      <td>27</td>
    </tr>
    <tr>
      <th>18</th>
      <td>18</td>
      <td>34</td>
    </tr>
    <tr>
      <th>19</th>
      <td>19</td>
      <td>23</td>
    </tr>
    <tr>
      <th>20</th>
      <td>20</td>
      <td>31</td>
    </tr>
    <tr>
      <th>21</th>
      <td>21</td>
      <td>24</td>
    </tr>
    <tr>
      <th>22</th>
      <td>22</td>
      <td>33</td>
    </tr>
    <tr>
      <th>23</th>
      <td>23</td>
      <td>25</td>
    </tr>
    <tr>
      <th>24</th>
      <td>24</td>
      <td>28</td>
    </tr>
    <tr>
      <th>25</th>
      <td>25</td>
      <td>24</td>
    </tr>
    <tr>
      <th>26</th>
      <td>26</td>
      <td>24</td>
    </tr>
    <tr>
      <th>27</th>
      <td>27</td>
      <td>24</td>
    </tr>
    <tr>
      <th>28</th>
      <td>28</td>
      <td>20</td>
    </tr>
    <tr>
      <th>29</th>
      <td>29</td>
      <td>27</td>
    </tr>
    <tr>
      <th>30</th>
      <td>30</td>
      <td>24</td>
    </tr>
    <tr>
      <th>31</th>
      <td>31</td>
      <td>30</td>
    </tr>
    <tr>
      <th>32</th>
      <td>32</td>
      <td>25</td>
    </tr>
    <tr>
      <th>33</th>
      <td>33</td>
      <td>24</td>
    </tr>
    <tr>
      <th>34</th>
      <td>34</td>
      <td>28</td>
    </tr>
    <tr>
      <th>35</th>
      <td>35</td>
      <td>21</td>
    </tr>
    <tr>
      <th>36</th>
      <td>36</td>
      <td>28</td>
    </tr>
    <tr>
      <th>37</th>
      <td>37</td>
      <td>26</td>
    </tr>
    <tr>
      <th>38</th>
      <td>38</td>
      <td>27</td>
    </tr>
    <tr>
      <th>39</th>
      <td>39</td>
      <td>26</td>
    </tr>
    <tr>
      <th>40</th>
      <td>40</td>
      <td>21</td>
    </tr>
    <tr>
      <th>41</th>
      <td>41</td>
      <td>26</td>
    </tr>
    <tr>
      <th>42</th>
      <td>42</td>
      <td>30</td>
    </tr>
    <tr>
      <th>43</th>
      <td>43</td>
      <td>24</td>
    </tr>
    <tr>
      <th>44</th>
      <td>44</td>
      <td>27</td>
    </tr>
  </tbody>
</table>
</div>




```python
import scipy.stats
import numpy as np

age_stats = scipy.stats.describe(df3['Age'])
print(age_stats,'\n')
print("Age moyen :",df3["Age"].mean())
print("Age median :", df3["Age"].median())
```

    DescribeResult(nobs=45, minmax=(np.int64(20), np.int64(34)), mean=np.float64(26.133333333333333), variance=np.float64(9.072727272727272), skewness=np.float64(0.5115362254241266), kurtosis=np.float64(0.3402606816840108)) 
    
    Age moyen : 26.133333333333333
    Age median : 26.0



```python
import matplotlib.pyplot as plt

moyenne = df3["Age"].mean()
mediane = df3["Age"].median()

plt.figure(figsize=(7, 5))

plt.boxplot(
    df["Age"],
    showmeans=True,
    meanprops={
        "marker": "o",
        "markerfacecolor": "green",
        "markeredgecolor": "green"
    },
    medianprops={
        "color": "red",
        "linewidth": 2
    }
)

plt.ylabel("Âge (années)")
plt.title("Distribution de l’âge des étudiants du DQPRM")
plt.xticks([1], ["Étudiants"])
plt.grid(axis="y", alpha=0.3)
plt.show()
```


    
![png](Exercices_files/Exercices_29_0.png)
    



```python
# Test de Student à un échantillon
# H0 : l'âge moyen est égal à 26 ans
# H1 : l'âge moyen est différent de 26 ans
statistique, pval = scipy.stats.ttest_1samp(
    df3["Age"],
    popmean=26
)

print(f"Statistique du test : {statistique:.4f}")
print(f"p-value : {pval:.4f}")

# Conclusion au seuil de 5 %
if pval < 0.05:
    print(
        "Hypothèse nulle rejetée : "
        "l'âge moyen diffère significativement de 26 ans."
    )
else:
    print(
        "Hypothèse nulle non rejetée : "
        "aucune différence significative avec 26 ans."
    )
```

    Statistique du test : 0.2969
    p-value : 0.7679
    Hypothèse nulle non rejetée : aucune différence significative avec 26 ans.


## Exercice 6
-----------

Le fichier `ages.csv` contenu dans le dossier `data` renseigne la taille (en $cm$) de 7 hommes et de 7 femmes.

**Question 1.** Regrouper les données selon le genre et les afficher sous forme de box-plots

**Question 2.** Vérifier que les échantillons homme/femme suivent une loi normale

**Question 3.** Vérifier que leur variance sont égales

**Question 4.** Comparer leur moyenne et conclure


```python
import pandas as pd

df = ...
df
```


```python
df.describe()
```


```python
df.groupby(...).describe()
```


```python
men = df.query('... == "..."')['...']
women = df.query('... == "..."')['..']
plt.boxplot(...)
plt.grid()
plt.show()
```


```python
...
```

## Exercice 7
-----------

Les fumeurs ont un risque accru d’événements thrombotiques artériels (formation anormale de caillots), à l’origine notamment l’infarctus du myocarde. Les plaquettes sont des cellules sanguines périphériques qui sont impliquées dans la formation de ces caillots en s’agrégeant.

Une étude a été conduite chez 11 sujets volontaires sains pour comparer l’agrégation des plaquettes avant et après qu’ils aient fumé une cigarette.

A partir des données fournies dans le tableau suivant, déterminez si l’agrégation plaquettaire est modifiée après avoir fumé une cigarette ?  On suppose les conditions de validité du test vérifiées mais vous pourrez vous en assurer a posteriori.

<table>
   <caption>Agrégation plaquettaire</caption>
   <tr>
       <td>Avant</td>
       <td>25</td>
       <td>25</td>
       <td>27</td>
       <td>29</td>
       <td>30</td>
       <td>45</td>
       <td>51</td>
       <td>51</td>
       <td>57</td>
       <td>61</td>
       <td>68</td>
   </tr>
   <tr>
       <td>Après</td>
       <td>27</td>
       <td>29</td>
       <td>37</td>
       <td>45</td>
       <td>42</td>
       <td>60</td>
       <td>55</td>
       <td>78</td>
       <td>66</td>
       <td>60</td>
       <td>83</td>
   </tr>
</table>


```python
...
```

## Exercice 8 - Evolution de l’alcoolémie au cours du temps
-----------

Par définition, on appelle «alcoolémie» la concentration en $g/L$ d’éthanol ($CH_3CH_2OH$) dans le sang d’une personne. En France, la loi interdit à une personne de conduire si son alcoolémie est supérieure à $0.5\ g/L$.

On  se  propose  dans  cet  exercice  d’étudier  comment  varie  l’alcoolémie  d’une  personne  à  partir  du moment  où  elle  boit  deux bières (chacune  de  $50\ cL$  et à $6\ \%$), de façon notamment à savoir à quel moment elle pourra prendre le volant.

Il faut pour cela étudier deux mécanismes différents :
* l’**absorption de l’alcool dans le sang**, qui se fait par diffusion à travers les parois de l’estomac et de l’intestin grêle
* l’**élimination de l’alcool contenu dans le sang**, qui est effectuée essentiellement par  des  enzymes au niveau du foie (grâce à une réaction d’oxydation)

On va étudier chacun de ces deux processus séparément (dans les parties A et B), puis on combinera les deux dans la partie C.

### A - Absorption de l'alool à travers la paroi stomacale

On cherche dans ce paragraphe à étudier la loi cinétique modélisant le processus d'absorption, c’est à dire que l’on cherche à déterminer son ordre (si elle en possède un) et sa constante de vitesse $k$.

Pour cela, on réalise l’expérience suivante : on fait boire à un homme (initialement à jeun, c’est à dire l’estomac vide) une boisson alcoolisée de volume $V = 250\  mL$ contenant $1\ mole$ d’éthanol. On mesure alors  la  concentration  $c_1$ de l’éthanol dans  l’estomac  de  l’homme  en  fonction  du  temps.  

Les  résultats obtenus sont regroupés dans le tableau ci-dessous:

<table>
   <tr>
       <td>$t$ (en min)</td>
       <td>0</td>
       <td>1,73</td>
       <td>2,8</td>
       <td>5,5</td>
       <td>18</td>
       <td>22</td>
   </tr>
   <tr>
       <td>$c_1$ (en mol/L)</td>
       <td>à déterminer</td>
       <td>3,0</td>
       <td>2,5</td>
       <td>1,6</td>
       <td>0,2</td>
       <td>0,1</td>
   </tr>
</table>



**Question 1.** Utiliser  ces  données  pour  prouver  graphiquement que  la  réaction  d’absorption  de  l’alcool  dans  le  sang  suit  une  loi  cinétique  d’ordre  $1$,  et déterminer sa constante de vitesse $k_1$ (en précisant son unité).

NB. On fera appel pour cela à la fonction [linregress](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.linregress.html) du sous-module `stats` de SciPy.

**Rappel**

Notons $c_1(t)$ la concentration de l’alcool dans l’estomac au cours du temps et $v_1=-\frac{dc_1}{dt}$ la vitesse d’absorption de l’alcool au niveau de la paroi de l’estomac.

Si la réaction est d’ordre 1, on aura aussi $v_1=kc_1(t)$ et $c_1(t)$ sera donc solution de l’équation différentielle :

$$\frac{dc_1(t)}{dt}+kc_1(t)= 0$$ qui se résout immédiatement en : $$c_1(t) =c_{1,0}.exp^{-kt}$$

où c$_{1,0}$ est la concentration initiale.

Ainsi, si la réaction est bien d’ordre 1, on aura :

$$ln(\frac{c_1(t)}{c_{1,0}})=-kt$$


```python
c10 = ...
print("La concentration initiale d'alcool dans l'estomac est de", c10, "mol/L")
```


```python
import numpy as np
import matplotlib.pyplot as plt
import scipy.stats

t1 = ...
c1 = ...
plt.plot(...,...)
plt.grid()
lr = ...
#print(lr)
k1 = ...
print("Le coefficient de corrélation vaut {:0.6f}".format(abs(...)))
print("La constante de vitesse de la réaction d'absorption vaut k1 = {:0.4f} min-1".format(...))
```

**Question 2.** Calculer  la  valeur  (en  minutes)  du  temps  de demi-réaction $t_{1/2,1}$ de la réaction d’absorption  de l’alcool dans le sang.


```python
tdemi1 = ...
print("Le temps de demi-réaction vaut {:0.3f} min".format(tdemi1))
```

### B - Oxydation de l’alcool dans le sang

Une fois que l’alcool est passé dans le sang, il est progressivement éliminé (surtout au niveau du foie) par une réaction d’oxydation qui le transforme en éthanal. Cette réaction a lieu grâce à une enzyme appelée alcool-déshydrogénase.

On cherche à présent à déterminer la loi de vitesse de cette réaction d’élimination de l’alcool.

Pour cela, on injecte directement (par voie veineuse) une certaine quantité d’alcool dans le sang d’un homme  et  on  mesure  par  des  prélèvements  successifs  l’évolution  de  la  concentration $c_2$ de l’alcool dans le sang de cet homme au cours du temps (on suppose que l’injection est quasi-instantanée et que la concentration de l’alcool dans le sang est la même en tout endroit du corps). On obtient les données du tableau suivant :

<table>
   <tr>
       <td>$t$ (en min)</td>
       <td>0</td>
       <td>120</td>
       <td>240</td>
       <td>360</td>
       <td>480</td>
       <td>600</td>
       <td>720</td>
   </tr>
   <tr>
       <td>$c_2$ (en mol/L)</td>
       <td>0,05</td>
       <td>0,0413</td>
       <td>0,0326</td>
       <td>0,0239</td>
       <td>0,0152</td>
       <td>0,0065</td>
       <td>0</td>
   </tr>
</table>

**Question 3.** A l’aide de ces données, déterminer l’ordre de cette réaction ainsi que sa constante de vitesse $𝑘_2$


```python
...
```


**Question 4.** Calculer  en  minutes  le  temps  de  demi  réaction $t_{1/2,2}$ de cette réaction et comparez le au temps de demi-réaction de l’absorption de l’alcool $t_{1/2,1}$. Commentaire?


```python
...
```

### C - Evolution de l’alcoolémie au cours du temps

Maintenant   que   l’on   connaît   les   lois   de   vitesse   de   la   réaction   d’absorption et   de   la   réaction d’élimination de l’alcool, on peut calculer comment évolue l’alcoolémie (concentration d’alcool dans le sang) au cours du temps, à partir du moment où une personne boit de l’alcool.

Notons $c$ la concentration (en $mol/L$) de l’alcool dans le sang et $v=\frac{dc}{dt}$ la vitesse à laquelle varie cette concentration.  On  note  également  $V_s$ le volume total du sang et  de  l’ensemble  compartiments hydriques  de  l’organisme (dans  lesquels se dissout l’alcool) et $V_e$ le volume de la boisson alcoolisée ingérée par la personne (qui correspond également au volume de son estomac puisqu’on considère que la personne était à jeun avant de boire).  

La concentration d'alcool dans le sang à l'instant $t$ s'écrit : $$c(t)=C_0\frac{V_e}{V_S}(1-e^{-k_1t})-k_2t$$ où $C_0$ est la concentration en alcool dans la boisson alcoolisée.

Lors d’une soirée, Alice boit deux bières, chacune de volume $V_0 = 50\ cL$ et de «degré alcoolique» $d =6\% $.

**Rappel** : le «degré alcoolique» correspond au pourcentage volumique d’éthanol dans la boisson, c’est à dire que: $d=\frac{V_{ethanol}}{V_{total}}$

**Question 5.** Sachant que  l’éthanol  a  une  masse  volumique $\rho_{eth}=0,79\ kg/L$, calculer  la  concentration  $C_0$ de l’éthanol dans la bière, en $g/L$ puis en $mol/L$ (on donne les masses molaires : $M_C = 12\ g/mol$, $M_H = 1,0\ g/mol$ et $M_O = 16\ g/mol$).


```python
d = ...
rhoeth = ...
C0m = ... # en g/L
Meth = ...
C0 = C0m/Meth
print("La concentration massique de l'éthanol dans la bière est de {} g/L ".format(C0m))
print("La concentration molaire de l'éthanol dans la bière est de {:0.3f} mol/L ".format(C0))
```

**Question 6.**  Tracer   la   fonction $c(t)=C_0\frac{V_e}{V_S}(1-e^{-k_1t})-k_2t$ représentant l’évolution de la concentration en éthanol dans le sang d’Alice (en $mol/L$) à partir du moment où elle boit ses deux bières. On prendra $Vs = 40 L$ comme volume total du sang et des compartiments hydriques dans le corps d’Alice.


```python
V0 = ...
Ve = ...
Vs = ...
t = np.arange(0,260,0.5)
c = ...
plt.figure(figsize=(8,5))
...
```

**Question 7.** Déterminer la valeur de concentration en éthanol maximale d'Alice


```python
cmax = ...
print("La valeur de concentration en éthanol maximale d'Alice est de {:0.4f} mol/L".format(cmax))
```

**Question 8.** Déterminer l’instant  $t_{max}$ auquel la concentration en éthanol est maximale dans le sang d’Alice


```python
tmax = ...
print("L'instant auquel la concentration en éthanol est maximale dans le sang d’Alice est t = {:0.1f} min".format(tmax))
```

**Question 9.** Alice a-t-elle le droit de conduire à ce moment là?


```python
Climmass = ... # en g/L
Climmol = ... # en mol/L
print(Climmol)
```

**Question 10.** Déterminer le temps au bout duquel Alice aura le droit de prendre le volant.


```python
condition = ...
tok = ...
print("Le temps au bout duquel Alice aura le droit de prendre le volant est t = {:0.1f} min".format(tok))
```

## Exercice 9 - Affichage et manipulation d'une image TEP
-----------

**Question 1.** Charger l'image `1-PT.nii` contenue dans le sous-dossier `data`

**Question 2.**  Afficher les dimensions de cette image

**Question 3.**  Convertir l'image en un tableau (array) NumPy de la même taille

**Question 4.**  Afficher les dimensions de ce tableau

**Question 5.**  Identifier un plan de coupe sur lequel on voit nettement la tumeur qui se trouve dans le poumon (via 3D Slicer ou ITK-SNAP)

**Question 6.**  Rogner l'image afin d'effecteur un zoom sur cette tumeur et afficher le résultat


```python
%matplotlib inline
import matplotlib.pyplot as plt

import numpy as np
import SimpleITK as sitk
from ipywidgets import interact
```


```python
image_pet = sitk.ReadImage(...)
```


```python
print("Taille de l'image CT (SimpleITK) = ",...)
```


```python
arr_image_pet = sitk.GetArrayFromImage(...)
```


```python
print("Taille du tableau (NumPy) correspondant = ",...)
```


```python
plan =
```


```python
tumeur = arr_image_pet[plan,...:...,...:...]
plt.imshow(tumeur,cmap='...')
```

## Exercice 10 - Calcul de fonctions rénales relatives


---
**Question 1.** Réutiliser la méthode vue dans le notebook `3_Introduction-ROI.ipynb` pour définir un masque du bruit de fond (par exemple en sélectionnant une région rectangulaire au-dessus des deux reins)

**Question 2.** Appliquer ce masque sur l'image de scintigraphie rénale de départ (`PosteriorStatic001_DS.dcm` contenue dans le dossier `data`)

**Question 3.** Déterminer le nombre de coups moyen correspondant au du bruit de fond

**Question 4.** Utiliser ce nombre de coups moyen correspondant au bruit de fond et les nombres de coups moyens dans chacun des deux reins pour calculer les fonctions rénales relatives dont la formule retenue est la suivante (exemple pour le rein droit) :

$$
FRR_{droit}=100\times \frac{Coups_{rein\ droit} - Coups_{fond}}{(Coups_{rein\ droit} - Coups_{fond})+(Coups_{rein\ gauche} - Coups_{fond})}
$$



```python
import numpy as np
import matplotlib.pyplot as plt
import SimpleITK as sitk
```


```python
rein = sitk.ReadImage('./data/PosteriorStatic001_DS.dcm')
rein_arr = sitk.GetArrayFromImage(rein).reshape(rein.GetWidth(),rein.GetHeight())
img = np.copy(rein_arr)

mask1 = np.zeros(img.shape)
mask2 = np.zeros(img.shape)

mask1[40:70,40:60] = 1
mask2[40:70,62:82] = 1

mask = mask1 + mask2
```

* Rein gauche


```python
rein_arr_segm1 = rein_arr * mask1 # Opération de mutliplication qui met à zéro ce qui est en dehors du masque
plt.imshow(rein_arr_segm1,cmap='jet')
plt.colorbar()
Ntot_g = rein_arr_segm1.sum() # Somme des intensités dans l'image
Nb_pixels_g = mask1.sum()  # Somme des intensités (0 ou 1) dans le masque ce qui donne ainsi sa taille (en nombre de pixels)
print("Nombre de coups total gauche :" , Ntot_g)
print("Nombre de pixels total gauche :" , Nb_pixels_g)
print("Nombre de coups moyen gauche = {:0.2f}".format(Ntot_g/Nb_pixels_g))
```

    Nombre de coups total gauche : 76292.0
    Nombre de pixels total gauche : 600.0
    Nombre de coups moyen gauche = 127.15



    
![png](Exercices_files/Exercices_75_1.png)
    


* Rein droit


```python
rein_arr_segm2 = rein_arr * mask2
plt.imshow(rein_arr_segm2,cmap='jet')
plt.colorbar()
Ntot_r = rein_arr_segm2.sum() # Somme des intensités dans l'image
Nb_pixels_r = mask2.sum()  # Somme des intensités (0 ou 1) dans le masque ce qui donne ainsi sa taille (en nombre de pixels)
print("Nombre de coups total droit :" , Ntot_r)
print("Nombre de pixels total droit :" , Nb_pixels_r)
print("Nombre de coups moyen droit = {:0.2f}".format(Ntot_r/Nb_pixels_r))
```

    Nombre de coups total droit : 86777.0
    Nombre de pixels total droit : 600.0
    Nombre de coups moyen droit = 144.63



    
![png](Exercices_files/Exercices_77_1.png)
    


* Bruit de fond


```python
maskbg = np.zeros(img.shape)
maskbg[40:70,40:82] = 1
plt.imshow(maskbg, cmap='gray');
```


    
![png](Exercices_files/Exercices_79_0.png)
    



```python
background = rein_arr* maskbg - rein_arr_segm1 - rein_arr_segm2
plt.imshow(background, vmin=0, vmax=rein_arr.max(), cmap='jet')
```




    <matplotlib.image.AxesImage at 0x119f65310>




    
![png](Exercices_files/Exercices_80_1.png)
    



```python
Ntot_bg = background.sum()
Nb_pixels_bg = maskbg.sum()
print("Nombre de coups total :" , Ntot_bg)
print("Nombre de pixels total :" , Nb_pixels_bg)
print("Nombre de coups moyen = {:0.2f}".format(Ntot_bg/Nb_pixels_bg))
```

    Nombre de coups total : 2736.0
    Nombre de pixels total : 1260.0
    Nombre de coups moyen = 2.17



```python
FRR_d = 100 * (Ntot_r/Nb_pixels_r - Ntot_bg/Nb_pixels_bg) / ((Ntot_r/Nb_pixels_r + Ntot_g/Nb_pixels_g -2*Ntot_bg/Nb_pixels_bg))
print("Fonction rénale relative droite = {:0.2f}".format(FRR_d))
```

    Fonction rénale relative droite = 53.27



```python
FRR_g = 100 * (Ntot_g/Nb_pixels_g - Ntot_bg/Nb_pixels_bg) / ((Ntot_r/Nb_pixels_r   + Ntot_g/Nb_pixels_g - 2*Ntot_bg/Nb_pixels_bg))
print("Fonction rénale relative gauche = {:0.2f}".format(FRR_g))
```

    Fonction rénale relative gauche = 46.73


## Exercice 11 - Votre ROI manuelle contre le contour clinique de référence

---

**Question 1 (prédiction).** Dice attendu, et effet attendu sur la FRR ?

**Question 2.** Vérifier le mapping label ↔ rectangle par comparaison directe.

**Question 3.** Dice/Jaccard/FN/FP/Hausdorff entre le rectangle et le contour de référence.

**Question 4.** FRR de référence (CSV) vs FRR du rectangle.

---


```python
import numpy as np
import matplotlib.pyplot as plt
import SimpleITK as sitk

rein = sitk.ReadImage('./data/rein/PosteriorStatic001_DS.nii')
rein_arr = sitk.GetArrayFromImage(rein).reshape(rein.GetWidth(), rein.GetHeight())

ref = sitk.ReadImage('./data/rein/output/maskTot.nii')
ref_arr = sitk.GetArrayFromImage(ref)

# vos rectangles de l'exercice 10
mask_reinD = np.zeros(rein_arr.shape)
mask_reinD[40:70, 62:82] = 1
mask_reinG = np.zeros(rein_arr.shape)
mask_reinG[40:70, 40:60] = 1
```


```python
# FRR de référence à partir des CSV, vs votre FRR de l'exercice 10
# Les fichiers CSV sont tabulés (séparateur '\t'), pas des CSV standards à virgules.
def parse_csv_clinique(path):
    with open(path) as f:
        header = f.readline().rstrip('\n').split('\t')
        row = f.readline().rstrip('\n').split('\t')
    return dict(zip(header[1:], row[1:]))  # la 1re colonne est un simple index de ligne

ref_droit = parse_csv_clinique('./data/rein/RightKidney.csv')
ref_gauche = parse_csv_clinique('./data/rein/LeftKidney.csv')
ref_fond = parse_csv_clinique('./data/rein/Background.csv')
```

## Exercice 12 - Sensibilité du seuillage TEP

Reprend et prolonge le §7-9 de `5_TEP.ipynb` (segmentation de la tumeur par seuillage relatif du SUVmax, calcul du volume et de la TLG).

---

**Question 1 (prédiction).** Si l'on fait varier le seuil relatif de segmentation de 10 % à 50 % du SUVmax, comment pensez-vous que le **volume segmenté** et la **TLG** vont évoluer ? Lequel des deux vous semble le plus sensible au choix du seuil?

**Question 2.** Calculez, pour des seuils relatifs de 10 % à 50 % (pas de 2,5 %), le volume segmenté (mm³) et la TLG correspondants, à partir du volume TEP rogné autour de la tumeur du patient 4 (repartez du volume `IMAGE_cropped_np` construit en section 5 de `5_TEP.ipynb`). Tracez les deux courbes en fonction du seuil sur une même figure (deux axes y).

**Question 3.** Comparez le résultat obtenu à votre prédiction de la Question 1.

---


```python
import numpy as np
import matplotlib.pyplot as plt

# Réutilisez ici le volume SUV rogné autour de la tumeur (section 5 et 6 de 5_TEP.ipynb)
# et le facteur de conversion voxel -> mm3 (vox2vol_Factor)
IMAGE_np = ...        # volume rogné, en unités SUV (array NumPy)
vox2vol_Factor = ...  # mm3 par voxel
```


```python
seuils = np.arange(0.10, 0.525, 0.025)  # de 10% à 50% par pas de 2.5%
volumes_mm3 = []
tlgs = []

suv_max = IMAGE_np.max()

for seuil in seuils:
    mask = ...                      # masque booléen au-dessus de seuil * suv_max
    nb_vox = ...
    vol_mm3 = ...
    suv_mean = ...
    tlg = ...                       # TLG = SUVmean * volume (en mL, donc en cm3)
    volumes_mm3.append(vol_mm3)
    tlgs.append(tlg)
```


```python
fig, ax1 = plt.subplots(figsize=(8, 5))
...
plt.title("Sensibilité du volume et de la TLG au seuil de segmentation");
```

## Exercice 13 - Trois façons de calculer des statistiques par label

Reprend le §2.4 de `3_Introduction-ROI.ipynb` (`sitk.LabelIntensityStatisticsImageFilter` appliqué à `0-CT.nii` et `segmentation.nii.gz`).

---

**Question 1.** Écrivez une fonction `stats_boucle(arr_img, arr_lab, label)` avec des boucles `for` explicites.

**Question 2.** Écrivez une fonction `stats_vectorise(arr_img, arr_lab, label)` avec des opérations NumPy vectorisées.

**Question 3.** Vérifiez que les trois méthodes donnent le même résultat.

**Question 4.** Chronométrez les trois approches sur une seule coupe 2D.

**Question 5.** Classez les trois approches par ordre de rapidité et expliquez l'écart.

---


```python
import time
import numpy as np
import SimpleITK as sitk

img_ct = sitk.ReadImage('./data/0-CT.nii')
arr_img_ct = sitk.GetArrayFromImage(img_ct)
img_lab = sitk.ReadImage('./data/segmentation.nii.gz')
arr_img_lab = sitk.GetArrayFromImage(img_lab)

coupe = ...
arr_img_2d = arr_img_ct[coupe]
arr_lab_2d = arr_img_lab[coupe]
```


```python
# (pas d'indexation booléenne NumPy, pas de .mean()/.std())

def stats_boucle(arr_img, arr_lab, label):
    ...
```


```python
# implémentez stats_vectorise uniquement avec des opérations NumPy vectorisées

def stats_vectorise(arr_img, arr_lab, label):
    ...
```


```python
label_test = 6 # liver

m1, s1 = stats_boucle(arr_img_2d, arr_lab_2d, label_test)
m2, s2 = stats_vectorise(arr_img_2d, arr_lab_2d, label_test)

stats_sitk = sitk.LabelIntensityStatisticsImageFilter()
stats_sitk.Execute(..., ...)   # attention: LabelIntensityStatisticsImageFilter attend des images sitk, pas des arrays
m3 = stats_sitk.GetMean(label_test)
s3 = stats_sitk.GetStandardDeviation(label_test)

print("Boucle     :", m1, s1)
print("Vectorisé  :", m2, s2)
print("sitk filter:", m3, s3)
```


```python
#  chronométrage (utilisez %timeit -o pour récupérer les temps dans des variables)
t_boucle = %timeit -o stats_boucle(arr_img_2d, arr_lab_2d, label_test)
```

## Exercice 14 - Problème de variance

Le code ci-dessous prétend recalculer "à la main" la variance de l'image de scintigraphie rénale, pour la comparer à `arr.var()` de NumPy. **Exécutez-le d'abord tel quel, sans le corriger.**

---


```python
import numpy as np
import SimpleITK as sitk

rein = sitk.ReadImage('./data/rein/PosteriorStatic001_DS.nii')
rein_arr = sitk.GetArrayFromImage(rein).reshape(rein.GetWidth(), rein.GetHeight())

def variance_maison(arr):
    n = arr.size
    somme = arr.sum()
    somme_carres = (arr ** 2).sum()   # E[X^2]
    moyenne = somme / n
    return somme_carres / n - moyenne ** 2   # E[X^2] - E[X]^2

print("Variance (maison) :", variance_maison(rein_arr))
print("Variance (NumPy)  :", rein_arr.var())
```

---

**Question 1.** Le résultat de `variance_maison` est-il cohérent avec celui de `rein_arr.var()` ? Quantifiez l'écart.

**Question 2.** Diagnostiquez la cause du problème.

**Question 3.** Corrigez `variance_maison` pour qu'elle donne le même résultat que `rein_arr.var()` à 1e-6 près.

---

## Exercice 15 - Les références

---

**Question 1 (prédiction).** `b = a[2:5]` puis `b[0]=999` ; `c = a[a>5]` puis `c[0]=999` : `a` est-il affecté dans chaque cas ?

**Question 2.** Vérification avec `np.shares_memory`.

**Question 3.** Bug réel sur le volume CT.

**Question 4.** Coût mesuré copie vs vue.

**Question 5.** Vue ou copie, en pratique ?

**Question 6.** Accumulation de copies dans un pipeline : mesurer le pic mémoire réel.

---


```python
import numpy as np

a = np.arange(10)
print("a =", a)
```

    a = [0 1 2 3 4 5 6 7 8 9]



```python
#  vérification sur le petit array
a = np.arange(10)
b = a[2:5]
b[0] = 999
print("apres modif de b : a =", a, " | shares_memory(a,b) =", np.shares_memory(a, b))

a = np.arange(10)
c = a[a > 5]
c[0] = 999
print("apres modif de c : a =", a, " | shares_memory(a,c) =", np.shares_memory(a, c))

a = np.arange(10)
d = a[[1, 2, 3]]
print("shares_memory(a,d) =", np.shares_memory(a, d))
```

    apres modif de b : a = [  0   1 999   3   4   5   6   7   8   9]  | shares_memory(a,b) = True
    apres modif de c : a = [0 1 2 3 4 5 6 7 8 9]  | shares_memory(a,c) = False
    shares_memory(a,d) = False



```python
# Question 3 : reproduction du bug sur le volume CT réel, puis correction
import SimpleITK as sitk

img_ct = sitk.ReadImage('./data/0-CT.nii')
arr_ct = sitk.GetArrayFromImage(img_ct)

...   # reproduisez le bug : prenez une coupe par slicing basique, modifiez-la,
      # vérifiez l'effet sur arr_ct

...   # puis la version corrigée
```




    Ellipsis




```python
# Question 4 : mesure du coût copie vs vue
...
```


```python
# Question 6 : pipeline naif
# Objectif : un petit pretraitement HU (clip min/max) + conversion en float32,
# en copiant "par prudence" a chaque etape

def pipeline_naif(img):
    arr1 = sitk.GetArrayFromImage(img)                  # copie #1
    arr2 = arr1.copy()                                   # copie #2
    arr2[arr2 < -1000] = -1000                           # clip HU min
    arr3 = arr2.copy()                                    # copie #3
    arr3[arr3 > 3000] = 3000                               # clip HU max
    arr4 = arr3.copy()                                     # copie #4
    arr4 = arr4.astype(np.float32)                          # copie #5
    # a ce point, arr1, arr2, arr3 et arr4 sont TOUS encore references
    pic_memoire = arr1.nbytes + arr2.nbytes + arr3.nbytes + arr4.nbytes
    return arr4, pic_memoire
```


```python
# Question 6 : pipeline optimise -- a completer
# Meme resultat, mais en minimisant les copies (in place quand c'est possible)

def pipeline_optimise(img):
    arr = sitk.GetArrayFromImage(img)      # copie necessaire : on va modifier les donnees
    pic_memoire = arr.nbytes
    np.clip(arr, -1000, 3000, out=arr)     # in place : aucune nouvelle allocation
    arr = arr.astype(np.float32)            # changement de dtype = nouveau buffer, inevitable ici,
                                              # mais l'ancien buffer int16 peut etre libere aussitot
    pic_memoire = max(pic_memoire, arr.nbytes)
    return arr, pic_memoire
```


```python
import SimpleITK as sitk
import numpy as np

img_ct = sitk.ReadImage('./data/0-CT.nii')

resultat_naif, pic_naif = pipeline_naif(img_ct)
resultat_opt, pic_opt = pipeline_optimise(img_ct)

print("Pic memoire (naif)     :", pic_naif / 1e6, "MB")
print("Pic memoire (optimise) :", pic_opt / 1e6, "MB")
print("Resultats identiques ? :", np.allclose(resultat_naif, resultat_opt))

%timeit ...
```

**Votre comparaison pic mémoire / temps, et le lien avec votre réponse sur "la mémoire peut-elle ralentir les calculs"**
