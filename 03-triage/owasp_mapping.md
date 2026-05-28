\# Mapping OWASP MASVS



\## FIND-001 - AWS API Key potentielle



\* \*\*Catégorie OWASP\*\* : MASVS-STORAGE

\* \*\*Justification\*\* : Les clés API, tokens et secrets ne doivent pas être stockés en clair dans l'application cliente. Leur présence dans le code ou les chaînes de caractères peut exposer des services externes si la clé est valide.



\## FIND-002 - Exported Activity



\* \*\*Catégorie OWASP\*\* : MASVS-PLATFORM

\* \*\*Justification\*\* : Les composants Android exportés peuvent être accessibles par d'autres applications s'ils ne sont pas correctement protégés par des permissions ou par une configuration stricte du fichier `AndroidManifest.xml`.



\## FIND-003 - Weak Crypto Algorithms



\* \*\*Catégorie OWASP\*\* : MASVS-CRYPTO

\* \*\*Justification\*\* : L'utilisation d'algorithmes cryptographiques faibles peut compromettre la confidentialité et l'intégrité des données si ces algorithmes sont utilisés pour protéger des informations sensibles.



\## FIND-004 - Generic API Key potentielle



\* \*\*Catégorie OWASP\*\* : MASVS-STORAGE

\* \*\*Justification\*\* : Une chaîne ressemblant à une clé API doit être vérifiée, car les secrets ne doivent pas être hardcodés dans une application mobile.



\## FIND-005 - Permissions risquées



\* \*\*Catégorie OWASP\*\* : MASVS-PLATFORM

\* \*\*Justification\*\* : Les permissions Android doivent être limitées au strict nécessaire afin de réduire la surface d'exposition de l'application.



\## FIND-006 - Assets réseau exposés



\* \*\*Catégorie OWASP\*\* : MASVS-NETWORK

\* \*\*Justification\*\* : Les domaines, URLs et endpoints utilisés par l'application doivent être identifiés, documentés et sécurisés afin d'éviter l'exposition de services sensibles.



\## FIND-007 - Absence de malware détecté



\* \*\*Catégorie OWASP\*\* : Non applicable

\* \*\*Justification\*\* : Ce constat est une information de contexte. Il indique que BeVigil n'a pas signalé de malware, mais il ne correspond pas directement à une exigence MASVS.



\## FIND-008 - Insecure communication



\* \*\*Catégorie OWASP\*\* : MASVS-NETWORK

\* \*\*Justification\*\* : Les communications réseau doivent être protégées par des mécanismes sécurisés comme HTTPS/TLS afin d'éviter l'interception ou la modification des données en transit.



\## FIND-009 - Improper export of receiver



\* \*\*Catégorie OWASP\*\* : MASVS-PLATFORM

\* \*\*Justification\*\* : Un receiver exporté peut être invoqué par d'autres applications. Il doit être désactivé avec `android:exported="false"` ou protégé par une permission si son exposition est nécessaire.



\## FIND-010 - Insecure ECB mode



\* \*\*Catégorie OWASP\*\* : MASVS-CRYPTO

\* \*\*Justification\*\* : Le mode ECB est considéré comme faible car il peut révéler des motifs dans les données chiffrées. Il est recommandé d'utiliser des modes plus sûrs comme GCM ou CBC avec une gestion correcte de l'IV.



\## FIND-011 - Insecure algorithm DES



\* \*\*Catégorie OWASP\*\* : MASVS-CRYPTO

\* \*\*Justification\*\* : DES est un algorithme ancien et faible. Il doit être remplacé par un algorithme moderne comme AES avec une configuration sécurisée.



\## FIND-012 - Use of insufficiently random values



\* \*\*Catégorie OWASP\*\* : MASVS-CRYPTO

\* \*\*Justification\*\* : Les valeurs utilisées dans un contexte de sécurité doivent être générées avec un générateur cryptographiquement sûr comme `SecureRandom`.



\## FIND-013 - URLs liées détectées



\* \*\*Catégorie OWASP\*\* : MASVS-NETWORK

\* \*\*Justification\*\* : Les URLs et services externes utilisés par l'application doivent être documentés et vérifiés afin de s'assurer qu'ils appartiennent au périmètre autorisé et qu'ils utilisent des communications sécurisées.



\## FIND-014 - Stockage potentiel dans SharedPreferences



\* \*\*Catégorie OWASP\*\* : MASVS-STORAGE

\* \*\*Justification\*\* : Les données sensibles ne doivent pas être stockées en clair dans `SharedPreferences`. Il est recommandé d'utiliser `EncryptedSharedPreferences` ou Android Keystore lorsque des données sensibles doivent être conservées localement.



\## FIND-015 - Vulnérabilités liées au code



\* \*\*Catégorie OWASP\*\* : MASVS-CODE

\* \*\*Justification\*\* : Les vulnérabilités liées au code, comme les requêtes SQL non paramétrées ou la désérialisation d'objets, doivent être analysées et corrigées selon les bonnes pratiques de développement sécurisé.



