<template>
  <div class="hero">
    <!-- Desktop -->
    <div class="d-none d-md-block">
      <div class="row mt-2">
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h1>
                <strong> Komik terupdate, </strong> <br />
                Setiap Hari !!!
              </h1>
              <p>Ayo segera koleksi komik barumu !!</p>
              <router-link class="btn btn-lg btn-danger" to="/"
                >Tambah Koleksi</router-link
              >
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <img src="../assets/images/image.png" width="100%" />
        </div>
      </div>
    </div>

    <!-- Mobile  -->
    <div class="d-sm-block d-md-none">
      <div class="row mt-2">
        <div class="col-md-6">
          <img src="../assets/images/image.png" width="100%" />
        </div>
        <div class="col-md-6">
          <div class="d-flex h-100">
            <div class="justify-content-center align-self-center">
              <h1>
                <strong> Komik terupdate, </strong> <br />
                Setiap Hari !!!
              </h1>
              <p>Ayo segera koleksi komik barumu !!</p>
              <router-link class="btn btn-lg btn-danger" to="/"
                >Tambah Koleksi</router-link
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <!-- <div class="row">
    <div class="col mt-5">
        <div class="d-flex">
            <div class="justify-content-center align-self-center rounded">
                <h1>
                    <strong>Komik terupdate, </strong> <br />
                    Setiap Hari !!!
                </h1>
                <p> Ayo segera koleksi komik barumu !! </p>
                <router-link class="btn btn-lg btn-danger" to="/">Tambah Koleksi</router-link>
            </div>
        </div>
    </div>
    <div class="col">
      <div class="card" style="width:45rem">
        <img src="../assets/images/image.png" class="card-img-top rounded" />
      </div>
    </div>
  </div> -->
</template>

<script>
export default {
  name: "AppHero",
};
</script>

<style>
</style>