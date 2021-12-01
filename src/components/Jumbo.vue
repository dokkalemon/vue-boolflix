<template>
  <section class="jumbo ">
      <div class="img">
        <img src="https://image.tmdb.org/t/p/original/wEmexPKgF2sgYvvl6MxI5rTn2qM.jpg" alt="">
    </div>

    <div class="description-container px-40">
        <div class="description">
            <div class="title">
                <h1>TROY</h1>
            </div>
            <div class="text">
                <p>Nel 1193 A.C., Paride, principe di Troia, rapisce Elena, regina di Sparta e moglie di Menelao. Questo sarŕ l'evento che scatenerŕ la guerra tra la Grecia micenea e Troia, una guerra lunga dieci anni che vedrà protagonisti due eroi contrapposti: Achille per i greci ed Ettore per i troiani.</p>
            </div>
            <div class="button">
                <button><i class="fas fa-play"></i> RIPRODUCI ORA</button>
                <button><i class="fas fa-info-circle"></i> ALTRE INFO</button>
            </div>
        </div>
    </div>

  </section>
</template>

<script>
export default {
    name: 'Jumbo',

    props: {
        pathBackdropFilm: String,
        pathBackdropSeries: String,
    }
    
    }
</script>


<style scoped lang="scss">
@import '@/styles/vars.scss';

.jumbo {
    height: 100vh;
    width: 100%;
    padding-top: 80px;
    position: relative;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    
    .img {
        position: absolute;
        top: 0;
        height: 100%;
        width: 100%;
        z-index: 1;
        img {
            height: 100%;
            width: 100%;
            object-fit: cover;
            position: relative;
            filter: brightness(50%);
        }
    }
    .description-container {
        width: 100%;
        position: relative;
        z-index: 20;
        .description {
            width: 35%;
            border-radius: 30px;
            padding: 20px;
            background-color: rgba(0, 0, 0, 0.726);
            .title {
                h1 {
                    color: $text;
                    font-size: 60px;
                    padding: 10px;
                }
            }
            .text {
                p {
                    color: $text;
                    font-size: 20px;
                    padding: 10px;
                }
            }
            .button {
                padding-top: 30px;
                button {
                    padding: 15px 10px;
                    font-size: 18px;
                    width: 48%;
                    margin-right: 10px;
                    background-color: $primary-button-back;
                    border-radius: 10px;
                    border: 1px solid $primary-button-back; 
                    color: $primary-button-text;
                    cursor:pointer;
                    transition: all 0.4s ease;
                    &:hover {
                        background-color: $background;
                    }
                    &:last-child {
                        margin-right: none;
                        background-color: transparent;
                        border: 1px solid $secondary-button-border;
                        color: $secondary-button-text;
                    }
                    &:last-child:hover {
                        background-color: $secondary-button-border;
                        color: white;
                    }
                }
            }
        
        }
        
    }

}

</style>