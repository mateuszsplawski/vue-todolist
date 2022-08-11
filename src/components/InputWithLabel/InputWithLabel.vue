<script>
export default {
  props: {
    label: String,
    placeholder: String,
    value: String,
  },
  emits: ["update:value"],
  methods: {
    emitValue(event) {
      const value = event.currentTarget.value;
      this.$emit("update:value", value);
    },
  },
};
</script>

<template>
  <label>
    {{ label }}
    <input :placeholder="placeholder" :value="value" @input="emitValue" />
  </label>
</template>
