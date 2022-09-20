<template>
  <div class="wrapper">
    <section class="sBar">
      <SideBar />
    </section>

    <section class="content">

      <div class="avatar">
        <img src="https://mdbcdn.b-cdn.net/img/new/avatars/2.webp" class="avatar rounded-circle" style="width: 150px;"
          alt="Avatar" />
      </div>


      <ul class="d-flex mapList">
        <li> <span>Published</span></li>
        <li><span>Scheduled</span></li>
        <li><span>Need Approval</span></li>
        <li><span>Error</span></li>
        <li><span>Notes</span></li>
      </ul>

      <div class="container">

        <div class="row" v-for="(date,id) in posts" :key="id">
          <h1 class="text-start">{{formattedDate(id)}}</h1>


          <div class="col-4" v-for="(post,idx) in date" :key="idx">
            <!-- {{id}}
            {{idx}} -->


            <div class="card d-flex flex-row">

              <div class="card-side" :class=" 
              post.status==0 && 'approval' ||
              post.status==1 && 'scheduled' ||
              post.status==2 && 'notes' ||
              post.status==3 && 'published' ||
              post.status==4 && 'error'
              ">
                <div class="logo" v-if="post.account.channel==='instagrambusiness'"><i class="bi bi-instagram"></i>
                </div>
                <div class="logo" v-if="post.account.channel==='twitter'"><i class="bi bi-twitter"></i></div>
                <div class="logo" v-if="post.account.channel==='facebook'"><i class="bi bi-facebook"></i></div>

              </div>

              <div class="card-content">

                <div class="card-body">

                  <div class="card-top d-flex flex-row">
                    <h5 class="card-text mb-3 text-start opacity-75 w-75">{{cardDate(post.published_at)}}</h5>
                    <ul v-if="post.status==3" class="d-flex list-unstyled ">
                      <li class="ms-5"><a @click="deletePost(id, idx)"><i class="bi bi-trash "></i> </a> </li>
                      <li><a> <i class="bi bi-three-dots"></i></a></li>

                    </ul>
                    <ul v-if="post.status==1" class="d-flex list-unstyled ">
                      <li><a><i class="bi bi-slash-circle"></i> </a> </li>
                      <li><a><i class="bi bi-trash"></i> </a></li>
                      <li><a> <i class="bi bi-three-dots"></i></a></li>

                    </ul>
                    <ul v-if="post.status==0" class="d-flex list-unstyled ">
                      <li><a><i class="bi bi-check-lg"></i> </a> </li>
                      <li><a><i class="bi bi-trash"></i></a></li>
                      <li><a> <i class="bi bi-three-dots"></i></a></li>

                    </ul>


                  </div>


                  <p class="card-text text-start text-muted">{{post.entry.message}}</p>

                </div>

                <img class="img" :src="post.entry.image" @error="setAltImg" alt="Card image cap">
                <ul v-if="idx==1" class="d-flex justify-content-between w-75 mt-4 actions list-unstyled">
                  <li> <a class="heart" @click="likeAction"> <i aria-hidden="true" class="bi bi-heart"></i></a></li>
                  <li> <a class="repeat"><i class="bi bi-repeat"></i></a> </li>
                  <li><a class="chat"><i class="bi bi-chat"></i></a> </li>
                  <li><a class="eye"><i class="bi bi-eye"></i></a> </li>
                </ul>
                <ul v-else class="d-flex justify-content-between w-75 mt-4 actions list-unstyled">
                  <li><a class="like"><i class="bi bi-hand-thumbs-up"></i></a> </li>
                  <li><a class="chat"><i class="bi bi-chat"></i></a> </li>
                  <li><a class="share"><i class="bi bi-share"></i></a> </li>
                  <li><a class="eye"><i class="bi bi-eye"></i></a> </li>

                </ul>

              </div>


            </div>
          </div>
          <!-- <div class="col-4">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">Special title treatment</h5>
              <p class="card-text">With supporting text below as a natural lead-in to additional content.</p>
              <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </div>
        <div class="col-4">
          <div class="card">
            <div class="card-body">
              <h5 class="card-title">Special title treatment</h5>
              <p class="card-text">With supporting text below as a natural lead-in to additional content.</p>
              <a href="#" class="btn btn-primary">Go somewhere</a>
            </div>
          </div>
        </div> -->

        </div>
      </div>
    </section>


  </div>
