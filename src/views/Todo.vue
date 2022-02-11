<template>
  <v-container>
  
    <h1>การบ้าน/งานที่ได้รับมอบหมาย</h1>

    เพิ่มงาน

    <v-select :items="items" label="--กรุณาเลือกหัวข้อ--" dense solo></v-select>
    <v-text-field
      v-model="work"
      label="รายการ"
      placeholder="รายการ"
      outlined
      dense
    ></v-text-field>
    <v-btn class="mr-4" @click="addTodo()"> เพิ่ม </v-btn>

    <v-container>
      <h1>รายการที่เพิ่ม</h1>
      <v-list dense>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-list-item v-for="(item, i) in additems" :key="i">
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title v-text="item.text"></v-list-item-title>
            </v-list-item-content>
            <!-- <v-btn color="warning">ลบ</v-btn> -->
            <v-btn
              class="ma-2"
              fab
              dark
              small
              color="error"
              @click="deleteTodo(i)"
            >
              <v-icon dark>mdi-minus</v-icon>
            </v-btn>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-container>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      subject:"",
      work:"",
      items: ["วิชา web", "วิชา SA", "วิชาML", "อิ่นๆ"],
      selectedItem: 1,
      additems: [
        // { text: 'วิชา web Assingment500', icon: 'mdi-clock' },ใส่ไอคอน
        { text: "วิชา web Assingment500" },
        { text: "วิชา SA Assingment1" },
        { text: "วิชาML ออกแบบ" },
      ],
    };
  },
  methods: {
    addTodo() {
      // console.log("click add todo") ;
      // เพิ่มข้อมูล --> array
      console.log(this.subject+this.work);
      this.additems.push({ text: this.subject + " " + this.work });
    },
    deleteTodo(index) {
      this.additems.splice(index, 1);
    },
  },
};
</script>

<style></style>