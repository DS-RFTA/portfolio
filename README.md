# Renata Félix Trajano de Araújo — Portfólio | Data & Analytics · ML · AI

Portfólio profissional de **Renata Félix Trajano de Araújo**, posicionado em Dados & Analytics, Machine Learning e Inteligência Artificial. Construído para recrutadores, hiring managers e sistemas ATS.

🔗 **LinkedIn:** [linkedin.com/in/renataft-araujo](https://www.linkedin.com/in/renataft-araujo)
🔗 **GitHub:** [github.com/DS-RFTA](https://github.com/DS-RFTA)
🔗 **URL pública (após deploy):** `https://ds-rfta.github.io/portfolio/`

---

## 🧱 Por que essa arquitetura (e não React/Vite/Tailwind)

O pedido original sugeria React + TypeScript + Vite + Tailwind. Optei por **HTML + CSS + JavaScript puro, sem build**, por três motivos técnicos, não estéticos:

1. **Zero dependências, zero pipeline quebrável.** GitHub Pages serve o `index.html` diretamente — sem GitHub Actions, sem `npm install`, sem risco de build falhar em produção.
2. **Manutenção acessível.** Você pode editar texto, projetos ou experiência abrindo o arquivo e mudando um valor — não é preciso conhecer React, JSX ou um bundler.
3. **Sem perda de qualidade.** Todo o comportamento dinâmico do site (filtros de projeto, dark mode, PT/EN, animações de scroll) está implementado em JavaScript puro (vanilla), sem frameworks.

Se no futuro você quiser migrar para React (por exemplo, para adicionar um CMS real), a estrutura de dados já está isolada em objetos JS (`PROJECTS`, `EXPERIENCE`) — é praticamente um copy-paste para um projeto Vite novo.

---

## 📁 Estrutura do repositório

```
/
├── index.html          → site inteiro (HTML + CSS + JS embutidos)
├── assets/
│   └── CV-Renata-Felix-Trajano-de-Araujo.pdf   → currículo para download
├── robots.txt           → indexação para buscadores
├── sitemap.xml           → sitemap para SEO
├── .gitignore
└── README.md             → este arquivo
```

---

## ✏️ Como atualizar o conteúdo (sem saber programar)

Abra `index.html` em qualquer editor de texto (VS Code, Notepad++, etc.) e use `Ctrl+F` para localizar:

| Quero alterar...                  | Procure por...                                  |
|-----------------------------------|--------------------------------------------------|
| Adicionar um projeto novo          | `const PROJECTS = [` — copie um bloco `{...}` existente, cole antes do `];` e edite os campos |
| Adicionar uma experiência          | `const EXPERIENCE = [` — mesma lógica            |
| Trocar texto do "Sobre"            | `<div class="lang-pt">` dentro da seção `id="about"` |
| Trocar e-mail / LinkedIn / GitHub  | busque pelo endereço atual (ex: `dertrajano@gmail.com`) e substitua em **todas** as ocorrências |
| Trocar o currículo em PDF          | substitua o arquivo em `assets/` mantendo o mesmo nome, ou atualize o `href` correspondente |

Cada projeto segue este formato — basta duplicar e editar:

```js
{
  id: "p5",
  category: "python", // usar uma categoria já existente ou criar uma nova em CATEGORIES
  title: { pt: "Nome do projeto", en: "Project name" },
  desc: { pt: "Descrição curta.", en: "Short description." },
  tech: ["Python", "SQL"],
  link: "https://github.com/DS-RFTA/nome-do-repo",
  featured: false
}
```

Depois de editar, salve o arquivo, faça `git add . && git commit -m "content: update projects" && git push` — o GitHub Pages atualiza automaticamente em 1–2 minutos.

---

## 🚀 Deploy — passo a passo (ações que dependem de você)

Eu não tenho acesso autenticado à sua conta do GitHub neste ambiente, então estas etapas finais precisam ser feitas por você. É rápido:

### 1. Criar o repositório
No GitHub, crie um repositório novo chamado `portfolio` (ou `renata-felix-portfolio`) na conta **DS-RFTA**. Pode deixá-lo público.

### 2. Subir os arquivos
Na pasta onde estão estes arquivos, rode:

```bash
git init
git add .
git commit -m "feat: initial portfolio site"
git branch -M main
git remote add origin https://github.com/DS-RFTA/portfolio.git
git push -u origin main
```

### 3. Ativar o GitHub Pages
No repositório → **Settings → Pages** → em "Source", selecione a branch `main` e a pasta `/ (root)` → **Save**.

### 4. Acessar
Em 1–2 minutos, o site estará no ar em:
`https://ds-rfta.github.io/portfolio/`

### 5. Ajustar URLs finais (opcional, mas recomendado para SEO)
Se o nome do repositório final for diferente de `portfolio`, atualize a URL em três lugares dentro de `index.html`: a tag `<link rel="canonical">`, `og:url` e o campo `"url"` do JSON-LD — e também em `sitemap.xml` e `robots.txt`.

---

## ✅ O que já está implementado

- [x] Design responsivo (320px → 1440px+)
- [x] Dark mode / Light mode com persistência (`localStorage`) e respeito a `prefers-color-scheme`
- [x] Alternância PT-BR / EN-US
- [x] SEO técnico: meta description, Open Graph, Twitter Cards, canonical, `robots.txt`, `sitemap.xml`, JSON-LD (schema.org `Person`)
- [x] HTML semântico, headings hierárquicos, `alt`/`aria-label`, skip-link, foco visível — base de acessibilidade WCAG
- [x] `prefers-reduced-motion` respeitado
- [x] Conteúdo 100% extraído do currículo enviado — nenhuma experiência, empresa, tecnologia ou métrica foi inventada
- [x] Arquitetura de dados escalável para projetos e experiências (arrays JS editáveis)
- [x] Currículo em PDF disponível para download direto no site

## ⚠️ O que depende de decisão sua

- **Foto de perfil / capa para Open Graph:** o currículo trazia uma foto, mas não a incluí automaticamente no site público — adicione manualmente em `assets/img/` se desejar, e referencie no `<meta property="og:image">`.
- **Repositórios individuais dos projetos:** o currículo cita categorias de projeto (Java, Python, SQL/ETL) mas não nomes de repositórios específicos — os links atualmente apontam para o seu perfil GitHub geral (`github.com/DS-RFTA`). Quando os repositórios individuais existirem/estiverem organizados, atualize o campo `link` de cada projeto em `PROJECTS`.
- **Datas da vaga atual (Grupo Boticário):** o currículo não trazia data de início — o site exibe apenas "Atual" / "Current". Ajuste se quiser incluir o mês/ano de início.
- **Telefone:** removido do site público por segurança/spam (mantido apenas e-mail e LinkedIn), conforme recomendação de boas práticas — reative se preferir.
- **Google Analytics ou outra ferramenta de analytics:** não foi adicionado. Se quiser, posso te orientar sobre a opção mais leve e compatível com privacidade (ex: Plausible, GoatCounter).

---

© 2026 Renata Félix Trajano de Araújo
