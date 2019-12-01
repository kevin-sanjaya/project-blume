<template>
  <div>
    <md-table v-model="trips" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Timestamp">
          <span>{{ getFormattedDate(item) }}</span>
          {{ item.time_start }} - {{ item.time_end }}
        </md-table-cell>
        <md-table-cell md-label="Duration">
          <span>{{ getFormattedDuration(item.duration) }}</span>
          {{ item.point }} point
        </md-table-cell>
        <md-table-cell md-label="Origin">
          <span>{{ item.origin.location }}</span>
          {{ item.origin.city }}, {{ item.origin.state }}
        </md-table-cell>
        <md-table-cell md-label="Destination">
          <span>{{ item.destination.location }}</span>
          {{ item.destination.city }}, {{ item.destination.state }}
        </md-table-cell>
        <md-table-cell md-label="Distance">
          <span>{{ item.distance }} mi</span>
        </md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
export default {
  name: "simple-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: ""
    }
  },
  methods: {
    getFormattedDate(trip) {
      const date = new Date(trip.date);
      return `${this.dateName[date.getDay()]}, ${
        this.monthName[date.getMonth()]
      } ${
        date.getDate() > 9 ? date.getDate() : `0${date.getDate()}`
      } ${date.getFullYear()}`;
    },
    getFormattedDuration(duration) {
      const hour = duration.split(":")[0];
      const minute = duration.split(":")[1];
      return `${hour === "00" ? "" : `${parseInt(hour)}hr`} ${minute} min`;
    }
  },
  data() {
    return {
      dateName: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"],
      monthName: [
        "Jan",
        "Feb",
        "Mar",
        "Apr",
        "May",
        "Jun",
        "Jul",
        "Aug",
        "Sep",
        "Oct",
        "Nov",
        "Dec"
      ],
      selected: [],
      trips: [
        {
          date: "10/05/2019",
          time_start: "09:32",
          time_end: "10:15",
          duration: "00:42",
          origin: {
            location: "Pacific Beach",
            city: "San Diego",
            state: "CA"
          },
          destination: {
            location: "Culver West",
            city: "Los Angeles",
            state: "CA"
          },
          distance: "113.9",
          point: "227"
        },
        {
          date: "10/18/2019",
          time_start: "14:32",
          time_end: "16:11",
          duration: "01:32",
          origin: {
            location: "South Park",
            city: "San Diego",
            state: "CA"
          },
          destination: {
            location: "Paradise Valley",
            city: "San Diego",
            state: "CA"
          },
          distance: "122.4",
          point: "332"
        }
      ]
    };
  }
};
</script>

<style scoped>
span {
  font-weight: 500;
  color: #616161;
  display: block;
  margin-bottom: 5px;
}
</style>
