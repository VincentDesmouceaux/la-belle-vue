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
  
  <style scoped>
/* Stylisation du bouton */
button {
  background-color: #4caf50; /* Couleur de fond */
  color: white; /* Couleur du texte */
  border: none; /* Supprime les bordures */
  padding: 4px 8px; /* Espacement interne réduit pour réduire la taille du bouton */
  font-size: 14px; /* Taille de la police */
  cursor: pointer; /* Curseur au survol */
  transition: background-color 0.3s ease; /* Animation de transition */
}

/* Stylisation du bouton au survol */
button:hover {
  background-color: #45a049; /* Nouvelle couleur de fond au survol */
}
</style>
  