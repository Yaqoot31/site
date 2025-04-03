---
layout: home
---

<div class="break-out-full-width h-full bg-averas bg-cover">
    <div class="w-3/4 m-auto flex flex-wrap items-stretch">
        <h2 class="text-center text-3xl font-bold text-white mb-8">Our Team Members</h2>
        <div v-for="member in members" class="w-1/3 lg:w-1/4 xl:w-1/5 p-4 mb-8 relative">
            <div class="bg-gray-800 p-4 h-full text-white flex flex-col items-center rounded-lg shadow-lg transition-transform transform hover:scale-105">
                <img :src="member.avatar_url" class="block w-1/2 rounded-full border-2 border-white mb-4">
                <h3 class="mt-2 text-lg font-semibold">{{member.login}}</h3>
            </div>
        </div>
    </div>
</div>

<script>
export default {
    data: () => ({
        members: []
    }),
    async created() {
        let response = await fetch('https://api.github.com/orgs/inexorgame/members')
        if (response.ok) {
            this.members = await response.json()
        } else {
            console.error("Error fetching members:", response.statusText);
        }
    }
}
</script>
