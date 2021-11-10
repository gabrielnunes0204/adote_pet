<template>
  <section>
    <h1 class="titulo_fotos">Confira algumas fotos de nossos Pets</h1>
    <div class="fotos">
      <div @click="nomeCachorros">
        <span class="modal">
          <h1>Esse é o <strong>Thor</strong></h1>
        </span>
        <img src="../assets/dog1.png" alt="Cachorro 1" />
        <figcaption id="fig1"></figcaption>
      </div>
      <div @click="nomeCachorros">
        <span class="modal">
          <h1>Esse é o <strong>Bob</strong></h1>
        </span>
        <img src="../assets/dog2.png" alt="Cachorro 2" />
        <figcaption id="fig2"></figcaption>
      </div>
      <div @click="nomeCachorros">
        <span class="modal">
          <h1>Essa é a <strong>Luna</strong></h1>
        </span>
        <img src="../assets/dog3.png" alt="Cachorro 3" />
        <figcaption id="fig3"></figcaption>
      </div>
      <div @click="nomeCachorros">
        <span class="modal">
          <h1>Essa é a <strong>Lola</strong></h1>
        </span>
        <img src="../assets/cat1.png" alt="Gato 1" />
        <figcaption id="fig4"></figcaption>
      </div>
      <div @click="nomeCachorros">
        <span class="modal">
          <h1>Esse é o <strong>Max</strong></h1>
        </span>
        <img src="../assets/dog4.png" alt="Cachorro 4" />
        <figcaption id="fig5"></figcaption>
      </div>
      <div @click="nomeCachorros">
        <span class="modal">
          <h1>Essa é a <strong>Pandora</strong></h1>
        </span>
        <img src="../assets/cat2.png" alt="Gato 2" />
        <figcaption id="fig6"></figcaption>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Fotos",
  methods: {
    nomeCachorros(event) {
      const nomeDog = event.currentTarget.children[0];
      nomeDog.style.display = "block";
      setTimeout(() => {
        nomeDog.style.display = "none";
      }, 2000);
    },
  },
};
</script>

<style>
.titulo_fotos {
  font-size: 2.5rem;
  letter-spacing: 1.5px;
  text-align: center;
  padding: 30px;
}

.fotos {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.fotos img {
  width: 100%;
  z-index: 1;
}

.fotos div {
  display: inline-block;
  position: relative;
}

.fotos figcaption {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  transition: all 1s;
  background: rgba(0, 0, 0, 0.5);
}

.fotos #fig1:hover {
  background: url("../assets/dog1-2.png") no-repeat;
  background-size: 100%;
  cursor: pointer;
}

.fotos #fig2:hover {
  background: url("../assets/dog2-2.png") no-repeat;
  background-size: 100%;
  cursor: pointer;
}

.fotos #fig3:hover {
  background: url("../assets/dog3-2.png") no-repeat;
  background-size: 100%;
  cursor: pointer;
}

.fotos #fig4:hover {
  background: url("../assets/cat1-2.png") no-repeat;
  background-size: 100%;
  cursor: pointer;
}

.fotos #fig5:hover {
  background: url("../assets/dog4-2.png") no-repeat;
  background-size: 100%;
  cursor: pointer;
}

.fotos #fig6:hover {
  background: url("../assets/cat2-2.png") no-repeat;
  background-size: 100%;
  cursor: pointer;
}

.modal {
  position: absolute;
  top: -50px;
  left: 0;
  width: 100%;
  border: 1px solid rgba(0, 0, 0, 0.5);
  padding: 10px;
  text-align: center;
  background: #fff;
  display: none;
}

.modal h1 {
  font-weight: normal;
}

@media (max-width: 760px) {
  .titulo_fotos {
    font-size: 2rem;
  }

  .fotos {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 500px) {
  .fotos {
    grid-template-columns: 1fr;
  }

  .fotos img {
    width: 80%;
  }

  .fotos div {
    display: inline-block;
    position: relative;
    text-align: center;
    margin-bottom: 10px;
  }

  .fotos figcaption {
    position: absolute;
    top: 0;
    left: 49px;
    width: 80%;
    height: 83.5vh;
    background: rgba(0, 0, 0, 0.3);
  }

  .modal {
    width: 80%;
    left: 48px;
  }
}
</style>
