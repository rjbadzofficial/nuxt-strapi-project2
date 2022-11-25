<template>
    <img :width="`${width}px`" :src="getMedia(src)" :alt="alt">
</template>

<script>
import { getMedia } from '~/utils/media'
export default {
    props: {
        width: 0,
        height: 0,
        src: '',
        alt: ''
    },
    methods: {
        getMedia
    }
}
</script>