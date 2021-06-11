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
    };
  },
  methods: {
    handleSubmit() {
      axios
        .post("https://saybis-node.default.45.79.180.102.xip.io", this.RequestTarget)
        .then((res) => {
          console.log(res);
          // this.form = {
          //   RequestTarget: "",
          // };
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>
