<template>
    <div>
        <div class="image-container">
            <span :class="fontawesome"></span>
        </div>
        <div class="decription-container">
            <p class="description">
                {{description}}
            </p>
        </div>
    </div>
    
</template>

<script>
export default{
    props: ['fontawesome', 'description']
}
</script>

<style scoped>
.cards-container{
    text-align: center;
    box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.25);
    -webkit-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.25);
    -moz-box-shadow: 0px 0px 4px 0px rgba(0,0,0,0.25);
    border-bottom: 0.5rem solid #00b6e6;
}
.image-container{
    background-color: #00b6e6;
    color: #ffffff;
    padding: 4rem 0;
}
.image-container .fas{
    font-size: 4rem;
}
.decription-container{
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem;
    min-height: 120px;
    font-weight: 600;
}
.description{
    margin: 0;
}
</style>

<style>
    .slick-slide{
        padding: 0.5rem 1.5rem;
    }
</style>