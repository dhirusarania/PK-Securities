<template>
  <div>
    <Breadcrumbs title="Training and Orientation" subtitle crumbs="Home > Training and Orientation"></Breadcrumbs>
    <div class="container-small" style="margin-top:50px!important" @click="removeTrans">
      <div class="row" style="#333333">
        <div class="col-12 col-lg-7">
          <div class="train-pad">
            <p>With a view to provide adequate training to security personnel for service realization, we at BIS with state of Art infrastructure maintaining full-fledged training center in different states.</p>
            <p>These training centers are named as IISM which are established with a view to provide training to our workforce equivalent to paramilitary forces. These training centers were established much before enactment of PSARA Act 2005.</p>
            <p>Training as per PSARA Act 2005 is compulsorily provided to security personnel recruited for deployment free of cost. A proper course of syllabus is being followed at all our IISM which is well equipped and managed by competent training staff and experts.</p>
          </div>
        </div>
        <div class="col-12 col-lg-5">
          <iframe
            src="https://maps.google.com/maps?q=pk%20security&t=&z=13&ie=UTF8&iwloc=&output=embed"
            frameborder="0"
            style="border:0;width: 100%;height: 500px"
            allowfullscreen
          ></iframe>
        </div>
      </div>

      <div class="mt-5">
        <div class="row">
          <div class="col-12 col-sm-4 train" v-for="(x,y) in 3" :key="y" :id="y">
            <img class="w-100" src="/images/train1.jpg" alt />
          </div>
          <!-- <div class="col-12 col-sm-4 train">
            <img class="w-100" src="/images/train1.jpg" alt />
          </div>
          <div class="col-12 col-sm-4 train">
            <img class="w-100" src="/images/train1.jpg" alt />
          </div>-->
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import Breadcrumbs from "@/components/breadcrumbs.vue";
export default {
  components: {
    Breadcrumbs
  },
  mounted() {
    $(".train")
      .click(function() {
        $(".train").addClass("train-zoom");
        $(".backdrop").addClass("backdrop--active");
      })
      .siblings()
      .removeClass("train-zoom");
  },
  methods: {
    hide() {
      $(".train").removeClass("train-zoom");
      $(".backdrop").removeClass("backdrop--active");
    },
    removeTrans: function(event) {
      $(event.target)
        .children()
        .children()
        .children()
        .children()
        .removeClass("train-zoom");
    }
  }
};
</script>
<style scoped>
.backdrop {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  pointer-events: none;
  z-index: 100;
}

.backdrop--active {
  pointer-events: all;
  /* z-index: 1000; */
}

.train-pad {
  padding: 0 10px 10px;
}

.train-pad > p {
  font-size: 18px;
  color: #707070;
  text-align: justify;
}

.train {
  transition: all 0.4s;
}

.train-zoom {
  transform: scale(1.5);
}
</style>
