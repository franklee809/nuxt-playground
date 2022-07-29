<template>
  <div>
    <h1>Event #{{ this.id}} </h1>
  </div>
</template>

<script>
  export default {
    head() {
      return {
        title: 'Event#' + this.id,
        meta: [
          {
            hid: "description",
            name: "description",
            content: "What do you need to know about this event ?" + this.id,
          },
        ],
      };
    },
    computed:{
      id(){
        return this.$route.params.id;
      }
    },
  };
</script>
