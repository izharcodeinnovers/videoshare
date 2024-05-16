<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Head } from '@inertiajs/vue3';
import PrimaryButton from "@/Components/PrimaryButton.vue";

/*const captureWebcam = () => {
    navigator.mediaDevices.getUserMedia({
        video: true,
        audio: false
    }).then((stream) => {
        console.log(stream);
    })
}*/

const initializeWebcam = () => {
    if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
        navigator.mediaDevices.getUserMedia({ video: true, audio: false })
            .then((stream) => {
                console.log(stream);
            })
            .catch((error) => {
                console.error('Error accessing getUserMedia:', error);
            });
    } else {
        console.error('getUserMedia is not supported');
    }
};

initializeWebcam();


</script>

<template>
    <Head title="Capture" />

    <AuthenticatedLayout>

        <div class="py-12">
            <div class="max-w-4xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-sm sm:rounded-lg">
                    <div class="p-6 text-gray-900">
                         <div class="flex items-center justify-center space-x-4">
                             <PrimaryButton v-on:click="captureWebcam">
                                 Capture Webcam
                             </PrimaryButton>
                         </div>
                    </div>
                </div>
            </div>
        </div>
    </AuthenticatedLayout>
</template>
