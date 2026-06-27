# Chapitre 5 — Comprendre les pompes à chaleur modernes

## Introduction

Les principes thermodynamiques d'une pompe à chaleur n'ont pas changé depuis les années 1980. Ce qui a radicalement évolué, c'est la façon dont ces principes sont mis en œuvre : l'électronique de puissance, les microcontrôleurs et les nouveaux fluides frigorigènes ont transformé une machine mécanique relativement simple en un système complexe et performant.

Ce chapitre s'adresse aux lecteurs qui souhaitent comprendre ce qui se passe réellement à l'intérieur d'une PAC moderne — non pas pour reproduire les travaux de Suominen, mais pour être capables de dialoguer avec un installateur, de lire une documentation technique, ou d'aborder sereinement le diagnostic d'une panne.

---

## Le cycle frigorifique : la base de tout

Une pompe à chaleur est une machine thermodynamique qui déplace de la chaleur d'un milieu froid vers un milieu chaud — à l'inverse du sens naturel des échanges thermiques. Elle utilise pour cela un **fluide frigorigène** qui change d'état en absorbant ou en libérant de la chaleur.

Le cycle de base comporte quatre étapes :

**1. Évaporation** — Le fluide frigorigène, sous basse pression, absorbe la chaleur de la source froide (air extérieur, sol, eau) et se vaporise. C'est le rôle de l'évaporateur.

**2. Compression** — Le compresseur aspire la vapeur et l'amène à haute pression et haute température. C'est l'étape qui consomme de l'énergie électrique.

**3. Condensation** — Le fluide chaud et sous pression cède sa chaleur au circuit de chauffage du bâtiment et se liquéfie. C'est le rôle du condenseur (ou échangeur intérieur).

**4. Détente** — Le fluide liquide passe à travers un détendeur qui abaisse brutalement sa pression, ce qui provoque un refroidissement important. Le cycle peut recommencer.

> **Le point clé** : la chaleur restituée au bâtiment est la somme de la chaleur prélevée à l'extérieur *et* de l'énergie électrique consommée par le compresseur. C'est pourquoi le COP[^1] est supérieur à 1 — on ne crée pas d'énergie, on la déplace.

*: **COP** (*Coefficient of Performance*) : rapport entre l'énergie thermique restituée et l'énergie électrique consommée. Un COP de 4 signifie que pour 1 kWh électrique consommé, la machine produit 4 kWh de chaleur — dont 3 kWh prélevés gratuitement dans l'environnement.

---

## Détente directe (DX) vs circuit intermédiaire

Il existe deux grandes architectures de pompes à chaleur géothermiques, qui correspondent exactement au débat que Suominen avait ouvert dans les années 1980.

### Circuit intermédiaire (eau glycolée)

C'est l'architecture la plus répandue aujourd'hui pour la géothermie :
- Un circuit de capteurs enterrés contient de l'eau glycolée (antigel)
- Cette eau glycolée circule entre le sol et un échangeur dans la PAC
- L'échangeur transfère la chaleur au circuit frigorifique

**Avantage** : sécurité (le fluide frigorigène reste confiné dans la machine), facilité de maintenance.  
**Inconvénient** : double échange thermique = pertes supplémentaires = COP légèrement réduit.

### Détente directe (DX — *Direct eXpansion*)

C'est le principe que Suominen préconisait :
- Le fluide frigorigène circule directement dans les capteurs enterrés
- L'évaporation se produit dans le sol lui-même
- Un seul échange thermique au lieu de deux

