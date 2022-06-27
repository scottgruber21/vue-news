<template>
    <div class="news-item">
        <div class="news-text">
        <h2><a :href="story.url" target="_blank">{{story.title}}</a></h2>
        <div class="story-source">
            <h3>{{new Date(story.publishedAt).toLocaleDateString('en-us', {year:"numeric", month:"short", day:"numeric"}) }}</h3>
            <h4>{{story.source.name}}</h4>
            <h4>{{story.author}}</h4>
        </div>
        <p>{{story.description}}</p>
        <p><a :href="story.url" target="_blank">Read More</a></p>
        </div>
        <div class="news-image">
            <a :href="story.url" target="_blank"><img v-show="story.urlToImage" class="story-img" :src="story.urlToImage" /></a>
        </div>
    </div>
    <hr v-if="isLast" />
</template>

<script>
export default{
    name: 'NewsItem',
    props: {
        story: Object,
        isLast: Boolean
    }
}
</script>

<style scoped>
    .news-item{
        padding: 30px 0;
        text-align: left;
        display: grid;
        grid-template-areas: "news-text news-text news-text news-text news-image news-image"
    }

    .news-text{
        padding-right: 50px;
                grid-area: news-text;
    }

    h2{
        margin-bottom: 8px;
        margin-top: 0px;
    }

    h2 a{
        text-decoration: none;
    }

    .story-source h4{
        margin-top: 3px;
        margin-bottom: 3px;
        font-size: .9rem;
    }

    .story-img{
        max-width: 100%;
    }

    .news-image{
        grid-area: news-image;
    }

@media (max-width: 767px){
    .news-item{
        grid-template-columns: 1fr;
        grid-template-areas: "news-image"
                            "news-text"
    }

    .news-image{
        padding-bottom: 20px;
    }
}

</style>