<template>
  <div class="container-fluid">
    <div class="row mt-4 d-flex justify-content-evenly">
      <div class="col-lg-4">
        <div class="card">
          <div class="card-body">
            <img src="~/assets/img/cover2.jpg" width="220px" height="340px" class="cover" alt="cover2">
          </div>
        </div>
      </div>
      <div class="col-4">
        <h2>Detail buku</h2>
        <p>Penulis : Sejarah</p>
        <p>Tahun terbit : 2017</p>
        <p>Penerbit : Kemendikbud</p>
        <p>Jumblah halaman : -</p>
        <p>Rak : -</p>
      </div>
    </div>
    <div class="row mt-5">
      <h2>Sinopsis</h2>
      <p class="mt-3"> -</p>
    </div>
    <nuxt-link to="/buku">
      <button type="button" class="btn btn-dark mt-5">Kembali</button>
    </nuxt-link>
  </div>
</template>

<style scoped>
.card {
  width: 255px;
  height: 370px;
  box-shadow: 1px 1px 10px #424242;
}
</style>
