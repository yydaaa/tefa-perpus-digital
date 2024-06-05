<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row py-5 justify-content-around">
        <div class="col-lg-5">
          <nuxt-link to="/pengunjung/tambah" class="text-decoration-none">
            <div class="card bg-pengunjung rounded-5">
              <div class="card-body">
                <h2 class="text-center text-light" style="margin-top: 80px;">Pengunjung</h2>
              </div>
            </div>
          </nuxt-link>
        </div>
        <div class="col-lg-5">
          <nuxt-link to="/buku" class="text-decoration-none">
            <div class="card bg-buku rounded-5">
              <div class="card-body">
                <h2 class="text-center text-light"  style="margin-top: 80px;">Pencarian Buku</h2>
              </div>
            </div>
          </nuxt-link>
        </div>
        <div class="col-lg-12">
          <h2 class="text-center my-4">RIWAYAT PENGUNJUNG</h2>
          <div class="my-3">
            <form @submit.prevent="getPengunjung">
              <input v-model="keyword" type="search" class="form-control form-control-lg rounded-5" placeholder="Cari..." @input="getPengunjung" />
            </form>
          </div>
          <div class="my-3 text-muted">menampilkan 1 dari 1</div>
          <div class="table-responsive">

            <table class="table table-striped border-dark">
              <thead>
                <tr>
                  <td>NO</td>
                  <td>NAMA</td>
                  <td>KEANGGOTAAN</td>
                  <td>TINGKAT</td>
                  <td>JURUSAN</td>
                  <td>KELAS</td>
                  <td>KEPERLUAN</td>
                  <td>TANGGAL</td>
                  <td>WAKTU</td>
                </tr>
              </thead>
  
              <tbody>
                <tr v-for="(visitors,i) in visitors" :key="i">
                  <td>{{ i+1 }}.</td>
                  <td>{{ visitors.nama }}</td>
                  <td>{{ visitors.keanggotaan.nama }}</td>
                  <td>{{ visitors.tingkat}}</td>
                  <td>{{ visitors.jurusan }}</td>
                  <td>{{ visitors.kelas }}</td>
                  <td>{{ visitors.keperluan.nama }}</td>
                  <td>{{ visitors.tanggal }}</td>
                  <td>{{ visitors.waktu.split(".")[0] }} </td>
                </tr>
              </tbody>
            </table>
          </div>
            
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const supabase= useSupabaseClient()

const keyword = ref('')
const visitors = ref([])

const getPengunjung =async () => {
  const { data, error } = await supabase
  .from('pengunjung')
  .select(`*, keanggotaan(*), keperluan(*)`)
  .ilike("nama",`%${keyword.value}%`)
  if(data) visitors.value = data
}
onMounted(() =>{
  getPengunjung()
})

</script>

<style scoped>
.content{
  background-color: rgba(67, 199, 255, 43%);
  width: 100%;
  /* height: 100vh; */
  
}
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #424242;
}
.card.bg-pengunjung {
  background-image: url('../assets/img/bg-home-kunjungan.png');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 75%;
}
.card.bg-buku {
  background-image: url('../assets/img/bg-home-cari-buku.jpg') ;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
.card.bg-riwayat {
  background-image: url('../assets/img/bg-home-cari-buku.jpg') ;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
/* .card.bg-spengunjung {
  background-color: #ECEE7F;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
.card.bg-sbuku {
  background-color: #A8FFEF;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
}
.card.bg-sriwayat {
  background-color: #A8FFEF;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
} */
</style>