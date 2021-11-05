<template>
  <div class="home">
    <button type="button" id="get-joke" @click="fetchAPIData">
      Get a Bike!!
    </button>

    {{ result }}
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
// import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      result: "",
      responseAvailable: false,
      apiKey: "cb50711466msh8ab234bdc5f2765p1e59a1jsnd0b9f945cd64",
    };
  },
  methods: {
    async fetchApiData() {
      this.responseAvailable = false;

      await fetch("https://motorcycle-specs-database.p.rapidapi.com/make", {
        method: "GET",
        headers: {
          "x-rapidapi-host": "motorcycle-specs-database.p.rapidapi.com",
          "x-rapidapi-key": this.apiKey,
        },
      })
        .then((response) => {
          if (response.ok) {
            return response.json();
          } else {
            alert(
              "Server returned " + response.status + " : " + response.statusText
            );
          }
        })
        .then((response) => {
          this.result = response.body;
          this.responseAvailable = true;
        })
        .catch((err) => {
          console.error(err);
        });
      // axios
      //   .get(
      //     "https://motorcycle-specs-database.p.rapidapi.com/article/2020/Yamaha/YZF%20R15"
      //   )
      //   .then((response) => (this.info = response.articleCompleteInfo));
    },
  },
  components: {},
};
</script>
