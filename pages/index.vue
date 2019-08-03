<template>
<section class="hero is-fullheight">

  <div class="hero-head">
    <nav class="navbar">
      <div class="container">
        <div class="navbar-brand">
          <a class="navbar-item">
            <span class="icon is-large">
              <i class="fas fa-chart-bar fa-3x"></i>
            </span>
          </a>
          <span class="navbar-burger burger" data-target="navbarMenuHeroB">
            <span></span>
            <span></span>
            <span></span>
          </span>
        </div>
        <div id="navbarMenuHeroB" class="navbar-menu">
          <div class="navbar-end">
            <a class="navbar-item is-active">
              Home
            </a>
            <a class="navbar-item">
              Examples
            </a>
            <a class="navbar-item">
              Documentation
            </a>
            <span class="navbar-item">
              <a class="button is-info is-inverted">
                <span class="icon">
                  <i class="fab fa-github"></i>
                </span>
                <span>Download</span>
              </a>
            </span>
          </div>
        </div>
      </div>
    </nav>
  </div>

  <div class="hero-body">
    <div class="container has-text-centered">
      <div class="columns is-vcentered">
        <div class="column">
          <div class="columns is-vcentered">
            <div class="column has-text-right">
              <span class="icon is-large">
                <i class="fas fa-lg fa-chart-bar"></i>
              </span>
            </div>
            <div class="column is-narrow">
              <p class="is-size-1 has-text-weight-bold">
                Monitoreo de la canasta básica
              </p>
            </div>
            <div class="column">
              <p class="subtitle">
                Según la SEDECO
              </p>
            </div>
          </div>
        </div>
      </div>
      <grafico-lineal
      :etiquetas="['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo']"
      :prices="prices"
      />
    </div>
  </div>

  <div class="hero-foot">
    <nav class="tabs is-boxed is-fullwidth">
      <div class="container">
        <ul class="menu">
          <li class="is-active">
            <a @click="getPreciosCanastaBasicaPorCodigo(0, this)">Panificados</a>
          </li>
          <li>
            <a @click="getPreciosCanastaBasicaPorCodigo(1, this)">Granel</a>
          </li>
          <li>
            <a @click="getPreciosCanastaBasicaPorCodigo(2, this)">Cárnicos</a>
          </li>
          <li>
            <a @click="getPreciosCanastaBasicaPorCodigo(3, this)">Almacén</a>
          </li>
          <li>
            <a @click="getPreciosCanastaBasicaPorCodigo(4, this)">Queso y lácteos</a>
          </li>
          <li>
            <a @click="getPreciosCanastaBasicaPorCodigo(5, this)">Domisanitarios</a>
          </li>
          <li>
            <a @click="getPreciosCanastaBasicaPorCodigo(6, this)">Frutas y verduras</a>
          </li>
        </ul>
      </div>
    </nav>
  </div>
</section>
<!-- -->

</template>

<script>
import Logo from "~/components/Logo.vue";
import graficoLineal from "~/components/lineaHorizontal.vue";

