<template>
  <div class="container-fluid">
    <div class="row my-5 justify-content-around">
      <div class="col-lg-5">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
              <h2 style="font-family: ;">Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      <div class="col-lg-5">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2 style="font-family: ;">Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      <div class="col-lg-5">
        <nuxt-link to="/riwayat">
          <div class="card bg-riwayat rounded-5">
            <div class="card-body">
              <h2 style="font-family: ;">riwayat</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #424242;
}
.card.bg-pengunjung {
  background-image: url('../assets/img/bg-home-pengunjung.jpeg');
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  opacity: 60%;
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
.card.bg-spengunjung {
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
}
</style>
