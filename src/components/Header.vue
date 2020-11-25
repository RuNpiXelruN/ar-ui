<template>
    <div class="header-wrapper">
        <h1>Events</h1>
        <div class="search-header-wrapper">
            <div class="input-container">
                <span class="search-icon"></span>
                <input class="search-input" type="text" :placeholder="searchPlaceholder">
            </div>
            <button class="create-button">
                <img src="../assets/create-icon.svg" class="create-icon" alt="" role="presentation" />
                Create<span class="create-button-span"> new event</span></button>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Header',
    props: {
        count: Number
    },
    computed: {
        searchPlaceholder() {
            return `Search ${this.count} events...`
        },
    },
}
</script>
<style lang="scss" scoped>

$media-iPad: 767px;
$media-mob: 478px;
$header-grey: #43516B;
$card-border-grey: #DCDEE4;
$input-green: #2DC26A;

@mixin fontBody {
    font-family: 'GraphikRegular';
    font-weight: 400;
}
@mixin flexRow {
    display: flex;
    flex-flow: row nowrap;
}

.header-wrapper {
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    justify-content: space-between;
    width: 90%;
    border-bottom: 1px solid $card-border-grey;
    padding: 26px 0 20px;
    max-width: 1222px;
    position: fixed;
    top: 0;
    z-index: 20;
    background: #F6F9FC;

    @media screen and (max-width: $media-iPad) {
        padding-top: 6px;
        padding-bottom: 31px;
    }
    
    @media screen and (max-width: $media-iPad) and (orientation: landscape) {
        position: relative;
    }

    @media screen and (max-width: $media-mob) {
        width: 95%;
        padding-top: 2px;
        position: relative;
    }

    h1 {
        @include fontBody;
        font-size: 30px;
        line-height: 33px;
        color: $header-grey;
        text-align: left;

        @media screen and (max-width: $media-iPad) {
            width: 100%;
            margin-bottom: 28px;
        }
    }

    .search-header-wrapper {
        @include flexRow;
        align-items: center;
        justify-content: flex-end;

        @media screen and (max-width: $media-iPad) {
            width: 100%;
        }

        .input-container {
            @include fontBody;
            @include flexRow;
            align-items: center;
            justify-content: flex-start;
            width: 300px;
            border-radius: 3px;
            border: 1px solid $card-border-grey;
            background: white;
            margin-right: 10px;

            @media screen and (max-width: $media-iPad) {
                flex-grow: 1;
            }            

            .search-icon {
                background: url('~@/assets/search-icon.svg') no-repeat;
                background-size: contain;
                background-position-x: 15px;
                height: 17px;
                width: 36px;
                display: block;
                position: absolute;

                @media screen and (max-width: $media-mob) {
                    display: none;
                }
            }
            .search-input {
                @include fontBody;
                font-size: 14px;
                border: none;
                width: 300px;
                color: $header-grey;
                line-height: 48px;
                border-radius: 4px;
                padding-left: 44px;
                margin: 0 !important;  /* to remove default top/bottom margin in Safari */

                @media screen and (max-width: $media-iPad) {
                    width: 100%;
                }

                @media screen and (max-width: $media-mob) {
                    padding-left: 10px;
                }

                &::placeholder {      /* Chrome, Firefox, Opera, Safari 10.1+ */
                    color: #B4B9C4;
                    opacity: 1;       /* Firefox */
                }

                &:focus {
                    outline: 0 none;
                    border: 1px solid $input-green;
                    -webkit-box-shadow: 0 0 0 3px rgba(45, 194, 106, 0.15);
                            box-shadow: 0 0 0 3px rgba(45, 194, 106, 0.15);
                    caret-color: $input-green;
                }
            }
        }

        .create-button {
            font-family: 'GraphikMedium';
            font-weight: 400;
            color: white;
            font-size: 14px;
            line-height: 14px;
            background: #7344C0;
            padding: 19px 28px 19px 24px;
            border-radius: 3px;
            border: none;
            cursor: pointer;
            transition: background 0.2s ease;

            @media screen and (max-width: $media-iPad) {
                padding: 19px 52px;

                .create-button-span, img {
                    display: none;
                }
            }
            
            @media screen and (max-width: $media-mob) {
                padding: 19px 20px;
            }

            &:hover {
                background: #592F9D;
            }

            img {
                width: 15px;
                height: 15px;
                margin-bottom: -3px;
                margin-right: 8px;
            }
        }
    }
}
</style>