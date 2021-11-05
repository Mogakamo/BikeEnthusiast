<template>
  <div class="home">{{ info }}</div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      result: "",
      responseAvailable: false,
      apiKey: "<YOUR_RAPIDAPI_KEY>",
    };
  },
  mounted() {
    axios
      .get(
        "https://motorcycle-specs-database.p.rapidapi.com/article/2020/Yamaha/YZF%20R15"
      )
      .then((response) => (this.info = response.articleCompleteInfo));
  },
  components: {},
};
</script>
