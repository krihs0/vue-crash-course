<script setup>
    import Hero from '@/components/Hero.vue';
    import HomeCard from '@/components/HomeCard.vue';
    import JobListings from '@/components/JobListings.vue';
</script>

<template>
<Hero
        title="Become a Kristicker"
        subTitle="Find the Kristick job that fits your skills and needs"
    />
    <HomeCard />
    <JobListings :limit="6" :showButton/>
</template>