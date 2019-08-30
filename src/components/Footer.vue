<template>
    <div>
        <v-footer
          fixed
          height="40"
          color="#eee">
            <v-btn
                absolute
                fab
                top
                left
                color="#eee"
                @click="sheet = !sheet"
                depressed>
                <v-icon>fa fa-calendar-o</v-icon>
            </v-btn>
            <v-btn
                absolute
                fab
                top
                right
                color="white"
                @click="dialog = !dialog"
                depressed>
                <v-icon>fa fa-paw</v-icon>
                <!-- <v-avatar size="36">
                    <img src="https://vuetifyjs.com/apple-touch-icon-180x180.png" alt="avatar">
                </v-avatar> -->
            </v-btn>
        </v-footer>
        <v-bottom-sheet
            v-model="sheet"
            hide-overlay>
            <Calendar />
        </v-bottom-sheet>
        <v-dialog
            v-model="dialog">
            <Dialog :point="point" />
        </v-dialog>
    </div>
</template>

<script>
import Calendar from '@/components/Calendar';
import Dialog from '@/components/Dialog';

export default {
    components: {
        Calendar,
        Dialog
    },
    props: {
        point: Number
    },
    data: () => ({
        sheet: false,
        dialog: false
    }),
}
</script>
