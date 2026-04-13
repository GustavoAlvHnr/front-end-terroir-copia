<script setup>
import { onMounted, ref } from 'vue'
import appHeader from '@/components/layout/appHeader.vue';
import { useProdutosStore } from '@/stores/produtos';
import Loading from 'vue-loading-overlay';

import { mdiArrowDownDropCircleOutline, mdiArrowLeftDropCircleOutline } from '@mdi/js';
import svgIconVue from '@jamescoyle/vue-icon';

const produtosStore = useProdutosStore()
const mdiArrowDownIcon = ref(mdiArrowDownDropCircleOutline)
const mdiArrowLeftIcon = ref(mdiArrowLeftDropCircleOutline)

const open = ref(false)

onMounted(() => {
  produtosStore.fetchProdutos()
})
</script>

<template>
  <appHeader show-menu show-cart />
  <main class="container">
    <div class="banner">
      <Loading v-model:active="produtosStore.loading" is-full-page/>
      <h2>placeholder</h2>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Quis non corporis veritatis incidunt ullam, esse deleniti accusamus, veniam iste unde mollitia blanditiis libero inventore animi aliquam perferendis molestias enim explicabo.
      </p>
    </div>
    <div class="lista-produtos">
      <h2>Em destaque <svgIconVue type="mdi" :path="mdiArrowLeftIcon" v-if="open"/> <svgIconVue type="mdi" :path="mdiArrowDownIcon" v-else/></h2>
      <div class="produtos">
        <Loading v-model:active="produtosStore.loading" is-full-page/>
        <!-- Aqui vão os produtos em destaque -->
         <div v-for="produto in produtosStore.produtos" :key="produto.id" class="produto">
          <img :src="produto.imagem_url" :alt="produto.nome" class="imagem-produto"/>
          <h3>{{ produto.nome }}</h3>
          <p>{{ produto.descricao }}</p>
          <p class="preco">R$ {{ produto.preco }}</p>
          <button>Adicionar ao carrinho</button>
         </div>
      </div>
    </div>
  </main>
</template>
<style scoped>
main{
    margin-top: 30px;
}
.lista-produtos h2{
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-top: 10px;
  padding: 10px;
  font-size: 24px;
  background-color: #74403e;
  border-radius: 56px;
  color: #fff;
}

</style>
