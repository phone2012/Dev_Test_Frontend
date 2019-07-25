<template>
  <v-data-table
    :headers="headers"
    :items="desserts"
    hide-actions
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.Branch_id }}</td>
      <td>{{ props.item.Collect_id }}</td>
      <td>{{ props.item.Branch_Name }}</td>
      <td>{{ props.item.Id_product }}</td>
      <td>{{ props.item.Name_product }}</td>
      <td>{{ props.item.Price_product }}</td>
      <td>{{ props.item.Quantity }}</td>
    </template>
  </v-data-table>
</template>

<script>
  export default {
    props: {
      items: {
        type: Array,
        default: () => [],
      },
    },
    data () {
      return {

        headers: [
          {
            text: 'Branch_id',
            align: 'left',
            sortable: false,
            value: 'Branch_id'
          },
          { text: 'Collect_code', sortable: false, value: 'Collect_id' },
          { text: 'Branch_Name', sortable: false, value: 'Branch_Name' },
          { text: 'Id_product', sortable: false, value: 'Id_product' },
          { text: 'Name_product', sortable: false, value: 'Name_product' },
          { text: 'Price_product', sortable: false, value: 'Price_product' },
          { text: 'Quantity', sortable: false, value: 'Quantity' }
        ],
        desserts: [
          {
            Collect_id:null,
            Branch_id: null,
            Branch_Name: null,
            Id_product: null,
            Name_product: null,
            Price_product: null,
            Quantity: null,
            },
          {
            Collect_id:null,
            Branch_id: null,
            Branch_Name: null,
            Id_product: null,
            Name_product: null,
            Price_product: null,
            Quantity: null,
            },
          {
            Collect_id:null,
            Branch_id: null,
            Branch_Name: null,
            Id_product: null,
            Name_product: null,
            Price_product: null,
            Quantity: null,
            },
          {
            Collect_id:null,
            Branch_id: null,
            Branch_Name: null,
            Id_product: null,
            Name_product: null,
            Price_product: null,
            Quantity: null,
            },
          {
            Collect_id:null,
            Branch_id: null,
            Branch_Name: null,
            Id_product: null,
            Name_product: null,
            Price_product: null,
            Quantity: null,
            },
          {
            Collect_id:null,
            Branch_id: null,
            Branch_Name: null,
            Id_product: null,
            Name_product: null,
            Price_product: null,
            Quantity: null,
            },
      ]
    }
  },
  watch: {
   items: async function() {
     for (var key in this.desserts) {
        this.desserts[key].Collect_id = null
       this.desserts[key].Branch_id = null
       this.desserts[key].Branch_Name = null
       this.desserts[key].Id_product = null
       this.desserts[key].Name_product = null
       this.desserts[key].Price_product = null
       this.desserts[key].Name_product = null
       this.desserts[key].Price_product = null
       this.desserts[key].Quantity = null
   }
    for (var key in this.items) {
      var data4 = this.items[key]
      this.desserts[key].Collect_id = data4.Collect_id
      this.desserts[key].Quantity = data4.Quantity
      this.desserts[key].Branch_id = data4.BRANCH_ID
      this.desserts[key].Branch_Name = data4.branch.Branch_Name
      this.desserts[key].Id_product = data4.product.Id_product
      this.desserts[key].Name_product = data4.product.Name_product
      this.desserts[key].Price_product = data4.product.Price_product
  }
  }
},
  }
</script>
