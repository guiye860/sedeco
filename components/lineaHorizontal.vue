<template>
    <div>
        <Bar :chartData="datacollection" :options="options" />
    </div>
</template>

<script>
import Bar from '~/assets/js/Bar.js'

export default {
  props:{
    etiquetas: Array,
    titulo: String,
    prices: Array,
  },
  components: {
    Bar
  },
  data () {
      return {
          colores: ['#4ecdc4','#ff6b6b','#247ba0','#ff1654','#e55934','#247ba0','#ffe066','#50514f','#70c1b3','#06d6a0','#118ab2'],
          options: {responsive: true, maintainAspectRatio: false, legend: {position: 'right',}},
      }
  },
  computed: {
    datacollection: function(){
      let _etiquetas = this.etiquetas;

      let obj = {labels: [], datasets: []},
      datasetChild = {label:'', backgroundColor:'', data: []};

      [...obj.labels] = _etiquetas;
//      obj.datasets = (this.prices.length) ? this.prices.map(e => e.precios) : [datasetChild];
      [...obj.datasets] = (this.prices.length) ? this.prices[0].precios : [datasetChild];
      return obj;

    }
  },
}
</script>
