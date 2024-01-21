<script>
export default {
  data() {
    return {
      // form:{
      //   name:'',
      // mobile:'',
      // },
      // img:{
      //   src:`/img/logo.svg`,
      //   capshion: 'dcfgdsf'
      // },
      // number:{
      //   num:10
      // }
      // form: {
      //   name: "",
      //   lastname: "",
      //   email: "",
      //   number: "",
      // },
      // isemailinvalid: false,
      // iseLastNameValid: false,
      ///////return////////\

      product: null,
    };
  },
  methods: {
    // click() {
    //   let error = document.querySelector(".error");
    //   // console.log(error);
    //   if (this.form.email == "") {
    //     // error.classList.add('!flex')
    //     this.isemailinvalid = true;
    //   } else {
    //     this.isemailinvalid = false;
    //   }
    // },
    ///////////methodes//////////////]
    formatMounth(card) {
      return new Date(card.createDate).toLocaleString("fa-IR", {
        day: "numeric",
        month: "short",
        year: "numeric",
      });
    },
  },
  computed: {
    // isNameValid() {
    //   if (this.form.name.length < 12) {
    //     return true;
    //   } else {
    //     return false;
    //   }
    // },
    // isLastaNameValid(){
    //   if(this.form.lastname.length <12){
    //     return true
    //   }else{
    //     return false
    //   }
    // }
    ///////////computed/////////////
  },
  mounted() {
    fetch(
      "https://api.liproj.com/api/Product/GetLatestProduct?pageNumber=1&count=8",
      { method: "POST" }
    )
      .then((res) => res.json())
      .then((myproduct) => {
        this.product = myproduct.products;
        console.log(this.product);
      });
  },
};
</script>

<template>
  <main class="w-full bg-yellow-100 border border-red-600 h-screen" dir="rtl">
    <!-- <input type="text" v-model="form.name">
    <input type="text" v-model="form.mobile">
    <p>{{form.name}}</p>
    <p>{{form.mobile}}</p>

    <button type="button" @click="signIn">click me</button>  
    

    
    <p v-text="img.capshion"></p>
    <h2 v-if="number.num > 10"> if</h2>
    <h3 v-else> else</h3> -->

    <!-- /////////////////////////////////////////////////////// -->
    <!-- <img src="/img/bg-intro-desktop.png" alt=""> -->

    <!-- <section
      class="w-full flex h-[700px] justify-center items-center text-center bg-[url('/img/bg-intro-desktop.png')] bg-cover bg-red-400"
    >
      <div class="w-1/2 m-16">
        <h1 class="text-[30px] text-black">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Assumenda,
          pariatur.
        </h1>
        <p class="text-white mt-7">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. In deleniti
          iste adipisci provident sit dolor iusto unde incidunt accusamus
          dolorum?
        </p>
      </div> -->

    <!-- ////////////////////////////////form/////////// -->

    <!--       
      <div class="w-1/2 h-[400px] bg-white m-16 rounded-[25px]">
        <button class="w-[250px] h-[40px] bg-blue-500 rounded-[15px]">
          Lorem ipsum dolor sit amet.
        </button>
        
        <div
          class="h-[200px] flex flex-col justify-center items-center mt-7 gap-4"
        >
          <input
            type="text"
            class="w-[250px] h-[40px] border rounded-[5px] outline-none"
            v-model="form.name"
            placeholder="name"
          />
          <span v-if="!isLastaNameValid">error</span>

          <input
            type="text"
            class="w-[250px] h-[40px] border rounded-[5px] outline-none"
            v-model="form.lastname"
            placeholder="lastname"
          />
          <span v-if="!isNameValid">error</span>
          <input
            type="email"
            class="w-[250px] h-[40px] border rounded-[5px] outline-none"
            v-model="form.email"
            placeholder="email"
          />
          <span v-if="isemailinvalid" class="text-red-500 text-[8px] error"
            >لطفا ایمیل خود را وارد کنید</span
          >
          <input
            type="number"
            class="w-[250px] h-[40px] border rounded-[5px] outline-none"
            v-model="form.number"
            placeholder="number"
          />
          <input
            @click="click()"
            type="submit"
            value="Submit"
            class="bg-green-500 w-[250px] rounded-[10px]"
          />
        </div>
      </div>
    </section> -->

    <!-- //////////////////////////////////////////////////////////card/////////////////////////// -->

    <section
      class="grid grid-cols-10 xl:w-10/12 mx-auto gap-2 justify-center items-center"
    >
      <div
        v-for="(card, idx) in product"
        :key="idx"
        class="col-span-2 border grid grid-cols-1 bg-white rounded-[15px]"
      >
        <div class="w-11/12 h-[150px] m-4 rounded-xl">
          <img
            class="w-full h-[140px]"
            :src="
              'https://api.liproj.com/media/Gallery/product/' +
              card.photos[0].base64
            "
            alt=""
          />
        </div>
        <div class="flex flex-col gap-3 px-3">
          <div class="flex flex-col gap-2">
            <div>
              <span
                class="font-bold text-xs py-1 px-4 rounded-sm bg-yellow-300"
                v-if="card.variablePrices"
              ></span>
            </div>
            <p class="text-gray-400 text-[10px]">
              انتشار {{ formatMounth(card) }}
            </p>
          </div>
          <div class="flex flex-col gap-2 mb-3">
            <h1 class="text-[19px] line-clamp-1">{{ card.title }}</h1>
            <p class="text-gray-400 text-[10px]">{{ card.seourl }}</p>
          </div>
        </div>
        <!-- <div class="flex mt-6 ml-3">
          <img class="w-[30px] h-[20px]" src="/public/img/logo.svg" alt="">
          <h2 class="pl-2">lorem</h2>
        </div> -->
      </div>
    </section>
  </main>
</template>

<style >
</style>
