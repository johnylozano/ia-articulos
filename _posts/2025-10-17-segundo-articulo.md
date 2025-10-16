---
layout: post
title: "xxxxx"
date: 2025-10-17
categories: inteligencia-artificial
---


Perfecto! 😄 Vamos a crear un repositorio mínimo de ejemplo que funcione 100% con GitHub Pages y Jekyll, donde todos tus posts se publiquen correctamente y la página de archivo funcione sin 404.

1️⃣ Estructura del repositorio
ia-articulos/
├─ _posts/
│  ├─ 2025-10-16-primer-articulo-ia.md
│  ├─ 2025-10-17-segundo-articulo-ia.md
│  └─ 2025-10-18-tercer-articulo-ia.md
├─ _config.yml
├─ archivo.md
└─ .github/
   └─ workflows/jekyll-gh-pages.yml


Todos los archivos deben estar en la raíz, excepto el workflow que va dentro de .github/workflows/.

2️⃣ Contenido de _config.yml
title: "Blog de Investigación Tecnológica"
description: "Artículos sobre Inteligencia Artificial y Tecnología"
baseurl: ""
url: "https://johnylozano.github.io/ia-articulos"
theme: minima

3️⃣ Ejemplo de posts en _posts/
2025-10-16-primer-articulo-ia.md
---
layout: post
title: "Primer Artículo de IA"
date: 2025-10-16
categories: inteligencia-artificial
---

¡Bienvenido a mi blog tecnológico! Este es mi primer artículo sobre Inteligencia Artificial.

2025-10-17-segundo-articulo-ia.md
---
layout: post
title: "Segundo Artículo de IA"
date: 2025-10-17
categories: inteligencia-artificial
---

Aquí comparto más investigaciones y lecturas sobre inteligencia artificial.

2025-10-18-tercer-articulo-ia.md
---
layout: post
title: "Tercer Artículo de IA"
date: 2025-10-18
categories: inteligencia-artificial
---

Continuamos con el análisis de nuevos artículos y tendencias en tecnología.

4️⃣ Archivo archivo.md para listar posts
---
layout: default
title: "Archivo de Artículos"
permalink: /archivo/
---

# Archivo de Artículos

Aquí encontrarás todos los artículos publicados en este blog:

<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ post.url }}">{{ post.title }}</a> - {{ post.date | date: "%d %B %Y" }}
  </li>
{% endfor %}
</ul>

5️⃣ Workflow .github/workflows/jekyll-gh-pages.yml
name: Deploy Jekyll with GitHub Pages dependencies preinstalled

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Pages
        uses: actions/configure-pages@v5
      - name: Build with Jekyll
        uses: actions/jekyll-build-pages@v1
        with:
          source: ./
          destination: ./_site
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4

6️⃣ Pasos finales para publicar

Haz commit de todos los archivos en la rama main.

GitHub Actions ejecutará automáticamente el workflow.

Espera unos minutos y abre:

https://johnylozano.github.io/ia-articulos/


Todos los posts aparecerán.

La página de archivo estará en:

https://johnylozano.github.io/ia-articulos/archivo/
