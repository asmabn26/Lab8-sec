\# Notes d'analyse BeVigil



\## 1. Informations générales



\* \*\*Outil utilisé\*\* : BeVigil

\* \*\*Application analysée\*\* : InjuredAndroid

\* \*\*Fichier APK\*\* : InjuredAndroid.apk

\* \*\*Package Android\*\* : b3nac.injuredandroid

\* \*\*Version de l'application\*\* : 1.0.9

\* \*\*Type d'analyse\*\* : Analyse défensive de posture mobile

\* \*\*Cadre\*\* : Lab pédagogique autorisé



\## 2. Statut de l'analyse



L'APK a été soumis avec succès à BeVigil. La plateforme a exécuté les étapes suivantes :



\* `INITIATED - App scan started`

\* `PROCESSING - Meta-data extraction complete`

\* `ANALYSING - App analysis complete`

\* `DONE - Security report is ready`



Le rapport de sécurité a donc été généré avec succès et consulté depuis l'interface web.



\## 3. Score global



\* \*\*Security Rating\*\* : 6.9

\* \*\*Niveau\*\* : Average

\* \*\*Total detected issues\*\* : 7



Répartition des problèmes détectés :



| Niveau | Nombre |

| ------ | -----: |

| High   |      1 |

| Medium |      2 |

| Low    |      4 |



\## 4. Captures associées



Les résultats BeVigil sont documentés à l'aide des captures suivantes :



\* `docs/images/06-bevigil-overview.png`

\* `docs/images/07-bevigil-summary.png`

\* `docs/images/08-bevigil-permissions-assets.png`

\* `docs/images/09-bevigil-manifest-scanner.png`



\## 5. Résumé des constats détectés



\### FIND-001 — AWS API Key potentielle



\* \*\*Source\*\* : BeVigil / Strings

\* \*\*Sévérité\*\* : High

\* \*\*Confiance\*\* : Forte

\* \*\*Description\*\* : BeVigil signale la présence potentielle d'une clé AWS API dans les chaînes de caractères de l'application.

\* \*\*Impact potentiel\*\* : Si la clé est valide, elle pourrait permettre un accès non autorisé à des services cloud.

\* \*\*Recommandation\*\* :



&#x20; \* Ne jamais exposer de clé API complète dans le code client.

&#x20; \* Masquer toute valeur sensible dans les rapports.

&#x20; \* Révoquer la clé si elle est réellement active.

&#x20; \* Déplacer la logique sensible côté serveur.

\* \*\*Statut\*\* : À confirmer manuellement.



\### FIND-002 — Possible Task Hijacking



\* \*\*Source\*\* : BeVigil / Issues

\* \*\*Sévérité\*\* : Medium

\* \*\*Confiance\*\* : Moyenne

\* \*\*Description\*\* : BeVigil signale un risque potentiel de détournement de tâche Android.

\* \*\*Impact potentiel\*\* : Une mauvaise configuration des activités Android peut permettre une confusion dans la navigation ou l'affichage de l'application.

\* \*\*Recommandation\*\* :



&#x20; \* Vérifier les attributs `taskAffinity`, `launchMode` et `exported` dans le fichier `AndroidManifest.xml`.

&#x20; \* Éviter les configurations inutiles comme `singleTask` si elles ne sont pas nécessaires.

&#x20; \* Protéger les activités sensibles.

\* \*\*Statut\*\* : À confirmer.



\### FIND-003 — Weak Crypto Algorithms



\* \*\*Source\*\* : BeVigil / Vulnerabilities

\* \*\*Sévérité\*\* : Low

\* \*\*Confiance\*\* : Moyenne

\* \*\*Description\*\* : BeVigil détecte l'utilisation potentielle d'algorithmes cryptographiques faibles.

\* \*\*Impact potentiel\*\* : Si ces algorithmes sont utilisés pour protéger des données sensibles, la confidentialité ou l'intégrité des données pourrait être compromise.

