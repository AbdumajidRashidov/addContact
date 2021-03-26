<template>
  <div>
    <li>
      <h1>{{ name }} {{ isFavorite ? "Favorite" : "" }}</h1>
      <button v-on:click="toggleFavorite">Toggle Favorite</button>
      <button v-on:click="toggleDetails">
        {{ detailsAreVisible ? "Hide" : "Show" }} Details
      </button>
      <button @click="this.$emit('delete', id)">Delete</button>
    </li>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong>{{ phoneNumber }}</li>
      <li><strong>email:</strong>{{ emailAddress }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      // validator: function (value) {
      //   return value === "1" || value === "0";
      // },
    },
  },
  emits: ["toggle-favorite", "delete"],
  // emits: {
  //   "toggle-favorite": function (id) {
  //     if (id) {
  //       return true;
  //     } else {
  //       console.warn("id is missing!");
  //       return false;
  //     }
  //   },
  // },
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
      this.$emit("toggle-favorite", this.id);
    },
  },
};
</script>

<style></style>
