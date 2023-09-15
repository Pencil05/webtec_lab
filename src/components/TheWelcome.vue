<template>
  <div>
    <h2 class="text-2xl mb-4">รายละเอียดการจอง</h2>
    <div class="bg-white p-4 border rounded-lg">
      <div>
        <strong>ชื่อ:</strong> {{ reservation.name }}
      </div>
      <div>
        <strong>เบอร์โทร:</strong> {{ reservation.phone }}
      </div>
      <div>
        <strong>วันที่:</strong> {{ reservation.date }}
      </div>
      <div>
        <strong>เวลา:</strong> {{ reservation.time }}
      </div>
      <div>
        <strong>จำนวนโต๊ะ:</strong> {{ reservation.tableCount }}
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const reservation = ref(null); // เก็บข้อมูลการจองโต๊ะ

// สร้างฟังก์ชันสำหรับรับข้อมูลการจอง
function setReservation(data) {
  reservation.value = data;
}
</script>

<style scoped>
/* เสริมสไตล์ CSS ตามที่ต้องการ */
</style>
