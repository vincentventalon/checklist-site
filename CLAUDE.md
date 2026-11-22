# checklist-site — la checklist Claude Code pour ton site

Ce repo contient des prompts et une skill qui analysent un site web : vitesse, sécurité, SEO,
légal, accessibilité. La personne qui t'a ouvert ici a vu une vidéo et veut savoir ce qui ne va
pas sur son site, pas un cours.

## Structure

```
prompts/                      # un prompt à coller par section, plus tout.md (tout d'un coup)
skills/checklist-site/        # la skill : SKILL.md + references/ (les mêmes prompts, en consignes)
captures/                     # les images du README
```

## Comment travailler

- **Lecture seule d'abord.** On mesure, on montre les chiffres, puis on attend l'accord avant de
  modifier quoi que ce soit sur le site de la personne.
- **Installer la skill** : `npx skills add vincentventalon/checklist-site` dans le dossier de son
  site (scope projet), ou copier `skills/checklist-site/` dans `~/.claude/skills/`.
- **Chrome DevTools MCP** est nécessaire pour la vitesse, le légal (cookies) et l'accessibilité :
  `claude mcp add chrome-devtools --scope user npx chrome-devtools-mcp@latest`, puis redémarrer
  Claude Code. Vérifier avec `/mcp`.
- Un prompt de `prompts/` et son double dans `skills/checklist-site/references/` disent la même
  chose : si tu en modifies un, modifie l'autre.

## Versions testées

Claude Code 2.1.330, chrome-devtools-mcp 1.13.0, skills (CLI) 1.9.0, le 22/11/2026. Si la
personne a plus récent et qu'une commande change, la doc officielle fait foi :
https://github.com/ChromeDevTools/chrome-devtools-mcp

## Ce que ce repo ne fait pas

- Mesurer depuis un autre pays : le profil réseau lent est une simulation.
- Remplacer les données réelles des visiteurs (Search Console, CrUX) : c'est une mesure de labo.
- Donner un conseil juridique : la section légal compare le site aux pages de la CNIL et de
  service-public.fr, c'est tout.
- Tester les attaques : la sécurité se lit dans le code et les en-têtes, rien n'est attaqué.
