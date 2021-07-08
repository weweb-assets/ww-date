<template>
    <div class="ww-date">
        <wwElement v-bind="content.el" :ww-props="{ text: formatedDate }" />
    </div>
</template>

<script>
import * as dayjs from 'dayjs';
const customParseFormat = require('dayjs/plugin/customParseFormat');

export default {
    props: {
        content: { type: Object, required: true },
    },
    wwDefaultContent: {
        el: wwLib.element('ww-text'),
        date: '2021-03-11T10:11:20.000+00:00',
        format: 'DD/MM/YYYY',
        customFormat: '',
    },
    computed: {
        formatedDate() {
            return dayjs(this.content.date).format(this.formatToUse);
        },
        formatToUse() {
            return this.content.customFormat.length ? this.content.customFormat : this.content.format;
        },
    },
    mounted() {
        dayjs.extend(customParseFormat);
    },
    methods: {
        goToDoc() {
            window.open('https://day.js.org/docs/en/display/format#docsNav', '_blank');
        },
    },
};
</script>
