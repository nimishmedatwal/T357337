<template>
    <div>
      <cdx-search-input
        v-model="inputValue"
        button-label="Search"
        aria-label="SearchInput with Button demo"
        @update:model-value="onUpdate"
        @submit-click="onSearch"
        class="inputseach"
      />
    </div>
  </template>
  
  <script>
  import { defineComponent, ref } from "vue";
  import { CdxSearchInput } from "@wikimedia/codex";
  import '@wikimedia/codex/dist/codex.style.css'

  export default defineComponent({
    name: "SearchBar",
    components: { CdxSearchInput },
    setup(_, { emit }) {
      const inputValue = ref("");
  
      const onUpdate = (value) => {
        inputValue.value = value;
      };
  
      const onSearch = () => {
        if (inputValue.value.trim() !== "") {
          // Emit search event
          emit("search", inputValue.value.trim());
        }
      };
  
      return {
        inputValue,
        onUpdate,
        onSearch,
      };
    },
  });
  </script>
  
<style>
.inputseach{
    width: 30vw;
    margin-top:5vh;
}
</style>