<template>
  <div>
    <div class="row">
      <h3>Sensor 1</h3>
    </div>
    <div class="row">
      <div class="col-lg-4" :class="{'text-right': isRTL}">
        <card type="chart">
          <template slot="header">
            <h3 class="card-title">
              Temperatura
            </h3>
          </template>
          <div class="chart-area">
            <line-chart
              style="height: 100%"
              chart-id="temperature-line-chart"
              :chart-data="temperatureLineChart.chartData"
              :gradient-stops="temperatureLineChart.gradientStops"
              :extra-options="temperatureLineChart.extraOptions"
            ></line-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-4" :class="{'text-right': isRTL}">
        <card type="chart">
          <template slot="header">
            <h3 class="card-title">
              Humedad
            </h3>
          </template>
          <div class="chart-area">
            <line-chart
              style="height: 100%"
              chart-id="humidity-line-chart"
              :chart-data="humidityLineChart.chartData"
              :gradient-stops="humidityLineChart.gradientStops"
              :extra-options="humidityLineChart.extraOptions"
            ></line-chart>
          </div>
        </card>
      </div>
    </div>
    <div class="row">
      <h3>Sensor 2</h3>
    </div>
    <div class="row">
      <div class="col-lg-4" :class="{'text-right': isRTL}">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">Sensor 2</h5>
            <h3 class="card-title">
              Temperatura
            </h3>
          </template>
          <div class="chart-area">
            <line-chart
              style="height: 100%"
              chart-id="temperature-line-chart-2"
              :chart-data="temperatureLineChart2.chartData"
              :gradient-stops="temperatureLineChart.gradientStops"
              :extra-options="temperatureLineChart.extraOptions"
            ></line-chart>
          </div>
        </card>
      </div>
      <div class="col-lg-4" :class="{'text-right': isRTL}">
        <card type="chart">
          <template slot="header">
            <h5 class="card-category">Sensor 2</h5>
            <h3 class="card-title">
             Humedad
            </h3>
          </template>
          <div class="chart-area">
            <line-chart
              style="height: 100%"
              chart-id="humidity-line-chart-2"
              :chart-data="humidityLineChart2.chartData"
              :gradient-stops="humidityLineChart.gradientStops"
              :extra-options="temperatureLineChart.extraOptions"
            ></line-chart>
          </div>
        </card>
      </div>
    </div>
    <div class="row"></div>
  </div>
</template>
<script>
import LineChart from "@/components/Charts/LineChart";
import * as chartConfigs from "@/components/Charts/config";
import "chartjs-gauge";
import Pusher from "pusher-js";
import config from "@/config";

const pusher = new Pusher("30f17c740a590039031a", {
  cluster: "us2",
});

const channel = pusher.subscribe("my-channel");

