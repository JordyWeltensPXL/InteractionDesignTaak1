<template>
    <div id="mydiv">
      <!-- Include a header DIV with the same name as the draggable DIV, followed by "header" -->
      <div id="mydivheader">Click here to move</div>
      <p>Move</p>
      <p>this</p>
      <p>DIV</p>
    </div>
  </template>
  
  <script>
  export default {
    mounted() {
      // Call the dragElement function for your specific element
      this.dragElement(document.getElementById("mydiv"));
    },
    methods: {
      dragElement(elmnt) {
        // Your existing dragElement logic goes here
        // ...
      },
    },
  };
  </script>

<style scoped>

#mydiv {
  position: absolute;
  z-index: 9;
  background-color: #ff0000;
  border: 1px solid #d3d3d3;
  text-align: center;
}

#mydivheader {
  padding: 10px;
  cursor: move;
  z-index: 10;
  background-color: #2196F3;
  color: #fff;
}

</style>