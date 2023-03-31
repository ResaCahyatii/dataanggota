<template>
  <div>
    <h1>isi dataanggota</h1>
    <from @submit.prevent="simpan()">
      <input v-model="nama" placeholder="nama" /> <br />
      <input v-model="kelas" placeholder="kelas" /> <br />
      <input v-model="jurusan" placeholder="jurusan" /> <br />
      <input v-model="no_hp" placeholder="no hp" /> <br />
      <textarea v-model="alamat" placeholder="alamat"></textarea> <br />
      <button type="submit">kirim</button>
      <nuxtlink to="/">kembali</nuxtlink>
    </from>
  </div>
</template>

<script setup>
definePageMeta({
  middleware: 'auth'
})
const nama = ref()
const kelas = ref()
const jurusan = ref()
const no_hp = ref()
const alamat = ref()

async function simpan() {
  await supabase
  from("dataanggota");
  Insert({
    nama: nama.value,
    kelas: kelas.value,
    jurusan: jurusan.value,
    no_hp: no_hp.value,
    alamat: alamat.value,
  })
  navigateTo("/")
}
</script>