<template>
  <div class="ww-date">
    <wwObject v-bind="content.el" :wwProps="{ text: formatedDate }"></wwObject>
  </div>
</template>

<script>
import * as dayjs from "dayjs";
var customParseFormat = require("dayjs/plugin/customParseFormat");

export default {
  wwDefaultContent: {
    el: wwLib.element("ww-text"),
    date: "2021-03-11T10:11:20.000+00:00",
    format: "DD/MM/YYYY",
    customFormat: "",
  },
  props: {
    content: { type: "Object", required: true },
  },
  computed: {
    formatedDate() {
      return dayjs(this.content.date).format(this.formatToUse);
    },
    formatToUse() {
      return this.content.customFormat.length
        ? this.content.customFormat
        : this.content.format;
    },
  },
  mounted() {
    dayjs.extend(customParseFormat);
  },
};
</script>

<style lang="scss" scoped></style>
