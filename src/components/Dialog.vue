<template>
    <v-container
        fluid
        class="white">
        <h4 class="text-center mb-2">全部で {{ point }}E 持ってるよ</h4>
        <v-row no-gutters>
            <v-col
                v-for="(item, i) in items"
                :key="i"
                cols="6">
                <div class="pa-3 text-center">
                    <v-img
                    :src="item.img"
                    aspect-ratio="1"
                    class="mb-2"
                    ></v-img>
                    <v-chip
                        color="light-blue lighten-3">
                        {{ item.point }}Eで交換</v-chip>
                </div>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
    props: {
        point: Number // 文字列型のみ許可する
    },
    data () {
        return {
            items: [
                {
                    img: require('@/assets/2496.png'),
                    point: 100
                },
                {
                    img: require('@/assets/2379.png'),
                    point: 100
                },
                {
                    img: '',
                    point: 50
                },
                {
                    img: '',
                    point: 50
                },
                {
                    img: '',
                    point: 50
                },
                {
                    img: '',
                    point: 50
                },
                {
                    img: '',
                    point: 50
                },
                {
                    img: '',
                    point: 50
                }
            ]
        }
    }
}
</script>
