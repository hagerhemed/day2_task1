<template>
<div>
  <navbarComponent class="mb-3"/>
  <studentsComponent/>
  <footerComponent class="mt-3"/>

 </div>
</template>

<script>
import navbarComponent from '@/components/navbarComponent'
import footerComponent from '@/components/footerComponent'
import studentsComponent from '@/components/studentsComponent'

export default {
    data:()=>({}),
    method:{},
    components:{
        navbarComponent,footerComponent,studentsComponent
    }
    

}
</script>

<style>

</style>