**Avantage** : meilleur COP, capteurs plus courts (l'échange est plus efficace).  
**Inconvénient** : plus grande quantité de fluide frigorigène en circulation, contraintes de sécurité plus strictes, maintenance plus délicate.

La détente directe reste une niche technique — utilisée par quelques fabricants spécialisés — mais elle confirme quarante ans plus tard que Suominen avait identifié la solution thermodynamiquement optimale.

---

## Le compresseur Inverter : le cœur de la PAC moderne

### Principe de l'onduleur

Un compresseur Inverter est un compresseur dont la vitesse de rotation est variable, contrôlée par un **onduleur** (ou *variateur de fréquence*) électronique.

L'onduleur fonctionne en trois étapes :
1. **Redressement** : le courant alternatif du secteur (230 V AC) est converti en courant continu (300–400 V DC)
2. **Filtrage** : des condensateurs de forte capacité lissent la tension du bus DC
3. **Découpage** : des transistors de puissance (IGBT) reconstituent un courant alternatif de fréquence variable pour alimenter le moteur du compresseur

C'est ce bus DC à 300–400 V qui constitue le point de vigilance lors d'une intervention de maintenance — exactement comme les condensateurs haute tension d'un amplificateur à lampes, ils restent chargés plusieurs minutes après la coupure secteur.

### Pourquoi c'est important

Un compresseur à vitesse fixe fonctionne à pleine puissance ou s'arrête — c'est le tout-ou-rien que Suominen critiquait. Un compresseur Inverter peut tourner à 30 %, 60 %, 100 % de sa puissance nominale, et tout point intermédiaire.

Conséquences directes :
- **COP maximisé en permanence** : la machine travaille au point de rendement optimal
- **Confort amélioré** : la température intérieure est stable, sans oscillations
- **Usure réduite** : moins de démarrages à pleine charge, durée de vie augmentée
- **Fonctionnement à très basse température** : la machine peut tourner lentement plutôt que de s'arrêter

---

## La régulation : le cerveau du système

### Architecture générale

Une PAC moderne comporte deux niveaux de régulation :

**Régulation interne** (carte électronique de l'unité extérieure) :
- Contrôle du compresseur Inverter
- Gestion du dégivrage
- Protection des composants (pressions, températures, courants)
- Communication avec l'unité intérieure

**Régulation système** (thermostat ou tableau de bord) :
- Courbe climatique — calcul de la température de départ en fonction de la température extérieure
- Gestion des modes (chauffage, eau chaude sanitaire, rafraîchissement)
- Interface utilisateur
- Connexion domotique

### La courbe climatique

C'est le principe de régulation le plus important à comprendre. Au lieu de réagir à une température intérieure (comme un simple thermostat), la PAC *anticipe* les besoins en fonction de la température extérieure.

Une courbe climatique typique pourrait être :
- À +10 °C extérieur → départ circuit à 35 °C
- À 0 °C extérieur → départ circuit à 45 °C
- À −10 °C extérieur → départ circuit à 55 °C

Cette courbe est paramétrable selon le type d'émetteurs (plancher chauffant, radiateurs basse température, radiateurs haute température) et l'isolation du bâtiment. Un mauvais réglage de courbe climatique est l'une des causes les plus fréquentes de sous-performance d'une installation pourtant bien dimensionnée.

### Les protocoles de communication

Les unités intérieure et extérieure communiquent via des protocoles série propriétaires ou standardisés. Quelques exemples :
- **Daikin** : protocole S21 ou D-BUS
- **Mitsubishi** : protocole CN105
- **Atlantic / Hitachi** : protocoles propriétaires

Ces protocoles sont de plus en plus documentés par la communauté open source, ce qui ouvre des possibilités intéressantes pour l'intégration domotique — notamment via des passerelles ESP32 qui permettent de lire les données de la PAC et de les intégrer dans Home Assistant, Node-RED ou MQTT.

---

## Les fluides frigorigènes : évolution et contraintes

| Fluide | Époque | GWP[*] | Remarque |
|--------|--------|---------|----------|
| R22 | 1980s–2000s | 1810 | Interdit depuis 2015 (destruction couche d'ozone) |
| R410A | 2000s–2020s | 2088 | En cours de remplacement (GWP trop élevé) |
| R32 | 2015– | 675 | Majoritaire aujourd'hui, légèrement inflammable |
| R290 (propane) | 2020– | 3 | Excellent thermodynamiquement, inflammable |
| R454B | 2023– | 466 | Successeur probable du R410A |

[*]: **GWP** (*Global Warming Potential*) : potentiel de réchauffement climatique du fluide, exprimé en équivalent CO₂ sur 100 ans. Le R290 (propane) a un GWP de 3 — quasi neutre — mais son inflammabilité impose des contraintes d'installation spécifiques.

La tendance est claire : les fluides de demain seront à faible GWP, au prix d'une inflammabilité accrue qui impose de nouvelles règles de sécurité pour les installateurs et les techniciens de maintenance.

---

## Ce qu'un Maker doit retenir

- Le cycle frigorifique est immuable — ce qui évolue, c'est la façon de le piloter
- L'Inverter est la clé de la performance moderne — comprendre son fonctionnement, c'est comprendre 80 % des pannes électroniques
- La courbe climatique est le réglage le plus impactant — une PAC bien dimensionnée mais mal réglée sous-performe systématiquement
- Les protocoles de communication sont de plus en plus accessibles — un ESP32 peut lire et piloter une PAC moderne
- Le bus DC de l'onduleur reste sous tension après coupure — même réflexe que devant un ampli à lampes : on attend, on mesure avant de toucher

Le chapitre suivant aborde le diagnostic et le dépannage — avec les précautions de sécurité qui s'imposent.
