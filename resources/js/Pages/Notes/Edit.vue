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
                            <h3 class="text-lg text-gray-900">Editar de una nota</h3>
                            <p class="text-sm text-gray-600">Si editas no podrás volver al estado anterior</p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <form>
                                <label class="block font-medium text-sm text-gray-700" for="excerpt">Resumen</label>
                                <textarea class="form-input w-full rounded-md shadow-sm"
                                          v-model="form.excerpt" name="excerpt" id="excerpt"></textarea>

                                <label class="block font-medium text-sm text-gray-700" for="content">Contenido</label>
                                <textarea class="form-input w-full rounded-md shadow-sm"
                                          v-model="form.content" name="content" id="content" rows="5"></textarea>
                                <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-md">
                                    Editar
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
        props: {
            note: Object,
        },
        data() {
            return {
                form: {
                    excerpt: this.note.excerpt,
                    content: this.note.content,
                }
            }
        }
    }
</script>
