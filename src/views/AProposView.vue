<script setup>
  import Bouton from "@/components/bouton.vue";
  import emailjs from 'emailjs-com';
</script>

<template>
<section class="pt-8 sm:pt-20 overflow-hidden">
  <div class="flex justify-between">
            <h2 class="px-4 sm:px-20 text-center sm:text-left">A propos </h2>
            <img src="/public/images/Design/PlantesTombantesLongues.svg" class="rotate-90 w-[200px] -my-[1200px] hidden sm:block" alt="Dessin Plantes Tombantes">
        </div>
    <div class=" grid grid-cols-1 lg:grid-cols-2">
      <div class="px-4 sm:px-20">
          <div class="flex justify-center items-center flex-col p-10 sm:p-20">
                  <img src="/public/images/PortraitPhoto.jpg" class="h-64 sm:h-96 w-auto" alt="Photo Rose MENEGAIN">
          </div>
      </div>
      <div class="bg-clearbeige p-20">
        <h2>Rose Menegain</h2> 
        <h4 class="text-brown">
            Etudiante en BUT MMI 
        </h4>
        <p class="my-5">
          Après mon Bac STI2D, j'ai donc fait le choix de continuer mes études en BUT MMI (Métiers du Multimédia et de l'Internet). <br>
          Ces études me permettent d'acquérir petit à petit des compétences variées dans les domaines de : <br> 
          La communication, du marketing, du design web, de la conception web, <br> 
          de l'audiovisuel et du développement informatique.
        </p>
        <p class="underline">
          Contactez moi : 
        </p>
        <div class="flex mt-2 sm:mt-5">
                <a href="https://www.instagram.com/eiku_s/">
                    <img src="/public/Icons/Instagram.svg" class="w-8 mr-5 hover:bg-whiteb hover:bg-opacity-75 hover:rounded-sm hover:p-1" alt="Logo Instagram">
                </a>
                <a href="https://www.linkedin.com/in/rose-menegain/">
                    <img src="/public/Icons/Linkedin.svg" class="w-8 mr-5 hover:bg-whiteb hover:bg-opacity-75 hover:rounded-sm hover:p-1" alt="Logo Linkedin">
                </a>
                <p class=" mr-5 hover:bg-whiteb hover:bg-opacity-75 hover:rounded-sm hover:p-1">rose.menegain@gmail.com</p>
          </div>
    </div>
</div>
</section>

<section class="relative first-letter:mx-10 sm:mx-20 mt-10 sm:mt-20">
    <div class="absolute top-0 left-0 w-full h-full bg-blackgreen bg-opacity-75 text-whiteb rounded-lg flex justify-center items-center">
      <h3>En maintenance</h3>
    </div>
    <form id="my-form" class="bg-clearbrown p-6 rounded-lg shadow-md" @submit.prevent="sendEmail">
      <div class="mb-4">
          <label class="block text-blackgreen font-bold mb-2" for="name">Nom</label>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-darkgreen leading-tight focus:outline-none focus:shadow-outline" id="name" type="text" placeholder="Votre nom">
        </div>
        <div class="mb-4">
          <label class="block text-blackgreen font-bold mb-2" for="email">Email</label>
          <input class="shadow appearance-none border rounded w-full py-2 px-3 text-darkgreen leading-tight focus:outline-none focus:shadow-outline" id="email" type="email" placeholder="Votre email">
        </div>
        <div class="mb-6">
          <label class="block text-blackgreen font-bold mb-2" for="message">Message</label>
          <textarea class="shadow appearance-none border rounded w-full py-2 px-3 text-darkgreen leading-tight focus:outline-none focus:shadow-outline" id="message" placeholder="Votre message"></textarea>
        </div>
        <div class="flex justify-end">
          <Bouton class="my-4 sm:my-10" type="submit">
            Envoyer
          </Bouton>
        </div> 
    </form>


</section>



</template>

<script>
export default {
  methods: {
    submitForm() {
      const name = document.getElementById('name').value
      const email = document.getElementById('email').value
      const message = document.getElementById('message').value
      
      console.log(`Nom: ${name}`)
      console.log(`Email: ${email}`)
      console.log(`Message: ${message}`)
    },
    sendEmail() {
      emailjs.sendForm('service_y9mcl0a', '__ejs-test-mail-service__', 'my-form', 'Public Key')
        .then((response) => {
          console.log('SUCCESS!', response.status, response.text);
        }, (error) => {
          console.log('FAILED...', error);
        });
    }
  }
}
</script>
