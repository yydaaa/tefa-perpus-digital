<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-19">
          <h2 class="text-center my-4">ISI FROM PENGUNJUNG</h2>
          <form @submit.prevent="kirimData" >
            <div class="mb-3">
              <input type="text" class="form-control form-control-lg " placeholder="NAMA...">
            </div>
            <div class="mb-3">
              <select v-model="keanggotan" class="form-control form-control-lg from-select " placeholder="Keanggotaan">
                <option value="">KEANGGOTAAN</option>
                <option value="Siswa">Siswa</option>
                <option value="Guru">Guru</option>
                <option value="Staf">Staf</option>
                <option value="Umum">Umum</option>
              </select> 
            </div>
            <div class="mb-3" v-if="keanggotan == 'Siswa'">
              <div class="row">
                <div class="col-md-4">
                  <select class="form-control form-control-lg from-select  mb-2">
                    <option value="">TINGKAT</option>
                    <option value="X">X</option>
                    <option value="XI">XI</option>
                    <option value="XII">XII</option>
                  </select>
                </div>
                <div class="col-md-4">
                  <select class="form-control form-control-lg from-select  mb-2">
                    <option value="">JURUSAN</option>
                    <option value="PPLG">PPLG</option>
                    <option value="TJKT">TJKT</option>
                    <option value="TSM">TSM</option>
                    <option value="DKV">DKV</option>
                    <option value="TOI">TOI</option>
                  </select>
                </div>
                <div class="col-md-4">
                  <select class="form-control form-control-lg from-select  mb-2">
                    <option value="">KELAS</option>
                    <option value="1">1</option>
                    <option value="2">2</option>
                    <option value="3">3</option>
                    <option value="4">4</option>
                  </select>
                </div>
              </div>
            </div>
            <div class="mb-3">
              <select v-model="Keperluan" class="form-control form-control-lg from-select">
                <option value="">KEPERLUAN</option>
                <option value="Pinjam">Pinjam Buku</option>
                <option value="Kembalikan">Kembalikan</option>
                <option value="Lainnya">Lainnya</option>
              </select>
            </div>
            <div class="mb-3" v-if="Keperluan == 'Lainnya'">
              <div class="mb-3">
                <input type="text" class="form-control form-control-lg " placeholder="Isi disini">
              </div>
            </div>
            <nuxt-link to="../"><button type="submit" class="btn rounded-5 px-5" text="center">SUMBIT</button></nuxt-link>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const supabase = useSupabaseClient()

const keanggotan = ref ('')
const Keperluan = ref ('')

const form = ref({
    nama: "",
    keanggotaan: "",
    tingkat: "",
    jurusan: "",
    kelas: "",
    keperluan: "",
  })

  const kirimData = async () => {
    const { error } = await supabase.from('pengunjung').insert([form.value])
    if(!error) navigateTo('/pengunjung')
  }

  const getKeanggotaan = async () => {
    const { data, error } = await supabase.from('keanggotaan').select('*')
    if(data) members.value = data
  }

  const getKeperluan = async () => {
    const { data, error } = await supabase.from('keperluan').select('*')
    if(data) objectives.value = data
  }

  onMounted(() => {
    getKeanggotaan()
    getKeperluan()
  })

</script>
<style scoped>

.container-fluid {
  background-color: rgba(67, 199, 255, 43%); 
  width: 100%;
  height: 80vh;
  display: flex;
  justify-content: space-evenly;
  flex-direction: row;
  flex-wrap: wrap;
  align-content: center;

}
.from-control{
  box-shadow: 2px 3px  rgb(77, 77, 77);
}
.btn {
  background: #00fffb;
  margin: 10px 30% ;
  box-shadow: 2px 3px  rgb(77, 77, 77);
}
</style>
