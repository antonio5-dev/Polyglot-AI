# Polyglot AI – Professor de Idiomas com IA e Voz (PWA)

App web instalável (PWA) de professor de idiomas: conversa com IA, cenários, mini-lições com exercícios, ouvir e repetir (ditado), flashcards com repetição espaçada, progresso e uma pequena memória do aluno. HTML/CSS/JS puros, sem build e sem backend.

- **Interface em 8 idiomas** (inglês é o padrão): English, Português (BR), Español, Français, Deutsch, 中文, 한국어, 日本語
- **IA:** Gemini direto do navegador, com **a sua chave de API** (grátis em <https://aistudio.google.com/apikey>)
- **Voz:** Web Speech API do Chrome

## Opção 1 – Usar a versão hospedada (recomendada)
Abra o **link da Vercel** do projeto no **Google Chrome** (PC ou Android). A voz (microfone) **só funciona em HTTPS ou `localhost`**, e o link da Vercel é HTTPS.

1. Em **Configurações**, cole a chave Gemini e escolha idioma da interface, idioma nativo e idioma(s) a praticar.
2. Em **Início**, comece uma conversa e permita o microfone.

**Instalar:** botão verde **Instalar app** (Início ou Configurações) ou menu **⋮ → Instalar app** do Chrome.

**Desinstalar:**
- **Chrome no PC:** abra o app, clique em **⋮** na barra de título → **Desinstalar** (ou `chrome://apps` → botão direito → **Remover**).
- **Android:** toque e segure o ícone → **Desinstalar** (ou Configurações → Apps → Polyglot AI).
- Os dados continuam no navegador até você limpar os dados do site. Exporte um backup antes, em Configurações.

## Opção 2 – Baixar/clonar o repositório e rodar localmente
```bash
git clone https://github.com/SEU-USUARIO/SEU-REPO.git
cd SEU-REPO
python3 -m http.server 8000
```
Abra <http://localhost:8000> no Chrome. **Não** abra o `index.html` com duplo clique (`file://`): reconhecimento de fala e service worker não funcionam.

## Publicar a sua cópia (GitHub → Vercel)
1. Coloque no repositório: `index.html`, `manifest.json`, `sw.js`, `vercel.json`, os 3 ícones e os READMEs.
2. Na Vercel: **Add New → Project → Import** do repositório, preset **Other**, sem build. **Deploy**.
3. A cada `git push` há novo deploy. Ao alterar arquivos, incremente `CACHE_VERSION` no `sw.js`.

## Recursos novos
- **Progresso totalmente separado por idioma:** nível, meta, meta diária, sequência, minutos, vocabulário, erros, histórico de lições e memória (máx. 20 itens por idioma).
- Botão **Apagar todos os dados** (Configurações, no fim) para recomeçar do zero, com opção de manter a chave de API.

## Observações
- O reconhecimento de fala mostra apenas o que o reconhecedor **entendeu**; **não** é nota de pronúncia.
- Sem voz instalada para um idioma no Android: Configurações → Sistema → Idiomas → Texto para fala.
- **Privacidade:** a chave fica só no localStorage do navegador e só é enviada ao Gemini; a exportação não a inclui. Os dados de estudo ficam no IndexedDB local.
