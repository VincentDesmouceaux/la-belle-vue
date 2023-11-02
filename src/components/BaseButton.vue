<template>
    <button v-on="$attrs">
      <slot></slot>
    </button>
  </template>
  
  <script>
  export default {
    name: 'BaseButton'
  }
  </script>
  
  <style></style>
  