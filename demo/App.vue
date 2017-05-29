<template>
    <div id="app">
        <!--Example dependecies-->
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.4.1/css/bulma.min.css">
        <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
        <a :href="base.repoUrl"><img
                style="position: absolute; top: 0; right: 0; border: 0;"
                src="https://camo.githubusercontent.com/38ef81f8aca64bb9a64448d0d70f1308ef5341ab/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6461726b626c75655f3132313632312e706e67"
                alt="Fork me on GitHub"
                data-canonical-src="https://s3.amazonaws.com/github/ribbons/forkme_right_darkblue_121621.png"></a>

        <!--Example Elements-->
        <section class="hero">
            <div class="hero-body" style="padding: 1rem 0">
                <div class="container">
                    <div class="columns">
                        <div class="column is-8 is-offset-3" style="display: flex; align-items: center;">
                            <div class="is-pulled-left">
                                <img width="350px" src="./assets/logo.png">
                            </div>
                            <div class="is-pulled-left" style="text-align: left">
                                <h1 class="title text-medium-grey" style="margin-bottom: .5rem">
                                    {{base.title}}
                                </h1>
                                <hr class="is-marginless">
                                <h2 class="subtitle text-light-grey" style="margin-top: .5rem">
                                    A {{base.subTitle}}
                                </h2>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section class="section" style="padding-top: .5rem">
            <div class="container">
                <div class="columns">
                    <div class="column is-8 is-offset-2">
                        <div class="box formated">
                            <div class="heading">
                                <div class="columns">
                                    <div class="column">
                                        <i class="material-icons top-left">code</i>
                                        <span class="is-pulled-right"><b>Example</b></span>
                                    </div>
                                </div>
                            </div>
                            <div class="content">
                                <div class="columns">
                                    <div class="column">
                                        <div class="field is-horizontal">
                                            <div class="field-label is-normal">
                                                <label class="label">Label</label>
                                            </div>
                                            <div class="field-body">
                                                <div class="field">
                                                    <p class="control">
                                                        <input type="text" class="input" v-model="label">
                                                    </p>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="field is-horizontal">
                                            <div class="field-label is-normal">
                                                <label class="label">Timeout</label>
                                            </div>
                                            <div class="field-body">
                                                <div class="field">
                                                    <p class="control">
                                                        <input class="input" type="text" placeholder="2000" v-model="timeOut">
                                                    </p>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                    <div class="column">
                                        <div class="field is-horizontal">
                                            <label style="margin-right: 1rem"><h6><b>Overlay</b></h6></label>
                                            <div class="field">
                                                <p class="control">
                                                    <label class="radio">
                                                        <input type="radio" name="question" :value="true" checked v-model="overlay">
                                                        Yes
                                                    </label>
                                                    <label class="radio">
                                                        <input type="radio" name="question" :value="false" v-model="overlay">
                                                        No
                                                    </label>
                                                </p>
                                            </div>
                                        </div>
                                        <button class="button is-primary" style="width: 100%" @click="showMe">Show loader</button>
                                    </div>
                                </div>
                                <div class="columns">
                                    <div class="column has-text-centered">
                                        <a :href="base.repoUrl">Installation & Code usage</a>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>
        <loading
            :show="show"
            :label="label"
            :overlay="overlay">

        </loading>
        <footer class="footer">
            <div class="container">
                <div class="content has-text-centered">
                    <p>
                        <strong>{{base.title}} {{base.subTitle}}</strong> by <a
                            :href="base.teamUrl">Pygmy Team</a>.
                    </p>
                    <p v-if="base.dependencies.length > 0">
                        <small>Used dependencies for this demo:
                            <template v-for="dep in base.dependencies">
                            <a :href="dep.url">{{dep.name}}</a>
                                |
                            </template>
                        </small>
                    </p>
                </div>
            </div>
        </footer>
    </div>
</template>

<script>
    import Loading from '../src/Loading.vue';

    const base = {
        title : 'Full Loading Spinner',
        subTitle : 'Vue Component',
        teamUrl : 'https://github.com/PygmySlowLoris',
        repoUrl : 'https://github.com/PygmySlowLoris/vue-full-loading',
        dependencies : [
            {
                name: 'bulma',
                url: 'http://bulma.io'
            }
        ]
    };

    export default {
        name: 'app',
        components: {
            Loading
        },
        data(){
            return {
                base,
                show: false,
                label: 'Loading...',
                timeOut: 2000,
                overlay: true
            }
        },
        methods: {
            showMe()
            {
                this.show = true;

                setTimeout(() => {
                    this.show = false;
                }, this.timeOut)
            }
        }
    }
</script>

<style scoped>
    #app {
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }

    .pointer {
        cursor: pointer;
    }

    h1, h2 {
        font-weight: normal;
    }

    hr {
        background-color: transparent;
        border: none;
        display: block;
        height: inherit;
        margin: 1.5rem 0;
        border-top: dashed 1px;
    }


    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #0b99b9;
        text-decoration: underline;
    }

    .text-medium-grey {
        color: #333;
    }

    .text-light-grey {
        color: #888;
    }

    .box.formated {
        position: relative;
        padding: 0;
    }

    .box.formated .heading {
        font-size: 1rem;
        text-transform: capitalize;
        padding: .8rem 1.5rem;
        background-color: #fafafa;
    }

    .box.formated .content {
        padding: 1rem 2rem;
    }

    i.top-left {
        position: absolute;
        left: 1.5rem;
        top: 0.8rem;
    }

    .vertical-separator {
        display: flex; justify-content: space-around;
    }

    .vertical-separator .line {
        border-right: 1px solid #cccccc;
    }
</style>
