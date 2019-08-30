<template>
    <v-app>
        <v-app-bar app flat color="#fafafa">
            <v-toolbar-title>
                <span>{{ today }}</span>
                <span class="ml-5">今日 <strong>{{ point }}</strong> えらい！</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-app-bar-nav-icon></v-app-bar-nav-icon>
        </v-app-bar>

        <v-content>
            <TimeLine v-on:add-point="addPoint" />
            <Footer :point="point" />
        </v-content>
    </v-app>
</template>

<script>
import moment from 'moment';
import TimeLine from '@/components/TimeLine';
import Footer from '@/components/Footer';

export default {
    components: {
        TimeLine,
        Footer,
    },
    data () {
        return {
            today: '',
            point: 0
        }
    },
    created: function () {
        this.today = this.getToday()
    },
    methods: {
        getToday () {
            return moment(new Date).format('M/DD')
        },
        addPoint () {
            this.point++
        }
    }
}
</script>
