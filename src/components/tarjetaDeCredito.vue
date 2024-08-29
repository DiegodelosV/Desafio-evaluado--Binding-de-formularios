<script>
export default {
  name: "tarjetaDeCredito",
  data() {
    return {
      tarjeta: {
        tituloDeLaTarjeta: "",
        chipSRC: "../src/assets/img/chip.png",
        numero: "",
        fechaDeExpiracion: "",
        propietario: "",
        tipoDeTarjetaSRC: "../src/assets/img/visa.png",
      },
    };
  },
  // metodo para aplicar el formato de separación de los digitos y los espacios
  methods: {
    aplicarFormatoNumero() {
      let valor = this.tarjeta.numero.replace(/ /g, "");
      // formato separación cada 4 digitos con uso de expresiones regulares
      valor = valor.replace(/(\d{4})/g, "$1 ");
      this.tarjeta.numero = valor;
    },
  },
};
</script>
<template>
  <body>
    <div id="app">
      <form>
        <div>
          <label>Título de la tarjeta: </label>
          <input v-model="tarjeta.tituloDeLaTarjeta" />
        </div>

        <div>
          <label>Chip SRC: </label>
          <input v-model="tarjeta.chipSRC" />
        </div>

        <div>
          <label>Número: </label>
          <!-- se aplica el metodo aplicarFormatoNumero -->
          <input
            v-model="tarjeta.numero"
            @input="aplicarFormatoNumero" 
            maxlength="19"
          />
        </div>

        <div>
          <label>Fecha de expiración: </label>
          <input
            v-model="tarjeta.fechaDeExpiracion"
            type="month"
            min="2022-01"
            placeholder="MM/AA"
            maxlength="5"
          />
        </div>

        <div>
          <label>Propietario: </label>
          <input v-model="tarjeta.propietario" />
        </div>

        <div>
          <label>Tipo de tarjeta SRC: </label>
          <input v-model="tarjeta.tipoDeTarjetaSRC" />
        </div>
      </form>

      <div class="carnet">
        <h3>{{ tarjeta.tituloDeLaTarjeta }}</h3>
        <img width="40px" :src="tarjeta.chipSRC"   alt="chip src" />
        <div>
          <h2>{{ tarjeta.numero }}</h2>
          <span
            >Fecha Exp: <b>{{ tarjeta.fechaDeExpiracion }}</b></span
          >
        </div>
        <footer>
          <span>{{ tarjeta.propietario }}</span>
          <img :src= "tarjeta.tipoDeTarjetaSRC" width="60" />
        </footer>
      </div>
    </div>
  </body>
</template>
