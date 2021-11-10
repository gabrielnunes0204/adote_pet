<template>
  <div>
    <h1 class="titulo_contato">Entre em contato conosco</h1>
    <form>
      <h2>Nos ajude com doações</h2>
      <div>
        <article>
          <label for="nome"> Nome: </label>
          <input type="text" id="nome" class="dadosForm" placeholder="Nome" />
        </article>

        <article>
          <label for="email"> E-mail: </label>
          <input
            type="email"
            id="email"
            class="dadosForm"
            placeholder="E-mail"
          />
        </article>

        <article>
          <label for="cep"> CEP: </label>
          <input
            type="text"
            id="cep"
            maxlength="9"
            class="dadosForm"
            placeholder="xxxxx-xxx"
            @click="puxarCEP"
          />
        </article>

        <article>
          <label for="endereco"> Endereço: </label>
          <input
            type="text"
            id="endereco"
            class="dadosForm"
            placeholder="Rua Tal, 17"
            disabled
          />
        </article>

        <article class="textarea">
          <label for="mensagem"> Deixa sua mensagem </label>
          <textarea
            id="mensagem"
            class="dadosForm"
            placeholder="Como gostaria de colaborar?"
          ></textarea>
        </article>
        <button class="botaoForm" @click.prevent="validarFormulario">
          Enviar
        </button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "AjudeNos",
  data() {
    return {
      nomeRua: "",
    };
  },
  methods: {
    validarFormulario() {
      const dadosForm = document.querySelectorAll(".dadosForm");
      const arrayDados = Array.from(dadosForm);

      if (arrayDados[0].value === "") {
        alert("Preencha o campo de nome corretamente");
      } else if (
        arrayDados[1].value === "" ||
        !arrayDados[1].value.includes("@")
      ) {
        alert("Preencha o campo de e-mail corretamente");
      } else if (arrayDados[2].value === "") {
        alert("Preencha o campo de CEP corretamente");
      } else if (arrayDados[3].value === "") {
        alert("Preencha o campo de endereço corretamente");
      } else if (arrayDados[4].value === "") {
        alert("Preencha o campo da mensagem corretamente");
      } else {
        alert("Muito obrigado pela colaboração. Retornaremos seu contato.");
        arrayDados[0].value = "";
        arrayDados[1].value = "";
        arrayDados[2].value = "";
        arrayDados[3].value = "";
        arrayDados[4].value = "";
      }
    },
    puxarCEP() {
      const cep = document.querySelector("#cep");
      const endereco = document.querySelector("#endereco");
      cep.addEventListener("change", () => {
        if (cep.value === "") {
          endereco.value = "Erro";
        } else {
          const url = `https://viacep.com.br/ws/${cep.value}/json/`;
          fetch(url).then((response) => {
            response.json().then((body) => {
              this.nomeRua = body.logradouro;
              endereco.value = this.nomeRua;
            });
          });
        }
      });
    },
  },
};
</script>

<style>
.titulo_contato {
  padding: 30px;
  text-align: center;
}

form {
  border: 1px solid #000;
  box-shadow: 1px 1px 8px rgba(0, 0, 0, 0.5);
  padding: 30px;
  margin: 20px auto;
  width: 650px;
}

form div {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}

form h2 {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-size: 1.25rem;
}

input {
  font-family: "Roboto";
  font-size: 1rem;
  padding: 8px;
  width: 90%;
  margin-bottom: 15px;
  outline: 0;
}

.textarea {
  grid-column: 1 / 3;
  margin-bottom: 15px;
}

.textarea textarea {
  font-family: "Roboto";
  font-size: 1rem;
  padding: 10px;
  width: 95%;
  height: 100px;
  outline: 0;
}

.botaoForm {
  grid-column: 1 / 3;
  font-family: "Roboto";
  font-size: 1.25rem;
  letter-spacing: 1.5px;
  background: #b83133;
  color: #fff;
  border: none;
  width: 50%;
  padding: 12px;
  margin: 0 auto;
  transition: all 0.3s;
  cursor: pointer;
}

.botaoForm:hover {
  background: #fff;
  color: #b83133;
  border: 1px solid #b83133;
  transform: scale(1.1);
}

@media (max-width: 660px) {
  form {
    width: 400px;
  }

  form div {
    grid-template-columns: 1fr;
  }

  form article {
    grid-column: 1 / 3;
  }

  input,
  .textarea textarea,
  .botaoForm {
    width: 100%;
  }

  #cep {
    width: 50%;
  }
}
</style>
