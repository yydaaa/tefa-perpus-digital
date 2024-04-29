<template>
  <div class="container-fluid">
    <div class="row my-5 justify-content-around">
      <div class="col-lg-5">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5">
            <div class="card-body">
              <h2 style="font-family: ">Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      <div class="col-lg-5">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-5">
            <div class="card-body">
              <h2 style="font-family:">Pencarian Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT PENGUNJUNG</h2>
        <div class="my-3">
          <input type="search" class="form-control form-control-lg rounded-5" placeholder="Filter...">
        </div>
        <div class="my-3 text-muted">menampilkan 1 dari 1</div>
        <table class="table">
          <thead>
            <tr>
              <td>NO</td>
              <td>NAMA</td>
              <td>KEANGGOTAAN</td>
              <td>TINGKAT</td>
              <td>JURUSAN</td>
              <td>KELAS</td>
              <td>KEPERLUAN</td>
              <td>WAKTU</td>

            </tr>
          </thead>
          <tbody>
            <tr>
              <td>1.</td>
              <td>YUDA APRIANA SALAM</td>
              <td>Siswa</td>
              <td>XI</td>
              <td>PPLG</td>
              <td>3</td>
              <td>MEMBACA</td>
              <td>26 Februari 2024, 13:00</td>
              
            </tr>
          </tbody>
        </table>

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