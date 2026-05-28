\# Périmètre d'analyse



\## 1. Cible autorisée



\* \*\*Nom de l'application\*\* : InjuredAndroid

\* \*\*Fichier analysé\*\* : InjuredAndroid.apk

\* \*\*Package Android\*\* : b3nac.injuredandroid

\* \*\*Version de l'application\*\* : 1.0.9

\* \*\*Type d'artefact\*\* : APK pédagogique volontairement vulnérable

\* \*\*Contexte\*\* : LAB 8 - Analyse de posture et exposition d'applications mobiles avec BeVigil et Yaazhini



\## 2. Propriétaire / origine de la cible



L'application InjuredAndroid est utilisée comme application pédagogique dans le cadre du lab de sécurité mobile. Elle est volontairement vulnérable et destinée à l'apprentissage de l'analyse de sécurité des applications Android.



\## 3. Autorisation



\* \*\*Source de l'autorisation\*\* : Cours de sécurité des applications mobiles

\* \*\*Cadre\*\* : Travail académique encadré

\* \*\*Objectif\*\* : Analyse défensive, documentation des constats et corrélation avec OWASP MASVS

\* \*\*Preuve d'autorisation\*\* : Sujet du LAB 8 fourni dans le cadre du cours



\## 4. Type d'analyse réalisée



\* \[x] Analyse d'un APK pédagogique

\* \[ ] Analyse d'une application interne autorisée

\* \[ ] Analyse d'un domaine explicitement autorisé



Les outils utilisés sont :



\* \*\*BeVigil\*\* : analyse de posture et exposition externe

\* \*\*Yaazhini APK Scanner\*\* : analyse statique de l'APK



\## 5. Limites explicites



Cette analyse respecte un cadre strictement légal et défensif.



Les actions suivantes sont interdites dans ce lab :



\* Exploitation active des vulnérabilités détectées

\* Test intrusif contre une cible réelle

\* Contournement de mécanismes de sécurité

\* Attaque contre des services ou domaines externes

\* Utilisation abusive des endpoints ou clés détectées

\* Publication de secrets, tokens ou clés API en clair



Toute donnée sensible détectée doit être masquée dans les livrables.



\## 6. Période d'analyse



\* \*\*Date de début\*\* : 2026-05-28

\* \*\*Durée prévue\*\* : 2 heures

\* \*\*Environnement\*\* : Windows avec accès internet

\* \*\*Analyste\*\* : \[TON NOM]



\## 7. Artefact analysé



\* \*\*Nom du fichier\*\* : InjuredAndroid.apk

\* \*\*Emplacement dans le projet\*\* : `00-scope/InjuredAndroid.apk`

\* \*\*Hash SHA-256\*\* : \[COLLER ICI LE HASH SHA-256]



Le hash SHA-256 permet de garantir que l'APK analysé est bien l'artefact utilisé pendant le lab.



\## 8. Objectif de l'analyse



L'objectif est d'évaluer la posture de sécurité de l'application mobile à partir des signaux détectés par BeVigil et Yaazhini.



Les objectifs techniques sont :



\* Identifier les permissions Android déclarées

\* Repérer les URLs et domaines liés à l'application

\* Détecter les secrets potentiels

\* Identifier les composants Android exposés

\* Relever les vulnérabilités statiques détectées

\* Trier les résultats et supprimer les doublons

\* Corréler les constats avec OWASP MASVS

\* Produire un rapport exploitable et défensif



\## 9. Engagement éthique



Je certifie que cette analyse est réalisée uniquement dans un cadre pédagogique, légal et défensif. Aucune exploitation active n'a été effectuée. Les résultats sont utilisés uniquement pour documenter la posture de sécurité de l'application étudiée.



\*\*Signature\*\* : \[TON NOM]

\*\*Date\*\* : 2026-05-28



