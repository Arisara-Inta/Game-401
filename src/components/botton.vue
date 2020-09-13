<template>
  <div>
    <div class="row">
      <div class="col-sm">
        <p style="font-size: 150%">{{aplayer.name}}</p>
        <p>
          <img v-bind:style="{width: aplayer.hp + 'px'}" :src="hp1" alt height="20px" />
        </p>
        <p style="font-size: 150%">{{thp}}{{aplayer.hp}}</p>
        <p>
          <img style="width:45%" :src="aplayer.image" />
        </p>
      </div>
      <div class="row">
      <div class="col"></div>
      <div class="col"></div>
    </div>
      <div class="col-sm">
        <div class="row">
          <div class="col">
            <button class="btn btn-primary" @click="start()">START</button></div>
          <div class="col">
            <button v-bind:disabled="end" class="btn btn-danger" @click="attack()">ATTACK</button></div>
          <div class="col">
            <button v-bind:disabled="end" class="btn btn-dark" @click="specialattack()">SPECIAL ATTACK</button></div>
          <div class="col">
            <button class="btn btn-light" @click="reset()">RESET</button></div>
          <br />
          <img src="http://www.pngmart.com/files/11/Versus-Battle-PNG-File.png"
            width="100%"
          />
        </div>
        <div class="row">
          <div class="col-sm"></div>
          <div class="col-sm">
            <div id="score">
              <div v-if="amonster.hp <= 0"><FONT COLOR=red>YOU WIN!!!</FONT></div>
              <div v-else-if="aplayer.hp <= 0"><FONT COLOR=red>YOU LOSE!</FONT></div>
            </div>
          </div>
          <div class="col-sm"></div>
        </div>
      </div>
      <div class="col-sm">
        <p style="font-size: 150%">{{amonster.name}}</p>
        <p><img v-bind:style="{width: amonster.hp + 'px'}" :src="hp2" alt height="15px" /></p>
        <p style="font-size: 150%">{{thp}}{{amonster.hp}}</p>
        <p><img style="width:70%" :src="amonster.image" /></p>
      </div>
    </div>
    <hr />
  </div>
</template>
<script>
export default {
  data: function () {
    return {
      thp: "HP:",
      end: false,
      hp2:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      hp1:
        "https://i.ppy.sh/bca61e3c2183a86ddb4c1d75914fab845e2b128f/687474703a2f2f692e696d6775722e636f6d2f6953766c5662432e706e67",
      aplayer: { name: "", hp: 1, image: "", hp1: "" },
      player: [
        {name: "Sasuke",hp: 300,image:
            "https://i.pinimg.com/originals/be/e1/65/bee165b22c2f85735e359a2674c3d231.png",
        },
        {name: "Naruto",hp: 300,image:
            "https://s.isanook.com/ga/0/nrt/di/33ab1-obj-sec-3.png",
        },
        {name: "Natsu",hp: 270,image:
            "https://3.bp.blogspot.com/-MMctcSIR9pA/UqqvQKbn4DI/AAAAAAAAAAY/6odqxfk3meo/s1600/200px-Natsu_Dragneel_GMG.png",
        },
        {name: "Rimuru",hp: 400,image:
            "https://cdn.readawrite.com/publicassets/1948046/images/received_910595039324559.png",
        },
        {name: "Erza",hp: 350,image: 
            "https://1.bp.blogspot.com/-EFXjvnAyrRs/WK4s1W7CKmI/AAAAAAAAAJA/ffuonBOGFv4DkzKnAwyWGixGZPX937S6QCEw/s1600/Erza_Anime_S2.png",
        },
      ],
      amonster: { name: "", hp: 1, image: "", hp1: "" },
      monster: [
        {name: "Happy",hp: 100,image:
            "https://i.pinimg.com/originals/7d/b9/04/7db904c4cc93015285d0b0ada340875f.png",
        },
        {name: "Kirito",hp: 250,image:
            "https://www.sjskgamer.net/wp-content/uploads/2019/11/Kirito-A-Duty-to-Honor.png",
        },
        {name: "Goku",hp: 330,image: 
            "https://i.pinimg.com/originals/a9/e1/c5/a9e1c5d500c3b186faa411d5fec0d769.png",
        },
        {name: "Meliodas",hp: 400,image: 
            "https://i.pinimg.com/originals/c6/68/ba/c668ba3d743bded8f97e77cd7163131d.png",
        },
        {name: "Nezuko",hp: 280,image: 
            "https://i.pinimg.com/originals/65/65/ab/6565abe2a1cceae6328f7772a7d952ce.png",
        },
      ],
      player_max: "",
      monster_max: "",
    };
  },
  methods: {
    randomno: function (min, max) {
      return Math.max(Math.floor(Math.random() * max) + 1, min);
    },
    start: function () {
      this.aplayer = this.player[this.randomno(1, 5) - 1];
      this.amonster = this.monster[this.randomno(1, 6) - 1];
    },
    attack: function () {
      this.player_max = Math.floor(Math.random() * 7 + 3);
      this.amonster.hp = this.amonster.hp - this.player_max;
      this.monster_max = Math.floor(Math.random() * 10 + 3);
      this.aplayer.hp = this.aplayer.hp - this.monster_max;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    special: function () {
      this.player_max = Math.floor(Math.random() * 20 + 6);
      this.amonster.hp = this.amonster.hp - this.player_max;
      this.monster_max = Math.floor(Math.random() * 13 + 6);
      this.aplayer.hp = this.aplayer.hp - this.monster_max;
      if (this.aplayer.hp <= 0) {
        this.aplayer.hp = 0;
        this.end = true;
      } else if (this.amonster.hp <= 0) {
        this.amonster.hp = 0;
        this.end = true;
      }
    },
    reset: function () {
      window.location.reload();
    },
  },
};
</script>
<style>
#score {
  font-size: 100%;
  color: aliceblue;
}
</style>