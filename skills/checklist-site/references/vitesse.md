# Vitesse : les consignes

Copie du prompt `prompts/vitesse.md`. L'adresse du site remplace `https://ton-site.fr`.
Suis les étapes dans l'ordre, puis rends la section dans la forme de `SKILL.md` § 3.

Ouvre mon site https://ton-site.fr dans Chrome (Chrome DevTools MCP). Ne modifie rien : la seule chose que tu écris, c'est le fichier de résultats dans checklist/.
1. Chronomètre l'ouverture de la page à froid (cache vidé) : temps jusqu'au premier octet (TTFB), affichage du plus gros élément (LCP), décalage de la mise en page (CLS).
2. Dis-moi ce qui prend le plus de temps.
3. Fais la liste de tout ce que la page charge avant de s'afficher : chaque fichier, son poids, son temps. Tu ne touches à rien sans m'avoir montré ces chiffres.
4. Refais la même mesure comme si j'étais en Amérique, puis au Vietnam : simule une connexion lointaine et lente (profil réseau Slow 4G, puis Slow 3G), puis remets le réseau normal. Dis-moi clairement que c'est une simulation, pas une vraie mesure depuis ces pays.
5. Dis-moi ce qui se charge l'un après l'autre et pourrait se charger en même temps, et ce qui est demandé deux fois.
6. Regarde si on peut charger seulement le premier écran au début, et le reste au clic ou quand on descend. Attention : jamais de chargement différé (lazy) sur la grande image du haut.
7. Liste ce qui est chargé et ne sert jamais : le code JavaScript et CSS inutilisé, en ko par fichier (npx lighthouse avec les audits unused-javascript et unused-css-rules).
8. Vérifie le cache du navigateur (en-têtes Cache-Control de chaque fichier) et le format des images : WebP ou AVIF, avec une largeur et une hauteur ?
9. Note les chiffres d'aujourd'hui dans checklist/vitesse-AAAA-MM-JJ.md (date du jour) : c'est ma référence pour refaire la même analyse plus tard.
Ensuite, propose les corrections de la plus rentable à la moins rentable, et attends mon accord avant de modifier quoi que ce soit.
