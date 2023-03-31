<template>
    <div>
        <from @submit.prevent="masuk">
        <input type="email" v-model="email" class="from-control" /><br />
        <button type="submit" >login</button>
        </from>
    </div>
</template>

<script setup>

const supabase = UseSupabaseAuthClient();
const email = ref();
const password = ref();
async function masuk(){
    const { data, error } = await supabase.auth.signInWithPassword({
        email: email.value,
        password: password.value,
    })
    console.log(data);
    navigateTo("/");
}
</script>