<script lang="ts" setup>
import ActionsOrder from './ActionsOrder.vue'
import Swal from 'sweetalert2'
import { reactive } from 'vue';

const info_pedido = reactive({
  tipoPedido: null,
  nomeCliente: '',
  opcaoCarne: '',
  tipoPagamento: null,
});

const makeOrder = () => {
  Swal.fire(
    'Bom trabalho!',
    'Pedido adicionado a lista.',
    'success'
  )
  clearOrder()
}
const clearOrder = () => {
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
    <ActionsOrder 
      :info_pedido="info_pedido"
      @make_order="makeOrder"
      @cancel_order="clearOrder"
    />
  </div>
</template>