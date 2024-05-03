<template>
  <div class="content">

    <div class="container-fluid">
      <div class="row py-5 d-flex justify-content-evenly">
        <div class="col-lg-3">
          <div class="card">
            <div class="card-body">
              <img src="~/assets/img/cover2.jpg" width="220px" height="340px" class="cover" alt="cover2">
            </div>
          </div>
        </div>
        <div class="col">
          <div class="buku">
          <h2>Detail buku</h2>
          <p>Penulis : Sejarah</p>
          <p>Tahun terbit : 2017</p>
          <p>Penerbit : Kemendikbud</p>
          <p>Jumblah halaman : -</p>
          <p>Rak : -</p>
          </div>
        </div>
      </div>
      <div class="row mt-5">
        <h2>Sinopsis</h2>
        <p class="mt-3"> -</p>
      </div>
      <nuxt-link to="/buku" class="text-decoration-none">
        <button type="button" class="btn rounded-5 px-5">Kembali</button>
      </nuxt-link>
    </div>
  </div>
</template>

<style scoped>
.container-fluid{
  background-color: rgba(67, 199, 255, 43%);
  width: 100%;
  height: 100vh;
}
.card {
  width: 255px;
  height: 370px;
  box-shadow: 1px 1px 10px #424242;
}
.btn{
  background: #ffffff;
  color:rgb(0, 0, 0);
  margin: 10px 90%;
  border-radius: 50%;
  margin-left: 0%
  
}
</style>