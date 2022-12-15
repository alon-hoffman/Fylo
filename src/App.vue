<template>
  <div  id="app" class="main-layout flex column align-center">
    <app-header />
    <img class="intro-image" src="./assets/imgs/illustration-intro.png" alt="">
    <section class="hero flex column align-center"><h1 class="title">All your files in one secure location,<span class="line-break">
      accessible anywhere.</span></h1>
    
      <button class="main-cta">Get Started</button>
      <section class="demos">
        <div class="demo" v-for="demo in demos">
          <img :src="demo.img" alt="">
          <h1>{{demo.header}}</h1>
        </div>
      </section>
      <section class="image-text flex ">
        <img src="../src/assets/imgs/illustration-stay-productive.png" >
        <div class="text flex column space-between">
          <h1>Stay productive, <br>
            wherever you are</h1>
           
            <a href=""></a>
        </div>
      </section>

      <section class="reviews flex">
        <!-- <img src="../src/assets/imgs/bg-quotes.png" alt=""> -->
        <div class="review" v-for="review in reviews">
          <h2>{{review.body}}</h2>
          <div class="flex reviewer align-center"><img :src="review.profile" alt="">
          <div class="description-written">
          <p>{{review.name}}</p>
          <small>{{review.description}}</small>
        </div>
        </div>
        </div>
      </section>

      <section class="getting-started">
        <h1>Get early access today</h1>
        <p>It only takes a minute to sign up and our free starter tier is extremely generous. If you have any questions, our support team would be happy to help you.</p>
        <input type="text"><button >Get Started for free</button>
      </section>
    </section>

    <footer>
      <img src="../src/assets/imgs/logo.svg" alt=""/>
      <div class="info flex">
        <div class="description">
          <img src="../src/assets/imgs/icon-location.svg" alt="">
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua</p>
        <div>
          <img src="/src/assets/imgs/icon-phone.svg" alt="">
          <small>+1-543-123-4567</small>
        </div>
        
        </div>
        <img src="/src/assets/imgs/icon-email.svg">
        <small>example@fylo.com</small>
      </div>
    </footer>
  </div>
</template>

<script>
  import appHeader from './cmps/app-header.vue';
  export default {
    components: {
      appHeader,
    },
    computed:{
      demos(){
        return [
          {img:'/src/assets/imgs/icon-access-anywhere.svg',
           header:"Access your files anywhere",
           p:"The ability to use a smartphone, tablet, or computer to access your account means your files follow you everywhere."},
           {img:'/src/assets/imgs/icon-security.svg',header:'Security you can trust',
            p:'2-factor authentication and user-controlled encryption are just a couple of the security features we allow to help secure your files.'},
            {img:'/src/assets/imgs/icon-collaboration.svg', header:'Real-time collaboration',
            p:'Securely share files and folders with friends, family and colleagues for live collaboration. No email attachments required.'},
            {img:'/src/assets/imgs/icon-any-file.svg', header:'Store any type of file',
            p:"Whether you're sharing holidays photos or work documents, Fylo has you covered allowing for all file types to be securely stored and shared."}
        ]
      },
      reviews(){
        return[
          {body:'Fylo has improved our team productivity by an order of magnitude. Since making the switch our team has become a well-oiled collaboration machine.',
        profile:'/src/assets/imgs/profile-1.jpg', name:'Satish Patel',description:'Founder & CEO, Huddle'},
          {body:'Fylo has improved our team productivity by an order of magnitude. Since making the switch our team has become a well-oiled collaboration machine.',
          profile:'/src/assets/imgs/profile-2.jpg',name:'Bruce McKenzie', description:'Founder & CEO, Huddle'},
          {body:'Fylo has improved our team productivity by an order of magnitude. Since making the switch our team has become a well-oiled collaboration machine.',
          profile:'/src/assets/imgs/profile-3.jpg',name:'Iva Boyd', description:'Founder & CEO, Huddle'}
        ]
      }
    }
  };
</script>
