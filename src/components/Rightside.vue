<template>
  <div class="right-side">
    <div class="content">
      <p>{{ data.location }}</p>
      <p>{{ data.caption }}</p>
    </div>
  </div>
</template>

<script>
//da bi mogli da koristimo taj emit sto smo napravili u drugu komponentu moramo da 
//da napravimo tu magistralu koju cemo da koristimo izmedju tih komponenti
import EventBus from "../eventBus";
export default {
  data() {
    return {
      data: {
        location: "Location placeholder",
        caption: "Payload placeholder",
      },
    };
  },
  methods: {
    updateData(payload) {
      this.data = payload;
    },
  },
  mounted() {
    // sada prisluskujemo taj uniqe emit i uzimamo taj payload sto smo poslali iz druge
    //kompoenente
    EventBus.$on("DATA_PUBLISHED", (payload) => {
      this.updateData(payload);
    });
  },
};
</script>

<style scoped>
.right-side {
  width: 50%;
  height: 500px;
  float: right;
  background-color: #42b883;
  border: 1px;
  border-color: black;
}
</style>