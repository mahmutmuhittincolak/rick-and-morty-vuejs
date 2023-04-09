<template>
  <div class="container-fluid">
    <div class="background-img">
      <h1 class="header-h1">RİCK AND MORTY APP</h1>
      <div class="bg-img-div"></div>
    </div>
    <div class="content-showcase">
      <div class="content-showcase-area">
        <div
          v-for="(item, index) in chars"
          :key="index"
          class="content-showcase-area-card"
        >
          <div class="content-showcase-area-card-1">
            <img v-bind:src="item.image" alt="" />
          </div>
          <div class="content-showcase-area-card-2">
            <div class="section">
              <h2 class="text-white">{{ item.name }}</h2>
              <span class="status">
                <span class="status__icon"></span>
                {{ item.status }} - {{ item.species }}
              </span>
            </div>
            <div class="section">
              <span class="text-gray">Last known location:</span>
              <a class="text-white">{{ item.location.name }}</a>
            </div>
            <div class="section">
              <span class="text-gray">First seen in:</span>
              <a class="text-white">{{ item.origin.name }}</a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",

  data() {
    return {
      urlchar: "https://rickandmortyapi.com/api/character/?page=19",
      chars: [],
    };
  },
  methods: {
    alive(txt) {
      if (txt == "Alive") {
        this.spancolor = "#ff0000";
      } else if (txt == "Unkown") {
        this.spancolor = "#fafafa";
      } else {
        this.spancolor = "#00ff00";
      }
    },
  },
  created() {
    axios
      .get(this.urlchar)
      .then((response) => (this.chars = response.data.results));
  },
};
</script>

<style>
.container-fluid {
  padding: 0;
}
.content-showcase {
  display: flex;
  -webkit-box-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  align-items: center;
  padding: 4.5rem 0px;
  background: rgb(39, 43, 51);
  min-height: calc(50vh - 60px);
}
.content-showcase-area {
  display: flex;
  -webkit-box-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  align-items: center;
  flex-wrap: wrap;
  max-width: 1920px;
}
.content-showcase-area-card {
  width: 600px;
  height: 220px;
  display: flex;
  overflow: hidden;
  background: rgb(60, 62, 68);
  border-radius: 0.5rem;
  margin: 0.75rem;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 4px 6px -1px,
    rgba(0, 0, 0, 0.06) 0px 2px 4px -1px;
}
.content-showcase-area-card img {
  width: 100%;
  height: 100%;
  margin: 0px;
  opacity: 1;
  transition: opacity 0.5s ease 0s;
  object-position: center center;
  object-fit: cover;
}
.content-showcase-area-card-1 {
  flex: 2 1 0%;
  width: 100%;
}

.content-showcase-area-card-2 {
  flex: 3 1 0%;
  position: relative;
  padding: 0.75rem;
  color: rgb(255, 255, 255);
  display: flex;
  flex-direction: column;
}
.content-showcase-area-card-2 a {
  text-decoration: none;
}
.content-showcase-area-card-2 .section:first-child {
  -webkit-box-pack: start;
  justify-content: flex-start;
}
.content-showcase-area-card-2 .section:last-child {
  -webkit-box-pack: end;
  justify-content: flex-end;
}
.content-showcase-area-card-2 .section + .section {
  margin-top: 1.25rem;
}
.text-white {
  color: rgb(245, 245, 245);
}
.text-gray {
  color: rgb(158, 158, 158);
}
.content-showcase-area-card-2 .section {
  flex: 1 1 0%;
  display: flex;
  flex-direction: column;
  -webkit-box-pack: center;
  justify-content: center;
}
.content-showcase-area-card-2 span,
h2 {
  margin: 0px;
  padding: 0px;
}
.content-showcase-area-card-2 h2 {
  font-size: 1.5rem;
}
.content-showcase-area-card-2 span {
  font-size: 16px;
  font-weight: 500;
}
.content-showcase-area-card-2 .status {
  display: flex;
  -webkit-box-align: center;
  align-items: center;
  text-transform: capitalize;
}
.content-showcase-area-card-2 .status__icon {
  height: 0.5rem;
  width: 0.5rem;
  margin-right: 0.375rem;
  background: rgb(214, 61, 46);
  border-radius: 50%;
}
.status__icon {
  height: 0.5rem;
  width: 0.5rem;
  margin-right: 0.375rem;
  background: rgb(85, 204, 68);
  border-radius: 50%;
}
.header-h1 {
  margin: 0px;
  color: rgb(32, 35, 41);
  background-color: rgba(255, 255, 255, 0.367);
  padding: 5px 15px;
  border: none;
  font-weight: 900;
  z-index: 1;
  font-size: 5.625rem;
}
.background-img {
  display: flex;
  -webkit-box-pack: center;
  justify-content: center;
  -webkit-box-align: center;
  align-items: center;
  flex-direction: column;
  height: calc(50vh - 60px);
  text-align: center;
  position: relative;
}
@media (max-width: 40.625em) {
  .content-showcase {
    padding: 1.5rem;
  }
  .content-showcase-area-card {
    flex-direction: column;
    height: initial;
    width: 100%;
  }
  .content-showcase-area-card img {
    height: 300px;
  }
  .content-showcase-area-card-2 {
    pointer-events: none;
  }
  .content-showcase-area-card-2 .section + .section {
    margin-top: 1.25rem;
  }
  .background-img {
    padding: 0px 1.25rem;
  }
}

.bg-img-div {
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url("../src/assets/img/ram1.jpg");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
