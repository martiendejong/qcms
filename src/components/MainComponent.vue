<template>
  <q-page>
    <q-layout>
      <q-header class="text-h5">Quasar Key-Value Template Renderer</q-header>
      <q-page-container>
        <q-page>
          <q-card>
            <q-card-section>
              <KeyValueInput v-model:keyValuePairs.sync="keyValuePairs" />
            </q-card-section>
          </q-card>
          <q-card>
            <q-card-section>
              <TemplateEditor v-model:template.sync="template" />
            </q-card-section>
          </q-card>
          <q-card>
            <q-card-section>
              <TemplateRenderer
                :key="rendererKey"
                :template="template"
                :keyValuePairs="keyValuePairs"
              />
            </q-card-section>
          </q-card>
          {{ template }}
        </q-page>
      </q-page-container>
    </q-layout>
  </q-page>
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
