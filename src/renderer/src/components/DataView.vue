<script setup>
import DataTable from 'datatables.net-vue3'
import DataTablesCore from 'datatables.net'
import languageKO from 'datatables.net-plugins/i18n/ko.json'
import { ref } from 'vue'
import { db } from '../firebase'
import { collection, query, orderBy, onSnapshot } from "firebase/firestore";
import { format } from 'date-fns'
import { ko } from 'date-fns/esm/locale'
import Swal from 'sweetalert2'

//datatable
DataTable.use(DataTablesCore)

//initialize of firestore
const colRef = collection(db, "appointments")
const q = query(colRef, orderBy('createdAt', 'asc'))
const aptRef = ref([])
let appointments = aptRef.value
const options = {
  responsive: true,
  select: true,
  language: languageKO,
}

const unsubscribe = onSnapshot(q, (snap) => {
  snap.docChanges().forEach((change) => {
    let changedata = change.doc.data()

    //DateTime Conversion
    let preDate = changedata.createdAt.toDate()
    if (preDate) {
      // changedata.createdAt = formatDistance(preDate, new Date(), { locale: ko})
      changedata.createdAt = format(preDate, " MM월dd일p", { locale: ko })
    }

    //when new appointment add
    changedata.id = change.doc.id
    if (change.type === "added") {
      appointments.unshift(changedata)
      Swal.fire(`${changedata.name}, ${changedata.phone}, ${changedata.createdAt} 신청! `)
    }
    if (change.type === "modified") {
      let index = appointments.findIndex(apt => apt.id === changedata.id)
      Object.assign(appointments[index], changedata)
    }
    if (change.type === "removed") {
      let index = appointments.findIndex(apt => apt.id === changedata.id)
      appointments.splice(index, 1)
    }
  })
},
  (error) => {
    console.log(error)
  }
)

const columns = [
  { data: 'createdAt' },
  { data: 'name' },
  { data: 'jumin' },
  { data: 'history' },
  { data: 'memo' },
  { data: 'phone' },
  { data: 'why' },
  { data: 'email' },
]

</script>

<template>
  <DataTable class="display" :columns="columns" :data="aptRef" :options="options">
    <thead>
      <tr>
        <th>날짜</th>
        <th>이름</th>
        <th>주민번호</th>
        <th>재진?</th>
        <th>메모</th>
        <th>핸드폰</th>
        <th>내용</th>
        <th>이메일</th>
      </tr>
    </thead>
    <tfoot>
      <tr>
        <th>날짜</th>
        <th>이름</th>
        <th>주민번호</th>
        <th>재진?</th>
        <th>메모</th>
        <th>핸드폰</th>
        <th>내용</th>
        <th>이메일</th>
      </tr>
    </tfoot>
  </DataTable>
</template>
<style>
@import 'datatables.net-dt';
@import 'datatables.net-bs5';
@import '../../../../node_modules/sweetalert2/dist/sweetalert2.min.css'
</style>