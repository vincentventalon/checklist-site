# Tout d'un coup : la checklist complète

Les cinq sections à la suite, en un seul prompt : vitesse, sécurité, SEO, légal, accessibilité.
C'est plus long (un peu plus de 4 minutes sur mon test) : si tu as installé la skill, dis simplement « fais la checklist de mon site ».

```
Fais la checklist complète de mon site https://ton-site.fr, en lecture seule, dans Chrome (Chrome DevTools MCP) et dans le code de ce dossier. Ne modifie rien : la seule chose que tu écris, c'est le fichier de résultats dans checklist/.
1. Vitesse : chronomètre l'ouverture à froid (TTFB, LCP, CLS), dis ce qui prend le plus de temps, liste ce que la page charge avant de s'afficher, refais la mesure sur une connexion lente simulée (Slow 4G, puis Slow 3G : dis que c'est une simulation), puis cherche ce qui se charge l'un après l'autre, en double, ou sans jamais servir (npx lighthouse : unused-javascript, unused-css-rules), le cache et le format des images.
2. Sécurité : clés exposées (NEXT_PUBLIC_, VITE_, clés en dur), RLS Supabase ou règles Firebase, vérification côté serveur à chaque requête, en-têtes (curl -sI), CORS, rate limit, npm audit (jamais --force).
3. SEO : robots.txt, sitemap, title, description, canonical et H1 de chaque page, texte présent dans le HTML du serveur, vrais liens <a href>, 404 qui répond 404, noindex, JSON-LD, robots d'IA.
4. Légal (pas un conseil juridique ; ouvre et cite les pages de cnil.fr et service-public.fr) : cookies et requêtes avant consentement, bouton « Tout refuser », mentions légales, politique de confidentialité, champs de formulaire inutiles.
5. Accessibilité (RGAA) : Lighthouse accessibilité, alt des images, contrastes 4,5:1, navigation au clavier (appuie vraiment sur Tab) et focus visible, lang de la page, labels des champs.
Pour chaque section : un tableau avec les chiffres et les preuves, puis les corrections de la plus rentable à la moins rentable.
Note tout dans checklist/checklist-AAAA-MM-JJ.md (date du jour) pour refaire la même analyse plus tard.
Attends mon accord avant de modifier quoi que ce soit.
```
