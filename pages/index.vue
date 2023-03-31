<template>
  <div class="container">
    <h1 class="text-dark text-center">dataanggota</h1>
    <NuxLinlk to="/tambah" class="btn btn-primary mb-3">Tambah</NuxLinlk>
    <button @click="logout()" class="btn btn-danger">keluar</button>
    
    <table border="1" widht="50%" class="table bg-light w-full">
      <thead>
        <tr>
          <th>#</th>
          <th>nama</th>
          <th>kelas</th>
          <th>jurusan</th>
          <th>no hp</th>
          <th>alamat</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="visitor in datas" :key="visitor.id">
          <td>{{ visitor.id }}</td>
          <td>{{ visitor.nama }}</td>
          <td>{{ visitor.kelas }}</td>
          <td>{{ visitor.jurusan }}</td>
          <td>{{ visitor.no_hp }}</td>
          <td>{{ visitor.alamat }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
definePageMeta({
  middleware: 'auth'
})


const supa = useSupabaseclient()
const supabase = useSupabaseclient()
const datas = ref([])

async function getData() {
  const { data, eror } = await supabase
  .from("dataaanggota")
  .select()
  datas.value = data
}
function logout(){
  const { error } = supa.auth.signOut()
  navigateTo("/login")
}

onMounted(() => {
  getData()
})
</script>
<style>
.p{
  margin-right: 10px;
}
</style>