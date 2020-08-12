<template>
  <div>
    <md-table v-model="users" :table-header-color="tableHeaderColor">
      <md-table-row slot="md-table-row" slot-scope="{ item }">
        <md-table-cell md-label="Customer name">{{ item.customer_name }}</md-table-cell>
        <md-table-cell md-label="Hotel booking">{{ item.hotel_name }}</md-table-cell>
        <md-table-cell md-label="Booking date">{{ item.booking_date }}</md-table-cell>
      </md-table-row>
    </md-table>
  </div>
</template>

<script>
export default {
  name: "ordered-table",
  props: {
    tableHeaderColor: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      selected: [],
      users: [
        {
          id: 1,
          customer_name: "Dakota Rice",
          hotel_name: "$36,738",
          booking_date: "Niger",
        }
      ]
    };
  }
};
</script>