export default {
  components: {
    LineChart,
  },
  data() {
    return {
      temperatureLineChart: {
        extraOptions: chartConfigs.purpleChartOptions,
        dataSeries: [],
        chartData: {
          datasets: [
            {
              label: "My second dataset",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: "rgba(255,255,255,0)",
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [],
            },
          ],
        },
        gradientColors: [
          "rgba(66,134,121,0.15)",
          "rgba(66,134,121,0.0)",
          "rgba(66,134,121,0)",
        ],
        gradientStops: [1, 0.4, 0],
      },
      humidityLineChart: {
        dataSeries: [],
        extraOptions: chartConfigs.greenChartOptions,
        chartData: {
          datasets: [
            {
              label: "My First dataset",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: "rgba(255,255,255,0)",
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [],
            },
          ],
        },
        gradientColors: [
          "rgba(66,134,121,0.15)",
          "rgba(66,134,121,0.0)",
          "rgba(66,134,121,0)",
        ],
        gradientStops: [1, 0.4, 0],
      },
      temperatureLineChart2: {
        extraOptions: chartConfigs.greenChartOptions,
        dataSeries: [],
        chartData: {
          datasets: [
            {
              label: "My second dataset",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: "rgba(255,255,255,0)",
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [],
            },
          ],
        },
        gradientColors: [
          "rgba(66,134,121,0.15)",
          "rgba(66,134,121,0.0)",
          "rgba(66,134,121,0)",
        ],
        gradientStops: [1, 0.4, 0],
      },
      humidityLineChart2: {
        dataSeries: [],
        extraOptions: chartConfigs.greenChartOptions,
        chartData: {
          datasets: [
            {
              label: "My First dataset",
              fill: true,
              borderColor: config.colors.danger,
              borderWidth: 2,
              borderDash: [],
              borderDashOffset: 0.0,
              pointBackgroundColor: config.colors.danger,
              pointBorderColor: "rgba(255,255,255,0)",
              pointHoverBackgroundColor: config.colors.danger,
              pointBorderWidth: 20,
              pointHoverRadius: 4,
              pointHoverBorderWidth: 15,
              pointRadius: 4,
              data: [],
            },
          ],
        },
        gradientColors: [
          "rgba(66,134,121,0.15)",
          "rgba(66,134,121,0.0)",
          "rgba(66,134,121,0)",
        ],
        gradientStops: [1, 0.4, 0],
      },
    };
  },
  computed: {
    enableRTL() {
      return this.$route.query.enableRTL;
    },
    isRTL() {
      return this.$rtl.isRTL;
    },
    bigLineChartCategories() {
      return this.$t("dashboard.chartCategories");
    },
  },
  methods: {
    initBigChart(index) {
      let chartData = {
        datasets: [
          {
            fill: true,
            borderColor: config.colors.primary,
            borderWidth: 2,
            borderDash: [],
            borderDashOffset: 0.0,
            pointBackgroundColor: config.colors.primary,
            pointBorderColor: "rgba(255,255,255,0)",
            pointHoverBackgroundColor: config.colors.primary,
            pointBorderWidth: 20,
            pointHoverRadius: 4,
            pointHoverBorderWidth: 15,
            pointRadius: 4,
            data: this.bigLineChart.allData[index],
          },
        ],
        labels: [
          "JAN",
          "FEB",
          "MAR",
          "APR",
          "MAY",
          "JUN",
          "JUL",
          "AUG",
          "SEP",
          "OCT",
          "NOV",
          "DEC",
        ],
      };
      //this.$refs.bigChart.updateGradients(chartData);
      this.bigLineChart.chartData = chartData;
      this.bigLineChart.activeIndex = index;
    },
    fetchData() {
      channel.bind("new-message", (data) => {
        let newTemperaturePoint = {
          t: data.fechaGeneracion,
          y: data.temperatura,
        };

        let newHumidityPoint = {
          t: data.fechaGeneracion,
          y: data.humedad,
        };
        if (data.idDispositivo == 1) {
          this.temperatureLineChart.dataSeries.push(newTemperaturePoint);
          this.humidityLineChart.dataSeries.push(newHumidityPoint);
        
        } else if (data.idDispositivo == 2) {
          this.temperatureLineChart2.dataSeries.push(newTemperaturePoint);
          this.humidityLineChart2.dataSeries.push(newHumidityPoint);
        }
          let humidityChartData = {
            datasets: [
              {
                label: "My First dataset",
                fill: true,
                borderColor: config.colors.danger,
                borderWidth: 2,
                borderDash: [],
                borderDashOffset: 0.0,
                pointBackgroundColor: config.colors.danger,
                pointBorderColor: "rgba(255,255,255,0)",
                pointHoverBackgroundColor: config.colors.danger,
                pointBorderWidth: 20,
                pointHoverRadius: 4,
                pointHoverBorderWidth: 15,
                pointRadius: 4,
                data: this.humidityLineChart.dataSeries,
              },
            ],
          };
          let temperatureChartData = {
            datasets: [
              {
                label: "My second dataset",
                fill: true,
                borderColor: config.colors.danger,
                borderWidth: 2,
                borderDash: [],
                borderDashOffset: 0.0,
                pointBackgroundColor: config.colors.danger,
                pointBorderColor: "rgba(255,255,255,0)",
                pointHoverBackgroundColor: config.colors.danger,
                pointBorderWidth: 20,
                pointHoverRadius: 4,
                pointHoverBorderWidth: 15,
                pointRadius: 4,
                data: this.temperatureLineChart.dataSeries,
              },
            ],
          };
           let humidityChartData2 = {
            datasets: [
              {
                label: "Humedad dataset",
                fill: true,
                borderColor: config.colors.danger,
                borderWidth: 2,
                borderDash: [],
                borderDashOffset: 0.0,
                pointBackgroundColor: config.colors.danger,
                pointBorderColor: "rgba(255,255,255,0)",
                pointHoverBackgroundColor: config.colors.danger,
                pointBorderWidth: 20,
                pointHoverRadius: 4,
                pointHoverBorderWidth: 15,
                pointRadius: 4,
                data: this.humidityLineChart2.dataSeries,
              },
            ],
          };
          let temperatureChartData2 = {
            datasets: [
              {
                label: "Temperatura dataset",
                fill: true,
                borderColor: config.colors.danger,
                borderWidth: 2,
                borderDash: [],
                borderDashOffset: 0.0,
                pointBackgroundColor: config.colors.danger,
                pointBorderColor: "rgba(255,255,255,0)",
                pointHoverBackgroundColor: config.colors.danger,
                pointBorderWidth: 20,
                pointHoverRadius: 4,
                pointHoverBorderWidth: 15,
                pointRadius: 4,
                data: this.temperatureLineChart2.dataSeries,
              },
            ],
          };
        this.humidityLineChart2.chartData = humidityChartData2;
        this.temperatureLineChart2.chartData = temperatureChartData2;
        this.humidityLineChart.chartData = humidityChartData;
        this.temperatureLineChart.chartData = temperatureChartData;
      });
    },
  },
  mounted() {
    this.i18n = this.$i18n;
    if (this.enableRTL) {
      this.i18n.locale = "ar";
      this.$rtl.enableRTL();
    }

    this.fetchData();
  },
  beforeDestroy() {
    if (this.$rtl.isRTL) {
      this.i18n.locale = "en";
      this.$rtl.disableRTL();
    }
  },
};
</script>
<style>
.style-chooser .vs__dropdown-toggle,
.style-chooser .vs__dropdown-menu {
  background: #389466;

  color: #ececec;
  text-transform: lowercase;
  font-variant: small-caps;
}

.style-chooser .vs__search::placeholder,
.style-chooser .vs__selected {
  color: #ececec;
}

.style-chooser .vs__dropdown-option {
  color: #ececec;
}

.style-chooser .vs__clear,
.style-chooser .vs__open-indicator {
  fill: #fde0f9;
}
</style>
