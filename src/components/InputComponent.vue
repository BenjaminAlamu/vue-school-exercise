<template>
  <div>
    <input
      :placeholder="placeholder"
      @input="trigger($event)"
      :type="type"
      :value="modelValue"
      class="w-full border p-2 my-2 rounded"
    />
  </div>
</template>
<script>
export default {
  props: {
    modelValue: {},
    placeholder: {
      type: String,
      default: "Placeholder",
    },
    type: {
      type: String,
      default: "text",
    },
  },
  setup(props, context) {
    const trigger = function (e) {
      context.emit(`update:modelValue`, e.target.value);
    };
    return { trigger };
  },
};
</script>
