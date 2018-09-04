<template>
  <v-form v-model="valid">
    <v-text-field
      v-model="member"
      :rules="memberRules"
      label="กรอกข้อมูล"
      required
    ></v-text-field>
     <v-btn color="primary" dark @click="Dosearch">ค้นหา
        <v-icon dark right>label</v-icon>
      </v-btn>
      <v-btn color="success" dark @click="Dosave">ล้างข้อมูล
        <v-icon dark right>label</v-icon>
      </v-btn>
      <div>
  <v-data-table
    :headers="headers"
    :items="desserts"
    class="elevation-1"
  >
    <template slot="items" slot-scope="props">
      <td>{{ props.item.s_id }}</td>
      <td class="text-xs-lelt">{{ props.item.s_code }}</td>
      <td class="text-xs-lelt">{{ props.item.s_name }}</td>
      <td class="text-xs-lelt">{{ props.item.s_class }}</td>
      <td class="text-xs-lelt">{{ props.item.s_group }}</td>
      
    </template>
    
    <template slot="pageText" slot-scope="props">
      Lignes {{ props.pageStart }} - {{ props.pageStop }} de {{ props.itemsLength }}
    
    </template>
  </v-data-table>
   <div>
    <v-btn color="success">เพิ่ม</v-btn>
    <v-btn color="warning">แก้ไข</v-btn>
    <v-btn color="error">ลบ</v-btn>
    </div>
  </div>
  </v-form>
</template>

<script>
export default {
  data () {
  return {
      headers: [
        {
          text: "ID",
          align: "left",
          sortable: false,
          value: "name"
        },
        { text: "Code ", value: "Code" },
        { text: "Name ", value: "Name" },
        { text: "Class ", value: "Class" },
        { text: "Group ", value: "Group" }
      ],
      desserts: []
    };
  },
  async created() {
   
   this.getstudent()
  
      
  },
  methods: {
    async Dosearch() {
      console.log(this.member);
      let res = await this.$http.post("http://127.0.0.1/php-test/search.php", {
        member: this.member
      })
      if (res.data.ok) {
        this.desserts = res.data.admin
      }
    },
    Dosave() {
      this.member = "";
    }
  }
  
}

</script>