---
marp: true
class:
  + invert
size: 16:9
paginate: true
---

# Next.js

### Dan Ellis Echavarria 2023

### Mateo Trujillo Giraldo 2023
![bg right vertical](https://www.nextjs.cn/static/images/nextjs-big-logo.png)

--- 

## Introducción

* ¿Qué es Next.js?

  Next.js es un framework de React para crear aplicaciones web de una sola página (SPA) o sitios web estáticos.

* ¿Por qué es importante conocer Next.js?

  Next.js permite crear aplicaciones web con mejor rendimiento y SEO gracias a su enfoque en el servidor, su pre-renderizado y la optimización de recursos.

* ¿Qué problemas resuelve?

  Next.js resuelve problemas como el tiempo de carga lento en SPA, la falta de soporte SEO y la complejidad de implementar server-side rendering. Además, proporciona una experiencia de desarrollo más eficiente y simplificada. 

---

## Configuración de Next.js

* Instalación de Next.js

  Para instalar Next.js, se puede utilizar el siguiente comando de npm:

```sh
npx create-next-app nombre-del-proyecto
```

---

* Configuración del proyecto

Next.js proporciona una serie de configuraciones por defecto para un nuevo proyecto, pero estas pueden ser modificadas según las necesidades del proyecto. Algunas de estas configuraciones incluyen:

* Configuración de la ruta de entrada y salida de los archivos.
* Configuración de variables de entorno.
* Configuración de las opciones de babel.
---
* Estructura del proyecto

La estructura de un proyecto de Next.js se compone de las siguientes carpetas principales:

* **pages**: Aquí se encuentran los archivos que definirán las diferentes rutas de la aplicación.
* **public**: Esta carpeta contiene los archivos públicos, como imágenes, fuentes y otros recursos estáticos.
* **components**: En esta carpeta se encuentran los componentes reutilizables de la aplicación.
* **styles**: Aquí se pueden definir los estilos globales de la aplicación.
* **utils**: Esta carpeta contiene funciones y utilidades reutilizables en la aplicación.

---

## Renderizado y Routing en Next.js

* Server-side rendering

  Next.js proporciona el server-side rendering (SSR) por defecto, lo que significa que las páginas se generan en el servidor antes de ser enviadas al cliente. Esto mejora la velocidad de carga y la experiencia de usuario en comparación con la renderización del lado del cliente (CSR).

* Client-side rendering

  Además del SSR, Next.js también admite el client-side rendering (CSR), que se utiliza cuando se necesita una mayor interactividad en la aplicación. Next.js utiliza la librería de React para manejar el CSR.
---
* Static site generation

  Next.js también admite el static site generation (SSG), que permite generar páginas HTML estáticas en tiempo de compilación. Esto es útil para sitios web que no requieren interactividad o actualizaciones en tiempo real, y mejora el rendimiento y la escalabilidad del sitio.

* Routing en Next.js

  Next.js utiliza un enrutador incorporado que se basa en el sistema de archivos del proyecto para manejar las rutas. Para crear una nueva página, se debe crear un archivo en la carpeta 'pages' con el nombre de la ruta deseada. El enrutador de Next.js se encarga de las rutas dinámicas y las rutas anidadas.

---

## Componentes y Estilos

* Componentes en Next.js

  Next.js utiliza la librería de React para manejar los componentes. Se pueden crear componentes personalizados en la carpeta 'components', y luego importarlos y utilizarlos en las páginas de la aplicación.
--- 

```jsx
  import React from 'react';

  function HomePage() {
    return (
      <div>
        <h1>Bienvenido a mi sitio web</h1>
        <p>Este es un sitio web creado con Next.js</p>
      </div>
    );
  }

  export default HomePage;
  ```

---

* Estilos en Next.js

  Next.js admite diferentes enfoques para manejar los estilos en la aplicación. Algunos de estos enfoques incluyen:

  + CSS Global: Se puede definir un archivo de estilos globales en la carpeta 'styles' para estilos que se aplican a toda la aplicación.
  + CSS en Módulos: Se pueden definir estilos específicos para un componente o página en particular mediante CSS en módulos. Estos estilos solo se aplicarán al componente o página específicos y no afectarán a otras partes de la aplicación.
  + CSS-in-JS: Next.js también admite bibliotecas de CSS-in-JS como Styled Components.
--- 
* Styled Components

  Styled Components es una biblioteca popular de CSS-in-JS que se utiliza para definir estilos en componentes de React. Next.js admite Styled Components y se pueden utilizar en cualquier componente de la aplicación. Con Styled Components, se puede definir CSS directamente en los componentes de la aplicación, lo que facilita la definición de estilos y la modularización de componentes.

---

## Obtención de datos con Next.js

En Next.js, podemos obtener datos de diferentes fuentes, como APIs externas o bases de datos. Podemos hacer esto utilizando el método `getStaticProps` o `getServerSideProps` . 

* `getStaticProps`: Este método se utiliza para obtener datos en tiempo de compilación. Esto significa que los datos se obtienen una vez y se guardan en caché. Los datos se pueden actualizar mediante la recompilación del sitio.

* `getServerSideProps`: Este método se utiliza para obtener datos en tiempo de ejecución. Los datos se obtienen en cada solicitud y, por lo tanto, siempre están actualizados. Este método es ideal para datos que cambian frecuentemente.

---

Para obtener datos, podemos utilizar la función `fetch` . Esta función se utiliza para enviar una solicitud HTTP a una API externa y obtener los datos. Podemos utilizar `fetch` en combinación con `getStaticProps` o `getServerSideProps` para obtener datos y pasarlos a nuestros componentes.

```js
export async function getStaticProps() {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts')
    const data = await res.json()

    return {
        props: {
            posts: data
        }
    }
}
```

---

## Layouts en Next.js

Los Layouts en Next.js son componentes que nos permiten definir una estructura común para nuestras páginas. Podemos utilizar Layouts para definir elementos comunes como encabezados, pies de página y menús de navegación.

Para crear un Layout en Next.js, podemos crear un componente de React que tenga un contenido variable. Podemos utilizar este componente en nuestras páginas para definir una estructura común.

---

```jsx
// components/Layout.js

import Header from './Header'

const Layout = ({
    children
}) => {
    return ( <
        div >
        <
        Header / >
        <
        main > {
            children
        } <
        /main> <
        footer >
        Copyright© {
            new Date().getFullYear()
        } </footer> < /div >
    )
}

export default Layout
```

---

```jsx
/ pages/index.js

import Layout from '../components/Layout'

const HomePage = () => {
    return ( <
        Layout >
        <
        h1 > Bienvenido a mi sitio web < /h1> <
        p > Este es un ejemplo de cómo usar Layouts en Next.js < /p> < /
        Layout >
    )
}

export default HomePage
```

---

## Enrutado en Next.js

Next.js utiliza un sistema de enrutado que nos permite definir rutas para nuestras páginas de forma sencilla y elegante. Podemos crear una carpeta `pages` en nuestro proyecto y dentro de ella, crear archivos que correspondan a las rutas de nuestra aplicación.

---

Por ejemplo, si queremos crear una página para la ruta `/acerca-de` , podemos crear un archivo `acerca-de.js` dentro de nuestra carpeta `pages` . En este archivo, podemos definir el contenido que queremos que se muestre en esa página:

```jsx
// pages/acerca-de.js

const AcercaDePage = () => {
    return ( <
        div >
        <
        h1 > Acerca de mi sitio web < /h1> <
        p > Este es un ejemplo de cómo funciona el enrutado en Next.js < /p> < /
        div >
    )
}

export default AcercaDePage
```

---

* Cuando accedemos a la ruta `/acerca-de` en nuestro navegador, Next.js automáticamente busca un archivo que coincida con esa ruta en la carpeta `pages` y renderiza el componente que contiene. De esta manera, podemos definir rutas para nuestra aplicación sin necesidad de configurar un sistema de enrutado externo.

* También podemos utilizar parámetros en nuestras rutas para crear páginas dinámicas. Por ejemplo, si queremos crear una página para la ruta `/usuarios/[id]` , podemos crear un archivo `usuarios/[id].js` en nuestra carpeta `pages` y utilizar el valor de `id` para mostrar información específica:

---

```jsx
// pages/usuarios/[id].js

const UsuarioPage = ({
    id
}) => {
    return ( <div>
        <h1> Información del usuario {
            id
        } </h1> <
        p> Aquí se mostraría la información específica del usuario con el ID {
            id
        } </p> </div>
    )
}

export default UsuarioPage

export async function getServerSideProps({
    params
}) {
    return {
        props: {
            id: params.id,
        },
    }
}
```

---

```jsx
  import Link from 'next/link';

  function HomePage() {
    return (
      <div>
        <h1>Bienvenido a mi sitio web</h1>
        <ul>
          <li>
            <Link href="/usuarios/1">
              <a>Usuario</a>
            </Link>
          </li>
          <li>
            <Link href="/acerca-de">
              <a>Acerca de mi</a>
            </Link>
          </li>
        </ul>
      </div>
    );
  }

  export default HomePage;
  ```

  
---

## API Routes

* ¿Qué son las API Routes?

  Las API Routes son una característica de Next.js que permite crear endpoints de API en la aplicación. Esto significa que se pueden crear rutas que devuelvan datos JSON en lugar de HTML. Las API Routes son una forma fácil y rápida de crear una API en la aplicación sin tener que configurar un servidor de API independiente.

* ¿Cómo crear una API Route?

  Para crear una API Route en Next.js, se debe crear un archivo en la carpeta 'pages/api' con el nombre de la ruta deseada. Dentro de este archivo, se pueden definir las funciones para manejar las solicitudes HTTP (GET, POST, PUT, DELETE, etc.). La función devolverá los datos en formato JSON y se pueden utilizar en la aplicación para recuperar datos de forma asíncrona.
---

* Ejemplos de uso API Routes

  Algunos ejemplos de API Routes pueden ser:

  + Recuperar los datos de un usuario desde una base de datos
  + Recuperar los datos de una publicación desde una base de datos
  + Enviar datos de formulario a un servicio externo
  + Recuperar los datos de un API externo y transformarlos para su uso en la aplicación
---
* Ejemplo 3: Creación de una API Route

```js
  export default function handler(req, res) {
      const {
          name,
          email
      } = req.body;

      // Guardar el usuario en la base de datos

      res.status(200).json({
          success: true
      });
  }
```

---

## Middleware en Next.js

* ¿Qué es el middleware?

  El middleware es una técnica de software que se utiliza para agregar funcionalidades adicionales a una aplicación sin tener que modificar su código fuente. En Next.js, el middleware se utiliza para manipular las solicitudes y las respuestas antes de que se envíen a los componentes de la aplicación.

* ¿Cómo funciona el middleware en Next.js?

  En Next.js, el middleware se puede implementar utilizando las funciones 'getServerSideProps' y 'getInitialProps'. Estas funciones se ejecutan en el servidor antes de enviar el contenido HTML al cliente y se pueden utilizar para agregar datos adicionales al componente antes de que se represente en la página.
---
* Ejemplos de uso de middleware en Next.js

  Algunos ejemplos de uso de middleware en Next.js pueden ser:

  + Autenticación: se puede utilizar el middleware para verificar si un usuario está autenticado antes de enviar una solicitud a la aplicación.
  + Validación: se puede utilizar el middleware para validar los datos enviados por un formulario antes de procesarlos en la aplicación.
  + Login: se puede utilizar el middleware para registrar información sobre las solicitudes y respuestas de la aplicación para fines de análisis.
  + Cacheo: se puede utilizar el middleware para almacenar en caché el contenido de la página y mejorar el rendimiento de la aplicación.

---

```jsx
  export async function getServerSideProps(context) {
    const { req, res } = context;

    // Verificar si el usuario está autenticado

    if (!user) {
      res.setHeader('location', '/login');
      res.statusCode = 302;
      res.end();
    }

    return {
      props: {
        // datos para el componente
      },
    };
  }
  ```

---

# Gracias por escuchar

![!bg  HAhaha vertical](https://media.tenor.com/gj_1JMalIiYAAAAd/rickroll-rick.gif)
