\# Notes d'analyse Yaazhini



\## 1. Informations générales



\* \*\*Outil utilisé\*\* : Yaazhini APK Scanner

\* \*\*Application analysée\*\* : lab8 / InjuredAndroid

\* \*\*Fichier APK\*\* : InjuredAndroid.apk

\* \*\*Package Android\*\* : b3nac.injuredandroid

\* \*\*Version de l'application\*\* : 1.0.9

\* \*\*Date du scan\*\* : 28-MAY-2026, 2:04 PM

\* \*\*Android Min SDK Version\*\* : 21

\* \*\*Android Target SDK Version\*\* : 29

\* \*\*Taille de l'application\*\* : 17.5 MB

\* \*\*Type d'analyse\*\* : Analyse statique APK



\## 2. Preuves collectées



Les captures suivantes documentent l'analyse Yaazhini :



\* `docs/images/15-yaazhini-app-summary.png`

\* `docs/images/17-expvul.png`

\* `docs/images/18-expvul.png`

\* `docs/images/19-expvul.png`

\* `docs/images/20-permissions.png`

\* `docs/images/21-activities.png`

\* `docs/images/22-recievers.png`

\* `docs/images/23-url.png`



\## 3. Résumé de l'application



Yaazhini a extrait les informations principales de l'APK :



| Élément                    | Valeur               |

| -------------------------- | -------------------- |

| App Name                   | lab8                 |

| Android Package            | b3nac.injuredandroid |

| Date of Scan               | 28-MAY-2026, 2:04 PM |

| App Version                | 1.0.9                |

| Android Min SDK Version    | 21                   |

| Android Target SDK Version | 29                   |

| App Size                   | 17.5 MB              |



\## 4. Vulnérabilités détectées



Yaazhini a classé les vulnérabilités en plusieurs niveaux de sévérité.



\### High



\#### Insecure communication



\* \*\*Nombre\*\* : 1

\* \*\*Fichier associé\*\* : `a2.java`

\* \*\*Preuve\*\* : `docs/images/17-expvul.png`

\* \*\*Observation\*\* : Yaazhini signale une communication non sécurisée.

\* \*\*Élément visible\*\* : présence d'une URL en `http://localhost`

\* \*\*Impact potentiel\*\* : une communication non chiffrée peut exposer des données en transit si elle est utilisée dans un contexte réel.

\* \*\*Recommandation\*\* : utiliser HTTPS/TLS pour toutes les communications réseau réelles.



\### Medium



\#### Improper export of receivers



\* \*\*Nombre\*\* : 1

\* \*\*Élément concerné\*\* : `b3nac.injuredandroid.FlagFiveReceiver`

\* \*\*Fichier associé\*\* : `AndroidManifest.xml`

\* \*\*Preuve\*\* : `docs/images/18-expvul.png`

\* \*\*Observation\*\* : le receiver est déclaré avec `android:exported="true"`.

\* \*\*Impact potentiel\*\* : un receiver exporté peut être appelé par d'autres applications si aucune protection n'est appliquée.

\* \*\*Recommandation\*\* : définir `android:exported="false"` si le receiver n'a pas besoin d'être exposé, ou ajouter une permission de protection.



\#### Insecure ECB mode



\* \*\*Nombre\*\* : 6

\* \*\*Observation\*\* : Yaazhini signale une utilisation potentielle du mode ECB.

\* \*\*Impact potentiel\*\* : ECB est considéré comme faible car il ne masque pas correctement les répétitions dans les données chiffrées.

\* \*\*Recommandation\*\* : éviter ECB et utiliser des modes plus sûrs comme GCM ou CBC avec IV correctement géré, selon le contexte.



\#### Insecure algorithm - DES



\* \*\*Nombre\*\* : 2

\* \*\*Fichier associé\*\* : `b3nac/injuredandroid/k.java`

\* \*\*Preuve\*\* : `docs/images/19-expvul.png`

\* \*\*Éléments visibles\*\* :



&#x20; \* `SecretKeyFactory.getInstance("DES")`

&#x20; \* `Cipher.getInstance("DES")`

\* \*\*Impact potentiel\*\* : DES est un algorithme ancien et faible.

\* \*\*Recommandation\*\* : remplacer DES par un algorithme moderne comme AES avec une configuration sécurisée.



