# SEO : est-ce que Google (et ChatGPT) peuvent lire ton site

Claude passe tes pages une par une, comme le ferait Google, et te dit ce qui les empêche d'être trouvées.
Pour les vrais chiffres (clics, positions), il te faut ensuite la Google Search Console : ce prompt-là regarde le site, pas le trafic.

```
Fais l'audit SEO de mon site https://ton-site.fr, en lecture seule. Ne modifie rien.
1. Lis robots.txt et sitemap.xml. Liste les pages du sitemap et vérifie que chacune répond 200.
2. Pour chaque page du sitemap, pas un échantillon : le title, la meta description, la balise canonical (adresse complète ?), le H1. Signale les titles et descriptions en double, et les pages qui n'en ont pas.
3. Vérifie que le texte de la page est dans le HTML envoyé par le serveur, pas seulement ajouté par JavaScript (compare curl et la page ouverte dans Chrome).
4. Vérifie que les liens entre pages sont de vrais <a href>, et qu'une adresse qui n'existe pas répond 404 (pas une page vide en 200).
5. Cherche une page en noindex par erreur, ou une page qu'on croit cacher avec robots.txt : robots.txt ne sort pas une page de Google, il faut noindex.
6. Liste les données structurées (JSON-LD) de chaque page, et dis lesquelles passer dans le test des résultats enrichis de Google.
7. IA : dis ce que robots.txt autorise pour OAI-SearchBot, GPTBot, ClaudeBot, Claude-SearchBot et Google-Extended, et ce que ça change pour moi.
8. Rends un tableau page par page. Note-le dans checklist/seo-AAAA-MM-JJ.md (date du jour) pour refaire la même analyse plus tard.
Attends mon accord avant de corriger quoi que ce soit.
```
