<template>
  <div class="container">
    <nav>
      <h1>Adote seu Pet</h1>
      <ul>
        <a href="" @click.prevent="componenteAtivo = 'Animais'"
          ><li>Home</li></a
        >
        <a href="" @click.prevent="componenteAtivo = 'Fotos'"><li>Fotos</li></a>
        <a href="" @click.prevent="componenteAtivo = 'AjudeNos'"
          ><li>Doações</li></a
        >
      </ul>
    </nav>
    <div class="pages">
      <transition mode="out-in">
        <components :is="componenteAtivo"></components>
      </transition>
    </div>
    <footer>
      <div>
        <h2>Contato</h2>
        <strong>E-mail: </strong><a href=""> adocao@adocao.com </a>
        <p><strong>Contato: </strong> (11) 2025-3797</p>
      </div>
      <div>
        <h2>Localização</h2>
        <p>Avenida Brasil, n° 107</p>
        <p>São Paulo - SP</p>
      </div>
      <div>
        <p>Nos ajude doando qualquer valor.</p>
        <a href="" @click.prevent="componenteAtivo = 'AjudeNos'">Ajude-nos aqui</a>
      </div>
    </footer>
  </div>
</template>

<script>
import Animais from "./componentes/Animais.vue";
import Fotos from "./componentes/Fotos.vue";
import AjudeNos from "./componentes/AjudeNos.vue";

export default {
  name: "app",
  data() {
    return {
      componenteAtivo: Animais,
    };
  },
  components: {
    Animais,
    Fotos,
    AjudeNos,
  },
};
</script>

<style>
* {
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}

.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  font-family: "Roboto";
}

a {
  text-decoration: none;
  color: #fff;
}

nav {
  grid-column: 1 / 5;
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: #b83133;
  color: #fff;
  padding: 30px;
}

nav h1 {
  font-size: 2.5rem;
}

ul {
  display: flex;
  list-style: none;
}

ul li {
  font-size: 1.25rem;
  color: #fff;
  margin-right: 30px;
  transition: all 0.3s;
  transform: skewY(-3deg);
}

ul li:hover {
  border-bottom: 1px solid #ddd;
}

footer {
  grid-column: 1 / 5;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 1rem;
  background: #b83133;
  color: #fff;
  padding: 30px;
  position: relative;
  bottom: 0px;
  width: 100%;
  text-align: center;
}

footer p {
  margin-top: 10px;
}

footer a:last-child {
  font-weight: bold;
}

.pages {
  grid-column: 1 / 5;
}

.v-enter-active,
.v-leave-active {
  transition: all 0.3s;
}

.v-enter,
.v-leave-to {
  opacity: 0;
  transform: translate3d(-30px, 0px, 0px);
}

@media (max-width: 760px) {
  nav {
    display: grid;
    grid-template-columns: 1fr;
    text-align: center;
  }

  nav h1 {
    margin-bottom: 10px;
  }

  ul {
    text-align: center;
    margin: 0 auto;
  }

  footer {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
  }

  footer div:last-child {
    grid-column: 1 / 5;
    padding: 20px;
    line-height: 25px;
  }
}
</style>
