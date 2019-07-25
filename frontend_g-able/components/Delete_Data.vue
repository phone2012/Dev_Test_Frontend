<template>
  <v-layout row justify-center>
    <v-dialog v-model="dialog" persistent max-width="450">
      <v-btn slot="activator" color="error" dark>Delete Data</v-btn>
      <v-card>
        <v-card-title class="title" >กรอก รหัสการจัดเก็บ ของข้อมูลที่คุณต้องการลบ
            {{ Collect_code }}
        </v-card-title>
        <v-container >
          <v-layout row wrap>
            <v-flex >
              <v-select
              :items="item"
              item-text="Collect_id"
              v-model="Collect_code"
              item-value="Collect_id"
              label="รหัสการจัดเก็บ"
              ></v-select>
            </v-flex>
          </v-layout>
        </v-container>
        <v-card-actions>
       <v-btn color="green darken-1" flat @click.native="dialog = false">ยกเลิก</v-btn>
       <v-btn color="green darken-1" flat @click="deletes">ยืนยัน</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-layout>
</template>

<script>
  export default {
    data: () => ({
      item: null,
      dialog: false,
      Collect_code: null

    }),
    async created() {
      var datas = await this.$http.get(`/collect_product/find/all`);
      this.item = datas.data
      console.log('dsfgh', this.item)
    },
    methods: {
      async deletes() {
        await this.$http.delete(`/collect_product/delete/${this.Collect_code}`);
        this.dialog = false
      },
    },
  }
</script>
