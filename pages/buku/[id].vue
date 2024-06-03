<template>
  <div class="content">
      <div class="container-fluid">
          <div class="row d-flex justify-content-center flex-md-wrap" style="padding-top: 190px;">
              <div class="col-3 ">
                <div class="cover " style="width:250px">
                  <img :src="buku.cover"  class="cover row img-fluid" alt="cover buku" >
                  <div class="row">
                  </div>
                </div>
              </div>
              <div class="col-8">
                  <div class="row">
                          <h3 class="list-group-item">JUDUL: {{ buku.judul }}</h3>
                          <h3 class="list-group-item">PENULIS: {{ buku.penulis }}</h3>
                          <h3 class="list-group-item">PENERBIT: {{ buku.penerbit }}</h3>
                          <h3 class="list-group-item">TAHUN TERBIT: {{ buku.tahun_terbit }}</h3>
                          <h3 class="list-group-item">RAK: {{ buku.rak }}</h3>
                          <h3 class="list-group-item">KATEGORI: {{ buku.kategori_buku?.nama }}</h3>
                  </div>
                  
                  </div>
              </div>
              <div class="row mt-2">
                  <h3 class="list-group-item m-5">SINOPSIS: {{ buku.deskripsi }}</h3>
              <div class="my-3">
            <nuxt-link to="/buku"><button type="submit" class="btn rounded-5 px-5" style="margin-left: 0%;">KEMBALI</button></nuxt-link>
        </div>
          </div>
      </div>
      </div>
</template>
<script setup>
import { onMounted } from 'vue';

const supabase = useSupabaseClient()
const route = useRoute()
const buku = ref([])
// const kategories = ref ([])

const getBookById = async () => {
    const { data, error } = await supabase
    .from('buku')
    .select(`*, kategori_buku(*)`)
    .eq('id', route.params.id)
    .single()
    if(data) buku.value = data
}
// const getKategori = async () => {
//     const { data, error } = await supabase
//     .from('kategori_buku')
//     .select('*')
//     if(data) kategories.value = data
// }


onMounted(() => {
    getBookById()
    // getKategori()
})


</script>
<style scoped>
.container-fluid{
  background-color: rgba(67, 199, 255, 43%); 
  width: 100%;
  height: 100vh;
  object-position: 0 30;
}
.btn{
  background: #ffffff;
  color:rgb(0, 0, 0);
  margin: 10px 90%;
  border-radius: 50%;
  margin-left: 0%
  
}
.cover{
  width: 270px;
  height: 370px;
  box-shadow: 5px 1px 10px #424242;
}
.cover{
  margin: 4px 7px;

}
</style>