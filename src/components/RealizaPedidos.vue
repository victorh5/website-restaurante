<script lang="ts" setup>
import { reactive } from 'vue'

const informacoesIniciais = {
  tipoPedido: null,
  nomeCliente: '',
  opcaoCarne: '',
  tipoPagamento: null,
}

const cliente = reactive({...informacoesIniciais})

function realizaPedido() {
  console.log(cliente)
}
function cancelaPedido() {
  Object.assign(cliente, informacoesIniciais)
}
</script>

<template>
  <div id="realiza-pedidos">
    <div class="informacoes-pedidos">
      <p>Qual vai ser o tipo de pedido?</p>
      <input type="radio" value="Marmitex" v-model="cliente.tipoPedido">
      <label for="marmitex">Marmitex</label>
      <input type="radio" value="Marmita" v-model="cliente.tipoPedido">
      <label for="marmita">Marmita</label>
      <p>Qual seu nome?</p>
      <input type="text" v-model="cliente.nomeCliente">
      <p>Qual sua opção de carne?</p>
      <input type="text" v-model="cliente.opcaoCarne">
      <p>Qual tipo do pagamento?</p>
      <select v-model="cliente.tipoPagamento">
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