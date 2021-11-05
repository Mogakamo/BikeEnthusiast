<template>
  <div class="home">{{ responseAvailable }}</div>
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
  mounted() {
    fetch(
      "https://motorcycle-specs-database.p.rapidapi.com/article/2020/Yamaha/YZF%20R15",
      {
        method: "GET",
        headers: {
          "x-rapidapi-host": "motorcycle-specs-database.p.rapidapi.com",
          "x-rapidapi-key":
            "cb50711466msh8ab234bdc5f2765p1e59a1jsnd0b9f945cd64",
        },
      }
    )
      .then((response) => (this.responseAvailable = response))
      .catch((err) => {
        console.error(err);
      });
    // axios
    //   .get(
    //     "https://motorcycle-specs-database.p.rapidapi.com/article/2020/Yamaha/YZF%20R15"
    //   )
    //   .then((response) => (this.info = response.articleCompleteInfo));
  },
  components: {},
};
</script>
