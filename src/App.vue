<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>Vuetify</span>
        <span class="font-weight-light">MATERIAL DESIGN</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn flat href="https://github.com/vuetifyjs/vuetify/releases/latest" target="_blank">
        <span class="mr-2">Latest Release</span>
        <v-icon>open_in_new</v-icon>
      </v-btn>
    </v-toolbar>

    <v-content>
      <v-card class="pb-2">
        <v-card-actions class="pb-0">
          <v-btn icon @click="$refs.calendar.prev()">
            <v-icon>chevron_left</v-icon>
          </v-btn>
          <v-btn icon @click="$refs.calendar.next()">
            <v-icon>chevron_right</v-icon>
          </v-btn>
          <v-btn @click="calendarStartDate = '2019-04-08'">go to wrong month</v-btn>
          <v-btn @click="calendarStartDate = '2017-05-01'">go to other wrong month</v-btn>
          <v-btn @click="calendarStartDate = '2015-06-01'">go to different wrong month</v-btn>
          current start date: {{calendarStartDate}}
        </v-card-actions>
        <v-card-text>
          <v-calendar
            :now="today"
            v-model="calendarStartDate"
            color="primary"
            ref="calendar"
            :locale="locale"
            :short-months="false"
            :short-weekdays="false"
            :weekdays="weekdayFormat"
          >
            <template slot="day" slot-scope="{ date }">
              <template v-for="(event, idx) in eventsMap[date]">
                <v-menu :key="idx" bottom left offset-y>
                  <div
                    v-if="!event.time"
                    slot="activator"
                    v-ripple
                    class="event"
                    :class="event.class"
                    v-html="event.title"
                  ></div>
                  <v-card flat>
                    <v-card-title class="pa-3" primary-title>{{event.details}}</v-card-title>
                  </v-card>
                </v-menu>
              </template>
            </template>
          </v-calendar>
        </v-card-text>
      </v-card>
    </v-content>
  </v-app>
</template>
<script>
export default {
  data: () => ({
    today: "2019-02-08",
    calendarStartDate: "2019-04-08",
    locale: "en",
    weekdayFormat: [1, 2, 3, 4, 5, 6, 0],
    eventsMap: {
      "2019-02-11": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-02-11",
          class: "my-event"
        }
      ],
      "2019-02-18": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-02-18",
          class: "my-event"
        }
      ],
      "2019-02-25": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-02-25",
          class: "my-event"
        }
      ],
      "2019-03-04": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-03-04",
          class: "my-event"
        }
      ],
      "2019-03-11": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-03-11",
          class: "my-event"
        }
      ],
      "2019-03-18": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-03-18",
          class: "my-event"
        }
      ],
      "2019-03-25": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-03-25",
          class: "my-event"
        }
      ],
      "2019-04-01": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-04-01",
          class: "my-event"
        }
      ],
      "2019-04-08": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-04-08",
          class: "my-event"
        }
      ],
      "2019-04-15": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-04-15",
          class: "my-event"
        }
      ],
      "2019-04-22": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-04-22",
          class: "my-event"
        }
      ],
      "2019-04-29": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-04-29",
          class: "my-event"
        }
      ],
      "2019-05-06": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-05-06",
          class: "my-event"
        }
      ],
      "2019-05-13": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-05-13",
          class: "my-event"
        }
      ],
      "2019-05-20": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-05-20",
          class: "my-event"
        }
      ],
      "2019-05-27": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-05-27",
          class: "my-event"
        }
      ],
      "2019-06-03": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-06-03",
          class: "my-event"
        }
      ],
      "2019-06-10": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-06-10",
          class: "my-event"
        }
      ],
      "2019-06-17": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-06-17",
          class: "my-event"
        }
      ],
      "2019-06-24": [
        {
          title: "calendar.job-start",
          details: "00:00",
          date: "2019-06-24",
          class: "my-event"
        }
      ]
    }
  })
};
</script>

<style scoped>
.event {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  border-radius: 2px;
  width: 100%;
  font-size: 12px;
  padding: 3px;
  cursor: pointer;
  margin-bottom: 1px;
  color: #ffffff;
}
.event.my-event {
  background-color: #1867c0;
  border: 1px solid #1867c0;
}
</style>