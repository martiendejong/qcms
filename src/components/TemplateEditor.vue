<template>
  <div>
    <q-input
      v-model="internalTemplate"
      type="textarea"
      rows="10"
      label="Vue Template"
      filled
      @update:model-value="updateTemplate"
    />
  </div>
</template>

<script>
export default {
  props: {
    template: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      internalTemplate: this.template,
    };
  },
  watch: {
    template(newTemplate) {
      this.internalTemplate = newTemplate;
    },
  },
  methods: {
    updateTemplate() {
      this.$emit('update:template', this.internalTemplate);
    },
  },
};
</script>
