---
title: 'Getting Started with React'
date: '2022-05-20'
---

### What is JSX?

JSX is a syntax extension for JavaScript that allows you to describe your UI in a familiar HTML-like syntax. The nice thing about JSX is that apart from following three [JSX rules](https://beta.reactjs.org/learn/writing-markup-with-jsx#the-rules-of-jsx), you don’t need to learn any new symbols or syntax outside of HTML and JavaScript.

### React Core Concepts

There are three key concepts to be familiar and start to build React applications. These are: 

* Components
* Props
* State

#### Build UI with components

User interfaces can be broken down into smaller blocks called **components**.

Components allow you to build self-contained, reusable pieces of code., we can think of components as LEGO bricks, and you take these individual bricks and combine them together to form larger structures.

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