\#### Use of insufficiently random values



\* \*\*Nombre\*\* : 2

\* \*\*Observation\*\* : Yaazhini signale un usage potentiel de valeurs aléatoires insuffisamment robustes.

\* \*\*Impact potentiel\*\* : si ces valeurs sont utilisées pour des tokens, clés ou secrets, elles peuvent être prévisibles.

\* \*\*Recommandation\*\* : utiliser `SecureRandom` pour tout usage lié à la sécurité.



\### Low



\* \*\*Nombre total\*\* : 2

\* \*\*Observation\*\* : Yaazhini signale aussi des constats de faible sévérité.

\* \*\*Recommandation\*\* : vérifier ces éléments pour distinguer les vrais risques des faux positifs.



\## 5. Permissions Android



Yaazhini a identifié les permissions suivantes :



| N° | Permission                                  | Description                                                 |

| -: | ------------------------------------------- | ----------------------------------------------------------- |

|  1 | `android.permission.ACCESS\_NETWORK\_STATE`   | Permet de connaître l'état des connexions réseau            |

|  2 | `android.permission.INTERNET`               | Permet à l'application d'accéder à Internet                 |

|  3 | `android.permission.WRITE\_EXTERNAL\_STORAGE` | Permet d'écrire sur le stockage externe                     |

|  4 | `android.permission.READ\_PHONE\_STATE`       | Permet de lire des informations liées à l'état du téléphone |

|  5 | `android.permission.READ\_EXTERNAL\_STORAGE`  | Permet de lire le contenu du stockage externe               |



\### Analyse



Les permissions `INTERNET` et `ACCESS\_NETWORK\_STATE` sont fréquentes dans les applications connectées. Cependant, les permissions liées au stockage externe et à l'état du téléphone doivent être justifiées.



\### Recommandations



\* Vérifier que chaque permission est réellement nécessaire.

\* Retirer les permissions inutilisées.

\* Limiter l'accès au stockage externe.

\* Éviter `READ\_PHONE\_STATE` si elle n'est pas indispensable.



\## 6. Activities détectées



Yaazhini a listé plusieurs activités Android, dont :



\* `b3nac.injuredandroid.FlagSeventeenActivity`

\* `b3nac.injuredandroid.CSPBypassActivity`

\* `b3nac.injuredandroid.AssemblyActivity`

\* `io.flutter.embedding.android.FlutterActivity`

\* `b3nac.injuredandroid.RCEActivity`

\* `b3nac.injuredandroid.SettingsActivity`

\* `b3nac.injuredandroid.ExportedProtectedIntent`

\* `b3nac.injuredandroid.QXV0aA`

\* `b3nac.injuredandroid.FlagTwelveProtectedActivity`

\* `b3nac.injuredandroid.DeepLinkActivity`

\* `b3nac.injuredandroid.FlagTenUnicodeActivity`

\* `b3nac.injuredandroid.FlagOneLoginActivity`

\* `b3nac.injuredandroid.FlagNineFirebaseActivity`

\* `b3nac.injuredandroid.FlagEightLoginActivity`



\### Analyse



La présence de nombreuses activités est normale pour une application pédagogique composée de plusieurs challenges. Cependant, les activités exposées ou liées à des deep links doivent être vérifiées afin d'éviter une exposition non contrôlée.



\### Recommandations



\* Vérifier l'attribut `android:exported` pour chaque activité sensible.

\* Protéger les activités sensibles par des permissions si nécessaire.

\* Vérifier les activités liées aux deep links.

\* Limiter les activités accessibles depuis l'extérieur de l'application.



\## 7. Receivers détectés



Yaazhini a détecté le receiver suivant :



| Receiver                                | Exported |

| --------------------------------------- | -------- |

| `b3nac.injuredandroid.FlagFiveReceiver` | true     |



\### Analyse



Le receiver `FlagFiveReceiver` est exporté. Cela confirme le constat Yaazhini relatif à l'export incorrect de receivers.



\### Impact potentiel



Un receiver exporté peut être invoqué par une autre application si aucune restriction n'est appliquée.



\### Recommandation



Définir `android:exported="false"` si le receiver ne doit pas être accessible par d'autres applications, ou utiliser une permission pour limiter son accès.



\## 8. Linked URLs détectées



