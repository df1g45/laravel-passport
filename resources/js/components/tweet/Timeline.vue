<template>
    <div class="card">
        <div class="card-header">Timeline</div>
        <div class="card-body">
            <post :tweets="tweets"></post>
            <hr />
            <div
                class="media mb-3"
                v-for="(tweet, index) in tweets"
                :key="index"
            >
                <img
                    src="https://placehold.it/64x64"
                    class="mr-3"
                    alt="Generic placehold image"
                />
                <div class="media-body">
                    <h5 class="mt-0">{{ tweet.user.name }}</h5>
                    <p>
                        {{ tweet.body }}
                    </p>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Post from "./Post";

export default {
    data() {
        return {
            tweets: [],
        };
    },

    components: {
        Post,
    },

    mounted() {
        axios
            .get("/tweets")
            .then((response) => {
                this.tweets = response.data;
            })
            .catch((err) => {
                console.log(err);
            });
    },
};
</script>
