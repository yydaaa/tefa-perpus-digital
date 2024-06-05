<template>
  <div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-19">
          <h2 class="text-center my-4">ISI FROM PENGUNJUNG</h2>
          <form @submit.prevent="kirimData" >
            <div class="mb-2">
              <input v-model="form.nama" type="text" placeholder="Nama ..." class="form-control  rounded-2" required>
            </div>

            <div class="mb-2">
              <select v-model="form.keanggotaan" @change="resetkelas" class="form-control form-control-lg form-select rounded-2" required>
                <option value="" disabled>KEANGGOTAAN</option>
                <option v-for="(keanggotaan,i) in members" :key="i" :value="keanggotaan.id">{{ keanggotaan.nama }}</option>
              </select>
            </div>

            <div class="mb-1" v-if="form.keanggotaan == '1'">
              <div class="row">
                <div class="col-md-4">
                    <select v-model="form.tingkat" class="form-control form-control-lg form-select rounded-2 mb-2" required>
                    <option value="" disabled>TINGKAT</option>
                    <option value="X">X</option>
                    <option value="XI">XI</option>
                    <option value="XII">XII</option>
                    </select>
                </div>

                <div class="col-md-4">
                <select v-model="form.jurusan" class="form-control form-control-lg form-select rounded-2 mb-2" required>
                  <option value="" disabled>JURUSAN</option>
                  <option value="PPLG">PPLG</option>
                  <option value="TJKT">TJKT</option>
                  <option value="TSM">TSM</option>
                  <option value="DKV">DKV</option>
                  <option value="TOI">TOI</option>
                  </select>
                </div>

                <div class="col-md-4 ">
                  <select v-model="form.kelas" class="form-control form-control-lg form-select rounded-2 mb-2" required>
                  <option value="" disabled>KELAS</option>
                  <option value="1">1</option>
                  <option value="2">2</option>
                  <option value="3">3</option>
                  <option value="4">4</option>
                  </select>
                </div>
              </div>
            </div>

            <div class="mb-2">
              <select v-model="form.keperluan"  class="form-control form-control-lg form-select rounded-2 " required>
              <option value="" disabled>KEPERLUAN</option>
              <option v-for="(item,i) in objectives" :key="i" :value="item.id">{{ item.nama }}</option>
              </select>
            </div>

            <!-- <div class="mb-2" v-if="form.keperluan == '4'">
              <div class="mb-3">
                <input type="text" class="form-control  " placeholder="Isi disini">
              </div>
            </div> -->

            <button type="submit" class="btn rounded-5 px-5" value="submit">SUBMIT</button>

          </form>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
const supabase = useSupabaseClient()

const members = ref ([])
const objectives = ref([])
const form = ref({
  nama: "",
  keanggotaan: "",
  tingkat: "",
  jurusan: "",
  kelas: "",
  keperluan: "",
})
const kirimData = async () => {
  console.log(form.value);
  const { error } = await supabase.from('pengunjung').insert([form.value])
  if (error) throw error
  else navigateTo('/')
}
const getKeanggotaan = async () => {
  const { data, error } = await supabase.from('keanggotaan').select('*')
  if(data) members.value = data
}
const getKeperluan = async () => {
  const { data, error } = await supabase.from('keperluan').select('*')
  if(data) objectives.value = data
}

const resetkelas = e => {
  if(e.target.value === '2' || '3' || '4'){
    form.value.tingkat = ''
    form.value.jurusan = ''
    form.value.kelas = ''
  }
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
  height: 100vh;
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
  background: #43C7FF;
  margin: 10px 30% ;
  box-shadow: 2px 3px  rgb(77, 77, 77);
}
</style>
