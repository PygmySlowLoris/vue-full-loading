<template>
    <transition
            enter-active-class="animated fadeIn"
            leave-active-class="animated fadeOut"
    >
        <div v-if="showing" :class="{[overlayClass]: overlay}">
            <slot name="loading-container">
                <div :class="loaderClass">
                    <slot name="loading-text">
                        <div class="pulled-left" v-html="label"></div>
                    </slot>
                    <slot name="loading-spinner">
                        <div class="wrapper">
                            <div class="spinner-container">
                                <div class="spinner-layer spinner-layer--blue">
                                    <div class="spinner-clipper spinner-clipper--left">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner--patch">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner-clipper spinner-clipper--right">
                                        <div class="spinner-circle"></div>
                                    </div>
                                </div>

                                <div class="spinner-layer spinner-layer--red">
                                    <div class="spinner-clipper spinner-clipper--left">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner--patch">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner-clipper spinner-clipper--right">
                                        <div class="spinner-circle"></div>
                                    </div>
                                </div>

                                <div class="spinner-layer spinner-layer--yellow">
                                    <div class="spinner-clipper spinner-clipper--left">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner--patch">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner-clipper spinner-clipper--right">
                                        <div class="spinner-circle"></div>
                                    </div>
                                </div>

                                <div class="spinner-layer spinner-layer--green">
                                    <div class="spinner-clipper spinner-clipper--left">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner--patch">
                                        <div class="spinner-circle"></div>
                                    </div>
                                    <div class="spinner-clipper spinner-clipper--right">
                                        <div class="spinner-circle"></div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </slot>
                </div>
            </slot>
        </div>
    </transition>
</template>

<script>
    export default {
        props: {
            label: {
                default: 'Loading...'
            },
            show: {
                default: false
            },
            overlay: {
                default: true
            },
            loaderClass: {
                default: 'loader-wrapper'
            },
            overlayClass: {
                default: 'white-overlay'
            },
            // central event bus
            eventBus: {
                default: null
            },
            eventShow: {
                default: 'show-full-loading'
            },
            eventHide: {
                default: 'hide-full-loading'
            }
        },
        data() {
            return {
                showing: false
            }
        },
        watch: {
            show(val){
                this.showing = val;
            }
        },
        methods: {
            showMe() {
                this.showing = true
            },
            hideMe() {
                this.showing = false
            },
            // Register eventBus methods.
            registerBusMethods()
            {
                this.eventBus.$on(this.eventShow, this.showMe);
                this.eventBus.$on(this.eventHide, this.hideMe);
            }
        },
        mounted() {
            // If event bus, register methods.
            if (this.eventBus)
                this.registerBusMethods();

        }
    }
