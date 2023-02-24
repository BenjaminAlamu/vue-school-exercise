<template>
  <div class="px-4 shadow-lg rounded-lg bg-white py-6 mt-3 mr-2">
    <h1 class="text-xl">New Location</h1>
    <InputComponent
      type="text"
      v-model="location.name"
      placeholder="Name of Location"
    />

    <InputComponent
      type="text"
      v-model="location.description"
      placeholder="Why you love it so so much"
    />

    <InputComponent
      type="text"
      v-model="location.image"
      :value="location.image"
      placeholder="An image of location"
    />

    <button
      @click.prevent="handleSubmit"
      class="mt-3 bg-blue-600 px-4 py-1 rounded-lg text-white font-semibold"
    >
      Submit
    </button>
  </div>
</template>

<script>
import { ref } from "vue";
import InputComponent from "./InputComponent.vue";
export default {
  components: {
    InputComponent,
  },
  setup(props, context) {
    let location = ref({ name: "", image: "", description: "" });
    const handleSubmit = function () {
      context.emit("newLocation", location.value);
      location.value = { name: "", image: "", description: "" };
    };

    return { handleSubmit, location };
  },
};
</script>
