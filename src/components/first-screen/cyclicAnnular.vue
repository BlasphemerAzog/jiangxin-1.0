<template>
  <div class="cyclic-annular" :id="ids"></div>
</template>

<script>
// import ringBg from "../../assets/images/material/circle.png";
export default {
  name: "",
  props: ["ids", "chartData"],
  created() {},
  mounted() {
    this.initChart(this.ids, this.chartData);
  },
  data() {
    return {};
  },
  computed: {},
  methods: {
    initChart(chartId, chartData) {
      let myChart = this.$echarts.init(document.getElementById(chartId));
      myChart.setOption({
        grid: {
          top: "5%",
          left: "20%"
        },
        color: [
          "#5B4CFF",
          "#00F7FF",
          "#1D9DFA",
          "#0048F1",
          "#48B188",
          "#4A5D73"
        ],
        series: [
          {
            color: [
              "#5B4CFF",
              "#00F7FF",
              "#1D9DFA",
              "#0048F1",
              "#48B188",
              "#4A5D73"
            ],
            type: "pie",
            radius: ["62", "100"],
            labelLine: {
              normal: {
                length: 15,
                length2: 80,
                lineStyle: {
                  type: "solid"
                }
              }
            },
            label: {
              normal: {
                formatter: params => {
                  // console.log(params);
                  return (
                    "{b| " +
                    params.name +
                    "}  " +
                    "\n" +
                    "{c|" +
                    params.percent.toFixed(1) +
                    "%}"
                  );
                },
                borderWidth: 0,
                borderRadius: 4,
                padding: [0, -60],
                height: 70,
                fontSize: 12,
                align: "left",
                color: "#3494BD",
                rich: {
                  b: {
                    fontSize: 14,
                    lineHeight: 20,
                    color: "rgba(255,255,255,.7)",
                    padding: [15, 0, 5, 0]
                  },
                  c: {
                    fontSize: 16,
                    lineHeight: 20,
                    color: "#fff",
                    padding: [15, 0, 5, 0]
                  }
                },
                // position: "outer",
                // alignTo: "edge",
                // margin: 50
              }
            },
            data: chartData
          },
          {
            type: "pie",
            radius: ["110", "111"],
            data: [100],
            label: {
              show: false
            }
          },
          {
            type: "pie",
            radius: ["50", "51"],
            data: [100],
            label: {
              show: false
            }
          }
          // {
          //   // name: "散点",
          //   type: "scatter",
          //   // zlevel: 60,
          //   itemStyle: {
          //     opacity: 1 // 控制 满意icon的 透明度
          //   },
          //   data: [
          //     {
          //       // 外圈 点状圈
          //       value: 5,
          //       symbol: `image://${require("@/assets/images/material/circle.png")}`,
          //       symbolSize: 200
          //       // symbolOffset: [0, 0]
          //     }
          //   ],
          //   coordinateSystem: "geo",
          //   // symbolSize: 0,
          //   zlevel: 0,
          //   label: {
          //     normal: {
          //       formatter: "{b}",
          //       position: "right",
          //       show: true
          //     },
          //     emphasis: {
          //       show: true
          //     }
          //   }
          // }
        ]
      });
    }
  },
  components: {},
  watch: {
    chartData: function(newVal) {
      this.initChart(this.ids, newVal);
    }
  }
};
</script>

<style lang="less" scoped>
</style>