</template>

<script>
import json from "../data.json"
import SideBar from '../components/SideBar.vue';
import altimg from "../assets/no-post-image.png";

import moment from "moment";

export default {
  name: "TaskHome",

  components: { SideBar },
  data() {
    return {
      posts: json.posts_by_date,
    }
  },
  mounted() {
    console.log(this.posts);
  },
  methods: {
    formattedDate(date) {
      return moment(date).format('D MMMM YYYY');
    },
    cardDate(date) {
      return moment(date).format('D MMMM YYYY - HH:mm');
    },

    setAltImg(event) {
      event.target.src = altimg
    },
    likeAction(event) {
      event.target.classList.toggle('active')
    },
    deletePost(id, idx) {

      console.log(this.posts[id][idx]);
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
@import url('https://fonts.googleapis.com/css2?family=Barlow+Semi+Condensed&family=Raleway&display=swap');

:root {
  --publishedColor: rgba(172, 172, 172, 1);
  --scheduledColor: rgba(58, 193, 131, 1);
  --approvalColor: rgba(247, 191, 56, 1);
  --errorColor: rgba(251, 100, 80, 1);
  --notesColor: rgba(103, 177, 242, 1);
}

.wrapper {
  display: flex;
  width: 100%;
  height: 100%;
  overflow: hidden;
  background-color: var(--bgcolor);
}

.content {
  margin-left: 19.5rem;
}

.avatar{
  width: 75px !important;
  position:fixed;
  top: 3%;
  right: 3%;
}

.mapList {
  list-style: none;
}

.mapList li {
  margin-top: 2rem;
  margin-left: 2.5rem;
}

.mapList li span {
  position: relative;
  bottom: 5.5px;
}

.mapList li::before {
  content: "\2022";
  font-weight: bold;
  font-size: 2rem;
  display: inline-block;
  width: .7em;
  margin-left: -1em;

}

.mapList li:nth-child(1)::before {
  color: var(--publishedColor);
}

.mapList li:nth-child(2)::before {
  color: var(--scheduledColor);
}

.mapList li:nth-child(3)::before {
  color: var(--approvalColor);
}

.mapList li:nth-child(4)::before {
  color: var(--errorColor);
}

.mapList li:nth-child(5)::before {
  color: var(--notesColor);
}

.container .row {
  margin-top: 1.5rem;
}

.container .row h1 {
  font-family: 'Barlow Semi Condensed', sans-serif;
  font-size: 22px;
  color: #959595;
}

.card {
  border: 0 !important;
  overflow: hidden;
  width: 372px !important;
  height: 450px !important;
}

.card-content {
  width: 100%;
}

.card-content .img {
  width: 287px;
  height: 240px;
}

.card-content .card-body .card-text {
  font-family: 'Raleway', sans-serif;
  font-weight: 700;
  color: #959595;
  width: 284px;
  height: 34;
  font-size: .9rem;
}

.card-body a {
  cursor: pointer;
}

.card-top ul li {
  margin-right: 1rem;
}

.card .published {
  background-color: var(--publishedColor);
}

.card .scheduled {
  background-color: var(--scheduledColor);
}

.card .approval {
  background-color: var(--approvalColor);
}

.card .error {
  background-color: var(--errorColor);
}

.card .notes {
  background-color: var(--notesColor);
}


.actions li:nth-child(1) {
  margin-left: 20px;
}

.actions li:nth-child(4) {
  margin-right: 30px;
}

.logo {
  width: 50px;
  position: relative;
  top: 50%;
  transform: translateY(-50%);
}



/* Icon Animations */

.actions a {
  display: inline-block;
}

.actions a:hover {
  animation: heart 1s ease-in infinite;

}

.actions a.active {

  animation: like 0.5s 1;

  color: red;
  border-radius: 100%;
  stroke: none;
}

@keyframes like {
  0% {
    transform: scale(1);
  }

  90% {
    transform: scale(1.2);
  }

  100% {
    transform: scale(1.1);
  }
}

@keyframes heart {
  0% {
    transform: scale(1);
  }

  50% {
    transform: scale(1.1);
  }

  100% {
    transform: scale(1);
  }
}
</style>
