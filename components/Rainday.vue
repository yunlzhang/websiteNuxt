<template>
    <img src="" alt="" id="rainyday">
</template>

<script>
import {instantiationEngine} from '../static/js/rain_engine'
let instant;
export default {
    name:'Rainday',
    mounted(){
        this.$nextTick(function(){
            instant = instantiationEngine();  
        })
    },
    beforeDestroy(){
        console.log('ranin destroy');
        if(typeof instant === 'object'){
            instant.engine.destroy();
            instant = null;
        }
    }
}
</script>

<style scope lang="scss">
    #rainyday{
        visibility:hidden;
        width: 100%;
        height: 100%;
        position:fixed;
        left:-10000000px;
    }
</style>
