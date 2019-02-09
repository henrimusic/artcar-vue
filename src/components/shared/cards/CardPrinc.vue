<template>
    <b-col cols="6" sm="6" md="4" lg="3" class="mt-5 d-flex align-content-center justify-content-center">
        <div class="card-prin">
            <div class="bg-full">
                <img class="card-img-top" :src="'data:image/png;base64,'+ img" style="max-height: 195px;border-top-left-radius: calc(1.25rem - 1px);border-top-right-radius: calc(1.25rem - 1px);">
            </div>
            <div class="body">
                <h5 class="color-3">{{ tipo }} modelo {{ modelo }}</h5>
                <hr>
                <div class="w-100 d-flex align-content-center justify-content-center">
                    <div class="price bg-color-3">
                        <p class="color-1">{{ anoModelo }}</p>
                    </div>
                </div>
                
            </div>
        </div>
    </b-col>
</template>


<script>
export default {

    props:['tipo', 'modelo', 'img', 'anoModelo']

}
</script>