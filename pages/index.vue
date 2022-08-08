<template>
  <div>
    <h1>Events</h1>

    <EventCard
      v-for="(event, index) in events"
      :key="index"
      :event="event"
      :data-index="index"
    />
  </div>
</template>

<script>
  import EventCard from "@/components/EventCard.vue";
  import {mapState} from 'vuex';

  export default {
    components: {
      EventCard,
    },
    head() {
      return {
        title: "Event Listing - Real world Events",
        meta: [
          {
            hid: "description",
            name: "description",
            content: "Where can you find all the events in your neighborhood?",
          },
        ],
      };
    },
    async fetch({ store, error }) {
      try {
        await store.dispatch('events/fetchEvents');
      } catch (e) {
          error({StatusCode: 503, Message: 'Service Unavailable'});
      }
    },
    computed:{
      ...mapState({
        events : state => state.events.events,
      }),
    },
  };
</script>
n
