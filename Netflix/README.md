# My Little Netflix

Aplicación web cliente que funciona como una base de datos de películas, hecha con HTML, CSS y JavaScript siguiendo el patrón **MVC**. Los datos se guardan en el `localStorage` del navegador y se pueden buscar películas en la API de **The Movie Database (TMDb)**.

Práctica de la asignatura **Tecnologías Web**.

## Funcionalidades

**Parte 1: gestión local**
- **View:** muestra título, director y portada.
- **Add / Create:** formulario para crear una película (el título es obligatorio).
- **Edit / Update:** modifica los datos de una película.
- **Delete:** elimina una película, pidiendo confirmación.
- **Reset:** restaura las películas iniciales.

**Parte 2: integración con TMDb**
- **Search TMDb:** busca películas por título (botón o tecla Enter), con validación de la búsqueda y mensajes para: búsqueda vacía, caracteres no válidos, sin conexión, clave inválida, error de la API y sin resultados.
- **Resultados:** cuadrícula con póster, título, fecha de estreno, valoración y sinopsis.
- **Add (desde la API):** añade la película a la base de datos local con la misma estructura (`title`, `director`, `thumbnail`). El director se obtiene de los créditos de TMDb. Evita duplicados y deshabilita el botón mientras se añade.

## Cómo ejecutarlo

1. Descarga o clona el repositorio.
2. Abre `index.html` en Chrome o Firefox.
3. Para usar la búsqueda necesitas una clave de TMDb (ver abajo).

## Clave de la API de TMDb

1. Crea una cuenta en <https://www.themoviedb.org> y solicita una clave de API (gratuita).
2. Copia el **API Read Access Token** (el token largo que empieza por `eyJ`).
3. Usa **una** de estas dos opciones:
   - **Desde la aplicación:** pulsa *Search TMDb* y pega el token en el recuadro amarillo. Se guarda solo en tu navegador (`localStorage`), nunca en el código.
   - **Con un archivo local:** copia `config.example.js` como `config.js` y escribe tu token. `config.js` está en `.gitignore`, por lo que no se sube a GitHub.

> No escribas el token dentro de `index.html` ni lo subas al repositorio.

## Publicar en GitHub Pages

1. Sube el proyecto a un repositorio público (`config.js` no se sube).
2. En GitHub: *Settings → Pages → Branch: main / root → Save*.
3. Abre la URL `https://TU_USUARIO.github.io/NOMBRE_REPO/` y pega tu token en *Search TMDb*.

## Estructura

```
Netflix/
├── index.html          # HTML, CSS y JavaScript (MVC)
├── config.example.js   # Plantilla de configuración de la clave
├── config.js           # Tu clave local (ignorado por git)
├── files/              # Portadas de las películas
└── tests/              # Tests de la práctica
```

## Arquitectura MVC

| Parte         | Elementos |
|---------------|-----------|
| Modelo        | Array en `localStorage` (`my_movies`) + resultados de TMDb |
| Vistas        | `indexView`, `showView`, `newView`, `editView`, `searchView`, `resultsView` |
| Controladores | `indexContr`, `showContr`, `newContr`, `createContr`, `editContr`, `updateContr`, `deleteContr`, `resetContr`, `searchContr`, `addFromAPIContr` |
| Router        | Listener de `click` (clases `index`, `show`, `new`, `create`, `edit`, `update`, `delete`, `reset`, `search`, `add-from-api`) y de `Enter` en el campo de búsqueda |

## Tecnologías

HTML5 · CSS3 · JavaScript (fetch, async/await) · localStorage · API REST de TMDb
