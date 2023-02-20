<script>
export default {
    props: {
        link: String,
    },
};
</script>

<template>
    <template v-if="this.getPreferenceBoolean('showWatchOnYouTube', false)">
        <!-- For large screens -->
        <a :href="link" class="btn lt-lg:hidden">
            <i18n-t keypath="player.watch_on" tag="strong">
                <i class="fa fa-download" style="font-size:24px"></i>
            </i18n-t>
        </a>
        <!-- For small screens -->
        <a :href="link" class="btn lg:hidden">
            <i class="fa fa-download" style="font-size:24px"></i>
        </a>
    </template>
</template>
