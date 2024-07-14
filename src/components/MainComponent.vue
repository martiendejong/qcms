<template>
  <q-col>
    <KeyValueInput v-model:keyValuePairs.sync="keyValuePairs" />
    <TemplateEditor v-model:template.sync="template" />
  </q-col>
  <q-col>
    <TemplateRenderer
      :key="rendererKey"
      :template="template"
      :keyValuePairs="keyValuePairs"
    />
  </q-col>
</template>

<script>
import KeyValueInput from './KeyValueInput.vue';
import TemplateEditor from './TemplateEditor.vue';
import TemplateRenderer from './TemplateRenderer.vue';

export default {
  components: {
    KeyValueInput,
    TemplateEditor,
    TemplateRenderer,
  },
  data() {
    return {
      keyValuePairs: [{ key: 'message', value: 'Hello, world!' }],
      template: '<div>{{ message }}</div>',
      renderedTemplate: '<div>{{ message }}</div>',
      rendererKey: 0,
    };
  },
  methods: {
    renderTemplate() {
      this.renderedTemplate = this.template;
      this.rendererKey += 1; // This forces TemplateRenderer to re-render
    },
  },
};
</script>
