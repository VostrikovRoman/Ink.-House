<template>
    <div class="card">
        <img class="painting" :src="image">
        <p class="text autor">{{autor}}</p>
        <p class="text name">{{name}}</p>
        <p class="text material">{{material}}</p>
        <p class="text price">{{price}} руб</p>
        <button class="butt butt_take">В корзину</button>
    </div>
</template>

<script setup>
import {defineProps} from 'vue'

defineProps({
  image: String,
  autor: String,
  name: String,
  material: String,
  price: Number
})



</script>

<style>
.card{
    background: var(--lightgreen);
    display: inline-block;
    padding: 15px;
    margin: 20px;
}
.painting{
    width: 100%;
}
.text.autor{
    color: var(--gray);
    font-size: 15px;
    font-weight: bold;
}
.text.name{
    font-weight: bold;
    font-size: 25px;
}
.text.material{
    font-weight: bold;
    font-size: 15px;
}
.text.price{
    color: var(--green);
    font-size: 20px;
    font-weight: bold;
}
.butt.butt_take{
    width: 100%;
}
</style>