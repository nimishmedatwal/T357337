<template>
    <center>
        <div class="mw-ui-card">
            <h2 class="mw-ui-heading-h2">{{ article.title }}</h2>
            <p class="mw-ui-body">{{ article.extract }}</p>
        </div>
    </center>   
  </template>
  
  <script>
  export default {
    props: {
      article: Object,
    },
  };
  </script>
  
  <style scoped>
  .mw-ui-card {
    background-color: var(--mw-ui-background-color);
    padding: 20px;
    border-radius: var(--mw-ui-border-radius);
    box-shadow: var(--mw-ui-box-shadow);
    margin-top: 20px;
  }
  
  .mw-ui-heading-h2 {
    margin-bottom: 10px;
  }
  
  .mw-ui-body {
    font-size: var(--mw-ui-font-size-body);
    line-height: var(--mw-ui-line-height-body);
  }
  </style>
  