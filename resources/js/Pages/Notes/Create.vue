<template>
    <app-layout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Módulo de Notas
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6">
                    <div class="md:col-span-1">
                        <div class="px-4 sm:px0">
                            <h3 class="text-lg text-gray-900">Crear una nota</h3>
                            <p class="text-sm text-gray-600">Luego de crear la podrás editar</p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <form @submit.prevent="submit">
                                <label class="block font-medium text-sm text-gray-700" for="excerpt">Resumen</label>
                                <textarea class="form-input w-full rounded-md shadow-sm"
                                          v-model="form.excerpt" name="excerpt" id="excerpt"></textarea>

                                <label class="block font-medium text-sm text-gray-700" for="content">Contenido</label>
                                <textarea class="form-input w-full rounded-md shadow-sm"
                                          v-model="form.content" name="content" id="content" rows="8"></textarea>
                                <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-md">
                                    Crear
                                </button>
                            </form>
                            <hr class="my-6">
                            <inertia-link :href="route('notes.index')">Volver</inertia-link>

                        </div>
                    </div>
                </div>
            </div>
        </div>
    </app-layout>
</template>

<script>
    import AppLayout from '@/Layouts/AppLayout'

    export default {
        components: {
            AppLayout
        },
        data() {
            return {
                form: {
                    excerpt: '',
                    content: '',
                }
            }
        },
        methods: {
            submit() {
                this.$inertia.put(this.route('notes.update', this.note.id), this.form)
            }
        }
    }
</script>
