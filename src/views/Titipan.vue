<template>
  <div class="wrapper">
    <parallax
      class="section page-header header-filter"
      :style="headerStyle"
    ></parallax>
    <div class="main main-raised">
      <div class="section profile-content">
        <div class="container">
          <div class="md-layout">
            <div class="md-layout-item md-size-100 mx-auto">
              <div class="profile">
                <div class="name">
                  <h3 class="title">Titipan Pesan untuk Alumni</h3>

                  <md-table v-model="list_titipan" md-card>
                    <md-table-row slot="md-table-row" slot-scope="{ item }">
                      <md-table-cell md-label="Nama">
                        {{ item.nama }}
                      </md-table-cell>

                      <md-table-cell md-label="Isi Pesan">
                        {{ item.isi }}
                      </md-table-cell>
                    </md-table-row>
                  </md-table>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
const host = "https://minggumalam-api.herokuapp.com";
export default {
  components: {},
  bodyClass: "profile-page",
  created() {
    axios
      .get(host + "/get-titipan")
      .then(response => {
        const titipan = response.data.data;
        titipan.forEach(pesan => {
          const id = pesan[0];
          const nama = pesan[1];
          const isi = pesan[3];
          this.list_titipan.push({
            id: id,
            nama: nama,
            isi: isi
          });
        });
      })
      .catch(e => {
        alert(e);
      });
  },
  data() {
    return {
      users: [
        {
          id: 1,
          name: "Shawna Dubbin",
          email: "sdubbin0@geocities.com",
          gender: "Male",
          title: "Assistant Media Planner"
        },
        {
          id: 2,
          name: "Odette Demageard",
          email: "odemageard1@spotify.com",
          gender: "Female",
          title: "Account Coordinator"
        },
        {
          id: 3,
          name: "Lonnie Izkovitz",
          email: "lizkovitz3@youtu.be",
          gender: "Female",
          title: "Operator"
        },
        {
          id: 4,
          name: "Thatcher Stave",
          email: "tstave4@reference.com",
          gender: "Male",
          title: "Software Test Engineer III"
        },
        {
          id: 5,
          name: "Clarinda Marieton",
          email: "cmarietonh@theatlantic.com",
          gender: "Female",
          title: "Paralegal"
        }
      ],
      list_titipan: []
    };
  },
  props: {
    header: {
      type: String,
      default: require("@/assets/img/city-profile.jpg")
    }
  },
  computed: {
    headerStyle() {
      return {
        backgroundImage: `url(${this.header})`
      };
    }
  }
};
</script>

<style lang="scss" scoped>
.section {
  padding: 0;
}

.profile-tabs::v-deep {
  .md-card-tabs .md-list {
    justify-content: left;
  }

  [class*="tab-pane-"] {
    margin-top: 3.213rem;
    padding-bottom: 50px;

    img {
      margin-bottom: 2.142rem;
    }
  }
}

.profile-page .profile {
  text-align: left;
}

.profile-page .page-header {
  height: 200px;
}

.title {
  color: white;
}
</style>
