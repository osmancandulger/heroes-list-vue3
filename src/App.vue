<template>
<AppHeader />
 <div class="w-full flex" >
<DcHeroes />
</div>
</template>
<script>

import AppHeader from "./components/AppHeader.vue";
import DcHeroes from "./components/DcHeroes.vue";
export default {
  name:"App",
  components:{AppHeader,DcHeroes},
  
  
  

}
</script>

<style>

</style>