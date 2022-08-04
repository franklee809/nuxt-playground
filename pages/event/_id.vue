<template>
  <div>
    <h1> {{ events.title }} </h1>
  </div>
</template>

<script>
  export default {
    head() {
      return {
        title: 'Event#' + this.events.title,
        meta: [
          {
            hid: "description",
            name: "description",
            content: "What do you need to know about this event ?" + this.events.title,
          },
        ],
      };
    },
    async asyncData({ $axios, error, params }) {
      try {
        const data = await $axios.$get(`http://localhost:3000/events/${params.id}`);
        return {
          events: data,
        };
      } catch (e) {
          error({StatusCode: 503, Message: 'Service Unavailable'});
      }
    },
  };
</script>
