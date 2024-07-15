![alt](./public/Captura%20de%20pantalla%202024-07-15%20182217.png)
# interfaces-interctivas-framework-vue

## Proyecto Pokémon

Este proyecto es una aplicación de Vue.js que muestra cartas de Pokémon. El usuario puede intentar adivinar el nombre del Pokémon y, si es correcto, se revelará la imagen completa y el nombre del Pokémon.

### Estructura del Proyecto

El proyecto consta de los siguientes componentes y archivos principales:

 <ul>
<li>App.vue: El componente principal que maneja la lista de Pokémon y el contador de Pokémon descubiertos.</li>
<li>CartaPokemon.vue: El componente que representa una carta individual de Pokémon, donde el usuario puede adivinar el nombre del Pokémon.</li>

 </ul>

## Características

 <ul>
<li>Mostrar una lista de cartas de Pokémon.
Permitir al usuario adivinar el nombre del Pokémon.</li>
<li>Revelar la imagen y el nombre del Pokémon si el usuario adivina correctamente.</li>
<li>Contador de Pokémon descubiertos.</li>
 </ul>

## Componentes

### App.vue

Este es el componente principal que se encarga de obtener la lista de Pokémon de la API y manejar el contador de Pokémon descubiertos.

### Métodos

getPokemon(): Realiza una llamada a la API de Pokémon para obtener la lista de Pokémon.
incrementarContador(): Incrementa el contador de Pokémon descubiertos cuando se descubre un Pokémon.
CartaPokemon.vue
Este componente representa una carta de Pokémon individual.

## Props

 <ul>
<li>poke: Un objeto que contiene la información del Pokémon.</li>
 </ul>

## Data

 <ul>
<li>namePoke: Cadena que almacena el nombre del Pokémon ingresado por el usuario.</li>
<li>descubierto: Booleano que indica si el Pokémon ha sido descubierto.</li>

 </ul>

## Computed

 <ul>
<li>imagenPokemon(): Devuelve la URL de la imagen del Pokémon.</li>

 </ul>

## Métodos

 <ul>
<li>handleSubmit(): Maneja la lógica cuando el usuario intenta adivinar el nombre del Pokémon.</li>

 </ul>

## Project setup

```
npm install
```

### Compiles and hot-reloads for development

```
npm run serve
```

### Compiles and minifies for production

```
npm run build
```

### Lints and fixes files

```
npm run lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).
