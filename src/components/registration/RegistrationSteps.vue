<template>
    <div class="steps">
        <div class="steps__item steps__item--filled">
            <div class="steps__step">
                <span class="steps__text steps__text--account">Account</span>
            </div>
        </div>
        <div class="steps__item steps__item--filled steps__item--active">
            <div class="steps__step">
                <span class="steps__text steps__text--verification">Verification</span>
            </div>
        </div>
        <div class="steps__item">
            <div class="steps__step">
                <span class="steps__text steps__text--profile">Profile</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'RegistrationSteps',
}
</script>

<style lang="scss">
    $c-white: #fff;
    $c-secondary: #2e2f6f;
    $c-active: #cf4492;

    .steps {
        $self: &;

        display: grid;
        grid-template-columns: minmax(max-content, auto) 3fr 3fr;
        padding-top: 28px;
        margin-bottom: 30px;

        &__item {
            display: flex;
            align-items: center;

            &::before {
                content: '';
                width: 100%;
                height: 1px;
                background-color: $c-secondary;
            }

            &--active {
                #{$self}__text {
                    color: $c-white;
                }
            }

            &--filled {
                &::before {
                    content: '';
                    width: 100%;
                    height: 1px;
                    background-color: $c-active;
                }

                #{$self}__step {
                    border-color: $c-active;
                }
            }
        }

        &__step {
            position: relative;
            background-color: $c-white;
            min-width: 30px;
            width: 30px;
            height: 30px;
            border: 10px solid $c-secondary;
            border-radius: 20px;
        }

        &__text {
            position: absolute;
            bottom: calc(100% + 18px);
            font-size: 14px;

            &--account {
                left: -10px;
            }

            &--verification {
                left: 50%;
                transform: translateX(-50%);
            }

            &--profile {
                right: -10px;
            }
        }
    }

    @media (max-width: 620px) {
        .steps__step {
            min-width: 20px;
            width: 20px;
            height: 20px;
            border: 6px solid $c-secondary;
        }
    }
</style>
