<template>
  <li>
    <h2>{{ name }} {{ isFav ? "Fav": ""}}</h2>
    <button @click="toggleFav"> Toggle Favorite</button>
    <button @click="toggleDetail">
      {{ detailVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="detailVisible">
      <li><strong> Phone: </strong> {{ phoneNo }}</li>
      <li><strong> Email: </strong> {{ emailAddress }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {  // to access data from parent
    id:{
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNo: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true
    },
    isFav:
    {
      type: Boolean,
      required: false
    },
  },
  data() {
    return {
      detailVisible: false,
      friend: {
        id: "mnuel",
        name: "Manuel Lorez",
        phone: "1111",
        email: "test@local",
      },
    };
  },
  methods: {
    toggleDetail() {
      this.detailVisible = !this.detailVisible;
    },
    toggleFav()
    {
      this.$emit('toggle-favorite',this.id); // to emit data to parent
    }
  },
};
</script>
