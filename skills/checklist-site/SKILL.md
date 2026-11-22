---
name: checklist-site
description: Analyse un site web en lecture seule, section par section (vitesse, sécurité, SEO, légal, accessibilité), et rend un rapport chiffré avant toute modification. Ouvre le site dans Chrome (Chrome DevTools MCP), chronomètre l'ouverture, liste ce qui charge, lit les en-têtes, le robots.txt, les cookies, les contrastes, puis note les chiffres dans checklist/ pour refaire la même analyse plus tard. Use when the user says "analyse mon site", "analyse ma page", "mon site est lent", "mon appli met du temps à s'ouvrir", "checklist de mon site", "audit de mon site", "audit sécurité de mon site", "audit SEO de mon site", "audit accessibilité de mon site", "mon site est-il conforme RGPD / cookies", "check my site", "why is my site slow".
---

# Checklist site

Tu analyses le site de la personne, section par section, et tu lui rends des chiffres. Tu ne
modifies rien (ni le code, ni le site, ni ses réglages) tant qu'elle n'a pas vu le rapport et dit
oui. Elle débute souvent : phrases courtes, chaque terme technique expliqué en quelques mots.

## 1. Ce qu'il te faut

- **L'adresse du site.** Si elle n'est pas dans la demande, demande-la (une question, rien d'autre).
- **Les sections.** Par défaut, celle que la demande vise (« mon site est lent » = vitesse). Si
  la demande est large (« analyse mon site », « la checklist »), fais les cinq, dans cet ordre :
  vitesse, sécurité, SEO, légal, accessibilité.
- **Chrome DevTools MCP** (outils `mcp__chrome-devtools__*`). S'il n'est pas branché, dis-le et
  donne la commande d'installation :
  `claude mcp add chrome-devtools --scope user npx chrome-devtools-mcp@latest`
  puis redémarrer Claude Code. En attendant, fais ce qui marche sans lui (`curl`,
  `npx lighthouse`) et écris dans le rapport ce qui n'a pas pu être mesuré.

## 2. Pour chaque section

Lis le fichier de la section dans `references/` et suis ses étapes dans l'ordre :

| Section | Fichier |
|---|---|
| Vitesse | `references/vitesse.md` |
| Sécurité | `references/securite.md` |
| SEO | `references/seo.md` |
| Légal | `references/legal.md` |
| Accessibilité | `references/accessibilite.md` |

Les outils qui servent (Chrome DevTools MCP) : `performance_start_trace` (avec rechargement et
cache ignoré) et `performance_analyze_insight` pour chronométrer ; `list_network_requests` pour ce
qui charge ; `emulate` pour le réseau lent ; `lighthouse_audit` pour l'accessibilité et le SEO ;
`press_key` (Tab) et `take_screenshot` pour le test au clavier ; `evaluate_script` pour lire les
cookies et le stockage. Le code inutilisé se mesure avec
`npx lighthouse <adresse> --only-audits=unused-javascript,unused-css-rules --output=json`.
Les pages sources du légal s'ouvrent (WebFetch) avant d'être citées.

Règles communes :

- **Mesure d'abord.** Chaque affirmation du rapport a sa preuve : un chiffre, une requête, un
  en-tête, un `fichier:ligne`. Ce que tu n'as pas pu mesurer est écrit « non mesuré », jamais deviné.
- **Lecture seule.** Pas de `npm audit fix`, pas de commit, pas de formulaire envoyé, pas de
  compte créé, pas de test d'attaque sur le site. La sécurité se lit dans le code et les en-têtes.
- **Une simulation se dit.** Un profil réseau lent (`emulate`) simule une connexion lointaine ; ce
  n'est pas une mesure depuis un autre pays. `emulate` remplace tout le réglage précédent :
  remets le réseau normal après.
- **Le légal n'est pas un conseil juridique.** Sources : cnil.fr et service-public.fr seulement,
  avec l'adresse de la page pour chaque point.

## 3. Le rapport

Une partie par section, dans cette forme :

```
## Vitesse — https://ton-site.fr — AAAA-MM-JJ
Les chiffres : <tableau : mesure, valeur, seuil « bon », verdict>
Ce qui coince : <3 à 5 lignes, chacune avec sa preuve>
À corriger, du plus rentable au moins rentable : <liste numérotée>
Non mesuré : <ce qui n'a pas pu tourner, et pourquoi>
```

Seuils « bon » à rappeler pour la vitesse (Core Web Vitals) : LCP ≤ 2,5 s, CLS ≤ 0,1,
INP ≤ 200 ms, TTFB ≤ 0,8 s. Une mesure de laboratoire n'est pas la donnée réelle des visiteurs.

Écris chaque section dans `checklist/<section>-AAAA-MM-JJ.md` à la racine du dossier ouvert (date
du jour), pour que la personne refasse la même analyse plus tard et compare. Si un fichier plus
ancien de la même section existe, compare les chiffres et dis ce qui a bougé.

## 4. Après le rapport

Termine par une question : « Je corrige lequel en premier ? ». Tu ne touches à rien avant la réponse.
Une correction faite, refais la mesure de la section et montre l'avant / après.
