<template>
    <header class="px-40 ">
        <div class="logo">
            <img src="../assets/boolflix-logo.svg" alt="">
        </div>

        <div class="search-conteiner">
        
            <!-- on focusout class active will be removed  -->
            <div class="search" :class="{active: activeSearch}" @focusout="activeSearch = false">
                <label for="search" @click="activeSearch = true"><i class="fas fa-search"></i></label>
                <input id="search" type="text" placeholder="Inserisci un titolo" v-model.trim="userSearch" @keyup.enter="$emit('searchFilm', userSearch)">
            </div>
        </div>

    </header>

</template>

<script>
export default {
    name: 'Header',

    data() {
        return {
            userSearch: '',
            //for class active on header
            activeSearch: false,
        }
    }
}
</script>

<style scoped lang="scss">
@import '@/styles/vars.scss';

header {
    height: 80px;
    width: 100%;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    background-color: $header-back;
    position: fixed;
    z-index: 999;
    .logo {
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-grow: 1;
        img {
            height: 30px;

        }
    }

    .search-conteiner {
        height: 100%;
        display: flex;
        justify-content: flex-end;
        align-items: center;
        flex-shrink: 1;

    }

    .search {
        height: 40px;
        border-radius: 30px;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        overflow:hidden;
        margin-right: 10px;
        transition: all 0.4s ease;
        label {
            cursor: pointer;
        }
        i {
            margin: 0px 10px;
            font-size: 18px;
            transition: all 0.4s ease
        }

        input {
            height: 100%;
            width: 0;
            background-color: transparent;
            border: none;
            color: black;
            font-size: 14px;
            outline: none;
            transition: all 0.4s ease;
        }

    }

    .active {
        border: 1px solid #006cfa;
        input {
            width: 250px;
        }
        i {
            color: $title
        }
    }
}







</style>