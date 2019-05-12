<template>
    <ion-card>
        <ion-card-header>
            <ion-label>
                {{ post.title }}
            </ion-label>
        </ion-card-header>
        <ion-card-content>
            <template v-if="this.image">
                <ion-img :src="image"></ion-img>
            </template>
            <template v-if="post.selftext">
                {{ post.selftext }}
            </template>
            <ion-button color="tertiary" expand="full" @click="$router.go(-1)">
                Go back
            </ion-button>
        </ion-card-content>
    </ion-card>
</template>

<script>
export default {
    props: {
        post: Object,
    },
    data(){
        return {
            image: ''
        }
    },
    mounted(){
        this.image = this.post.preview.images[0].source.url.replace('&amp;','&');
    }
}
</script>
