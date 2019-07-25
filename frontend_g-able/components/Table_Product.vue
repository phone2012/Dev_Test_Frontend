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
  console.log('12345',this.desserts);
  }
},
  }
</script>


<!-- <template>
  <v-layout row wrap>
  <v-data-table
    :headers="headers"
    :items="data3"
    hide-actions
    class="elevation-1"
  >
    <template slot="item" slot-scope="props">
       <td>{{ prop.items.branch.Branch_id }}</td>
      <td class="text-xs-right">{{ props.items.Branch_Name }}</td>
      <td class="text-xs-right">{{ props.items.product.Id_product }}</td>
      <td class="text-xs-right">{{ props.items.product.Id_product }}</td>
      <td class="text-xs-right">{{ props.items.product.Price_product }}</td>
    </template>
  </v-data-table>
    <v-flex xs12>

      <v-card>

      </v-card>
    </v-flex>
  </v-layout>
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
            text: 'BRANCH_ID',
            align: 'left',
            sortable: false,
            value: 'Branch_id'
          },
          { text: 'Branch_Name', value: 'Branch_Name' },
          { text: 'Id_product', value: 'Id_product' },
          { text: 'Name_product', value: 'Name_product' },
          { text: 'Price_product', value: 'Price_product' }
        ],
        data2: {
            Branch_id: null,
            Branch_Name: null,
            Id_product: null,
            Name_product: null,
            Price_product: null,
          },
        data3: [],
        data8: [{
            Name_product: null,
            Price_product: null,
          },{
              Name_product: null,
              Price_product: null,
            },{
                Name_product: null,
                Price_product: null,
              },{
                  Name_product: null,
                  Price_product: null,
                },{
                    Name_product: null,
                    Price_product: null,
                  },],
        data4:{},
        data5: {
            Name_product: null,
            Price_product: null,
          },
      }
    },
    watch: {
     items: async function() {
      var i;
     for (i = 0; i < this.items.length; i++) {
         this.data3.push(this.data5);
      }
       this.test();
      console.log('55555555555555',this.data3);
      for (i = 0; i < this.items.length; i++) {
        this.data4 = this.items[i]
        this.data3[i].Name_product = this.data4.product.Name_product
        this.data3[i].Price_product = this.data4.product.Price_product
        console.log(this.data3);

        this.test();
        this.data5.Name_product = this.data4.product.Name_product
        this.data5.Price_product = this.data4.product.Price_product
        console.log(this.data4);
        console.log(this.data5);
      }
      for (var key in this.items) {
        var data4 = this.items[key]
        this.data2.Branch_id = data4.BRANCH_ID
        this.data2.Branch_Name = data4.branch.Branch_Name
        this.data2.Id_product = data4.product.Id_product
        this.data2.Name_product = data4.product.Name_product
        this.data2.Price_product = data4.product.Price_product
        this.data5.Name_product = data4.product.Name_product
        this.data5.Price_product = data4.product.Price_product
        console.log(this.data2);
        console.log(this.data5);
        console.log(this.data3.push(this.data2));
        this.data3.push(this.data2);
    }
    console.log(this.data3);
    }
  },
  methods: {
    test() {
      console.log('4444444',this.data3);
      console.log('5555555555',this.data8);
      var l
      for (l = 0; l < this.items.length; l++) {
        this.data4 = this.items[l]
       this.data8[l].Name_product = this.data4.product.Name_product
       this.data8[l].Price_product = this.data4.product.Price_product
       this.data3[l].Name_product = this.data8[l].Name_product
       this.data3[l].Price_product = this.data8[l].Price_product
       console.log(this.data3);
       console.log(this.data8);
    }
    },
  },
}
</script> -->
