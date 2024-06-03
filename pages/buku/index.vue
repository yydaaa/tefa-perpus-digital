<template>
<div class="content">
    <div class="container-fluid">
      <div class="row">
        <div class="col-lg-12">
          <p></p>
            <form @submit.prevent="getBooks" class="col mb-3">
              <div class="input-group flex-nowrap rounded">
                <input v-model="keyword" type="search" class="form-control from-control-lg rounded-2" placeholder="Cari..." aria-label="Search" @input="getbooks" />
              </div>
            </form>
            <div class="my-3">menampilkan {{ books.length }} buku dari {{ books.length }}</div>
            <div class="col-sm-3 mb-2">
              <select v-model="keyword" class="form-select" aria-label="Default select example" style="box-shadow: 2px 2px 2px">
                <option value="">Kategori buku</option>
                <option v-for="(kategori, i) in kategories" :key="i" :value="kategori.nama">{{ kategori.nama }}</option>
              </select>
            </div>
          </div>
          
          <hr>
        </div>
          <div class="row">
              <div v-for="(book,i) in books" :key="i" class="col">
                  <div class="card mb-3 col-lg-2 col-2">
                    <nuxt-link :to="`/buku/${book.id}`">
                      <div class="card-body">
                        <img :src="book.cover" class="cover" alt="cover">
                      </div>
                    </nuxt-link>
                  </div>
              </div>
              <div class="my-3">
            <nuxt-link to="../"><button type="submit" class="btn rounded-5 px-5" style="margin-left: 0%;">KEMBALI</button></nuxt-link>
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

onMounted(() =>{
  getbooks()
  getKategori()
})

</script>
<style scoped>
.content{
  background-color: rgba(67, 199, 255, 43%); 
  width: 100%;
  height: 100%;
  object-position: 0 30;
}
.card-body {
  width: 220px;
  height: 20em;
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
  margin: 10px 90%;
  border-radius: 50%;
  margin-left: 0%
  
}
</style>