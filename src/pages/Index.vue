<template>
  <Layout>
    <form id="ProxyRequest" name="ProxyRequest" @submit.prevent="handleSubmit">
      <label for="RequestTarget">
        <input
          name="RequestTarget"
          id="RequestTarget"
          v-model="RequestTarget"
          type="text"
          placeholder="example.com"
          required
        />
      </label>
      <label>
        <button>
          Submit
        </button>
      </label>
    </form>
    <section id="proxied-webpage">
      <div v-show="webpage" v-html="webpage"></div>
    </section>
  </Layout>
</template>

<script>
import axios from "axios";

export default {
  metaInfo: {
    title: "devs are dum",
  },
  data() {
    return {
      RequestTarget: "",
      webpage: null
    };
  },
  methods: {
    handleSubmit() {
      axios
        .post("https://jordo.in", { RequestTarget: this.RequestTarget })
        .then((res) => {
          this.webpage = res.data
          this.form = {
            RequestTarget: "",
          };
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>
