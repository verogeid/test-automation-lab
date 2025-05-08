![Status][En-Construccion]
---

<h1 align="center">⚙️ Test Automation Lab ⚙️</h1>

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
![JMeter-logo]
![JWT-logo]
![JWE-logo]
![WCAG-logo]
![axe-core-logo]
![lighthouse-logo]
---

<a id="indice"></a>
[![LinkedIn][linkedin-logo]][linkedin-link] (C) Diego González Fernández. 

## 🧭 Índice

- [📘 Descripción del Proyecto](#descripcion-del-proyecto)
- [🔐 Flujo Completo de la Lógica de Seguridad y Comunicación entre Contenedores](#flujo-logica-contenedores)
- [📈 Modularidad y Escalabilidad en Pruebas No Funcionales](#modularidad-escalabilidad)
- [🛠️ Descripción del endpoint](#descripcion-endpoint)
- [🌐 Accesibilidad Beyond-WCAG](#accesibilidad-beyond-wcag)
- [🔍 Otras Pruebas No Funcionales](#otras-pruebas-no-funcionales)
- [⏳ Estado actual](#estado-actual)
---

<a id="descripcion-del-proyecto"></a>
## 📘 Descripción del Proyecto

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

[Volver al inicio](#indice)

---

<a id="flujo-logica-contenedores"></a>
## 🔐 Flujo Completo de la Lógica de Seguridad y Comunicación entre Contenedores

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

[Volver al inicio](#indice)

---

<a id="modularidad-escalabilidad"></a>
## 📈 Modularidad y Escalabilidad en Pruebas No Funcionales

La combinación de *Playwright* con la lógica *Python* modular permite que el sistema funcione prácticamente con cualquier endpoint, alternando entre idiomas y modos de visión si están disponibles.  
La configuración, definida en un archivo JSON, indica qué datos relevantes buscar y puede ampliarse fácilmente para cubrir otros endpoints, aumentando así su escalabilidad.  
Además, se puede ajustar el grado de tolerancia a fallos no funcionales de accesibilidad, es decir, qué porcentaje de degradación de la experiencia de usuario se considera aceptable.  
No es lo mismo una persona con cataratas incipientes que alguien casi ciego por la misma dolencia.

Este enfoque permite simular la interacción de un usuario real con la aplicación, centrándose en la percepción condicionada por su deficiencia visual o cognitiva.  
Aunque no sustituye la experiencia real de usuario, establece una base científica que va más allá del cumplimiento de las *WCAG*, facilitando que la tecnología sea más inclusiva.  
Es clave recordar que, si bien existen más de 300 millones de personas con daltonismo, el número de personas con presbicia —la mayoría de mayores de 40-45 años— es aún mayor, especialmente considerando la pirámide poblacional invertida.

Finalmente, esta manera de trabajar permitirá que automáticamente puedan visitarse todos los endpoints de un dominio realizando pruebas para cada uno y generando informes tanto por sección como globales, lo que servirá como base para la primera versión de mi algoritmo de accesibilidad personalizado.

[Volver al inicio](#indice)

---

<a id="descripcion-endpoint"></a>
## 🛠️ Descripción del endpoint

El endpoint está diseñado para ser **responsive** y ha sido implementado utilizando **React**, **Vite** y **TypeScript**. En cuanto a las funcionalidades, se cuenta con un **toggle** para alternar entre los diferentes modos de visión: **claro**, **oscuro** y **nocturno/monocromo**. Además, se incorpora un selector de idiomas para mejorar la experiencia de usuarios en diferentes regiones.

Este endpoint está dividido en varios componentes, entre los que destacan:

- **Header**: En donde se encuentran los **toggle** y **selectores** para cambiar entre modos de visión e idiomas.
- **Footer**: Un pie de página básico que permanece constante en toda la navegación.
- **Calendario**: Para gestionar el control de horas trabajadas, el cual interactúa con los datos almacenados.
- **Formulario de búsqueda**: Para filtrar datos de manera eficiente desde la base de datos.

En cuanto al manejo de usuarios, si el usuario no está **logueado**, sus datos se almacenarán únicamente durante la sesión activa. Si está **logueado**, podrá elegir entre varios métodos de autenticación (cuenta de Google, GitHub o MSN). Además, se está investigando la posibilidad de incorporar **certificados digitales** o **DNI electrónico** para mayor seguridad y confiabilidad en el proceso.

Este endpoint está destinado a ser un **endpoint de pruebas** sobre el que se realizarán pruebas **funcionales** y **no funcionales**. El objetivo principal es demostrar la validez de las pruebas, especialmente las pruebas **no funcionales**.

[Volver al inicio](#indice)

---

<a id="accesibilidad-beyond-wcag"></a>
## 🌐 Accesibilidad Beyond-WCAG

Este proyecto realiza pruebas avanzadas de accesibilidad, yendo más allá de *WCAG*: **analiza cómo percibe el usuario real el endpoint** bajo distintas condiciones visuales y cognitivas.

### ¿Qué simulamos?
- *Presbicia*
- *Daltonismo*
- *Cataratas*
- *Glaucoma*
- *Dislexia*
- *TDAH*

### ¿Cómo funciona?
El sistema evalúa el comportamiento del endpoint en los siguientes modos de visualización:
- Modo **claro**
- Modo **oscuro**
- Modo **monocromo** (alto contraste en móviles)

Cada uno de estos escenarios se analiza de forma independiente para identificar problemas de percepción y comprensión, simulando cómo se vería el endpoint para personas con deficiencias visuales o cognitivas. Si el endpoint no cuenta con los *CSS* necesarios para adaptarse a estos modos, la prueba **fallará** directamente al no haber contemplado este problema de accesibilidad.

Si el endpoint incluye los datos necesarios, se procede a realizar un análisis según tres grados de severidad:
- **Leveo**
- **Medio**
- **Severo**

Cada grado refleja una condición progresiva de deficiencia visual o cognitiva. Los resultados se calculan en un **contenedor Docker especializado** ejecutando lógica en *Python*, donde se evalúa cómo el usuario percibe la información.

### Evaluación de resultados
Dependiendo de los valores de aceptación configurados para la prueba, el resultado se validará en base al **grado de degradación** que experimenta el usuario al percibir la información. Si el grado de degradación supera el umbral de aceptación, la prueba **fallará**.

### Importante
⚠️ **Advertencia crítica:**  
Si el endpoint carece de soporte para los modos claro/oscuro/monocromo, se generará una alarma destacada que indica que los resultados pueden no ser confiables debido a limitaciones en el diseño original.

### Valor diferencial
Este enfoque permite detectar problemas reales que impactan a usuarios con necesidades específicas, incluso en proyectos que ya cumplen *WCAG*, ofreciendo una evaluación más precisa de la accesibilidad y una experiencia inclusiva para todos los usuarios.

[Volver al inicio](#inicio)

---

<a id="otras-pruebas-no-funcionales"></a>
## 🔍 Otras Pruebas No Funcionales

### 1. Textos Traducidos
En esta prueba, se verifica que todos los textos de la interfaz de usuario estén correctamente traducidos. No se comprueba la exactitud de la traducción, sino que se asegura que no haya párrafos no traducidos, a excepción de las citas. **Playwright cambiará automáticamente de idioma y realizará estas pruebas con todos los idiomas disponibles.**

### 2. Navegabilidad Mediante Teclado
Se prueba que todos los elementos interactivos de la interfaz sean accesibles y navegables utilizando solo el teclado, sin depender de un ratón u otros dispositivos de entrada.

### 3. Textos o Elementos Cortados o No Visibles por Solapamiento
Esta prueba se enfoca en verificar que no haya textos o elementos visuales que estén cortados o que no sean visibles debido a solapamientos en la interfaz de usuario.

### 4. Velocidad de Carga
Se verifica que el tiempo de carga de la página sea adecuado, asegurando que la aplicación o sitio web no experimente retrasos significativos que puedan afectar la experiencia del usuario.

### 5. Pruebas WCAG Estándar
Se llevan a cabo pruebas de conformidad con las **Web Content Accessibility Guidelines (WCAG)** para asegurar que el sitio o aplicación cumpla con los estándares de accesibilidad web, ofreciendo una experiencia adecuada para usuarios con discapacidades. **Estas pruebas no dependen del idioma, ya que las WCAG son estándares universales.**

[Volver al inicio](#inicio)

--

<a id="estado-actual"></a>
## ⏳ Estado actual

![Status][En-Construccion]

Este repositorio forma parte de mi portfolio técnico y está en fase de construcción. Ciertas partes, como la lógica visual en Python, están protegidas para evitar usos indebidos.

[Volver al inicio](#indice)

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
[JMeter-logo]: https://img.shields.io/badge/JMeter-D24939?style=for-the-badge&logo=apache-jmeter&logoColor=white
[axe-core-logo]: https://img.shields.io/badge/axe--core-darkgreen?style=for-the-badge&logo=axe&logoColor=white
[lighthouse-logo]: https://img.shields.io/badge/Lighthouse-orange?style=for-the-badge&logo=lighthouse&logoColor=white

<!-- Package Managers -->
[node-logo]: https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white

<!-- Others -->
[JWT-logo]: https://img.shields.io/badge/JWT-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white
[JWE-logo]: https://img.shields.io/badge/JWE-blue?style=for-the-badge

[WCAG-logo]: https://img.shields.io/badge/WCAG-005a9c?style=for-the-badge&logo=w3c&logoColor=white
[linkedin-logo]: https://img.shields.io/badge/LinkedIn-blue?style=for-the-badge&logo=linkedin&logoColor=white
[linkedin-link]: https://www.linkedin.com/in/diego-gonzalez-fernandez/