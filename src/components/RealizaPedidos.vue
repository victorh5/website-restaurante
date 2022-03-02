<script lang="ts" setup>
import Swal from 'sweetalert2'
// import axios from 'axios';
import { reactive } from 'vue';

const info_pedido = reactive({
  tipoPedido: null,
  nomeCliente: '',
  opcaoCarne: '',
  tipoPagamento: null,
});

async function realizaPedido() {
  // const response = await axios.post("/realizar-pedido", info_pedido)
  Swal.fire(
  'Bom trabalho!',
  'Pedido adicionado a lista.',
  'success'
)
}
function cancelaPedido() {
  Object.assign(info_pedido, {
    tipoPedido: null,
    nomeCliente: '',
    opcaoCarne: '',
    tipoPagamento: null,
  })
}
</script>

<template>
  <div id="realiza-pedidos">
    <div class="informacoes-pedidos">
      <p>Qual vai ser o tipo de pedido?</p>
      <input type="radio" value="Marmitex" v-model="info_pedido.tipoPedido">
      <label for="marmitex">Marmitex</label>
      <input type="radio" value="Marmita" v-model="info_pedido.tipoPedido">
      <label for="marmita">Marmita</label>
      <p>Qual seu nome?</p>
      <input type="text" v-model="info_pedido.nomeCliente">
      <p>Qual sua opção de carne?</p>
      <input type="text" v-model="info_pedido.opcaoCarne">
      <p>Qual tipo do pagamento?</p>
      <select v-model="info_pedido.tipoPagamento">
        <option>Dinheiro</option>
        <option>PIX</option>
        <option>Cartão</option>
        <option>Convênio</option>
      </select>
    </div>
    <div class="acoes-pedido">
      <button @click="realizaPedido">Realizar Pedido</button>
      <button @click="cancelaPedido">Cancelar Pedido</button>
    </div>
  </div>
</template>