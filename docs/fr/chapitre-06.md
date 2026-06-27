# Chapitre 6 — Diagnostic et dépannage des pompes à chaleur modernes

## Avertissement de sécurité

> ⚠️ **À lire avant toute intervention**
>
> Une pompe à chaleur moderne contient des tensions dangereuses. Le bus DC de l'onduleur atteint 300 à 400 V en monophasé résidentiel. Les condensateurs de filtrage restent chargés **plusieurs minutes après la coupure secteur** — exactement comme les condensateurs d'un amplificateur à lampes ou d'un téléviseur à tube cathodique.
>
> **Règle absolue : on coupe, on attend 10 minutes, on mesure avant de toucher.**
>
> Au-delà de 50 V DC, le courant traversant le corps peut être létal. Un voltmètre sur le bus DC avant toute intervention n'est pas une précaution — c'est une obligation.
>
> La manipulation du circuit frigorifique (fluide frigorigène, raccords, vannes) est légalement réservée aux techniciens titulaires de l'attestation d'aptitude. Ce chapitre ne couvre pas ces interventions.

---

## Ce qu'un Maker peut faire

Le diagnostic d'une PAC en panne se divise naturellement en deux zones :

**Zone verte — accessible sans certification :**
- Lecture des codes erreur
- Diagnostic des capteurs de température (sondes NTC)
- Vérification des alimentations basse tension
- Diagnostic des cartes de régulation
- Vérification du câblage et des connecteurs
- Intégration domotique et monitoring

**Zone orange — faisable avec précautions :**
- Diagnostic de la carte Inverter (après décharge confirmée des condensateurs)
- Mesure des tensions sur le bus DC
- Remplacement de la carte Inverter

**Zone rouge — certification obligatoire :**
- Tout ce qui touche au circuit frigorifique
- Manipulation des fluides frigorigènes
- Raccordements frigorifiques

---

## Lire les codes erreur

C'est toujours la première étape. Chaque fabricant dispose d'un système de codes erreur affiché sur l'unité intérieure ou accessible via l'interface de régulation.

### Accéder aux codes

Selon les machines :
- **Affichage direct** sur le tableau de bord (codes du type E1, F3, P8...)
- **LED clignotantes** sur la carte électronique de l'unité extérieure — le nombre de clignotements encode le code erreur
- **Application mobile** ou interface web propriétaire
- **Mode diagnostic** accessible par une séquence de touches sur la télécommande

### Décoder les codes

Les manuels techniques des fabricants sont généralement disponibles en ligne et documentent l'ensemble des codes erreur. Quelques codes fréquents communs à de nombreuses marques :

| Type de code | Cause fréquente |
|---|---|
| Erreur capteur température | Sonde NTC défectueuse ou déconnectée |
| Erreur haute pression | Condenseur encrassé, ventilateur défaillant, fluide surchargé |
| Erreur basse pression | Fuite de fluide, évaporateur givré, détendeur défaillant |
| Erreur communication | Câble de liaison inter-unités défectueux ou mauvaise configuration |
| Erreur Inverter | Carte Inverter défaillante, moteur compresseur en défaut |
| Erreur dégivrage | Sonde de dégivrage défectueuse, cycle de dégivrage bloqué |

---

## Diagnostic des capteurs de température (sondes NTC)

Les sondes NTC (*Negative Temperature Coefficient*) sont des thermistances dont la résistance diminue quand la température augmente. Elles sont omniprésentes dans une PAC : température extérieure, température de départ, température de retour, température d'évaporateur, température de condenseur...

### Mesure d'une sonde NTC

Une sonde NTC se mesure simplement avec un multimètre en mode résistance, **hors tension** :

| Température | Résistance typique (NTC 10kΩ à 25°C) |
|---|---|
| −20 °C | ~67 kΩ |
| 0 °C | ~27 kΩ |
| +25 °C | ~10 kΩ |
| +50 °C | ~4 kΩ |

Une sonde qui mesure 0 Ω (court-circuit) ou ∞ (circuit ouvert) est défectueuse. Une sonde qui donne une valeur incohérente avec la température ambiante est également suspecte.

### Remplacement

Les sondes NTC sont des composants standards, souvent interchangeables entre marques pour les valeurs courantes (10 kΩ à 25 °C, coefficient B standard). Le connecteur est parfois propriétaire mais le capteur lui-même est générique.

---

## Diagnostic de la carte de régulation

La carte de régulation (unité de contrôle) est le cerveau de la PAC. Elle gère la communication entre unités, pilote l'Inverter, surveille les capteurs et protège les composants.

### Points de contrôle

**Alimentations** — vérifier avec un multimètre les tensions d'alimentation de la carte :
- 12 V DC ou 24 V DC selon les fabricants
- 5 V DC pour les circuits logiques
- Une tension absente ou hors tolérance (± 10 %) indique un problème d'alimentation à vérifier avant de suspecter la carte elle-même

