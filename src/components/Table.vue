<script setup>

import {onMounted, ref} from 'vue';

const users = ref([]);

onMounted(async () => {
    const response = await fetch('https://jsonplaceholder.typicode.com/users');
    users.value = await response.json();
})

</script>

<template>
    <table
        v-if="users.length"
        class="table">
        <thead>
            <tr>
                <th width="120">Id</th>
                <th width="150">Username</th>
                <th class="table-name">Name</th>
                <th width="100">Email</th>
                <th>Phone</th>
                <th class="text-left table-website" width="200">Website</th>
                <th class="text-left" width="200">Company</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="user in users" :key="user.id">
                <td data-label="Id" class="table-id">
                    {{ user.id }}
                </td>
                <td data-label="Username" class="table-username">
                    {{ user.username }}
                </td>
                <td class="table-divider"/>
                <td data-label="Name" class="table-name">
                    {{ user.name }}
                </td>
                <td data-label="Email" class="table-email">
                    {{ user.email }}
                </td>
                <td class="table-divider"/>
                <td data-label="Website" class="table-website">
                    {{ user.website }}
                </td>
                <td data-label="Phone" class="table-phone text-left">
                    {{ user.phone.replace(/\s*x\d+$/, '') }}
                </td>
                <td data-label="Company" class="table-company text-left">
                    {{ user.company.name }}
                </td>
            </tr>
        </tbody>
    </table>
    <div v-else class="table-empty">
        <span class="head">No data</span>
    </div>
</template>
