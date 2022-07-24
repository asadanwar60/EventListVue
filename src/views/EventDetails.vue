<template>
  <div v-if="event">
    <h4>{{ event.title }}</h4>
    <span>@{{ event.time }} on {{ event.date }} @ {{ event.location }}</span>
    <p>{{ event.description }}</p>
  </div>
</template>
<script>
import EventService from "@/services/EventService";

export default {
  props: ["id"],
  data() {
    return {
      event: null,
    };
  },
  created() {
    EventService.getEvent(this.id)
      .then((response) => {
        // console.log("events", response.data);
        this.event = response.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>
