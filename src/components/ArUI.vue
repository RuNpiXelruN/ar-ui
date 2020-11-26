<template>
    <div class="ui-wrapper">
        <template v-for="(event, index) in events">
            <EventCard 
                :key="setKey(index)"
                :event="event"
            />
        </template>
    </div>
</template>
<script>
import EventCard from '@/components/EventCard.vue'

export default {
    name: 'ArUI',
    components: {
        EventCard
    },
    props: {
        events: Array
    },
    methods: {
        setKey(index) {
            let r = Math.random().toString(36).substring(7)
            return `${index}_${r}`
        }
    }
}
</script>
<style lang="scss" scoped>
    
    $media-iPad: 767px;
    $media-mob: 478px;

    .ui-wrapper {
        display: flex;
        flex-flow: row wrap;
        align-items: center;
        justify-content: center;
        width: calc(90% + 42px);
        padding-top: 26px;
        max-width: 1280px;
        margin-top: 110px;

        @media screen and (max-width: $media-iPad) {
            margin-top: 164px;
        }

        @media screen and (max-width: $media-iPad) and (orientation: landscape) {
            margin-top: 0px;
        }
        
        @media screen and (max-width: $media-mob) {
            margin-top: 0px;
            padding-top: 23px;
        }

        &::after {
            content: '';
            width: 380px;
            margin: 15px 20px;
        }
    }
</style>