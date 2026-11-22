# Sécurité : les consignes

Copie du prompt `prompts/securite.md`. L'adresse du site remplace `https://ton-site.fr`.
Suis les étapes dans l'ordre, puis rends la section dans la forme de `SKILL.md` § 3.

Fais l'audit sécurité de mon site, en lecture seule : le code de ce dossier et le site en ligne https://ton-site.fr. Ne modifie rien.
1. Clés exposées : tout ce qui commence par NEXT_PUBLIC_ ou VITE_ part dans le navigateur. Liste chaque variable et dis si c'est un secret. Cherche aussi des clés écrites en dur dans le code et dans l'historique git.
2. Supabase : la RLS est-elle activée sur chaque table ? La clé secrète (service_role) reste-t-elle côté serveur ? Firebase : montre mes règles, et dis s'il reste un "if true" ou un "auth != null" tout seul.
3. Pour chaque action qui lit ou écrit des données privées : le serveur vérifie-t-il qui demande, à chaque requête ? En lisant le code, dis ce qui se passe si quelqu'un change l'id dans l'adresse.
4. Lis les en-têtes du site (curl -sI) : Strict-Transport-Security, X-Content-Type-Options, Content-Security-Policy, Referrer-Policy. Dis ce qui manque.
5. CORS : mon API répond-elle Access-Control-Allow-Origin: * alors qu'elle utilise des cookies ?
6. Les routes sensibles (connexion, inscription, formulaires, appel d'IA payant) ont-elles une limite de requêtes (rate limit) ?
7. Lance npm audit. Ne lance jamais npm audit fix --force : dis-moi ce que chaque mise à jour risque de casser.
8. Rends un tableau : problème, gravité, preuve (fichier:ligne ou en-tête), correction proposée. Note-le dans checklist/securite-AAAA-MM-JJ.md (date du jour) pour refaire la même analyse plus tard.
Attends mon accord avant de corriger quoi que ce soit.
