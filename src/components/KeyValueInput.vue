<template>
  <div>
    <q-list>
      <q-item v-for="(pair, index) in keyValuePairs" :key="index">
        <q-input
          v-model="pair.key"
          label="Key"
          @input="updateKeyValuePairs"
        ></q-input>
        <q-input
          v-model="pair.value"
          label="Value"
          @input="updateKeyValuePairs"
        ></q-input>
        <q-btn color="negative" @click="removePair(index)">Remove</q-btn>
      </q-item>
    </q-list>
    <q-btn @click="addPair">Add Key-Value Pair</q-btn>
  </div>
</template>

<script>
export default {
  props: {
    keyValuePairs: {
      type: Array,
      required: true,
    },
  },
  methods: {
    addPair() {
      this.$emit('update:keyValuePairs', [
        ...this.keyValuePairs,
        { key: '', value: '' },
      ]);
    },
    removePair(index) {
      const updatedPairs = [...this.keyValuePairs];
      updatedPairs.splice(index, 1);
      this.$emit('update:keyValuePairs', updatedPairs);
    },
    updateKeyValuePairs() {
      this.$emit('update:keyValuePairs', this.keyValuePairs);
    },
  },
};
</script>
