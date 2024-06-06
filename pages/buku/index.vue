<template>
<div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12">
          <p></p>
            <form @submit.prevent="getbooks" class="col mb-3">
              <div class="input-group flex-nowrap rounded">
                <input v-model="keyword" type="search" class="form-control from-control-lg rounded-2" placeholder="Cari..." aria-label="Search" @input="getbooks" />
              </div>
            </form>
            
            <div class="row">
              <div class="col-lg-2 col-5">menampilkan {{ books.length }} buku dari {{ jmlhBuku }}
              </div>

              <div class="col-lg-10 col-7">
                <div class="row float-end">
                  <div class="col-4 col-3 pt-2 text-end">Kategori:</div>
                  <div class="col-8 col-4">
                    <select v-model="keyword" class="kategori rounded-5 form form-select form-control" aria-label="Default select example" >
                      <option value="" disabled>...</option>
                      <option v-for="(kategori, i) in kategories" :key="i" :value="kategori.nama">{{ kategori.nama }}</option>
                    </select>
                  </div>
                </div>
              </div>
            </div>
            
          </div>
          
          <hr class="y">
        </div>
          <div class="row">
              <div v-for="(book,i) in bookFiltered" :key="i" class="col mb-3">
                  <div class="card col-lg-2 col-2">
                    <div class="card-body">
                      <nuxt-link :to="`/buku/${book.id}`">
                          <img :src="book.cover" class="cover" alt="cover">
                      </nuxt-link>
                    </div>
                  </div>
              </div>
              <div class="">
                <nuxt-link to="/"><button type="submit" class="btn rounded-5 px-5">KEMBALI</button></nuxt-link>
              </div>
          </div>
    </div>
  </div>
</template>
<script setup>
const supabase= useSupabaseClient ()
const keyword = ref('')
const books = ref([])
const kategories = ref ([])
const jmlhBuku = ref(0)

const getbooks = async () => {
  const { data ,error } = await supabase
  .from('buku')
  .select(`*, kategori(*)`)
  .ilike("judul", `%${keyword.value}%`)
  .order('id')
  if(data) books.value = data
}

const getKategori = async () => {
    const { data, error } = await supabase
    .from('kategori_buku')
    .select('*')
    if(data) kategories.value = data
}

const bookFiltered = computed (() => {
    return books.value.filter((b) => {
        return (
            b.judul?.toLowerCase().includes(keyword.value?.toLowerCase()) ||
            b.kategori?.nama.toLowerCase().includes(keyword.value?.toLowerCase())
        )
    })
})

const getJmlhBuku = async() =>{
  const { data , count } = await supabase
  .from("buku")
  .select('*', { count: "exact"})
  if(data) jmlhBuku.value = count
}
onMounted(() =>{
  getbooks()
  getKategori()
  getJmlhBuku()
})

</script>
<style scoped>
.content{
  background-color: rgba(67, 199, 255, 43%); 
  width: 100%;
  /* height: 100%; */
  object-position: 0 30;
}
.card {
  width: 260px;
  height: 100%;
  padding: 0;
}
.cover {
  width: 220px;
  height: 100%;
  object-fit: cover;
  object-position: 0 30;
}

.btn{
  background: #ffffff;
  color:rgb(0, 0, 0);
  /* margin: 10px 90%; */
  border-radius: 50%;
  margin-left: 0%
  
}
.kategori{
  /* margin: -30px 10vh; */
  background-color:rgba(60, 196, 255, 100%);
}
.y{
  margin: 20px 0vh;
}
.k{
  display: flex !important;
  justify-content: flex-end !important;
  align-items: center !important;
}
</style>
