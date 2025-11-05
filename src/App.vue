<script setup>
import { ref } from "vue";

// 1. ประกาศตัวแปร name มีค่าเริ่มต้นเป็น ""
const name = ref("");

// 2. ประกาศตัวแปร participants เป็น Array เปล่าสำหรับเก็บชื่อทั้งหมด
const participants = ref([]);

// 3. ฟังก์ชันเพิ่มชื่อเข้า participants
const addParticipant = () => {
  if (name.value.trim() !== "") {
    participants.value.push(name.value.trim());
    name.value = ""; // เคลียร์ช่อง input หลังเพิ่มชื่อ
  }
};
</script>

<template>
  <div class="assignment-container">
    <h2>รายชื่อผู้เข้าร่วมกิจกรรม</h2>

    <!-- 4. ใช้ v-model เพื่อผูกค่ากับ name -->
    <input v-model="name" placeholder="กรอกชื่อผู้เข้าร่วม" />

    <!-- 5. เรียกใช้ addParticipant ตอนคลิก -->
    <button @click="addParticipant">เพิ่มชื่อ</button>

    <div class="participant-list" style="margin-top: 1rem">
      <!-- 6. ถ้ายังไม่มีชื่อเลย -->
      <p v-if="participants.length === 0">ยังไม่มีผู้เข้าร่วม</p>

      <!-- 7. ถ้ามีชื่อ -->
      <ul v-else>
        <!-- 8. ใช้ v-for ลูปแสดงรายชื่อ -->
        <li v-for="(p, index) in participants" :key="index">
          {{ index + 1 }}. {{ p }}
        </li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
.assignment-container {
  max-width: 400px;
  margin: auto;
  padding: 12px;
  border-radius: 8px;
  background: #d3f0fc;
}
button {
  margin-left: 8px;
}
</style>