\* \*\*Recommandation\*\* :



&#x20; \* Remplacer les algorithmes faibles par des algorithmes modernes.

&#x20; \* Vérifier si le code détecté est réellement utilisé dans une fonctionnalité sensible.

\* \*\*Statut\*\* : À confirmer.



\### FIND-004 — Exported Activity



\* \*\*Source\*\* : BeVigil / Manifest Scanner

\* \*\*Sévérité\*\* : Low

\* \*\*CWE\*\* : CWE-926

\* \*\*Confiance\*\* : Forte

\* \*\*Fichier concerné\*\* : AndroidManifest.xml

\* \*\*Description\*\* : Une activité Android exportée a été détectée. Une activité exportée peut être accessible depuis d'autres applications.

\* \*\*Impact potentiel\*\* : Une activité exposée peut augmenter la surface d'attaque si elle n'est pas correctement protégée.

\* \*\*Recommandation\*\* :



&#x20; \* Définir `android:exported="false"` pour les activités qui ne doivent pas être accessibles depuis l'extérieur.

&#x20; \* Ajouter des permissions si l'activité doit rester exportée.

&#x20; \* Vérifier les filtres d'intention.

\* \*\*Statut\*\* : Confirmé.



\### FIND-005 — Generic API Key potentielle



\* \*\*Source\*\* : BeVigil / Strings

\* \*\*Sévérité\*\* : Low

\* \*\*Confiance\*\* : Moyenne

\* \*\*Description\*\* : BeVigil signale une chaîne ressemblant à une clé API générique.

\* \*\*Impact potentiel\*\* : Si la chaîne correspond à une vraie clé, elle peut représenter un risque d'exposition de secret.

\* \*\*Recommandation\*\* :



&#x20; \* Vérifier manuellement la chaîne détectée.

&#x20; \* Masquer toute valeur sensible dans le rapport.

&#x20; \* Éviter le hardcoding des secrets dans l'application.

\* \*\*Statut\*\* : À confirmer.



\### FIND-006 — Non-parameterized SQL Query



\* \*\*Source\*\* : BeVigil / Vulnerabilities

\* \*\*Sévérité\*\* : Low à Medium

\* \*\*Confiance\*\* : Moyenne

\* \*\*Description\*\* : BeVigil signale une possible requête SQL non paramétrée.

\* \*\*Impact potentiel\*\* : Si une entrée utilisateur est concaténée directement dans une requête SQL, cela peut créer un risque d'injection SQL.

\* \*\*Recommandation\*\* :



&#x20; \* Utiliser des requêtes paramétrées.

&#x20; \* Éviter la concaténation directe dans les requêtes SQL.

&#x20; \* Vérifier si le code détecté appartient à l'application ou à une bibliothèque tierce.

\* \*\*Statut\*\* : À confirmer.



\### FIND-007 — Possible Object Deserialization



\* \*\*Source\*\* : BeVigil / Vulnerabilities

\* \*\*Sévérité\*\* : Low à Medium

\* \*\*Confiance\*\* : Moyenne

\* \*\*Description\*\* : BeVigil signale une possible utilisation de mécanismes de désérialisation d'objets.

\* \*\*Impact potentiel\*\* : La désérialisation de données non fiables peut présenter un risque si les données traitées ne sont pas contrôlées.

\* \*\*Recommandation\*\* :



&#x20; \* Éviter la désérialisation de données provenant de sources non fiables.

&#x20; \* Valider strictement les données avant traitement.

&#x20; \* Utiliser des formats de données plus sûrs si possible.

\* \*\*Statut\*\* : À confirmer.



\### FIND-008 — Insecure Random Used



\* \*\*Source\*\* : BeVigil / Vulnerabilities

\* \*\*Sévérité\*\* : Low

\* \*\*Confiance\*\* : Moyenne

\* \*\*Description\*\* : BeVigil signale l'utilisation possible de `java.util.Random`.

