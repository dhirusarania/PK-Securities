<template>
  <div class="bg-black">
    <Breadcrumbs title="Career" subtitle crumbs="Home > Career" image="breadcrumb5.jpg"></Breadcrumbs>
    <div class="container-small" style="padding-top:40px">
      <div>
        <div class="w-100">
          <div>
            <img class="coma" src="/images/asset1.png" alt="" />
          </div>
          <div class="container">
            <p
              style="color:white;opacity:.71;font-size:20px;text-align:justify"
            >Career at PK Security & PK Services has been said to be the most stable and safe for the employees working with us. At present there are more than 400+ personnel working for the company and around 100+ administrative and supervisory staff is working round the clock for the company.</p>
          </div>
          <div class="d-flex justify-content-end">
            <img style="right:100%" class="coma" src="/images/asset3.png" alt />
          </div>
        </div>
      </div>
      <div class="mt-5">
        <h2 class="text-center text-white">CURRENT OPENING</h2>
        <div class="accordion mt-5 mb-5 border-0" id="accordionExample">
          <div
            v-for="(p, index) in careers"
            :key="p.id"
            class="card border-bottom cursor-pointer"
            data-toggle="collapse"
            :data-target="'#collapseOne-' + index.replace(/[\s.;,?&%0-9]/g, '-')"
            aria-expanded="true"
            aria-controls="collapseOne"
          >
            <div class="card-header" id="headingOne">
              <button
                class="btn"
                type="button"
                style="color:white;font-size:20px;text-align:left"
              >{{index}}</button>
            </div>

            <div
              :id="'collapseOne-' + index.replace(/[\s.;,?&%0-9]/g, '-')"
              class="collapse"
              aria-labelledby="headingOne"
              data-parent="#accordionExample"
            >
              <div class="card-body">
                <table class="table">
                  <thead>
                    <tr>
                      <th>Experience</th>
                      <th>Location</th>
                      <th>Position Open</th>
                      <th>Position Type</th>
                      <th>Salary Offered</th>
                    </tr>
                  </thead>
                  <tbody v-for="q in p" :key="q.id">
                    <tr>
                      <td>{{q.experience}}</td>
                      <td>{{q.location}}</td>
                      <td>{{q.open_positions}}</td>
                      <td>{{q.job_type}}</td>
                      <td>{{q.salary_range}}</td>
                    </tr>
                  </tbody>
                </table>
                <div class="d-flex justify-content-center m-4">
                  <!-- <button class="btn btn-apply" type="button">APPLY NOW</button> -->
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
import Breadcrumbs from "@/components/breadcrumbs.vue";
import { mapState } from "vuex";

export default {
  data() {
    return {
      careers: []
    };
  },
  components: {
    Breadcrumbs
  },
  computed: {
    ...mapState(["career"])
  },

  mounted() {
    this.$store.dispatch("getAllCareer").then(res => {
      this.careers = this.groupBy(res.data, "category_name");
    });
  },
  methods: {
    groupBy(arr, property) {
      return arr.reduce(function(memo, x) {
        if (!memo[x[property]]) {
          memo[x[property]] = [];
        }
        memo[x[property]].push(x);
        return memo;
      }, {});
    }
  }
};
</script>

<style scoped>
.bg-black {
  background-color: black;
}

.accordion {
  background-color: #333333;
}

.accordion > .card {
  border-bottom: 0;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
  background-color: #9e7b5f;
}

.card-body {
  background-color: #333333;
}

.btn:focus {
  box-shadow: none;
}

.table thead th {
  vertical-align: bottom;
  color: white;
  border-bottom: none;
}

.table td,
.table th {
  padding: 0.75rem;
  vertical-align: top;
  color: white;
  border-top: none;
}

.table {
  background-color: #6c6c6c;
}

.btn-apply {
  color: white;
  font-size: 18px;
  background-color: #9e7b5f;
  height: 48px;
  width: 160px;
  border-radius: 0;
}

.cursor-pointer {
  cursor: pointer;
}
</style>
