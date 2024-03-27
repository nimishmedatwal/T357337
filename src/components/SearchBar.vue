<template>
    <center>
    <div class="mw-ui-icon-input">
      <input v-model="searchQuery" placeholder="Search Wikipedia" class="mw-ui-input" />
      <button @click="search" class="mw-ui-icon-btn">
        <i class="fa-solid fa-magnifying-glass"></i>
      </button>
    </div>
    </center>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchQuery: '',
      };
    },
    methods: {
      search() {
        this.$emit('search', this.searchQuery);
      },
    },
  };
  </script>

  <style scoped>
  .mw-ui-icon-input {
    display: flex;
    align-items: center;
    border: 1px solid var(--mw-ui-border-color);
    border-radius: var(--mw-ui-border-radius);
    overflow: hidden;
    width: 30vw;
    margin-top:30vh ;
  }
  
  .mw-ui-input {
    flex: 1;
    padding: 10px;

  }
  
  .mw-ui-icon-btn {
    padding: 10px;
    cursor: pointer;
  }
  
  .fas.fa-search {
    color: var(--mw-ui-color-brand);
  }
  </style>