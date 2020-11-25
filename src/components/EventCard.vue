<template>
    <div class="event-card-wrapper" :class="cardBoxShadow" @mouseover="showViewEvent(true)" @mouseleave="showViewEvent(false)">
        <div class="menu-dots" @click="handleShowMenu"></div>
        <div class="card-menu-wrapper" :class="menuOpenCSS" @mouseleave="handleShowMenu">
            <div class="card-menu-triangle"></div>
            <a href=""><div>Create campaign</div></a>
            <a href=""><div>Import ticket sales</div></a>
            <a href=""><div>Edit event details</div></a>
            <a href=""><div>Merge event</div></a>
            <a href=""><div>Delete event</div></a>
        </div>
        <div class="card-image-wrapper">
            <div class="view-event-wrapper" :class="viewEventCSS">
                <button>View event</button>
            </div>
            <img src="@/assets/beyond-valley.svg" alt="beyond the valley illustration" />
        </div>
        <div class="card-info-wrapper">
            <div class="card-copy">
                <div class="card-logo-wrapper" />
                <h3>{{event.title}}</h3>
                <p>{{ event.date }}</p>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'EventCard',
    props: {
        event: Object
    },
    data() {
        return {
            menuOpen: false,
            showEvent: false
        }
    },
    watch: {
        menuOpen() {
            if (this.menuOpen) {
                this.showEvent = false
            }
        },
    },
    computed: {
        menuOpenCSS() {
            return this.menuOpen ? 'menu-open' : 'menu-closed'
        },
        viewEventCSS() {
            let css
            if (this.menuOpen || !this.showEvent) {
                css = 'view-event-overlay-hidden'
            } else if (this.showEvent) {
                css = 'view-event-overlay-visible'
            }

            return css
        },
        cardBoxShadow() {
            return this.showEvent && !this.menuOpen ? 'card-box-shadow' : ''
        }
    },
    methods: {
        handleShowMenu() {
            return this.menuOpen = !this.menuOpen
        },
        showViewEvent(bool) {
            this.showEvent = bool
        }
    }
}
</script>
<style lang="scss" scoped>

$menu-border-grey: #D4D8E1;
$card-border-grey: #DCDEE4;
$card-primary-text-grey: #43516B;

@mixin fontBody {
    font-family: 'GraphikRegular';
    font-weight: 400;
}
@mixin flexRow {
    display: flex;
    flex-flow: row nowrap;
}
@mixin flexCol {
    display: flex;
    flex-flow: column nowrap;
}

.event-card-wrapper {
    @include flexCol;
    background: white;
    align-items: center;
    justify-content: center;
    border-radius: 4px;
    width: 380px;
    margin: 15px 20px;
    position: relative;
    transition: all 0.3s ease;

    .menu-dots {
        background: url('~@/assets/menu-dots.svg') no-repeat;
        background-position-x: 10px;
        width: 20px;
        height: 20px;
        position: absolute;
        top: 20px;
        right: 15px;
        z-index: 15;
        cursor: pointer;
    }

    .card-menu-wrapper {
        position: absolute;
        z-index: 20;
        background: white;
        border: 1px solid $menu-border-grey;
        border-radius: 5px;
        width: 205px;
        right: -13px;
        top: 60px;
        flex-flow: column nowrap;
        align-items: flex-start;
        padding: 12px 0 8px;
        -webkit-box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.1);
                box-shadow: 0px 1px 6px 1px rgba(0,0,0,0.1);

        .card-menu-triangle {
            width: 8px;
            height: 8px;
            background: white;
            position: absolute;
            right: 31px;
            top: -5px;
            transform: rotate(45deg);
            border-left: 1px solid $menu-border-grey;
            border-top: 1px solid $menu-border-grey;
            box-sizing: border-box;
        }

        a {
            @include flexRow;
            @include fontBody;
            width: 100%;
            align-items: center;
            justify-content: flex-start;
            text-decoration: inherit;
            color: $card-primary-text-grey;
            font-size: 14px;
            line-height: 20px;

            &:hover {
                background: #F2EDFF;
                color: #7344C0;
            }

            div {
                padding: 10px 0 10px 15px;
            }
        }
    }

    .card-image-wrapper {
        position: relative;
        overflow: hidden;
        height: 205px;
        width: 100%;
        border-top-left-radius: 4px;
        border-top-right-radius: 4px;

        img {
            position: absolute;
            min-width: 1000%;
            min-height: 1000%;
            margin: auto;
            top: -10000%;
            bottom: -10000%;
            left: -10000%;
            right: -10000%;
            transform: scale(0.1);
            z-index: 1;
        }

        .view-event-wrapper {
            @include flexRow;
            background: rgba(31, 40, 68, 0.9);
            position: absolute;
            height: 100%;
            width: 100%;
            z-index: 5;
            align-items: center;
            justify-content: center;
            transition: all 0.3s ease;

            button {
                font-family: 'GraphikMedium';
                font-weight: 400;
                font-size: 14px;
                line-height: 14px;
                background: transparent;
                color: white;
                border: 1px solid white;
                border-radius: 3px;
                padding: 12px 24px;
                cursor: pointer;
            }
        }
    }

    .card-info-wrapper {
        @include flexRow;
        border: 1px solid $card-border-grey;
        border-bottom-left-radius: 4px;
        border-bottom-right-radius: 4px;
        border-top: 1px solid #9FA0A2;
        box-sizing: border-box;
        align-items: center;
        justify-content: center;
        width: 100%;
        padding: 28px 0;
        position: relative;

        .card-copy {
            @include flexCol;;
            align-items: flex-start;
            width: 320px;
            overflow: hidden;

            .card-logo-wrapper {
                width: 30px;
                height: 30px;
                border: 1px solid $card-border-grey;
                border-radius: 100px;
                position: absolute;
                overflow: hidden;
                top: -15px;
                background-image: url('~@/assets/ar-logo.svg');
                background-repeat: no-repeat;
                background-size: contain;
                background-color: white;
                background-size: 15px 15px;
                background-position: 8px 7px;
                z-index: 10;
            }

            h3 {
                @include fontBody;
                margin: 0;
                font-size: 20px;
                line-height: 25px;
                color: $card-primary-text-grey;
                text-align: left;
                overflow: hidden;
                display: block;
                white-space: nowrap;
                text-overflow: ellipsis;
                width: 320px;
                margin-bottom: 5px;
            }
            p {
                @include fontBody;
                margin: 0;
                font-size: 16px;
                line-height: 25px;
                color: #8E97A6;
                text-align: left;          
            }
        }
    }
}

.menu-open {
    display: flex;
}
.menu-closed {
    display: none;
}
.view-event-overlay-visible {
    opacity: 1;
}
.view-event-overlay-hidden {
    opacity: 0;
}
.card-box-shadow {
    -webkit-box-shadow: 0px 10px 27px -9px rgba(0,0,0,0.2);
            box-shadow: 0px 10px 27px -9px rgba(0,0,0,0.2);
}
</style>