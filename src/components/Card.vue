<template>
        <section class="card-container">
            <div class="card ">

                <!-- img -->
                <div class="poster">
                    <img :src="image" alt="">
                </div>

            <!-- Card info -->
            <div class="info">
                <div class="title">
                    <h4>{{ title}}</h4>
                </div>

                <!-- overview -->
                <div class="overview">
                    <p>{{ overwiew }}</p>
                </div>

                <!-- vote and flag -->
                <div class="vote-flag">
                    <div class="vote">
                        <!-- v-for for stars -->
                       <i class="fas fa-star" v-for="(item, index) in Math.round(vote / 2)" :key="`id${index}`"></i>
                    </div>

                        <!-- v-if for flag or only abbreviation  -->
                        <img v-if="isFlag" :src="require(`../assets/${language}.png`)" alt="">
                        <span v-else> {{language}} </span>
                </div>

                <!-- button control -->
                <div class="user-control">
                    <i class="fas fa-play"></i>
                    <i class="fas fa-plus"></i>
                    <i class="fas fa-info" @click="$emit('getId', id)" ></i>
                </div>
            </div>
        </div>
        </section>

</template>

<script>

export default {
    name: 'Card',
    
    props: {
        title: String,
        originalTitle: String,
        language: String,
        vote: Number,
        image: String,
        id: Number,
        overwiew: String,
    },

    computed: {
        isFlag() {
            return this.availableFlag.includes(this.language)
        }
    },

    data() {
        return {
            //array languages
            availableFlag: ['it', 'en'],
        }
    },

    methods: {
    }
}
</script>

<style scoped lang="scss">
@import '@/styles/vars.scss';
.card-container {
    margin-top: 30px;
    width: calc(100% /5);
    padding: 5px;
    display: flex;
    flex-direction: column;
    position: relative;
    left: 0px;
    .card {
        height: 200px;
        width: 100%;
        position: relative;
        border-radius: 10px;
        overflow: hidden;
        cursor: pointer; 
        transition: all 0.4s ease;

        .poster {
            height: 100%;
            width: 100%;
            position: absolute;
            z-index: 0;
            img {
                height: 100%;
                width: 100%;
                object-fit: cover;
            }
        }

        .info {
            padding: 5px;
            min-height: 200px;
            width: 100%;
            background-color: #001632d8;
            color: white;
            display: flex;
            flex-direction: column;
            justify-content: center;
            opacity: 1;
            position: relative;
            bottom: 0;
            z-index: 22;
            opacity: 0;
            transition: all 0.4s ease;
            .title {
                display: flex;
                justify-content: flex-start;
                
                h4 {font-size: 11px;};
            }
            .overview {
                p {
                    font-size: 7px;
                    margin-bottom: 10px;
                }
            }
            .vote-flag {
                width: 100%;
                display: flex;
                align-items: center;
                justify-content: space-between;
                .vote {
                    display: flex;
                    align-items: center;
                    i {
                        font-size: 9px;
                        color: $secondary-button-border;
                    }
                }
                    img {
                        height: 10px;
                    }
            }
            .user-control {
                padding: 10px 0;
                width: 100%;
                font-size: 10px;
                display: flex;
                justify-content: flex-end;
                align-items: center;
                i {
                    border: 1px solid $secondary-button-border;
                    color: $secondary-button-border;
                    border-radius: 100%;
                    height: 20px;
                    width: 20px;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    margin-left: 5px;
                    &:hover {
                        color: white;
                        border: 1px solid white;
                    }
                }
            }
        }
    &:hover {
        height: auto;
        position: absolute;
        min-height: 200px;
        transform: scale(1.8);
        z-index: 30;
        box-shadow: 5px 0px 15px rgb(0, 0, 0);
        .info {
            opacity: 1;
            height: 100%;;
        }
    }
    }
}








ul {
    li {
        img {
            height: 15px;
        }
        .poster {
            img {
            height: auto
        }
        }
        
    }
}

</style>