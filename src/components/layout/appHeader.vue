<script setup>
defineProps({
    showBack: Boolean,
    showCart: Boolean,
    showMenu: Boolean,
})

import { ref } from 'vue'
import { useRouter } from 'vue-router'
import SvgIcon from '@jamescoyle/vue-icon'
import { mdiCart, mdiMenu, mdiArrowLeft } from '@mdi/js'
const router = useRouter()

const mdiCartIcon = ref(mdiCart)
const mdiMenuIcon = ref(mdiMenu)
const mdiArrowLeftIcon = ref(mdiArrowLeft)

</script>
<template>
<header>
    <ul class="container">
    <li>
        <button class="menu-hamburguer icon" v-if="showMenu">
            <SvgIcon type="mdi" :path="mdiMenuIcon" />
        </button>
    </li>
    <li>
        <button @click="router.back()" class="voltar icon" v-if="showBack">
            <SvgIcon type="mdi" :path="mdiArrowLeftIcon" />
        </button>
    </li>
    <li>
        <p><img src="/public/Logo.png" alt="Terroir Café" class="logo" /></p>
    </li>
    <li>
        <button @click="router.push('/cart')" class="carrinho icon" v-if="showCart">
            <SvgIcon type="mdi" :path="mdiCartIcon" />
        </button>
    </li>
    </ul>
</header>
</template>
<style scoped>
header{
    background-color: #74403E;
    height: 100px;
}

.container{
    display: flex;
    justify-content: space-around;
    align-items: center;
    list-style: none;
    padding: 20px;
}

.icon{
    text-decoration: none;
    background-color: transparent;
    border: none;
    padding: 10px;
    color:#fff;
}

.logo{
    width: 250px;
    height: auto;
}

</style>