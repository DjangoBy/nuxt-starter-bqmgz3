<template>
  <div>
    <apexchart
      :key="series"
      height="400"
      width="900"
      :options="options"
      :series="series"
    ></apexchart>
  </div>
  <button
    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
    @click="updateChart"
  >
    Change
  </button>

  <div>
    <apexchart
      :key="series2"
      height="400"
      width="900"
      :options="options2"
      :series="series2"
    ></apexchart>
  </div>
</template>

<script setup lang="ts">
const options = ref({
  chart: {
    type: 'bar',
  },
  xaxis: {
    categories: [
      'апр.23',
      'май.23',
      'июн.23',
      'июл.23',
      'авг.23',
      'сен.23',
      'окт.23',
      'ноя.23',
      'дек.23',
      'янв.24',
      'фев.24',
      'мар.24',
    ],
  },
  colors: ['#80c7fd'],
  plotOptions: {
    bar: {
      horizontal: false,
      columnWidth: '45%',
      endingShape: 'rounded',
    },
  },
  dataLabels: {
    enabled: false,
  },
});
const series = ref([
  {
    name: '',
    data: [30, 40, 45, 50, 49, 60, 70, 91],
  },
]);

const options2 = ref({
  chart: {
    type: 'bar',
  },
  xaxis: {
    categories: ['Этап 0', 'Этап 1', 'Этап 2', 'Этап 3', 'Этап 4'],
  },
  colors: ['#80f1cb', '#00E396'],
  plotOptions: {
    bar: {
      horizontal: false,
      columnWidth: '45%',
      endingShape: 'rounded',
    },
  },
  dataLabels: {
    enabled: false,
  },
});
const series2 = ref([
  {
    name: '',
    data: [3483960, 2672108, 2672108, 9165671, 8049812],
  },
]);

const updateChart = () => {
  //generate array of random numbers of length 10
  const data = Array.from({ length: 9 }, () =>
    Math.floor(Math.random() * 2000000)
  );
  // options.value = {
  //   ...options.value,
  //   xaxis: {
  //     categories: Array.from(
  //       { length: 10 },
  //       (_, i) => new Date().getFullYear() - i
  //     ), // array of last 10 years
  //   },
  // };
  series.value = [
    {
      name: '',
      data: data,
    },
  ];
};
onMounted(() => {
  updateChart();
});
</script>
