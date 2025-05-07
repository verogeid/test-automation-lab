![Status][En-Construccion]
---

<h1 align="center">Test Automation Lab</h1>

![vscode-logo]
![node-logo]
![react-logo]
![github-actions]
![docker-logo]
![jira-logo]
![testrail-logo]
![micro-focus-ALM-logo]
![cypress-logo]
![playwright-logo]
![typescript-logo]
![python-logo]
![JWT-logo]
![WCAG-logo]
![axe-core-logo]
![K6-logo]
![lighthouse-logo]
---

## Descripción del Proyecto

Este portfolio está en construcción activa y representa un entorno realista de trabajo como **QA Automation Engineer**. Incluye:

- Un *endpoint funcional* desarrollado con **React + Vite**, desplegado automáticamente a entornos QA y Producción mediante workflow.
- Ejecución de pruebas Funcionales en **Cypress** (entorno QA) y No Funcionales en **Playwright** (entorno Producción), ambas usando **TypeScript**.
- *Módulo de selectores* en TypeScript compartido entre Cypress y Playwright para optimizar el mantenimiento de tests automatizados.
- Lógica avanzada desarrollada en **Python**, encapsulada en un contenedor **Docker** protegido por *JWT rotativos* y validación de IP.
- Pruebas de carga y estrés con **JMeter**.
- Validaciones de accesibilidad con **axe-core** y simulaciones avanzadas en **Python** para:
  - *Protanopía* (ceguera al rojo)
  - *Deuteranopía* (ceguera al verde)
  - *Tritanopía* (ceguera al azul)
  - *Presbicia*
  - *Glaucoma*
  - *Cataratas*
  - *Dislexia*
  - *TDAH activo y pasivo*
  - *Asperger*

Todos los resultados se integran automáticamente en herramientas de gestión como **Jira**, **TestRail** o **Micro Focus ALM** (simulada), adaptándose según entorno mediante una variable `env`.

---

## Flujo Completo de la Lógica de Seguridad y Comunicación entre Contenedores

1. **Generación del Token e IV en Playwright:**
   - **Playwright** facilita un **token** y un **IV** único a **Docker Auth**. El **token** identifica al usuario y el **IV** se utiliza para la seguridad de la sesión.

2. **Validación del Rango de IPs en Docker Auth:**
   - **Docker Auth** recibe el **token** y el **IV** proporcionados por **Playwright**.
   - Consulta una base de datos encriptada con el **token** para obtener:
     - La **palabra clave** asociada al token.
     - El **rango de IPs** permitido.
   - Valida si la solicitud proviene de una IP dentro del rango permitido; si no, rechaza la solicitud.

3. **Generación del JWE Rotativo:**
   - Si la IP es válida, usa la **palabra clave** y el **IV** para generar un **JWE rotativo**, garantizando la seguridad en las futuras comunicaciones.

4. **Consulta API desde Playwright a Lógica Python:**
   - Con el **JWE rotativo**, Playwright consulta al contenedor Docker que ejecuta la lógica Python para analizar deficiencias visuales y cognitivas.

5. **Comunicaciones Seguras entre Contenedores:**
   - El contenedor Python usa una **palabra clave compartida** para comunicarse de forma segura con Docker Auth, obtener datos y desencriptar la información de Playwright.

6. **Desencriptación y Análisis de Resultados:**
   - El contenedor Python desencripta los datos usando la **palabra clave** e **IV**, analiza los resultados y los devuelve a Playwright en JSON cifrado.

7. **Desencriptación por Playwright:**
   - Playwright desencripta el JSON usando su **palabra clave** e **IV**, quedando listo para usar los resultados en sus pruebas.

---

[![LinkedIn][linkedin-logo]][linkedin-link] (C) Diego González Fernández. 

## Estado actual

Este repositorio forma parte de mi portfolio técnico y está en fase de construcción. Ciertas partes, como la lógica visual en Python, están protegidas para evitar usos indebidos.

<!-- Workspace -->
[En-Construccion]: https://img.shields.io/badge/status-en%20construcci%C3%B3n-orange
[vscode-logo]: https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white
[react-logo]: https://img.shields.io/badge/React-61DAFB?style=for-the-badge&logo=react&logoColor=black

<!-- QA tools -->
[jira-logo]: https://img.shields.io/badge/jira-%230A0FFF.svg?style=for-the-badge&logo=jira&logoColor=white
[testrail-logo]: https://img.shields.io/badge/TestRail-2496ED?style=for-the-badge&logo=testinglibrary&logoColor=white
[micro-focus-ALM-logo]: https://img.shields.io/badge/Micro%20Focus%20ALM-0277BD?style=for-the-badge&logoColor=white

<!-- CI Tool -->
[github-actions]: https://img.shields.io/badge/github%20actions-%232671E5.svg?style=for-the-badge&logo=githubactions&logoColor=white
[docker-logo]: https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white

<!-- Programming Languages -->
[typescript-logo]: https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white
[python-logo]: https://img.shields.io/badge/Python-black?logo=python&style=for-the-badge

<!-- Testing Frameworks -->
[cypress-logo]: https://img.shields.io/badge/-cypress-%23E5E5E5?style=for-the-badge&logo=cypress&logoColor=058a5e
[playwright-logo]: https://img.shields.io/badge/playwright-black?style=for-the-badge

<!-- Performance -->
[K6-logo]: https://img.shields.io/badge/k6-7D64FF?style=for-the-badge&logo=k6&logoColor=white
[axe-core-logo]: https://img.shields.io/badge/axe--core-darkgreen?style=for-the-badge&logo=axe&logoColor=white
[lighthouse-logo]: https://img.shields.io/badge/Lighthouse-orange?style=for-the-badge&logo=lighthouse&logoColor=white

<!-- Package Managers -->
[node-logo]: https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white

<!-- Others -->
[JWT-logo]: https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white
[WCAG-logo]: https://img.shields.io/badge/WCAG-005a9c?style=for-the-badge&logo=w3c&logoColor=white
[linkedin-logo]: https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white
[linkedin-link]: https://www.linkedin.com/in/diego-gonzalez-fernandez/

<!-- more badges here https://github.com/Ileriayo/markdown-badges -->