</script>
<style scoped>
    .white-overlay {
        background-color: rgba(255, 255, 255, 0.75);
        z-index: 9999;
        top: 0;
        left: 0;
        height: 100vh;
        width: 100vw;
        position: fixed;
        margin: 0;
    }

    .loader-wrapper {
        position: absolute;
        display: inline-block;
        right: 10vw;
        bottom: 10vh;
    }

    .pulled-left {
        float: left;
        padding: 10px 20px
    }

    *, *:before, *:after {
        box-sizing: border-box;
    }

    .wrapper {
        position: relative;
        display: inline-block;
        width: 40px;
        height: 40px;
        font-size: 0;
    }

    .spinner-container {
        width: 100%;
        height: 100%;
        -webkit-animation: container-rotate 1568ms linear infinite;
        animation: container-rotate 1568ms linear infinite;
    }

    @keyframes container-rotate {
        to {
            transform: rotate(360deg);
        }

    ;
    }

    .spinner-layer {
        position: absolute;
        width: 100%;
        height: 100%;
        opacity: 0;
    }

    .spinner-layer--blue {
        border-color: #4285f4;
        -webkit-animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, blue-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
        animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, blue-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
    }

    .spinner-layer--red {
        border-color: #db4437;
        -webkit-animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, red-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
        animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, red-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
    }

    .spinner-layer--yellow {
        border-color: #f4b400;
        -webkit-animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, yellow-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
        animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, yellow-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
    }

    .spinner-layer--green {
        border-color: #0f9d58;
        -webkit-animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, green-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
        animation: fill-unfill-rotate 5332ms cubic-bezier(.4, 0, .2, 1) infinite both, green-fade-in-out 5332ms cubic-bezier(.4, 0, .2, 1) infinite both;
    }

    @keyframes fill-unfill-rotate {
        12.5% {
            transform: rotate(135deg);
        }

        25% {
            transform: rotate(270deg);
        }

        37.5% {
            transform: rotate(405deg);
        }

        50% {
            transform: rotate(540deg);
        }

        62.5% {
            transform: rotate(675deg);
        }

        75% {
            transform: rotate(810deg);
        }

        87.5% {
            transform: rotate(945deg);
        }

        to {
            transform: rotate(1080deg);
        }

    ;
    }

    @keyframes blue-fade-in-out {
        from {
            opacity: 1;
        }

        25% {
            opacity: 1;
        }

        26% {
            opacity: 0;
        }

        89% {
            opacity: 0;
        }

        90% {
            opacity: 1;
        }

        100% {
            opacity: 1;
        }

    ;
    }

    @keyframes red-fade-in-out {
        from {
            opacity: 0;
        }

        15% {
            opacity: 0;
        }

        25% {
            opacity: 1;
        }

        50% {
            opacity: 1;
        }

        51% {
            opacity: 0;
        }

    ;
    }

    @keyframes yellow-fade-in-out {
        from {
            opacity: 0;
        }

        40% {
            opacity: 0;
        }

        50% {
            opacity: 1;
        }

        75% {
            opacity: 1;
        }

        76% {
            opacity: 0;
        }

    ;
    }

    @keyframes green-fade-in-out {
        from {
            opacity: 0;
        }

        65% {
            opacity: 0;
        }

        75% {
            opacity: 1;
        }

        90% {
            opacity: 1;
        }

        100% {
            opacity: 0;
        }

    ;
    }

    .spinner-clipper {
        position: relative;
        display: inline-block;
        width: 50%;
        height: 100%;
        overflow: hidden;
        border-color: inherit;
    }

    .spinner-circle {
        position: absolute;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        width: 200%;
        height: 100%;
        border-color: inherit;
        border-bottom-color: transparent !important;
        border-style: solid;
        border-width: 4px;
        border-radius: 50%;
        -webkit-animation: none;
        animation: none;
    }

    .spinner-clipper--left .spinner-circle {
        border-right-color: transparent !important;
        transform: rotate(129deg);
        -webkit-animation: left-spin 1333ms cubic-bezier(.4, 0, .2, 1) infinite both;
        animation: left-spin 1333ms cubic-bezier(.4, 0, .2, 1) infinite both;
    }

    .spinner-clipper--right .spinner-circle {
        left: -100%;
        border-left-color: transparent !important;
        transform: rotate(-129deg);
        -webkit-animation: right-spin 1333ms cubic-bezier(.4, 0, .2, 1) infinite both;
        animation: right-spin 1333ms cubic-bezier(.4, 0, .2, 1) infinite both;
    }

    @keyframes left-spin {
        from {
            transform: rotate(130deg);
        }

        50% {
            transform: rotate(-5deg);
        }

        to {
            transform: rotate(130deg);
        }

    }

    @keyframes right-spin {
        from {
            transform: rotate(-130deg);
        }

        50% {
            transform: rotate(5deg);
        }

        to {
            transform: rotate(-130deg);
        }

    }

    .spinner--patch {
        position: absolute;
        top: 0;
        left: 45%;
        width: 10%;
        height: 100%;
        overflow: hidden;
        border-color: inherit;
    }

    .spinner--patch .spinner-circle {
        left: -450%;
        width: 1000%;
    }

</style>
