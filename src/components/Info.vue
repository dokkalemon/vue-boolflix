<template>
      <div class="info-container" :class="{active: activeInfo}">
          <div class="info-content">
              <div class="info-cover">
                  <img :src="`https://image.tmdb.org/t/p/w1280/${infoFilm.backdrop_path}`" alt="">
                  <div class="info-cover-philter"></div>
              </div>
              <div class="info-text">
                  <div class="title">
                      <h2 v-if="infoFilm.title != null">{{ infoFilm.title }}</h2>
                      <h2 v-else>{{ infoFilm.name }}</h2>
                  </div>
                  <div class="buttons">
                      <button><i class="fas fa-play"></i> RIPRODUCI</button>
                      <i class="fas fa-plus"></i>
                      <i class="far fa-thumbs-up"></i>
                      <i class="fas fa-thumbs-down"></i>
                  </div>
                  <div class="info-film ">
                      <div class="info-film-item years ">
                          <span v-if="infoFilm.release_date != null">{{ infoFilm.release_date }}</span><span v-else>{{ infoFilm.first_air_date }}</span> &nbsp;&nbsp;&nbsp; <span v-if="infoFilm.runtime != null">{{ infoFilm.runtime }} min.</span><span v-else>{{ infoFilm.number_of_episodes }} Episodi, {{infoFilm.number_of_seasons}} Stagioni</span>
                      </div>
                      <div class="info-film-item genre  ">
                          <p>Cast: <span v-for="(item, index) in nameActor.slice(0, 5)" :key="`actor${index}`"> {{item.name}}, </span></p>
                          <p>Genere: <span v-for="(item, index) in infoFilm.genres" :key="`genre${index}`">{{item.name}}, </span></p>
                      </div>
                  </div>
                  <div class="overview">
                      <p>{{ infoFilm.overview }}</p>
                  </div>
                  <div class="related ">
                      <h3>Film Correlati:</h3>
                      <div class="related-film ">
                          <div class="related-film-scroll">
                              <div class="card-container" v-for="(item, index) in relatedFilm.slice(0, 6)" :key="`related${index}`">
                                  <div class="card" >
                                      <div class="card-cover">
                                            <img :src="`https://image.tmdb.org/t/p/w1280/${item.poster_path}`" alt="">
                                      </div>
                                      <h4>{{item.title}}</h4>
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
export default {
    name: 'Info',

    props: {
        activeInfo: Boolean,
        infoFilm: Object,
        nameActor: Array,
        relatedFilm: Array,
    }
    
}
</script>

<style scoped lang="scss">
@import '@/styles/vars.scss';

    .info-container {
        position: fixed;
        top: 200%;
        left: 50%;
        transform: translate(-50%, -50%);
        height: 80%;
        width: 700px;
        background-color: $background;
        overflow: auto;
        border-radius: 10px;
        box-shadow: 10px 0 15px rgba(0, 0, 0, 0.808);
        transition: all 1s ease;
        .info-content {
            width: 100%;
            position: relative;
            .info-cover {
                height: 300px;
                width: 100%;
                z-index: 0;
                position: absolute;
                top: 0;
                img {
                    height: 100%;
                    width: 100%;
                    object-fit: cover;
                }
                .info-cover-philter {
                    height: 100%;
                    width: 100%;
                    background-image: linear-gradient(rgba(0, 0, 255, 0), $background);
                    position: absolute;
                    top: 0;
                }
            }
            .info-text {
                padding: 0px 20px;
                position: relative; 
                z-index: 10;
                padding-top: 240px;
                display: flex;
                flex-direction: column;
                h2 {
                    color: $text;
                    font-size: 50px;
                    text-transform: uppercase;
                    font-weight: 400;
                    line-height: 50px;
                    margin-bottom: 20px;
                }
                .buttons {
                    display: flex;
                    justify-content: flex-start;
                    align-items: center;
                    button {
                        background-color: transparent;
                        border: 1px solid $secondary-button-border;
                        border-radius: 10px;
                        padding: 10px 20px;
                        font-size: 15px;
                        color: $secondary-button-border;
                        cursor: pointer;
                        transition: all 0.2s linear;
                        i {
                            color: $secondary-button-text;
                            border: none;
                            font-size: 15px;
                            height: 0;
                            width:auto;
                            display: inline;
                            margin: 0;
                            transition: all 0.2s linear;
                        }
                        &:hover {
                            background-color: $secondary-button-border;
                            color: $background;
                            i {
                                color: $background;
                            }
                        }
                    }
                    i {
                        color: white;
                        font-size: 20px;
                        border: 1px solid white;
                        height: 35px;
                        width: 35px;
                        border-radius: 100%;
                        display: flex;
                        justify-content: center;
                        align-items: center;
                        margin-left: 10px;
                        transition: all 0.2s linear;
                        cursor: pointer;
                        &:hover {
                            transform: scale(1.2)
                        }
                    }

                }
                .info-film {
                    margin-top: 30px;
                    display: flex;
                    .info-film-item {
                        width: 100%;
                        height: 100%;
                        color: $link;
                        font-size: 16px;
                        font-weight: 300;
                        p {
                            margin-bottom: 10px;
                            span {
                                font-weight: 700
                            }
                        }
                    }
                    .years {
                        width: 60%
                    }
                    .genre {
                        width: 40%;
                    }
                }
                .overview {
                    margin-top: 20px;
                    p {
                        color: $text;
                        font-weight: 300;
                    }
                }
                .related {
                    width: 100%;
                    margin-top: 30px;
                    h3 {
                        color: $text;
                        font-weight: 400;
                    }
                        .related-film {

                            width: 100%;
                            overflow-x: auto;
                            overflow-y: hidden;
                            margin-top: 10px;
                            .related-film-scroll {
                                height: 100%;
                                width: 200%;
                                .card-container {
                                    display: inline-block;;
                                    height: 100%;
                                    width: calc(100% / 6);
                                    padding: 10px;
                                    .card {
                                        height: 100%;
                                        width: 100%;
                                        
                                        .card-cover {
                                            border-radius: 10px;
                                            overflow: hidden;
                                            height: 300px;
                                            width: 100%;
                                            img {
                                                height: 100%;
                                                width: 100%;
                                                object-fit: cover;
                                            }
                                        }
                                        h4 {
                                            text-align: center;
                                            color: $text;
                                            font-weight: 300;
                                            margin-top: 5px;
                                            text-transform: capitalize;
                                        }
                                    }
                                }
                            }
                        }

                }

                .more-info {
                    height: 400px;
                    margin-top: 30px;
                    h3 {
                        color: $text;
                        font-weight: 400;

                    }
                }


            }
        }
    }
.active {
    top: 50%;
}

</style>