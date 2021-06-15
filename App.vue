<i18n>
    {
        "eng": {}
    }
</i18n>

<template>
    <wiz-root>
        <wiz-viewer>
            <header></header>
            <footer></footer>
        </wiz-viewer>
    </wiz-root>
</template>

<script>
export default {
  name: 'wiz-app',
  data() {
    return {};
  },
};

</script>

<style scoped>
    @import 'common/styles/imports.css';
    body {
        padding: 0;
        margin: 0;
    }
    .root {
        background-color: #fff;
    }
</style>
