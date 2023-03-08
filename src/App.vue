
<template lang="pug">

h1 Hello World!
button Click me!

</template>

<style lang="scss">

h1 {
  color: green;

  &:hover {
    color: greenyellow;
  }
}

button {
  color: red;
  background-color: blue;
  border: 1px solid black;
  border-radius: 5px;
  padding: 10px;
  font-size: 20px;
  cursor: pointer;

  &:hover {
    color: white;
    background-color: green;
  }
}

</style>