**Connecteurs** — les connecteurs à faible section sont fréquemment source de problèmes :
- Oxydation des contacts (fréquent en environnement extérieur humide)
- Connecteurs mal enfichés après une intervention précédente
- Fils arrachés sur les sondes

**Condensateurs électrolytiques** — comme sur tout équipement électronique, les condensateurs électrolytiques vieillissent et peuvent bomber ou fuir. Un contrôle visuel s'impose avant toute autre mesure.

### Communication inter-cartes

Le câble de liaison entre unité intérieure et unité extérieure est une source fréquente de pannes, souvent négligée :
- Section insuffisante pour la longueur de liaison
- Polarité inversée lors d'une installation ou réparation
- Câble endommagé mécaniquement (rongeurs, pincement)
- Perturbations électromagnétiques si le câble chemine près d'un câble de puissance

---

## Diagnostic de la carte Inverter

### Précautions préalables — obligatoires

1. Couper l'alimentation secteur au disjoncteur dédié
2. Attendre **au minimum 10 minutes**
3. Mesurer la tension sur le bus DC (bornes identifiées P et N sur la carte, ou condensateurs du bus) — elle doit être inférieure à 50 V avant toute manipulation
4. Travailler avec une main dans le dos si possible — réflexe de sécurité électricien

### Diagnostic visuel

Avant toute mesure électrique, un examen visuel minutieux s'impose :
- Traces de brûlure ou de claquage sur les IGBT
- Condensateurs de bus bombés ou ayant fui
- Résistances de décharge du bus calcinées
- Pistes PCB brûlées ou décollées

### Remplacement de carte Inverter

Les cartes Inverter sont disponibles en pièces détachées chez les revendeurs spécialisés et de plus en plus sur les places de marché en ligne. Le remplacement est souvent la solution la plus économique face à une carte défaillante — la réparation composant par composant est envisageable pour un électronicien expérimenté, mais les IGBT de puissance nécessitent un équipement de soudage adapté.

---

## Intégration domotique et monitoring

C'est un domaine particulièrement intéressant pour les Papy Makers : plusieurs fabricants permettent d'accéder aux données de la PAC via des protocoles documentés ou reverse-engineered par la communauté.

### Passerelles ESP32

Des projets open source permettent de connecter une PAC à un système domotique via un ESP32 :

- **ESPAltherma** (Daikin Altherma) — lecture et contrôle via le connecteur X10A de l'unité intérieure
- **CN105** (Mitsubishi Electric) — interface série documentée, nombreux projets Arduino/ESP32
- **Intégration MQTT** — les données lues peuvent être publiées sur un broker MQTT et intégrées dans Node-RED, Home Assistant, ou tout autre système

Ces passerelles permettent de monitorer en temps réel le COP, les températures, les puissances consommées et produites — des données précieuses pour optimiser le fonctionnement de l'installation et détecter une dégradation progressive des performances avant qu'elle ne devienne une panne franche.

### Ce qu'on peut monitorer

- Température extérieure et température de départ
- Puissance électrique consommée (Wh)
- Puissance thermique produite (calculée)
- COP instantané et COP moyen saisonnier (SCOP)
- Nombre et durée des cycles de dégivrage
- Codes erreur en temps réel

---

## Ressources et documentation

### Manuels techniques

La plupart des fabricants publient leurs manuels d'installation et de maintenance sur leur site professionnel. Certains nécessitent un compte installateur, mais les manuels de service complets circulent largement sur les forums spécialisés.

### Communautés en ligne

- **Forums PAC** (pac-clim.com, chauffage-piscine.fr) — retours d'expérience d'installateurs et de particuliers
- **Home Assistant Community** — intégration domotique des PAC
- **GitHub** — projets ESPAltherma, CN105, et autres passerelles open source

### Outillage minimum recommandé

| Outil | Usage |
|---|---|
| Multimètre True RMS | Mesures tension, résistance, courant |
| Pince ampèremétrique | Mesure courant sans coupure circuit |
| Thermomètre IR | Vérification températures surfaces |
| Oscilloscope (optionnel) | Diagnostic signaux de commande Inverter |
| ESP32 + câble adapté | Intégration domotique et monitoring |

---

## Ce qu'un Maker doit retenir

- **Commencer toujours par les codes erreur** — ils orientent le diagnostic et évitent de chercher au mauvais endroit
- **Les sondes NTC sont souvent en cause** — simples à mesurer, peu coûteuses à remplacer
- **Le bus DC reste dangereux après coupure** — 10 minutes d'attente et mesure avant intervention sur l'Inverter
- **La carte de régulation se diagnostique en basse tension** — alimentations, connecteurs, condensateurs
- **Un ESP32 peut transformer une PAC en source de données** — le monitoring prévient les pannes et optimise les performances
- **Le circuit frigorifique reste hors périmètre** — ce n'est pas une limite technique, c'est une obligation réglementaire
