<template>
     <div>
        <section id="top">
            <div class="graphics" id="graphic">
                <img src="~/assets/city_2.jpg" />
            </div>
            <div class="words" id="words">
                <h1 class="words__header">
                    Ahorra con tu plan de energía
                </h1>
                <div class="words__body">
                    Tu tarifa eléctrica depende de las necesidades que tengas y de la hora en que desarrolles tu actividad. Paga lo justo cuando lo necesitas.
                </div>
                <div class="words__link">
                    <a @click="scrollMeTo('gorates')">↓↓ Conoce nuestras tarifas </a>
                </div>
            </div>
        </section>
        <section ref="gorates" id="blockRates">
            <div class="block__heading">
                <h3 class="block__title">Te presentamos nuestra tarifas</h3>
                    <div class="block__description">
                        <p class="block__description-bigger">
                        Dependiendo de tu situación, puedes ahorrar mucho dinero si eliges el plan de energía adecuado.
                        Disponemos de distintos planes energéticos con distintos precios según la hora del día.
                        </p>
                        <p>
                        Este gráfico muestra el precio de cada tarifa según su hora. Te permite ver que tarifa se adapta a tus necesidades y que tienes que tener en cuenta para optimizar tu ahorro.
                        </p>
                        <ul>
                            <li><strong>UNPRECIO</strong>: El más simple es "unprecio". Tiene un solo período: paga el mismo precio todo el día.</li>    
                            <li><strong>DOSPRECIOS</strong>: Entonces tenemos una opción más inteligente que es "dosprecios". Tiene un precio de 13h a 23h y otro precio el resto del día.</li> 
                            <li><strong>3.0a</strong>: Finalmente, las empresas pueden beneficiarse de "3.0a". Presenta múltiples períodos de tiempo con diferentes precios.</li> 
                        </ul>
                    </div>
                <daily-rates-chart></daily-rates-chart>
            </div>
        </section>
    </div>
    
</template>
<script>
import DailyRatesChart from '~/components/DailyRatesChart';


export default {
  name: 'app',
  components: {
    DailyRatesChart
  },
  mounted: function()
  {
    setTimeout(() => this.scrollFix(this.$route.hash), 1);
  },
  methods: {
    scrollFix: function(hashbang)
    {
      location.hash = hashbang;
    },
     scrollMeTo(refName) {
        var element = this.$refs[refName];
        var top = element.offsetTop;

        window.scrollTo(0, top);
    }
  }
}

</script>

<style lang="scss">
section#top {
    height: 93vh;
    display: flex;
    flex-direction: row;
}

.graphics
    img {
        width: 100%;
        height: 93vh;
    }
.words, .graphics {
    width: 50%;
}
.words {
    display: flex;
    flex-direction: column;
    background: white;
    color: black;
    padding: 2vw 2vw 0 2vw;

    .words__header {
        font-size: 2.8rem;
        line-height: 2.8rem;
        margin-bottom: 10px;
    }
    .words__body {
        font-size: 2.3rem;
        line-height: 2.5rem;
    }
    .words__link {
        padding-top: 5%;
        a {
            font-size: 2rem;
            color: $gray-dark;
            cursor: pointer;
            &:hover{
                text-decoration: underline;
            }
        }
    }
}

section#blockRates {
    margin: 0 auto;
    padding: 5% 10%;
    min-height: 400px;
    background: #F6F6F6;
}
.block__heading {
    padding: 0 5%;
    .block__title {
        font-size: 2rem;
        font-weight: 400;
        margin-bottom: 2%;
    }
    .block__description-bigger {
        font-weight: bolder;
    }
}

@media (max-width: 768px) {
    section#top {
        display: flex;
        flex-direction: column;    
    }
    .graphics {
        width: 100%;
    }
    .words { 
        width: 100%;
        padding: 5%;
        position: absolute;
        .words__header {
            font-size: 1.8rem;
            line-height: 1.5rem;
            padding-bottom: 3%;
        }
        .words__body {
            font-size: 1.2rem;
            line-height: 1.3rem;
        }
        .words__link {
            a {
                font-size: 1.2rem;
                line-height: 1.3rem;
            }
        }
    }
    section#blockRates {
        padding: 0;
    }
    .block__heading {
        .block__title {
            font-size: 1.8rem;
            padding: 7% 0 3% 0;
            line-height: 1.8rem;
        }
    }
}

</style>
