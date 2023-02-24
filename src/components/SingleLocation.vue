<template>
  <div class="px-2 py-4">
    <div class="rounded-lg shadow-lg pb-4 bg-white">
      <img
        :src="image"
        :alt="`Image of ${name}`"
        class="object-cover w-full h-48 rounded-t"
      />
      <main class="text-left px-2">
        <h1 class="text-xl pt-1">{{ name }}</h1>
        <h3 class="text-sm">{{ description }}</h3>
      </main>
    </div>
  </div>
</template>

<script>
import { toRefs } from "vue";
export default {
  props: {
    location: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    const { name, image, description } = toRefs(props.location);
    return { name, image, description };
  },
};
</script>
