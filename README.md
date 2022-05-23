## Learning Next.js

### What is JSX?

JSX is a syntax extension for JavaScript that allows you to describe your UI in a familiar HTML-like syntax. The nice thing about JSX is that apart from following three [JSX rules](https://beta.reactjs.org/learn/writing-markup-with-jsx#the-rules-of-jsx), you don’t need to learn any new symbols or syntax outside of HTML and JavaScript.

### React Core Concepts

Hay tres conceptos claves de React para familiarizarse para empezara a construir aplicaciones con React. Estas son:

* Components
* Props
* State

#### Build UI with components

Las interfaces de usuario pueden ser destructuradas en pequeños bloques llamados **components**

Los componentes nos permiten construir pequeños pedazos, encapsulados de código reutilizable.
Podemos pensarlo como ladrillos de LEGO.

La modularidad de la aplicación permite que esto se vuelva bastante mantenible, ya que si una aplicación crece es facil agregar, actualizar o eliminar components sin tocar el resto de la aplicación

##### Creando componentes

Un componente es una función que retorna un elemento UI, como retorno de la función.

Primero los componentes de React deberan ser Capitalizados para distinguirlos de HTML y javascript plano.

Segundo, React utiiza la misma forma en la que se utilizan las etiquetas de HTML, con angle brackets <>

```react
<script type="text/jsx">

  const app = document.getElementById("app")

	function Header() {
		return <h1>Develop. Preview. Ship. 🚀</h1>
	}

	ReactDOM.render(<Header />, app)
</script>
```

The Next.js Compiler
Next.js handles much of these code transformations and underlying infrastructure to make it easier for your application to go to production.

**This is made possible because Next.js has a compiler written in Rust**, a low-level programming language, and SWC, a platform that can be used for compilation, minification, bundling, and more.

#### What is Compiling?

La compilación se refiere al proceso de tomar el código de un lenguaje para obtener una salida a otro lenguaje o una versión distinta del mismo.

#### What is Minifying?

Los desarrolladores escriben código para optimizar la lectura/analisis humano. Este código contiene información extra como espacios, comentarios, identaciones, multiples lineas. 

La minificación se refiere al proceso de remover código innecesario (descrito anteriormente) sin afectar a la funcionalidad del código. El objetivo es mejorar el rendimiento/performance de la aplicación a traves de reducir el peso de los archivos.

#### What is Bundling?

Los desarrolladores rompen la aplicación en modulos, componentes, y funciones que son usados para construir pedazos de la aplicación todavía mas grandes. De forma que exportando e importando estos modulos internos, asi también como librerias de terceros, se crea una compleja linea de de dependencias. 

Bundling se refiere al proceso de resolver las dependencias del proyecto y uniendolas en archivos optimizados para el navegador, el objetivo es reducir el numero de peticiones hacia archivos cuando el usuario visita la página web.

#### What is Code Splitting?

El desarrollo de una aplicación es usualmente hecho a traves de distintas paginas para que cada una de estas pueda ser accedida por diferentes url's. Donde cada uno de estas paginas se convierte en un acceso unico a la aplicación. 

Code-Splittling es el proceso de separar separar el bundle de la aplicación en pequeños pedazos (chunks) requeridos para cada punto de acceso. El objetivo así es mejorar la carga principal de la aplicación solo cargado el código que es requerido para cada página.

Por Next.js cada archivo dentro del directorio de pages/, sera automaticamente separado (split) en su propio JS bundle durante el paso de build.

#### Build time and Runtime

El Build time (o build step) es el nombre dado a la serie de pasos para preparar la aplicación para producción. 

Durante el build de la aplicación Next.js transforma el código a archivos optimizados-para-producción listos para ser lanzados a un servidor para después ser consumir y ser usado por el usaurio final.
Estos archios incluyen: HTML, código JavaScript para hacer render en el servidor, código Javascript para hacer paginas interactivas al cliente y archivos CSS.

Runtime se refiere al periodo de tiempo donde la aplicación se encuentra corriendo (activa) en respuesta de las peticiones de usuarios. Una vez que tu aplicación a sido empaquetada (built) y cargada (deployed).

#### What is Rendering?

Hay un proceso de trabajo que no puede ser evitado el cual es convertir tu código de react hacia HTML. Este proceso es llamada **rendering**.

El proceso puede tomar lugar en el lado del servidor o en el lado del cliente. 
Entonces esto puede suceder en el timepo de *build time*, o en cada request en *runtime*.

Con Next.js, se cuenta con tres tipos de metodos para rendereo
  1. Server-Side Rendering
  2. Static Site Generation
  3. Client-Site Rendering

#### Pre-Rendering

El pre-rendering se refiere tanto al server-side rendering como al static site rendering, porque la solicitud de información externa y transformación de componentes de React a HTML sucede antes de que el resultado sea enviado al cliente. 

##### Client-Side Rendering vs Pre-Rendering

En una aplicación de React estandar, el navegador recibe shell HTML vacio del servidor, junto con las instrucciones de JavaScript para construir la UI. Este proceso es llamado **client-side rendering** porque el porque el inicio del trabajo de render sucede en el dispositivo del usuario. 

En cambio, Next.js **pre-rendering** cada pagina por defecto. Pre-rendering significa que el HTML es generado antes, en el servidor, en vez de tener que hacer todo el trabajo en el dispositivo del usuario.

#### Server-Side Rendering

Con Server Side Rendering el HTML de la página es siempre generado en el servidor en cada request. El HTML, JSON data y JavaScript es generado para ser enviado al cliente.

Del lado del cliente, el HTMl es usado para mostrar una pagina rapida sin interactividad, mientras que React usa la JSON data e instrucciones de JS para hacer componentes interactivos (como agregar eventos a botones), **a este proceso se le llama Hidratación** (**Hydration**).

#### Static Site Generation

Con Statis side generation, el HTML es generado en el servidor pero al contrario de la estrategia de server-side rendering, aquí no hay servidor en runtime, en vez, el contenido es generado una vez, en build time cuando la aplicación es deployed, y en HTML es guardado en un CDN para ser reusado después para cada request. 

En Next.js esto sucede al utilizar **getStaticProps**.

Para aprender mas sobre cual es el sistema de render mejor para tu tipo de aplicación consulta la siguiente documentación [Data Fetching](https://nextjs.org/docs/basic-features/data-fetching/overview)

#### What is Network?

Una vez que la aplicación es cargada a la red, una aplicación de Next.js puede ser distribuida a traves de **Origin servers**, **Content Delivery Networks (CDNs)** y **The Edge**.

##### Origin Servers

Un origin server se refire a una computadora que guarda y corre la versión original de la aplicación. 
Se utiliza el termino *origin* para distinguir este servidor de los otro slugares donde el código puede ser distribuido. Tal como *CDN servers* o *Edge servers*.

Cuando un *Origin server* recibe una solicitud, este realiza un trabajo de computación antes de enviar la respuesta. 

Y el resultado de este trabajo de computación puede ser movido hacia un CDN.

##### Content Delivery Network

CDNs guarda contenido estatico (tales como HTML o imagenes) en multiples lugares alrededor del mundo, y estan localizados entre el cliente y el servidor de origen.

Cuando se recibe una solicitud, el CDN mas cercano a la ubicación del usuario responde con el resultado guardado (cached).

Esto reduce la carga del *origen* porque la computación no sucede en cada solicitud. A demas lo hace mas raído ya que se encuentra mas rápido de la ubicación del usuario. 

En Next.js desde que el **pre-rendering** puede ser hecho con anticipación, los CDNs se encuentran bien localizados guardando el resultado estatico del trabajo, logrando asi entregar contenido mas rápidamente.

##### The Edge

**The Edge** es un concepto generalizado para el borde/franja de la red, cerca del usuario. En realidad un CDN puede ser considerado parte del *Edge* porque guarda contenido estatico en el borde de la internet. 

De forma similar a un CDN, un **Edge** se encuentra distribuido en diferentes ubicaciones alredodor del mundo. Pero a diferencia de los CDN, los *Edge si pueden ejecutar código*.

Esto significa que *catching* y *code execution* puede ser hecho por un **Edge** cercas del usuario.

En Next.js se puede correr en el *Edge* con **Middleware**, rápidamente con *React Server Components*

## Pre-rendering

Por defecto Next.js hace pre rendering de cada pagina. Esto significa que Next.js genera HTML por cada pagina desde antes, en vez de tener que ser resuelto todo desde el lado del cliente (client-side Javascript). Pre-rendering puede resultar en un mejor efecto para el SEO.

De forma que si desabilitamos el JavaScript de nuestro navegador podemos observar que tendremos el HTML mostrado aun teniendo desactivado JS, esto es porque Next.js a pre rendereado al app en HTML estatico, lo que una vez que se habilita JS pasa a traves del step llamado `Hydration` lo cual da interactividad a los componentes integrados a la web por ejemplo `Link` de Next.js

Next.js tiene dos formas de pre-rendering 	**Static Generation** y **Server-side rendering**, la diferencia sucede *cuando* genera el HTML de la pagina.

* Static Generation
  * Es el metodo de pre rendering que genera HTML en *build time*. De esta forma el pre rendereado HTML es usando en cada request

* Server-side Rendering
  * Es el metodo que pre renderea el HTMl en cada request 

> Note: In development mode (when you run npm run dev or yarn dev), every page is pre-rendered on each request — even for pages that use Static Generation.

El uso de una u otra estrategia para el rendering, Next.js te permite elegir usar una u otra forma, generando un tipo de aplicación hibrida donde unas paginas sean Static Generation mientras que otras Server side. 

## When to Use Static Generation vs Server-side Generation

Se recomienda el uso de **Static Generation** (con o sin data) para que la pagina sea cargada una sola vez y *servida como CDN*, que lo hace mas rápido que estar cargando los elementos sobre cada request. 

Algunos ejemplos para Static Generation de uso en paginas son:
- Marketing pages
- Blog posts
- E-commerce product listings
- Help and documentation

En cambio si no es posible usar esta estrategia y la pagina que se consume muestra información que se actualiza frecuentemente o contiene cambios sobre cada request, entonces si debería usarse **Server-side Rendering**

### Static Generation with and without data 

Cuando una pagina necesita consultar una base de datos, realizar un request a una API o consultar un archivo, Static Generation permite realizar este flujo consultando primero la información para después servir el HTML estatico. 

Esto se logra a traves del uso de la función async *getStaticProps*

Se puede escribir código que se comunique directamente con la base de datos sin ningun problema ya que al utilizar getStaticProps, esto corre unicamente del lado del servidor, por lo que el cliente unca lo ve, inclusive esto no es incluido en el JS Bundle para el navegador. 

Finalmente, Static Generation no es una buena idea si no puedes pre renderear la pantalla antes de request del usuario, es decir, para paginas que muestren data actualizada sobre cada request que este haga, como ya se habia visto para este tipo de casos es que podemos intentar Server-side Rendering. 

## API Routes

Next.js has support for API Routes, which let you easily create an API endpoint as a Node.js serverless function.