<template>
  <div class="wrapper">
    <parallax class="section page-header header-filter" :style="headerStyle">
      <div class="container">
        <div class="md-layout">
          <div
            class="md-layout-item md-size-50 md-small-size-70 md-xsmall-size-100"
          >
            <h1 class="title" v-if="!isMobile">Everyone has Something Worth Sharing</h1>
            <h2 class="title" v-if="isMobile">Everyone has Something Worth Sharing</h2>
            <h4>
              Tiap minggu malam, kami Alumni SDIT Asy Syaamil Bontang mengadakan diskusi rutin yang membahas pengalaman, 
              ide, dan lintasan pikiran. Apa yang kami diskusikan dapat dilihat di channel YouTube kami.
            </h4>
            <br />
            <md-button
              href="https://www.youtube.com/watch?v=dQw4w9WgXcQ"
              class="md-danger md-lg"
              target="_blank"
              ><i class="fas fa-play"></i>Kunjungi Channel</md-button
            >
          </div>
        </div>
      </div>
    </parallax>
    <div class="main main-raised">
      <div class="section">
        <div class="container">
          <div class="md-layout">
            <div
              class="md-layout-item md-size-66 md-xsmall-size-100 mx-auto text-center"
            >
              <h2 class="title text-center">Tentang kami</h2>
              <h5 class="description">
                Kami adalah alumni SDIT Asy Syaamil Bontang yang menyempatkan diri untuk berdiskusi dengan sesama alumni tiap minggunya. Saling berkabar, berbagi cerita, dan berdiskusi adalah kegiatan yang kami lakukan tiap minggu malam. Kami percaya bahwa semua alumni, terlepas dari apapun jalan yang mereka pilih semenjak menjadi alumni, memiliki sesuatu yang bisa dibagi.
              </h5>
            </div>
          </div>
          <div class="features text-center">
            <div class="md-layout">
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="info">
                  <div class="icon icon-info">
                    <md-icon>chat</md-icon>
                  </div>
                  <h4 class="info-title">Diskusi Rutin</h4>
                  <p>
                    Nuansa maupun isi dari diskusi rutin yang kami lakukan sangat bervariasi. Terkadang, kami ngobrol seperti sedang nongkrong di kafe kopi. Namun, tidak jarang juga kami berdiskusi seperti organisasi penting yang sedang rapat untuk merumuskan sesuatu. 
                  </p>
                </div>
              </div>
              <div class="md-layout-item md-medium-size-33 md-small-size-100">
                <div class="info">
                  <div class="icon icon-success">
                    <md-icon>verified_user</md-icon>
                  </div>
                  <h4 class="info-title">Pendataan Alumni</h4>
                  <p>
                    Selain mengadakan diskusi rutin, kami juga melakukan pendataan alumni yang rencananya akan diadakan tiap tahun. Pendataan ini berguna untuk mengetahui aktivitas para alumni tiap tahunnya. Dari informasi yang didapat dari pendataan ini, kami berharap dapat melakukan suatu kegiatan yang bermanfaat untuk alumni itu sendiri, sekolah, maupun masyarakat. 
                  </p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <KenaliKami />

      <div class="section section-contacts">
        <div class="container">
          <div class="md-layout">
            <div class="md-layout-item md-size-66 md-xsmall-size-100 mx-auto">
              <h2 class="text-center title">Titip sampein ke alumni dong!</h2>
              <h4 class="text-center description">
                Kamu bisa titip salam, pertanyaan, atau bahkan iklan untuk para alumni. Kamu bisa bertanya tentang pengalaman ngampus, kerja, organisasi, bisnis, dll. Jika kamu punya bisnis, kamu juga bisa menitipkan iklan di sini agar bisnis kamu diketahui oleh semua alumni.
              </h4>
              <form @submit="kirimTitipan" class="contact-form">
                <div class="md-layout">
                  <div class="md-layout-item md-size-50">
                    <md-field class="has-green">
                      <label>Name</label>
                      <md-input v-model="nama" type="text"></md-input>
                    </md-field>
                  </div>
                  <div class="md-layout-item md-size-50">
                    <md-field class="has-green">
                      <label>Email</label>
                      <md-input v-model="email" type="email"></md-input>
                    </md-field>
                  </div>
                </div>
                <md-field class="has-green" maxlength="5">
                  <label>Titipan</label>
                  <md-textarea v-model="pesan"></md-textarea>
                </md-field>
                <div class="md-layout">
                  <div class="md-layout-item md-size-33 mx-auto text-center">
                    <md-button type="submit" class="md-success">Kirim</md-button>
                  </div>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import KenaliKami from './KenaliKami.vue';
import axios from 'axios';

// const host = 'http://localhost:5000';
const host = 'https://minggumalam-api.herokuapp.com';

export default {
  bodyClass: "landing-page",
  components: {
    KenaliKami,
  },
  props: {
    header: {
      type: String,
      default: require("@/assets/img/bg7.jpg")
    },
  },
  data() {
    return {
      nama: null,
      email: null,
      pesan: null
    };
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.header})`
      };
    },
    isMobile() {
        return ( /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent) ) 
    }
  },
  methods:{
    kirimTitipan(e){
      e.preventDefault();
      // alert(this.nama + this.email + this.pesan);
      if (this.nama && this.email && this.pesan) {
        axios.post(host + '/titip', {
          nama: this.nama,
          email: this.email,
          pesan: this.pesan
        })
        .then(r => {
          console.log(r);
          alert("Titipan kamu berhasil kami terima :)");
          location.reload();
        })
        .catch(e => {
          console.log(e);
          alert("Titipan kamu gagal kami terima :(");
          location.reload();
        })
      }
    }
  }
};
</script>

<style lang="scss" scoped>
.md-card-actions.text-center {
  display: flex;
  justify-content: center !important;
}
.contact-form {
  margin-top: 30px;
}

.md-has-textarea + .md-layout {
  margin-top: 15px;
}
</style>
