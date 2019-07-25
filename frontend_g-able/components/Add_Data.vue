<template>
  <v-layout row justify-center>
    <v-dialog v-model="dialog" persistent max-width="450">
      <v-btn slot="activator" color="green darken-1" dark>Add Data</v-btn>
      <v-card>
        <v-card-title class="title" >กรอก Collect_code ของข้อมูลที่คุณต้องการลบ
            {{ Collect_code }}
        </v-card-title>
        <v-container >
          <v-layout row wrap>
            <v-flex xs12>
                <v-text-field label="รหัสการจัดเก็บ" required></v-text-field>
              </v-flex>
            <v-flex >
              <v-select
              :items="item"
              item-text="Name_product"
              v-model="Add_data_body.Id_product"
              item-value="Id_product"
              label="ชื่อสินค้า"
              ></v-select>
            </v-flex>
            <v-flex >
              <v-select
              :items="barnch"
              item-text="Branch_Name"
              v-model="Add_data_body.Branch_id"
              item-value="Branch_id"
              label="ชื่อสาขา"
              ></v-select>
            </v-flex>
            <v-flex xs12>
                <v-text-field label="จำนวน" required></v-text-field>
              </v-flex>
          </v-layout>
        </v-container>
        <v-card-actions>
       <v-btn color="error"  @click.native="dialog = false">ยกเลิก</v-btn>
       <v-btn color="green darken-1"  @click="deletes">ยืนยัน</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-layout>
</template>

<script>
  export default {
    data: () => ({
      item: null,
      barnch: null,
      dialog: false,
      Collect_code: null,
      Add_data_body:  {Collect_id:null,Branch_id: null,Id_product: null,Quantity: null},


    }),
    async created() {
      var datas = await this.$http.get(`/product/find/all`);
      var data2 = await this.$http.get(`/branch/find/all`);
      this.item = datas.data
      this.barnch = data2.data
      console.log('dsfgh', this.barnch)
    },
    methods: {
      async deletes() {
        console.log(this.Add_data_body);
        this.dialog = false
      },
    },
  }
</script>
