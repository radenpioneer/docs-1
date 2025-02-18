---
title: Faça deploy do seu site Astro
description: Como fazer deploy do seu site Astro para a web.
layout: ~/layouts/MainLayout.astro
setup: import DeployGuidesNav from '~/components/DeployGuidesNav.astro';
i18nReady: true
---
**Pronto para fazer a build e deploy do seu site Astro?** Siga um dos nossos guias para diferentes serviços de deploy ou role para abaixo para um guia geral sobre como fazer deploy de um site Astro.

<DeployGuidesNav />

## Opções de Deploy Rápido

Você pode fazer build e deploy de um site Astro para diversos hosts rapidamente utilizando ou a UI do painel dessa plataforma ou por uma interface de linha de comando.

### UI do Website

Uma forma rápida de fazer deploy do seu website é conectando o repositório Git online (e.x. GitHub, GitLab, Bitbucket) de seu projeto Astro a uma provedor de hospedagem e se aproveitando de continuous deployment utilizando o Git.

Estas plataformas de host automaticamente detectam pushes no repositório fonte do seu projeto Astro, fazem a build do seu site e então fazem o deploy dele para a web em uma URL customizada ou em seu domínio pessoal. Geralmente, para configurar o deployment nessas plataformas você vai acabar seguindo passos como os seguintes: 

1. Adicione seu repositório para um provedor Git online (e.x. GitHub, GitLab, Bitbucket)

1. Escolha uma host que suporta **continuous deployment** (e.x. [Netlify](/pt-br/guides/deploy/netlify/) ou [Vercel](/pt-br/guides/deploy/vercel/)) e importe seu repositório Git como um novo site/projeto.

    Vários hosts comuns vão reconhecer seu projeto como um site Astro e devem escolher as opções de configuração apropriadas para fazer a build e deploy do seu site como indicado abaixo. (Caso contrário, essas configurações podem ser mudadas.)

    :::note[Opções de Deploy]
    - **Build Command (Comando de Build):** `astro build` ou `npm run build`
    - **Publish directory (Diretório de Publicação):** `dist`
    :::

1. Clique em "Deploy" e seu novo website será criado em uma URL única daquele host (e.x. `novo-site-astro.netlify.app`).

O host será automaticamente configurado para verificar a branch `main` do seu provedor Git por mudanças para então refazer a build e publicação do seu site a cada novo commit. Essas configurações tipicamente podem ser configuradas na UI do painel do seu host.

### Deploy por Interface de Linha de Comando

Alguns hosts vão ter suas próprias interfaces de linha de comando (CLI) que você pode instalar globalmente em sua máquina utilizando npm. Geralmente, utilizar uma CLI para fazer deploy se parece com isso:

1. Instale a CLI do seu host globalmente, por exemplo:

    ```bash
    npm install --global netlify-cli
    ```

1. Execute a CLI e siga as instruções para autorização, configuração, etc.

1. Faça build e então deploy do seu site para seu host

    Vários hosts comuns irão fazer build e deploy do seu site por você. Eles irão geralmente reconhecer o seu projeto como um site Astro, e então escolher as opções de configuração apropriadas para fazer a build e deploy como indicado abaixo. (Caso contrário, essas configurações podem ser mudadas.)

    :::note[Opções de Deploy]
    - **Build Command (Comando de Build):** `astro build` ou `npm run build`
    - **Publish directory (Diretório de Publicação):** `dist`
    :::


    Outros hosts vão precisar que você [faça build do seu site localmente](#fazendo-build-do-seu-site-localmente) e então faça o deploy utilizando a linha de comando.

## Fazendo Build do Seu Site Localmente

Vários hosts como Netlify e Vercel irão fazer a build do seu site por você e então publicar o resultado da build para a web. Porém, alguns sites vão precisar que você faça a build localmente e então execute o comando de deploy ou faça upload do resultado da build.

Você também pode desejar fazer a build localmente para visualizar seu site, ou para encontrar possíveis erros e avisos no seu próprio ambiente.

Execute o comando `npm run build` para fazer build do seu site Astro.

```bash
npm run build
```

Por padrão, o resultado da build será colocado em `dist/`. Este local pode ser modificado utilizando a [opção `outDir` da configuração](/pt-br/reference/configuration-reference/#outdir). 

## Adicionando um Adaptador para SSR

:::note
Antes de fazer deploy do seu site Astro com [SSR (renderização no lado do servidor)](/pt-br/guides/server-side-rendering/) ativado, certifique-se de que você:

    - Instalou o [adaptador correto](/pt-br/guides/server-side-rendering/#habilitando-o-ssr-em-seu-projeto) nas dependências do seu projeto (seja manualmente ou utilizando o comando `astro add` do adaptador, e.x. `npx astro add netlify`).
    - [Adicionou o adaptador](/pt-br/reference/configuration-reference/#integrações) na importação e exportação padrão do seu arquivo `astro.config.mjs` ao instalar manualmente. (O comando `astro add` irá tomar conta dessa etapa por você!)
:::

