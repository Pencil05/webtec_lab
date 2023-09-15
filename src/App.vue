<template class="hello">
  <div class="hello">
    <header class="bg-success text-white p-3 text-center">
      <h1 class="text-3xl">ร้าน Coffee</h1>
    </header>

    <main class="container mx-auto p-4">
      <div class="grid grid-cols-2 gap-4">
        <div v-for="(cafe, index) in cafes" :key="index" class="bg-white p-4 border rounded-lg">
          <!-- เพิ่มคลาส text-center เพื่อจัดให้รูปภาพและข้อความอยู่กึ่งกลาง -->
          <div class="text-center">
            <img src="src\playerRight.png" alt="" class="mx-auto mb-2" style="width: 150px; height: 150px;">
            <h2 class="text-xl">{{ cafe.name }}</h2>
          <p>{{ cafe.description }}</p>
          <button @click="reserveTable(index)" class="bg-info text-white px-2 py-1 mt-2">จองโต๊ะ</button>
        </div>
        </div>
      </div>
    </main>

    <!-- ส่วนแสดงผลรายละเอียดการจอง -->
    <section v-if="reservation" class="container mx-auto p-4">
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
    </section>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const cafes = ref([
      {
        name: 'ร้านกาแฟ A',
        description: 'ร้านกาแฟที่มีประวัติมานานกว่า200ปี',
      },
      {
        name: 'ร้านกาแฟ B',
        description: 'ร้านกาแฟเปิดใหม่ โปรโมชั่นลดราคาทุกแก้ว95%',
      },
    ]);

    const reservation = ref(null);

    function reserveTable(index) {
      const name = prompt('ชื่อผู้จอง:');
      const phone = prompt('เบอร์โทรศัพท์:');
      const date = prompt('วันที่:');
      const time = prompt('เวลา:');
      const tableCount = prompt('จำนวนโต๊ะ:');

      setReservation({ name, phone, date, time, tableCount });
    }

    function setReservation(data) {
      reservation.value = data;
    }

    return {
      cafes,
      reservation,
      reserveTable,
    };
  },
};
</script>

<style>
* {
  font-family: itim;
  margin: 0;
  padding: 0;
}
.grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 1rem;
}
.hello h1{
  font-size: 60px;
}
button{
  width: 180px;
}
</style>
