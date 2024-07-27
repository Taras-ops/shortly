<script setup>
import ShortenLinkComponent from './ShortenLinkComponent.vue';
import StatisticsCard from './StatisticsCard.vue';
</script>

<template>
  <section class="statistics">
    <div class="container">
      <ShortenLinkComponent />
      <div class="statistics-content">
        <h2>Advanced Statistics</h2>
        <p>
          Track how your links are performing across the web with our advanced
          statistics dashboard.
        </p>
      </div>
      <div class="statistics-cards-wrapper">
        <StatisticsCard
          iconName="icon-brand-recognition"
          title="Brand Recognition"
          description="Boost your brand recognition with each click. Generic links don’t mean a thing. Branded links help instil confidence in your content." />
        <StatisticsCard
          iconName="icon-detailed-records"
          title="Detailed Records"
          description="Gain insights into who is clicking your links. Knowing when and where people engage with your content helps inform better decisions." />
        <StatisticsCard
          iconName="icon-fully-customizable"
          title="Fully Customizable"
          description="Improve brand awareness and content discoverability through customizable links, supercharging audience engagement." />
      </div>
    </div>
  </section>
</template>
