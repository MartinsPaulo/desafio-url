<template>
    <app-layout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                URLs
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="bg-white overflow-hidden shadow-xl sm:rounded-lg p-4 lg:p-8">
                    <h1 class="text-lg lg:text-2xl font-bold text-shadow-md">Cadastro de Urls</h1>
                    <div class="mt-2">
                        <input class="border-black border rounded-md shadow-sm w-1/2 p1 lg:p-2" :value="form.url" type="url"/>
                        <button class="border rounded-md p-1 ml-4 px-3 border-gray-600 bg-gray-500 hover:bg-gray-700 text-white" @click.prevent="submitUrl()">Salvar</button>
                        <br>
                        <span class="text-red-800 text-md" :hidden="errorValidator">URL inválida. Adicione o caminho completo com http/htpps.</span>
                    </div>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import { defineComponent } from 'vue'
    import AppLayout from '@/Layouts/AppLayout.vue'

    export default defineComponent({
        components: {
            AppLayout,
        },
        data() {
            return {
                form: ({
                    url: '',
                    errorValidator: true,
                })
            }
        },
        methods:{
            validateUrl() {
                let regex = /^(http|https)/;
                if(this.form.url.length > 3 && !this.form.url.match(regex)) {
                    this.form.url = 'http://' + this.form.url;
                }
            },
            submitUrl(){

            }
        },
    })
</script>
