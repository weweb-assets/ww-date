<template>
    <div class="ww-date" :class="{ editing: isEditing, selected: isSelected }">
        <wwElement v-bind="content.el" :ww-props="{ text: formatedDate }" />

        <!-- wwEditor:start -->
        <div class="ww-date__menu">
            <wwEditorIcon small name="fontawesome/solid/calendar-day" />
        </div>
        <!-- wwEditor:end -->
    </div>
</template>

<script>
import * as dayjs from 'dayjs';
const customParseFormat = require('dayjs/plugin/customParseFormat');

export default {
    props: {
        content: { type: Object, required: true },
        /* wwEditor:start */
        wwEditorState: { type: Object, required: true },
        /* wwEditor:end */
    },
    computed: {
        isEditing() {
            /* wwEditor:start */
            return this.wwEditorState.editMode === wwLib.wwEditorHelper.EDIT_MODES.EDITION;
            /* wwEditor:end */
            // eslint-disable-next-line no-unreachable
            return false;
        },
        isSelected() {
            /* wwEditor:start */
            return this.wwEditorState.isSelected;
            /* wwEditor:end */
            // eslint-disable-next-line no-unreachable
            return false;
        },
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

<style lang="scss" scoped>
.ww-date {
    /* wwEditor:start */
    &.selected {
        > .ww-date__menu {
            opacity: 1;
            pointer-events: all;
        }
    }
    &.editing:hover {
        & > .border {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            border: 1px solid var(--ww-editor-color);
            pointer-events: none;
            z-index: 10;
        }
        > .ww-date__menu {
            opacity: 1;
            pointer-events: all;
        }
    }
    &__menu {
        display: flex;
        position: absolute;
        top: 0px;
        left: 5px;
        transform: translate(-50%, -50%);
        border-radius: 100%;
        padding: var(--ww-spacing-01);
        transition: opacity 0.2s ease;
        z-index: 101;
        cursor: pointer;
        background-color: var(--ww-color-blue-500);
        color: var(--ww-color-white);
        justify-content: center;
        align-items: center;
        opacity: 0;
        pointer-events: none;
        &:after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%) rotate(45deg);
        }
    }
    /* wwEditor:end */
}
</style>
