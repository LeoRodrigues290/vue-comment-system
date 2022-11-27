<template>
  <div>
    <section class="box-comment-content">
      <div class="container mt-5">
        <div class="d-flex justify-content-center row">
          <div class="col-md-8">
            <div class="d-flex flex-column comment-section" id="myGroup">
              <div class="bg-white p-2">
                <div class="d-flex flex-row user-info">
                  <img class="rounded-circle"
                       src="https://avatars.githubusercontent.com/u/89982099?s=400&u=903eb282e1d5151ce12a5e008acfe6de0b35bed2&v=4"
                       width="50">
                  <div class="d-flex flex-column justify-content-start ms-2"><span
                      class="d-block font-weight-bold name">Léo R.</span><span
                      class="date text-black-50">Publicado - Novembro 2022</span></div>
                </div>
                <div class="mt-2">
                  <p class="comment-text">Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do
                    eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
                    quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.</p>
                </div>
              </div>
              <div class="bg-white">
                <div class="d-flex flex-row fs-12">
                  <a target="_blank" href="https://github.com/LeoRodrigues290/vue-comment-system" class="like p-2 cursor">
                    <span class="ms-1">Curtir</span>
                  </a>
                  <a class="like p-2 cursor link-info action-collapse" data-toggle="collapse"
                     aria-expanded="true"
                     aria-controls="collapse-1" href="#collapse-1">
                    <span class="ml-1">Comentar</span>
                  </a>
                </div>
              </div>
              <div id="collapse-1" class="bg-light p-3 rounded collapse" data-parent="#myGroup">
                <div class="d-flex flex-row align-items-start">
                  <img class="rounded-circle me-2" src="https://cdn-icons-png.flaticon.com/512/149/149071.png"
                       width="40" alt="imagem-ilustrativa">
                  <div class="w-100">
                    <input v-model="name" class="form-control ml-1 shadow-none textarea mb-2" type="text">
                    <textarea v-model="message"
                              class="form-control ml-1 shadow-none textarea">
                          </textarea>
                  </div>
                </div>
                <div class="mt-2 text-right ms-4">
                  <button v-on:click="addComment" class="btn ms-4 btn-primary btn-sm shadow-none" type="button">
                    Postar Comentário
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
    <section class="comments-content">
      <div class="container mt-5">
        <div class="row  d-flex justify-content-center">
          <div class="col-md-8">
            <div v-for="(comment, index) in comments" :key="index" class="card p-3 px-4 mb-2">
              <div class="d-flex justify-content-between align-items-center">
                <div class="user d-flex flex-row align-items-center">
                  <img src="https://cdn-icons-png.flaticon.com/512/149/149071.png" width="30"
                       class="user-img rounded-circle me-2">
                  <span>
                                <small class="font-weight-bold text-primary">{{ comment.name }}</small>
                            </span>
                </div>
                <small>Agora</small>
              </div>
              <div class="my-3">
                {{ comment.message }}
              </div>
              <div class="action d-flex justify-content-between mt-2 align-items-center">
                <div class="reply">
                  <a href="#" v-on:click="removeComment" class="btn pb-2 btn-danger btn-sm shadow-none">
                    <small>Apagar</small>
                  </a>
                  <span class="dots"></span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comments: [],
      name: '',
      message: '',
    }
  },
  methods: {
    addComment() {
      if (this.name.trim() === '' || this.message.trim() === '') {
        return;
      }
      this.comments.push({
        name: this.name,
        message: this.message
      })

      this.name = '';
      this.message = '';
    },
    removeComment(index) {
      this.comments.splice(index, 1)
    }
  },
}
</script>