<template>
  <v-layout
    column
    justify-center
    align-center
  >
    <v-flex
      xs12
      sm10
      md10
    >
      <v-card>
        <v-card-title class="headline">
          Web Application for Managing Inventory of Products
        </v-card-title>
        <v-card-actions>
          <v-flex xs12>
     <v-select
       :items="items"
       :menu-props="{ top: true, offsetY: true }"
       v-model="branch_id"
       item-text="Branch_Name"
       item-value="Branch_id"
       label="เลือกสาขา"
     ></v-select>
   </v-flex>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
           @click="sendValue">
            show
          </v-btn>
        </v-card-actions>
      </v-card>
      <v-card>
        <v-container >
          <v-layout row wrap>
            <v-flex xs12 v-if="show_table">
              <Table
              :items="datas_Product"
              />
            </v-flex>
          </v-layout>
        </v-container>
        <v-card-actions v-if="show_table">
            <v-spacer />
            <v-flex xs6 md3>
              <Add/>
            </v-flex>
            <v-flex xs6 md3>
            <Delete/>
            </v-flex>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
 import Table from '~/components/Table_Product.vue'
 import Delete from '~/components/Delete_Data.vue'
 import Add from '~/components/Add_Data.vue'

export default {
  data: () => ({
      items: undefined,
      item: null,
      branch_id: null,
      datas: [],
      datas_Product: [],
      show_table: false,
    }),
  components: {
    Table,
    Delete,
    Add
  },
  async created() {

    this.item = await this.$http.get(`/branch/find/all`);
    this.items = this.item.data
  },
  methods: {
    async sendValue() {
      this.show_table = true
      this.datas = await this.$http.get(`/collect_product/find/id/${this.branch_id}`);
      this.datas_Product = this.datas.data
    },
  },
}
</script>
