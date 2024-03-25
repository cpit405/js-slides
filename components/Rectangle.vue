<template>
    <svg :width="width" :height="height" xmlns="http://www.w3.org/2000/svg">
        <rect :x="startX" :y="startY" :width="width" :height="height" style="stroke-width:3; stroke:black; fill:none" />
    </svg>
</template>

<script>
export default {
    name: 'Rectangle',
    props: {
        startX: {
            type: Number,
            required: true
        },
        startY: {
            type: Number,
            required: true
        },
        width: {
            type: Number,
            required: true
        },
        height: {
            type: Number,
            required: true
        }
    }
}
</script>