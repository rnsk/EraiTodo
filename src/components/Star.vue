<template>
    <v-row justify="center">
        <v-dialog
            v-model="dialog"
            max-width="290">
            <v-card>
                <lottie :options="starLottie" :height="300" :width="300" :animCreated="handleAnimation"/>
            </v-card>
        </v-dialog>
    </v-row>
</template>

<script>
import Lottie from '@/components/Lottie';
import * as star from '@/assets/8910-star.json';

export default {
    components: {
        Lottie
    },
    computed: {
        starLottie () {
            return { animationData: star }
        }
    },
    methods: {
        handleAnimation (anim) {
            this.anim = anim
        }
    }
}
</script>