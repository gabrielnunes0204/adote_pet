<template>
  <section>
    <div class="bloco">
      <div>
        <h1>Nos chame para adotar um animalzinho</h1>
        <h2>Eles estão te esperando</h2>
        <label for="email"> E-mail: </label>
        <input type="email" id="email" placeholder="Seu e-mail" />
        <button @click="enviarMensagem">Enviar</button>
      </div>
      <img src="../assets/dogs.jpg" alt="Cachorro" />
    </div>
    <h2 class="porqueAdotar">Porque adotar?</h2>
    <div class="quemSomos">
      <div>
        <strong>Neste exato momento</strong>
        existem milhares de doguinhos e gatinhos esperando um humano para chamar de seu.
      </div>
      <div>
        <strong>E não há recompensa maior</strong>
        do que vê-los se tornando aquela coisinha alegre e saudável depois de uma boa dose de cuidado e carinho.
      </div>
      <div>
        <strong>Pensando bem, a pergunta é outra:</strong>
        se você pode mudar o destino de um animal de rua, por que não faria isso?
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Animais",
  methods: {
    enviarMensagem() {
      const mensagem = document.querySelector("input");
      if (mensagem.value === '' || !mensagem.value.includes("@")) {
          alert('Preencha o campo corretamente');
      } else {
        alert('E-mail enviado, fique atento que entraremos em contato.');
        mensagem.value = '';
      }
    }
  }
};
</script>

<style>
section {
  display: grid;
  grid-template: repeat(4, 1fr);
}

section .bloco {
  grid-column: 1 / 5;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  align-items: center;
  padding: 30px;
  text-align: center;
}

.bloco h1 {
  font-size: 2.25rem;
}

.bloco h2 {
  font-size: 1.5rem;
  font-weight: normal;
  margin-bottom: 50px;
}

.bloco label {
  display: block;
  font-size: 1.5rem;
  margin-bottom: 5px;
}

.bloco input {
  display: block;
  font-size: 1.25rem;
  border: 1px solid rgba(0, 0, 0, 0.5);
  padding: 16px 8px;
  width: 50%;
  margin: 15px auto;
  outline: 0;
}

.bloco button {
  font-size: 1.25rem;
  letter-spacing: 1.5px;
  background: #b83133;
  color: #fff;
  border: none;
  border: 1px solid #fff;
  padding: 12px;
  width: 50%;
  transition: all 0.3s;
  cursor: pointer;
}

.bloco button:hover {
  background: #fff;
  color: #b83133;
  border: 1px solid #b83133;
  transform: scale(1.1);
}

.bloco img {
  max-width: 90%;
  border-radius: 50%;
}

.porqueAdotar {
  grid-column: 1 / 5;
  font-size: 2.5rem;
  text-align: center;
}

.quemSomos {
  grid-column: 1 / 5;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  text-align: justify;
  margin: 0 auto;
  padding: 10px;
}

.quemSomos div {
  border: 1px solid rgba(0, 0, 0, 0.2);
  font-size: 1rem;
  line-height: 35px;
  padding: 20px;
  margin: 10px;
}

@media(max-width: 760px) {
  section .bloco {
    display: grid;
    grid-template-columns: 1fr;
  }

  .bloco button {
    margin-bottom: 25px;
  }

  .bloco img {
    border-radius: 50%;
  }

  .quemSomos {
    display: grid;
    grid-template-columns: 1fr;
  }
}
</style>
