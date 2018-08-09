<template>
    <div>
        <Top></Top>
        <Qtzz></Qtzz>   
        <Bottom></Bottom>
    </div>
</template>
<script>
import Top from '../public/Top';
import Bottom from '../public/Bottom';
import Qtzz from '../public/Qtzz';
export default {
    name:"Index",
    data(){
        return {

        }
    },
    components:{
        Top,Bottom,Qtzz
    }
}
</script>
<style scpend lang="scss">

</style>
