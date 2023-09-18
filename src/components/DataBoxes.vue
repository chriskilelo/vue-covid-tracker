<template>
    <div class="grid md:grid-cols-2 gap-4">
        <!-- Cases Box -->
        <div class="shadow-md bg-blue-100 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">
                Cases
            </h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New: </span>
                {{ stats.new_confirmed }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total: </span>
                {{ stats.total_confirmed }}
            </div>
        </div>
        <!-- Recoveries Box -->
        <div class="shadow-md bg-blue-200 p-10 text-center rounded">
            <h3 class="text-3xl text-blue-900 font-bold mb-4">
                Recoveries
            </h3>
            <div class="text-2xl mb-4">
                <span class="font-bold">New: </span>
                {{ stats.new_recovered }}
            </div>
            <div class="text-2xl mb-4">
                <span class="font-bold">Total: </span>
                {{ stats.total_recovered }}
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'DataBoxes',
    props: ['stats']
}
</script>