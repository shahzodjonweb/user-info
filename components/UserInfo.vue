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
export default {
  mounted() {
    if (navigator.geolocation) {
      console.log(navigator.userAgent);
      navigator.geolocation.getCurrentPosition(success, error);
    } else {
      error("not supported");
    }
    function success(position) {
      console.log(position);
    }

    function error(msg) {
      console.log(msg);
    }
  },
};
</script>
