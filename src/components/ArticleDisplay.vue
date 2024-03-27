<template>
    <center>
      <div class="article-display">
        <div class="mw-ui-card">
          <h2 class="mw-ui-heading-h2">{{ article.title }}</h2>
          <p class="mw-ui-body">{{ article.extract }}</p>
        </div>
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
  .article-display {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
  }
  
  .mw-ui-card {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    margin-top: 20px;
    width: 80%;
    max-width: 600px;
  }
  
  .mw-ui-heading-h2 {
    margin-bottom: 10px;
    font-size: 24px;
    color: #333;
  }
  
  .mw-ui-body {
    font-size: 16px;
    line-height: 1.6;
    color: #666;
  }
  </style>
  