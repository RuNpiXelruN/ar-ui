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
    padding: 20px 0;
    max-width: 1220px;
    position: fixed;
    top: 0;
    z-index: 20;
    background: #F6F9FC;

    h1 {
        @include fontBody;
        font-size: 30px;
        line-height: 33px;
        color: #43516B;
        text-align: left;
    }

    .search-header-wrapper {
        @include flexRow;
        align-items: center;
        justify-content: flex-end;

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

            .search-icon {
                background: url('~@/assets/search-icon.svg') no-repeat;
                background-size: contain;
                background-position: center;
                height: 17px;
                width: 36px;
                display: block;
                position: absolute;
            }
            .search-input {
                @include fontBody;
                font-size: 14px;
                border: none;
                width: 300px;
                line-height: 48px;
                border-radius: 4px;
                padding-left: 36px;
                margin-top: 0;        /* to remove default top/bottom margin in Safari */
                margin-bottom: 0;     /* to remove default top/bottom margin in Safari */

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
            padding: 19px 24px;
            border-radius: 3px;
            border: none;
            cursor: pointer;
            transition: background 0.2s ease;

            &:hover {
                background: #592F9D;
            }

            img {
                width: 15px;
                height: 15px;
                margin-bottom: -3px;
                margin-right: 10px;
            }
        }
    }
}
</style>