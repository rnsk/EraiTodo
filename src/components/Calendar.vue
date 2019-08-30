<template>
  <v-sheet
    height="500">
    <v-calendar
      class="transparent"
      type="month"
      :events="events"
      :event-color="getEventColor"
      event-text-color="light-blue darken-4"
      event-name="point"
      locale="Ja-JP"
      :day-format="formatDate"
      :show-month-on-first="showMonthOnFirst"
    ></v-calendar>
  </v-sheet>
</template>

<script>
import moment from 'moment';

  export default {
    data: () => ({
      today: '',
      showMonthOnFirst: false,
      events: [
        {
          point: '10',
          start: '2019-08-06',
          color: 'yellow lighten-3'
        },
        {
          point: '15',
          start: '2019-08-07'
        },
        {
          point: '12',
          start: '2019-08-08'
        },
        {
          point: '8',
          start: '2019-08-09'
        },
        {
          point: '15',
          start: '2019-08-10'
        },
        {
          point: '0',
          start: '2019-08-30'
        },
      ],
    }),
    created: function () {
        this.today = this.getToday()
    },
    methods: {
        getToday: function () {
            return moment(new Date).format('YYYY-MM-DD')
        },
        formatDate: function (date) {
            if (moment(date).isValid()) {
                return moment(date).format('D');
            }
            return '';
        },
        getEventColor: function (event) {
            if (event.color) {
                return event.color
            }
            return 'light-blue lighten-3'
        }
    }
  }
</script>