<template>
  <div>
    <component :is="dynamicComponent"></component>
  </div>
</template>

<script>
import { compile } from 'vue';

export default {
  props: {
    template: {
      type: String,
      required: true,
    },
    keyValuePairs: {
      type: Array,
      required: true,
    },
  },
  computed: {
    dynamicComponent() {
      const data = this.keyValuePairs.reduce((acc, pair) => {
        acc[pair.key] = pair.value;
        return acc;
      }, {});

      const compiledTemplate = compile(this.template);

      return {
        render: compiledTemplate,
        data() {
          return data;
        },
      };
    },
  },
};
</script>
