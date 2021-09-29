<template>
<div class="chart">
  <canvas id="threeRatesChart"></canvas>
</div>
</template>

<script>
import Chart from 'chart.js';

const ratesData =   {
    "unprecio": [
        {
        "0-23": 0.123
        }
    ],
    "dosprecios": [
        {
        "0-13": 0.079
        },
        {
        "14-23": 0.155
        }
    ],
    "3.0a": [
        {"0-7": 0.055},
        {"8-12": 0.082},
        {"13-16": 0.190},
        {"17-20": 0.078},
        {"21-23": 0.045}
    ]
}

export default {
  name: 'daily-rates-chart',
    data() {
        return {
        lineChartData: {
            unprecio: [
              {"0-23": 0.123}],
            dosprecios: [
              {"0-13": 0.079}, 
              {"14-23": 0.155}],
            "3.0a": [
              {"0-7": 0.055},
              {"8-12": 0.082},
              {"13-16": 0.19},
              {"17-20": 0.078},
              {"21-23": 0.045},
            ],
        },
        unprecio: [],
        dosprecios: [],
        threeZeroA: []
        };
    },
    mounted() {
        this.unprecio = this.setupRatesData(ratesData.unprecio);
        this.dosprecios = this.setupRatesData(ratesData.dosprecios);  
        this.threeZeroA = this.setupRatesData(ratesData["3.0a"]);
        this.createLineChart("threeRatesChart", this.setRatesData(this.unprecio, this.dosprecios, this.threeZeroA));
  },
    methods: {
    setupRatesData: function(range) {
          var datarates = [];
          var num = range.length;
          for (var i = 0; i < num; i++) {
            let obj = range[i];
            let first = Object.keys(obj)[0];
            let second = Object.values(obj)[0];
            let z = first.split('-', 2);
            
            for (var y = 0; y <= z[1] - z[0]; y++){
                datarates.push({"y": Number(second).toFixed(3) });
            }
          }
         return datarates;
      },
    createLineChart(chartId, lineChartData) {
      const ctx = document.getElementById(chartId);
      new Chart(ctx, {
        type: lineChartData.type,
        data: lineChartData.data,
        options: {
          title: {
            display: true,
            text: "",
            padding: 30,
          },
          legend: {
            position: "bottom",
            labels: {
              padding: 60,
              boxWidth: 25,
              fontFamily: "system-ui",
            },
          },
          layout: {
            padding: {
              right: 50,
            },
          },
          tooltips: {
            backgroundColor: "#c2c2c2",
            titleFontSize: 16,
            titleFontColor: '#fff',
            bodyFontColor: '#000',
            bodyFontSize: 14,
            displayColors: false,
          },
          elements: {
            line: {
              borderWidth: 8,
              fill: false,
            },
            point: {
              radius: 6,
              borderWidth: 4,
              hoverRadius: 8,
              hoverBorderWidth: 4,
            },
          },
          responsive: true,
          maintainAspectRatio: true,
          lineTension: 1,
          scales: {
            yAxes: [
              {
                ticks: {
                  beginAtZero: true,
                  padding: 25,
                },
              },
            ],
          },
        },
      });
    },
    setRatesData(dataRatesOne, dataRatesTwo, dataRatesThree) {
      this.labels = Object.keys(this.lineChartData);
      return {
        type: "line",
        data: {
          labels: [0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23],
          datasets: [
            {
              label: this.labels[0],
              data: dataRatesOne,
              borderColor: ["#b3005d"],
              borderWidth: 4,
            },
            {
              label: this.labels[1],
              data: dataRatesTwo,
              borderColor: ["#c8c0ab"],
              borderWidth: 4,
            },
            {
              label: this.labels[2],
              data: dataRatesThree,
              borderColor: ["#296c89"],
              borderWidth: 4,
            },
          ],
        },
        
      };
    },
  },
  
}
</script>