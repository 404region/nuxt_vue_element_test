<template>
  <div>
    <NavVue/>
    <DataTable/>
  </div>
</template>
<script>
import DataTable from '../components/DataTable.vue';
  export default {
    name: "IndexPage",
    components: { DataTable }
}
</script>
