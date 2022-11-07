<template>
    <img :width="`${width}px`" :src="`http://localhost:1337${src}`" :alt="alt">
</template>

<script>
export default {
    props: {
        width: 0,
        height: 0,
        src: '',
        alt: ''
    }
}
</script>