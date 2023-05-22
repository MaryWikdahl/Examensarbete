<template>
    <Bar
      :chart-options="chartOptions"
      :chart-data="chartData"
      :chart-id="chartId"
      :dataset-id-key="datasetIdKey"
      :plugins="plugins"
      :css-classes="cssClasses"
      :styles="styles"
      :width="width"
      :height="height"
    />
  </template>
  
  <script>
  import { Bar } from 'vue-chartjs/legacy'
  
  import {
    Chart as ChartJS,
    Title,
    Tooltip,
    Legend,
    BarElement,
    CategoryScale,
    LinearScale
  } from 'chart.js'
  
  ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
  
  export default {
    name: 'BarChart',
    components: {
      Bar
    },
    props: {
        result: {
        required: true
    },
      chartId: {
        type: String,
        default: 'bar-chart'
      },
      datasetIdKey: {
        type: String,
        default: 'label'
      },
      width: {
        type: Number,
        default: 400
      },
      height: {
        type: Number,
        default: 400
      },
      cssClasses: {
        default: '',
        type: String
      },
      styles: {
        type: Object,
        default: () => {}
      },
      plugins: {
        type: Array,
        default: () => []
      }
    },
    methods: {
        getLabels() {
            return Object.keys(this.result)
        },
        getData() {           
            const result = [] 
            Object.keys(this.result).forEach(k => result.push(this.result[k]));
            return result;
        }
    },
    data() {
      return {
        chartData: {
          labels: this.getLabels(),
          datasets: [
            {
            label: 'Data',
           backgroundColor:  ['#41B883', '#E46651', '#00D8FF', '#DD1B16'],
           data: this.getData()
            }
          ]
        },
         chartOptions: {
          responsive: true,
          maintainAspectRatio: false
        }
      }
    }
  }
  </script>
  