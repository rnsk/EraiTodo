<template>
    <v-container>
        <v-dialog
            v-model="dialog"
            max-width="290">
            <v-card>
                <lottie :options="starLottie" :height="300" :width="300" :animCreated="handleAnimation"/>
            </v-card>
        </v-dialog>
        <v-timeline dense>
            <v-timeline-item
                v-for="(item, i) in items"
                :key="i"
                :color="item.color"
                small
                fill-dot>
                <h3>{{ item.datetime | moment }}</h3>
                <div
                    @click.prevent="done(i)">
                    <v-alert
                        :color="getColor(item)"
                        dense
                        dark
                        border="right">
                        <strong>{{item.content}}</strong>
                    </v-alert>
                </div>
            </v-timeline-item>
        </v-timeline>
    </v-container>
</template>

<script>
import moment from 'moment';
import Lottie from '@/components/Lottie';
import * as star from '@/assets/8910-star.json';

export default {
    components: {
        Lottie
    },
    data: () => ({
        dialog: false,
        items: [
            {
                id: 1,
                color: 'indigo lighten-2',
                datetime: '2019-08-30 08:00:00',
                content: '朝起きた',
                done: false
            },
            {
                id: 2,
                color: 'indigo lighten-2',
                datetime: '2019-08-30 09:00:00',
                content: '電車に乗った',
                done: false
            },
            {
                id: 3,
                color: 'red lighten-3',
                datetime: '2019-08-30 10:00:00',
                content: '出社してPCつけた。がんばった',
                done: false
            },
            {
                id: 4,
                color: 'indigo lighten-2',
                datetime: '2019-08-30 12:00:00',
                content: '昼まで仕事やった',
                done: false
            },
            {
                id: 5,
                color: 'indigo lighten-2',
                datetime: '2019-08-30 13:00:00',
                content: 'お昼食べた',
                done: false
            },
            {
                id: 6,
                color: 'cyan',
                datetime: '2019-08-30 17:00:00',
                content: '仕事終わった',
                done: false
            },
        ],
    }),
    filters: {
        moment: function (date) {
            return moment(date).format('H:mm');
        }
    },
    computed: {
        starLottie () {
            return { animationData: star }
        }
    },
    methods: {
        getColor (item) {
            if (!item.done) {
                return item.color;
            } else {
                return 'grey lighten-1'
            }
        },
        done (index) {
            if (this.items[index].done === false) {
                // ポイント加算
                this.$emit('add-point')

                this.$set(this.items[index], 'done', true);
                this.dialog = true;
                setTimeout(() => {
                    this.dialog = false
                }, 2000)
            }
        },
        handleAnimation (anim) {
            this.anim = anim
        }
    }
}
</script>