Yaazhini a identifié plusieurs URLs et domaines liés à l'application :



| Host                                    | Server          | URL                                                                                                                        |

| --------------------------------------- | --------------- | -------------------------------------------------------------------------------------------------------------------------- |

| `http://schemas.android.com`            | Non indiqué     | `http://schemas.android.com/apk/res/android`, `http://schemas.android.com/apk/res-auto`, `http://schemas.android.com/aapt` |

| `https://injuredandroid.firebaseio.com` | nginx           | `https://injuredandroid.firebaseio.com`                                                                                    |

| `https://m.do.co`                       | cloudflare      | `https://m.do.co/c/9348bb7410b4`                                                                                           |

| `https://plus.google.com`               | sffe            | `https://plus.google.com/`                                                                                                 |

| `https://cloud.google.com`              | ESF             | `https://cloud.google.com/kms/docs/reference/rest/v1/projects.locations.keyRings.cryptoKeys#CryptoKey`                     |

| `https://console.firebase.google.com`   | ESF             | `https://console.firebase.google.com/`                                                                                     |

| `https://firebase.google.com`           | Google Frontend | URLs liées à la documentation Firebase                                                                                     |

| `https://github.com`                    | github.com      | URLs liées à Firebase SDK et Flutter                                                                                       |



\### Analyse



Les URLs détectées montrent que l'application utilise ou référence des services externes comme Firebase, Google Cloud, GitHub et DigitalOcean. Ces URLs permettent de cartographier les services et dépendances visibles dans l'application.



\### Recommandations



\* Vérifier que les URLs détectées sont nécessaires.

\* Vérifier que les communications utilisent HTTPS.

\* Éviter d'exposer des endpoints sensibles dans le code client.

\* Documenter les domaines utilisés dans le périmètre de l'application.



\## 9. Corrélation avec BeVigil



Les résultats Yaazhini confirment plusieurs signaux déjà détectés par BeVigil :



| Constat                               | BeVigil      | Yaazhini                                     | Statut   |

| ------------------------------------- | ------------ | -------------------------------------------- | -------- |

| Exported Activity / composant exporté | Oui          | Partiellement confirmé avec receiver exporté | Confirmé |

| Weak Crypto Algorithms                | Oui          | DES et ECB détectés                          | Confirmé |

| URLs / Assets réseau                  | Oui          | URLs Firebase, Google, GitHub détectées      | Confirmé |

| Permissions risquées                  | Oui          | Permissions stockage et téléphone détectées  | Confirmé |

| Communication non sécurisée           | Non détaillé | HTTP détecté dans `a2.java`                  | Confirmé |

| Receiver exporté                      | Non détaillé | `FlagFiveReceiver` exporté                   | Confirmé |



\## 10. Faux positifs possibles



Certains constats doivent être interprétés avec prudence :



\* Les URLs de documentation peuvent être présentes dans le code sans être utilisées en production.

\* Une permission déclarée n'est pas automatiquement une vulnérabilité.

\* Une activité ou un receiver exporté peut être volontaire dans une application pédagogique.

\* Les détections liées aux bibliothèques tierces doivent être distinguées du code applicatif principal.

\* Les chaînes détectées comme sensibles doivent être vérifiées avant d'être considérées comme secrets réels.



\## 11. Recommandations générales



\* Utiliser HTTPS/TLS pour toutes les communications réelles.

\* Remplacer DES et ECB par des mécanismes cryptographiques modernes.

\* Utiliser `SecureRandom` pour les valeurs liées à la sécurité.

\* Limiter les permissions Android au strict nécessaire.

\* Vérifier les composants exportés dans le fichier `AndroidManifest.xml`.

\* Protéger les receivers et activités sensibles.

\* Éviter de stocker ou exposer des secrets dans le code client.

\* Documenter les dépendances et services externes utilisés.



\## 12. Conclusion



L'analyse Yaazhini a permis de compléter les résultats BeVigil par une analyse statique de l'APK. Les principaux constats concernent une communication non sécurisée, l'utilisation d'algorithmes cryptographiques faibles, l'exposition d'un receiver, la présence de permissions sensibles et la détection d'URLs liées à Firebase, Google, GitHub et DigitalOcean.



Ces résultats seront intégrés dans le triage final et corrélés aux catégories OWASP MASVS afin de produire un rapport défensif complet.



