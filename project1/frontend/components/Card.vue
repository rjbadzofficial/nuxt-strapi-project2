<template>
    <div class="cards-container">
        <div class="image-container">
            <span :class="card.fontawesome"></span>
        </div>
        <p>
            {{card.description}}
        </p>
    </div>
    
</template>

<script>
export default{
    props: ['card']
}
</script>

<style scoped>
.cards-container{
    text-align: center;
}
.image-container{
    background-color: #00b6e6;
    color: #ffffff;
}
.image-container .fas{
    font-size: 4rem;
}
</style>