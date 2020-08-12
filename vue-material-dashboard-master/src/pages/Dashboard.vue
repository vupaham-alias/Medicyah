<template>
  <div class="content">
    <div v-for="item in hotelData" :key="item.id" class="md-layout" md="3">
      <div
        class="md-layout-item md-medium-size-100 md-xsmall-size-100 md-size-33"
      >
        <chart-card
          :chart-data="dailySalesChart.data"
          :chart-options="dailySalesChart.options"
          :chart-type="'Line'"
          data-background-color="blue"
        >
          <template slot="content">
            <h4 class="title">{{ item.name }}</h4>
            <p class="category">
              <span class="text-success"
                > {{ item.name }}
              </span>
              {{ item.description }}.
            </p>
          </template>

          <template slot="footer">
            <div class="stats">
              <md-icon>{{ item.phone }}</md-icon>
              <md-button class="md-raised md-success" @click="bookHotel(item.name)">Book</md-button>
            </div>
          </template>
        </chart-card>
      </div>
    </div>
  </div>
</template>

<script>
import {
  ChartCard,
} from "@/components";

export default {
  components: {
    ChartCard,
  },
  data() {
    return {
      hotelData: [
        {id: 1, name: 'vania', description: 'near vashara bearch, beautiful view sun rise, sun set, free tea at evening', phone: '090884121'},
        {id: 2, name: 'vania', description: 'near vashara bearch, beautiful view sun rise, sun set, free tea at evening', phone: '090884121'},
        {id: 3, name: 'vania', description: 'near vashara bearch, beautiful view sun rise, sun set, free tea at evening', phone: '090884121'},
        {id: 4, name: 'vania', description: 'near vashara bearch, beautiful view sun rise, sun set, free tea at evening', phone: '090884121'},
        {id: 5, name: 'vania', description: 'near vashara bearch, beautiful view sun rise, sun set, free tea at evening', phone: '090884121'},
        {id: 6, name: 'vania', description: 'near vashara bearch, beautiful view sun rise, sun set, free tea at evening', phone: '090884121'},
        {id: 7, name: 'vania', description: 'near vashara bearch, beautiful view sun rise, sun set, free tea at evening', phone: '090884121'}
      ],
      dailySalesChart: {
        data: {
          labels: ["M", "T", "W", "T", "F", "S", "S"],
          series: [[12, 17, 7, 17, 23, 18, 38]]
        },
        options: {
          lineSmooth: this.$Chartist.Interpolation.cardinal({
            tension: 0
          }),
          low: 0,
          high: 50, // creative tim: we recommend you to set the high sa the biggest value + something for a better look
          chartPadding: {
            top: 0,
            right: 0,
            bottom: 0,
            left: 0
          }
        }
      },
    };
  },
  methods: {
    bookHotel(name){
      let params = {
        hotelName: name,
        CustomerName: 'hey'
      }
      alert(params)
    }
  }
};
</script>
<style>
.md-layout-item.md-size-33 {
  min-width: 50% !important;
  max-width: 50%;
  flex: 0 1 33.3333%;
}
</style>