<template>
  <div>
    <CRow>
      <CCol sm="12">
        <CTableWrapper
          :items="getShuffledUsersData()"
          hover
          striped
          border
          table-filter
          small
          fixed
          caption="Listado de Productos"
        />
      </CCol>
    </CRow>
  </div>
</template>

<script>
import CTableWrapper from './Table'
import axios from "axios";
export default {
  data () {
    return {
      productos: null
    }
  },
  mounted () {
    axios.get('https://localhost:44341/api/Productos')
        .then(resp => {this.productos = resp.data});
  },
  name: 'Productos',
  tableFilter:true,
  components: { CTableWrapper },
  methods: {
    getShuffledUsersData () {
      return this.productos
    }
  }
}
</script>
