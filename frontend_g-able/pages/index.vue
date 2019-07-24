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
        <v-card-text>
            {{ branch_id }}
            {{ datas.data }}
        </v-card-text>
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
            flat
            nuxt
           @click="sendValue">
            show
          </v-btn>
        </v-card-actions>
      </v-card>
      <v-card>
        <v-card-title class="headline">

        </v-card-title>
        <v-card-actions>
          <v-flex xs12>
            <Table/>
          </v-flex>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
// import Logo from '~/components/Logo.vue'
 import Table from '~/components/Table_Product.vue'

export default {
  data: () => ({
      items: null,
      item: null,
      branch_id: null,
      datas: [],
    }),
  components: {
    // Logo,
    Table,
    // VuetifyLogo
  },
  async created() {
    // console.log('created')
    //const result = await this.$axios.$get(`/team/hierarchy?team_id=${COOKIES.userInfo.ams.team_id}`);
    this.item = await this.$http.get(`/branch/find/all`);
    this.items = this.item.data
    console.log(this.item.data)
  },
  methods: {
    async sendValue() {
      this.datas = await this.$http.get(`/collect_product/find/id/${this.branch_id}`);
    },
  },
}
</script>