export default {
  components: {
    Logo,
    graficoLineal
  },
  data() {
    return {
      datos:[]
    }
  },
  mounted(){
    this.getPreciosCanastaBasicaPorCodigo(0, 0);
    document.addEventListener("click", 
    function(e)
      {
        if(e.target.localName === 'a' && e.target.parentNode.parentNode.className === 'menu'){
          document.querySelector("ul.menu li.is-active").classList.remove("is-active");
          e.target.parentNode.classList.add('is-active');
          console.log(e.target)
        }
      }
    )

  },
  computed:
  {
    prices: function(){
      return this.datos;
    }
  },
  methods: 
  {
    getPreciosCanastaBasicaPorCodigo: function(codigo, elemento){
      
      
      let precios = [
        {
          categoria: "Panificado",
          precios: [
            {label: "Pan Felipito", backgroundColor: "#4ecdc4", borderColor: "#4ecdc4", fill: false, data: [4141,4075,4048,4108,4080] , },
            {label: "Galleta", backgroundColor: "#ff6b6b", borderColor: "#ff6b6b", fill: false, data: [5113,4650,4736,4583,4750] , },
            {label: "Coquito", backgroundColor: "#247ba0", borderColor: "#247ba0", fill: false, data: [8625,8525,8679,8842,8856] , },
          ]
        },
        {
          categoria: "Granel",
          precios: [
            {label:'Poroto Rojo (Kg.)' ,backgroundColor:'#4ecdc4', borderColor: '#4ecdc4' ,fill: false, data:[8325,8398,9050,10200,11510], },
            {label:'Arroz (Kg.)' ,backgroundColor:'#ff6b6b', borderColor: '#ff6b6b' ,fill: false, data:[2594,2445,2459,2429,2485], },
            {label:'Azúcar (Kg.)' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[4650,4602,4646,4675,4659], },
            {label:'Harina (Kg.)' ,backgroundColor:'#ff1654', borderColor: '#ff1654' ,fill: false, data:[2742,2667,2742,2717,2757], },
          ]
        },
        {
          categoria: "Cárnicos",
          precios: [
            {label:'Puchero de primera  (Kg.)' ,backgroundColor:'#4ecdc4', borderColor: '#4ecdc4' ,fill: false, data:[10910,14579,15348,13583,14600], },
            {label:'Puchero de segunda (Kg.)' ,backgroundColor:'#ff6b6b', borderColor: '#ff6b6b' ,fill: false, data:[5491,5518,5376,6151,6368], },
            {label:'Costilla de Primera (Kg.)' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[25797,23058,23528,23458,25403], },
            {label:'Carnaza de Primera (Kg.)' ,backgroundColor:'#ff1654', borderColor: '#ff1654' ,fill: false, data:[33244,33385,33235,32667,33223], },
            {label:'Carnaza de Segunda (Kg.)' ,backgroundColor:'#e55934', borderColor: '#e55934' ,fill: false, data:[22745,22366,21924,22233,21865], },
            {label:'Vacio (Kg.)' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[31742,29065,28586,28842,31055], },
            {label:'Pierna de cerdo (Kg.)' ,backgroundColor:'#ffe066', borderColor: '#ffe066' ,fill: false, data:[16363,15843,15432,15033,14705], },
            {label:'Pollo entero  (Kg.)' ,backgroundColor:'#50514f', borderColor: '#50514f' ,fill: false, data:[10588,9688,10053,10067,9935], },
            {label:'Pechuga de Pollo (kg.)' ,backgroundColor:'#70c1b3', borderColor: '#70c1b3' ,fill: false, data:[11625,12600,11080,11075,10385], },
          ]
        },
        {
          categoria: "Almacén",
          precios: [
            {label:'Yerba Mate (Paq. 1 Kl.)' ,backgroundColor:'#4ecdc4', borderColor: '#4ecdc4' ,fill: false, data:[13925,14183,13478,14054,14012], },
            {label:'Aceite de soja - 900cc' ,backgroundColor:'#ff6b6b', borderColor: '#ff6b6b' ,fill: false, data:[8073,7788,8046,8071,7355], },
            {label:'Huevos de gallina (1/2doc.)' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[4022,4398,5089,5008,4573], },
            {label:'Sal Fina (500 gr.)' ,backgroundColor:'#ff1654', borderColor: '#ff1654' ,fill: false, data:[2209,2177,2213,2193,2240], },
          ]
        },
        {
          categoria: "Queso y Lácteos",
          precios: [
            {label:'Leche sachet - 1lt' ,backgroundColor:'#4ecdc4', borderColor: '#4ecdc4' ,fill: false, data:[3949,4118,3886,3992,4028], },
            {label:'Lecha larga vida - 1 lt.' ,backgroundColor:'#ff6b6b', borderColor: '#ff6b6b' ,fill: false, data:[5121,4779,4781,4904,5003], },
            {label:'Yogurt - 350 gr.' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[3513,3550,3525,3550,3523], },
            {label:'Queso Paraguay (Kg.)' ,backgroundColor:'#ff1654', borderColor: '#ff1654' ,fill: false, data:[23772,21345,23721,27871,27560], },
          ]
        },
        {
          categoria: "Domisanitarios",
          precios: [
            {label:'Detergente (1/2 lt.)' ,backgroundColor:'#4ecdc4', borderColor: '#4ecdc4' ,fill: false, data:[2938,2937,2901,3025,3248], },
            {label:'Lavandina (1 lt)' ,backgroundColor:'#ff6b6b', borderColor: '#ff6b6b' ,fill: false, data:[3259,3464,3464,3583,3210], },
            {label:'Jabón en polvo (400 gr.)' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[5688,5725,5602,5833,6087], },
          ]
        },
        {
          categoria: "Frutas y verduras",
          precios: [
            {label:'Naranja (Kg.)' ,backgroundColor:'#4ecdc4', borderColor: '#4ecdc4' ,fill: false, data:[3931,4750,4455,4179,4362], },
            {label:'Banana karape (Kg.)' ,backgroundColor:'#ff6b6b', borderColor: '#ff6b6b' ,fill: false, data:[4125,4057,4428,4041,3435], },
            {label:'Locote (Kg.)' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[5184,9233,6753,9353,10833], },
            {label:'Zanahoria (Kg.)' ,backgroundColor:'#ff1654', borderColor: '#ff1654' ,fill: false, data:[4116,5847,6082,5692,6045], },
            {label:'Tomate Sta. Cruz (Kg.)' ,backgroundColor:'#e55934', borderColor: '#e55934' ,fill: false, data:[7791,10633,10001,10017,12015], },
            {label:'Mandioca (Kg.)' ,backgroundColor:'#247ba0', borderColor: '#247ba0' ,fill: false, data:[2400,2000,1977,1742,1628], },
            {label:'Cebolla (Kg.)' ,backgroundColor:'#ffe066', borderColor: '#ffe066' ,fill: false, data:[4141,4489,5009,4733,5125, ]}
          ]
        }

      ];
      [...this.datos] = [precios[codigo]];
    }
  }
};
</script>