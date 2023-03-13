<template>
    <div id="bee-plugin-container" style="height: 500px" />
    <button @click="bee.save()">Save Changes</button>
</template>

<script setup lang="ts">
import Bee from '@mailupinc/bee-plugin';
import { onMounted } from 'vue';
import { beeTemplate } from './beeTemplate';

const bee = new Bee();

const payload = {
    client_id: import.meta.env.VITE_BEE_PLUGIN_CLIENT_ID,
    client_secret: import.meta.env.VITE_BEE_PLUGIN_CLIENT_SECRET
};

await bee.getToken(payload.client_id, payload.client_secret);

const template = localStorage.getItem('bee__template')
    ? JSON.parse(localStorage.getItem('bee__template'))
    : beeTemplate;

console.log(template);

onMounted(() => {
    bee.start({
        uid: 'test',
        container: 'bee-plugin-container',
        onSave(template, html) {
            localStorage.setItem('bee__template', JSON.stringify(template));
        }
    }, template);
});
</script>