<template>
    <div>
        <from @submit.prevent="signup">
        <input type="email" v-model="email" /><br />
        <input type="password" v-model="password" />
        <button type="submit" >daftar</button>
    </from>
    </div>
</template>

< script setup>
const supabase = UseSupabaseAuthClient();
const email = ref();
const password = ref();
async function signup(){
    const { data, eror } = await supabase.auth.signUp({
        email: email.value,
        password: password.value,
    });
    console.log('p')
    navigateTo="/login"
}
</script>