\* \*\*Impact potentiel\*\* : Si cette classe est utilisée pour générer des valeurs sensibles, les valeurs produites peuvent être prévisibles.

\* \*\*Recommandation\*\* :



&#x20; \* Utiliser `SecureRandom` pour les usages de sécurité.

&#x20; \* Vérifier le contexte réel d'utilisation.

\* \*\*Statut\*\* : À confirmer.



\### FIND-009 — Stockage d'informations sensibles dans SharedPreferences



\* \*\*Source\*\* : BeVigil / Issues

\* \*\*Sévérité\*\* : Medium

\* \*\*Confiance\*\* : Moyenne

\* \*\*Description\*\* : BeVigil signale un stockage potentiel de données sensibles dans `SharedPreferences`.

\* \*\*Impact potentiel\*\* : Les données stockées localement peuvent être exposées si elles ne sont pas protégées.

\* \*\*Recommandation\*\* :



&#x20; \* Utiliser `EncryptedSharedPreferences`.

&#x20; \* Utiliser Android Keystore pour protéger les clés.

&#x20; \* Éviter de stocker des secrets côté client.

\* \*\*Statut\*\* : À confirmer.



\## 6. Permissions



Le résumé des permissions indique :



| Type de permission | Nombre |

| ------------------ | -----: |

| Safe               |      2 |

| Risky              |      3 |

| Dangerous          |      0 |



\### Interprétation



Aucune permission dangereuse n'a été détectée, mais trois permissions sont classées comme risquées. Ces permissions doivent être vérifiées afin de confirmer qu'elles sont nécessaires au fonctionnement de l'application.



\## 7. Assets et domaines détectés



BeVigil a détecté plusieurs assets réseau et domaines associés à l'application.



Exemples visibles dans le rapport :



\* `us.google.com`

\* `m.do.co`

\* `injuredandroid.firebaseio.com`



\### Interprétation



Ces domaines permettent de cartographier une partie des services utilisés par l'application. Ils ne constituent pas automatiquement des vulnérabilités, mais doivent être documentés dans le cadre de l'analyse de posture.



\## 8. Malware



\* \*\*Malwares détectés\*\* : 0



\### Interprétation



BeVigil ne signale aucun malware dans l'application analysée. Ce résultat est conservé comme information de contexte.



\## 9. Limitation du téléchargement du rapport



Le rapport BeVigil était visible dans l'interface web. Cependant, le bouton `DOWNLOAD REPORT` a redirigé vers une page CloudSEK proposant une démonstration de la plateforme au lieu de télécharger directement un fichier PDF.



Par conséquent, les résultats ont été conservés sous forme de captures d'écran et d'exports disponibles.



\## 10. Corrélation avec OWASP MASVS



| Constat                     | Catégorie OWASP |

| --------------------------- | --------------- |

| AWS API Key potentielle     | MASVS-STORAGE   |

| Generic API Key potentielle | MASVS-STORAGE   |

| Exported Activity           | MASVS-PLATFORM  |

| Possible Task Hijacking     | MASVS-PLATFORM  |

| Weak Crypto Algorithms      | MASVS-CRYPTO    |

| Non-parameterized SQL Query | MASVS-CODE      |

| Insecure Random Used        | MASVS-CRYPTO    |

| Assets réseau exposés       | MASVS-NETWORK   |

| SharedPreferences sensibles | MASVS-STORAGE   |



\## 11. Conclusion



L'analyse BeVigil de l'application InjuredAndroid a permis d'identifier plusieurs signaux de sécurité importants. Le score global obtenu est `6.9`, classé `Average`. Les principaux constats concernent une possible clé AWS API, des activités exportées, des algorithmes cryptographiques faibles, des permissions risquées, des assets réseau et des pratiques de stockage local à vérifier.



Ces résultats doivent être considérés comme des signaux d'exposition. Ils nécessitent une validation manuelle avec Yaazhini et une phase de triage avant d'être classés comme vulnérabilités confirmées.



