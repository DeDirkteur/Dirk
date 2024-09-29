<template>
    <v-card>
        <v-layout>
            <v-app-bar color="secondary" prominent>
                <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

                <v-toolbar-title>My files</v-toolbar-title>
            </v-app-bar>

            <v-navigation-drawer v-model="drawer" :location="$vuetify.display.mobile ? 'bottom' : undefined" temporary>
                <v-list :items="items"></v-list>
            </v-navigation-drawer>

            <v-main style="height: 500px;">
                <v-container>
                    <v-row>
                        <v-col cols="3" v-for="slider in sliders">
                            <v-card class="pa-4 text-center" :title="slider.name" :subtitle="slider.tooltip"
                                :color="slider.color">
                                <v-btn>{{ slider.sliderValue }}</v-btn>
                                <v-slider :onchange="addAllSliderValues()" v-model="slider.sliderValue" min="0" max="10"
                                    step="1"></v-slider>
                            </v-card>
                        </v-col>
                    </v-row>
                    <v-row>
                        <v-spacer></v-spacer>
                        <v-col>
                            <v-btn width="100%" @click="showTable = !showTable" color="error" variant="tonal" style="al">
                                <v-icon v-if="!showTable">mdi-chevron-down</v-icon>
                                <v-icon v-if="showTable">mdi-chevron-up</v-icon>
                            </v-btn>
                        </v-col><v-spacer></v-spacer>
                    </v-row>
                    <v-row v-if="showTable">
                        <v-card>
                            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Beatae quidem ducimus, recusandae
                            eaque earum
                            consequuntur
                            odio est rem adipisci quis aperiam deleniti at et sequi atque cumque facilis officia commodi.
                        </v-card>
                    </v-row>
                </v-container>
            </v-main>
        </v-layout>
    </v-card>
</template>
<script setup>
import { ref } from "vue";

const showTable = ref(false);

const drawer = ref(false);

const sliders = ref([
    {
        name: "Templating",
        tooltip: "This is for templating",
        sliderValue: 5,
        color: "secondary",
    },
    {
        name: "User experience",
        tooltip: "This is for templating",
        sliderValue: 5,
        color: "warning",
    },
    {
        name: "Templating",
        tooltip: "This is for templating",
        sliderValue: 5,
        color: "green",
    },
    {
        name: "Templating",
        tooltip: "This is for templating",
        sliderValue: 5,
        color: "info",
    },
    {
        name: "User Exp",
        tooltip: "This is for templating",
        sliderValue: 5,
        color: "surface",
    },

])

function addAllSliderValues() {
    var sum = 0;
    for (var i = 0; i < sliders.value.length; i++) {
        sum += sliders.value[i].sliderValue;
    }
    console.log(sum);
}



</script>
<style></style>