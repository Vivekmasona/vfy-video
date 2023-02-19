<template>
    <footer class="text-center py-4 rounded-xl children:(mx-3) w-full mt-10">
        <a aria-label="GitHub" href="https://vivekfy.netlify.app/music" target="_blank">
            <font-awesome-icon :icon="['fab', 'music']" />
            <span class="ml-2" v-t="'VFY-MUSIC🎧'" />
        </a>
        <a href="https://vivekfy.onrender.com/" target="_blank">
            <font-awesome-icon :icon="['fa', 'internate']" />
            <span class="ml-2" v-t="'VFY-SERVER🌐'" />
        </a>
        <a href="https://vivekfy.netlify.app" target="_blank">
            <font-awesome-icon :icon="['fab', 'home']" />
            <span class="ml-2" v-t="'VFY-DOWNLOADER⬇️'" />
        </a>
        <a v-if="statusPageHref" :href="statusPageHref">
            <font-awesome-icon :icon="['fa', 'server']" />
            <span class="ml-2" v-t="''" />
        </a>
        <a v-if="donationHref" :href="donationHref">
            <font-awesome-icon :icon="['fa', 'music']" />
            <span class="ml-2" v-t="''" />
        </a>
    </footer>
</template>

<script>
export default {
    data() {
        return {
            donationHref: null,
            statusPageHref: null,
        };
    },
    mounted() {
        this.fetchConfig();
    },
    methods: {
        async fetchConfig() {
            this.fetchJson(this.apiUrl() + "/config").then(config => {
                this.donationHref = config?.donationUrl;
                this.statusPageHref = config?.statusPageUrl;
            });
        },
    },
};
</script>

<style>
footer {
    @apply bg-light-900;
}
.dark footer {
    @apply bg-dark-800;
}
</style>
