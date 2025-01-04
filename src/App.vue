<template>
  <div class=" min-h-screen w-full bg-[#002510] relative bg flex flex-col">

    <div class="container mx-auto">

   
    <!-- NAV AREA -->
     <div class=" w-full flex-row flex justify-between items-center p-6">
      <div>
        <img src="./assets/logo_long.png" class=" h-6"/>
      </div>

      <div class="flex flex-row text-lg text-white font-medium gap-6 items-center">
        <span>About</span>
        <a href="https://whatsapp.com/channel/0029Vae6Q3g4IBh7pV0IDP0f" target="_blank">
          <button class=" rounded-md w-fit px-3 bg-slate-50 text-black text-[15px]"> <i class="bi bi-whatsapp"></i> <span class=" ml-2 hidden md:inline-block">Join Channel</span></button>
        </a>
      </div>
     </div>

     <!-- HERO CONTENT -->
      <div class="flex flex-col justify-center items-center text-white gap-3 mt-12">
        <h1 class=" text-2xl font-medium">Launch Countdown</h1>
        <span class=" text-gray-400 p-1 px-3 rounded-sm bg-black bg-opacity-30"> <i class="bi bi-calendar-check mr-2"></i>20th January, 2025</span>
        <div class="flex flex-row gap-4 flex-wrap p-5 justify-center items-center text-center">

          <!-- TIME DAYS -->
          <div data-aos="fade-up" data-aos-delay="300" class="time_box">
            <span class=" text-3xl font-bold">{{ days }}</span>
            <span>days</span>
          </div>

          <!-- TIME HOURS -->
          <div data-aos="fade-up" data-aos-delay="400" class="time_box">
            <span class=" text-3xl font-bold">{{ hours }}</span>
            <span>hours</span>
          </div>

           <!-- TIME MINS -->
           <div data-aos="fade-up" data-aos-delay="500" class="time_box">
            <span class=" text-3xl font-bold">{{ minutes }}</span>
            <span>mins</span>
          </div>

          <!-- TIME SECS -->
          <div data-aos="fade-up" data-aos-delay="600" class="time_box">
            <span class=" text-3xl font-bold">{{ seconds }}</span>
            <span>secs</span>
          </div>
        </div>

        <div class=" mt-12 flex flex-col justify-center items-center text-center gap-8 max-w-md p-5">
          <h2 class=" text-5xl font-bold ">It's almost time!</h2>
          <p>Join the waitlist and be part of the excitement: Receive Exclusive Launch Updates and Notifications</p>
          <form class="flex flex-row gap-3 text-[14px]">
            <input class="p-4 bg-white bg-opacity-10 text-white border-none outline-none md:w-[300px] rounded-md" placeholder="Your Email Address..."/>
            <button class=" bg-[#47C67F] rounded-md px-6 text-nowrap">Join Waitlist</button>
          </form>
        </div>
       
      </div>

    <!-- ABOUT US -->
     <div class="flex flex-col mt-12 justify-center items-center text-white p-8" data-aos="fade-up" data-aos-delay="400">
        <h3 class="font-medium"> <i class="bi bi-people mr-2 "></i>About Us</h3>
        <div class=" flex md:flex-row gap-6 justify-center items-center mt-10">
          <div class="flex flex-col flex-1 gap-5 text-justify">
            <span class=" font-bold text-lg">Meet WhatSell – Your Commerce Companion</span>
            <p class=" mt-3s">Buying and selling on WhatsApp can be exhausting.</p>
            <p class="">As a vendor, you’re stuck with a small audience, posting products on your status over and over, only to get a handful of views. Answering the same questions repeatedly? Draining.</p>
            <p>As a buyer, finding what you need feels like searching for a needle in a haystack. Too many statuses, not enough clarity.</p>
            <p>WhatSell changes the game. It’s your go-to platform to simplify and supercharge WhatsApp commerce.</p>
            <ol class=" flex flex-col gap-3 md:ml-8 list-disc">
              <li><b>For Vendors:</b> List products, showcase with videos (Glips), auto-post to social media, and connect with buyers beyond your contact list. Want more reach? Sponsor listings or boost your shop with ease.</li>
              <li><b>For Vendors:</b> Quickly find trusted vendors near you, browse products, watch demos, and chat directly with vendors on WhatsApp</li>
            </ol>
            <p>WhatSell bridges the gap, making buying and selling easy, fast, and effective.</p>
          </div>
          <div class=" flex-1 justify-end items-center hidden md:flex overflow-auto no-scrollbar">
            <img src="../src/assets/phone.png" class=" h-auto" data-aos="zoom-out-left"/>
          </div>
        </div>
     </div>

     <!-- FOOTER -->
      <div class=" flex flex-row gap-5 justify-center items-center p-12 text-white">
        <span><i class="bi bi-facebook"></i></span>
        <span><i class="bi bi-twitter"></i></span>
        <span><i class="bi bi-instagram"></i></span>
      </div>
    </div>
  </div>
</template>

<script>
import AOS from 'aos'
import 'aos/dist/aos.css'

  export default {
    data(){
      return{
        target_date: new Date('2025-01-20'),
        days: 0,
        hours: 0,
        minutes: 0,
        seconds: 0,

        diff: null,
        timer: ''
        
      }
    },
    methods: {
      getTimeLeft() {
        
        const now = new Date();
        const diff = new Date(this.target_date) - now;
        this.diff = diff;
      
        if (diff <= 0) return { days: 0, hours: 0, minutes: 0, seconds: 0 };
      
        this.days = Math.floor(diff / (1000 * 60 * 60 * 24));
        this.hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
        this.minutes = Math.floor((diff / (1000 * 60)) % 60);
        this.seconds = Math.floor((diff / 1000) % 60);
      
        // return { days, hours, minutes, seconds };
      },

      
    },

    created(){
      AOS.init();

      const timer = setInterval(this.getTimeLeft, 1000);
      timer;
      if(this.diff <= 0){
        
        // clearInterval(timer)
      }
    }
  }
</script>

<style scoped>
.waves{
  /* background: linear-gradient(114.4deg, rgba(71, 198, 127, 0.85) 29.6%, rgba(255, 119, 0, 0.85) 61.44%); */

}

.bg{
  background-image: url('./assets/bg.png');
  /* background-image: url('./assets/whatsell_wailist_bg.png'); */
  background-size: cover;
  /* background-size: 150%; */
  background-repeat: no-repeat;
  background-position: top;
  position: relative;
}


.time_box{
  @apply flex flex-col gap-2 bg-white bg-opacity-10  p-8 max-h-40 rounded-lg border border-opacity-10 border-white
}
</style>