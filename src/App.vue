<template>
  <div>
    <main class="mx-auto">
      <p class="text-2xl font-bold">My Favourite Locations</p>
      <InputComponent
        v-model="search"
        class="w-1/3 mx-auto"
        placeholder="Search..."
      />
    </main>

    <main class="container w-full flex flex-wrap mx-auto">
      <main class="w-1/5">
        <AddLocation @newLocation="addLocation" />
      </main>
      <main class="w-4/5 flex flex-wrap">
        <SingleLocation
          class="w-1/3"
          v-for="(location, i) in filteredLocations"
          :key="i"
          :location="location"
        />
      </main>
    </main>
  </div>
</template>

<script>
import SingleLocation from "./components/SingleLocation.vue";
import AddLocation from "./components/AddLocation.vue";
import InputComponent from "./components/InputComponent.vue";
import { ref, computed } from "vue";

export default {
  name: "App",
  components: {
    SingleLocation,
    AddLocation,
    InputComponent,
  },
  setup() {
    const search = ref("");
    const locations = ref([
      {
        name: "Lagos, Nigeria",
        image: "https://picsum.photos/id/16/200",
        description: "I love the food",
      },
      {
        name: "Nairobi, Kenya",
        image: "https://picsum.photos/id/17/200",
        description: "Awesome people",
      },
      {
        name: "Cape Town, South Africa",
        image: "https://picsum.photos/id/18/200",
        description: "Lovely ladies",
      },
      {
        name: "Lome, Togo",
        image: "https://picsum.photos/id/19/200",
        description: "The night life is great",
      },
      {
        name: "Dakar, Senegal",
        image: "https://picsum.photos/id/14/200",
        description: "I love the beaches",
      },
      {
        name: "Accra, Ghana",
        image: "https://picsum.photos/id/15/200",
        description: "Green Scenery",
      },
    ]);
    const addLocation = function (data) {
      locations.value = [...locations.value, data];
    };

    const filteredLocations = computed(() => {
      return locations.value.filter((loc) => {
        return loc.name.toLowerCase().includes(search.value.toLowerCase());
      });
    });
    return { filteredLocations, addLocation, search };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 60px;
  background: #fdf8e7;
  min-height: 100vh;
}
</style>
