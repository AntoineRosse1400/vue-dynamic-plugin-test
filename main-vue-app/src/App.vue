<script setup lang="ts">
import { ref, onMounted } from 'vue';

const url = "https://picsum.photos/200/300"
const customFormLoaded = ref(false);
const customFormComponent = ref(null);
  const pluginName = 'testvuejsplugin';
  const componentName = 'SpecialUploader';

const loadCustomFormPackage = () => {
  // Dynamically load the custom form package and its components
  import('testvuejsplugin').then((customForms) => {
    customFormComponent.value = customForms[componentName];
    if(customFormComponent.value !== undefined) {
      customFormLoaded.value = true;
    } else {
      console.error(`Error loading component ${componentName} from plugin ${pluginName}:`);
    }
  })
    .catch((error) => {
      console.error("Error loading custom form:", error);
    });
};

onMounted(() => {
  // loadCustomFormPackage();
});

</script>

<template>
  <h1>Main App</h1>
  <button @click="loadCustomFormPackage">Load plugin</button>
  <h2 v-if="!customFormLoaded">Default view...</h2>
  <component :is="customFormComponent"></component>
</template>

<style scoped></style>
