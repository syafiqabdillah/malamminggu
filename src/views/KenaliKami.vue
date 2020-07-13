<template>
  <div class="section text-center">
    <div class="container">
      <h2 class="title">Kenali anggota kami!</h2>
      <div class="team">
        <div class="md-layout">

          <div class="md-layout-item md-medium-size-33 md-small-size-100">
            
          </div>

          <div class="md-layout-item md-medium-size-33 md-small-size-100">
            <div class="team-player">
              <md-card class="md-card-plain">
                <div class="md-layout-item md-size-50 mx-auto">
                  <img
                    :src="teamImg1"
                    alt="Thumbnail Image"
                    class="img-raised rounded-circle img-fluid"
                  />
                </div>
                <h4 class="card-title">
                  Syafiq Abdillah Umarghanis
                  <br />
                  <small class="card-description text-muted">ELI ( Expert Larry Impersonator )</small>
                </h4>

                <md-card-content>
                  <p class="card-description">
                    Aku ingin hidup seperti Larry
                  </p>
                </md-card-content>

                <md-card-actions class="text-center">
                  <md-button target="_blank" href="https://twitter.com/umarghanis" class="md-just-icon md-simple">
                    <i class="fab fa-twitter"></i>
                  </md-button>
                  <md-button target="_blank" href="https://www.instagram.com/syafiq.au/" class="md-just-icon md-simple">
                    <i class="fab fa-instagram"></i>
                  </md-button>
                  <!-- <md-button href="javascript:void(0)" class="md-just-icon md-simple">
                    <i class="fab fa-facebook-square"></i>
                  </md-button> -->
                </md-card-actions>
              </md-card>
            </div>
          </div>

          <div class="md-layout-item md-medium-size-33 md-small-size-100">
            
          </div>
          
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      teamImg1: require("@/assets/img/faces/syafiq.jpg")
    };
  }
};
</script>

<style lang="scss" scoped>
.text-center {
  display: flex;
  justify-content: center !important;
}
</style>