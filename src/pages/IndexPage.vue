<template>
  <q-page class="bg-grey-3 q-px-md">
    <h3 class="q-my-none text-center q-py-lg">Search Jobs</h3>
    <div class="row  q-py-lg q-col-gutter-lg justify-center">
      <div class="col-sm-12 col-md-3">
        <q-card flat bordered class="q-pa-md">
          <div class="text-grey text-bold q-mb-md">Search Jobs</div>
          <q-separator />
          <q-expansion-item header-class="text-bold" label="Job Type">
            <div class="q-pa-md">
              <q-option-group @change="filterFunction" :options="options" type="checkbox" v-model="jobTypeFilters" />
            </div>
          </q-expansion-item>
        </q-card>
        <q-card flat bordered class=" q-mt-lg q-pa-md">
          <div class="text-grey text-bold q-mb-md">Country</div>
          <q-separator />
          <q-expansion-item header-class="text-bold" label="Select Country">
            <div class="q-pa-md">
              <q-option-group @change="filterFunction" :options="options2" type="checkbox" v-model="countryFilters" />
            </div>
          </q-expansion-item>
        </q-card>
        <q-card flat bordered class=" q-mt-lg q-pa-md">
          <div class="text-grey text-bold q-mb-md">Industry</div>
          <q-separator />
          <q-expansion-item header-class="text-bold" label="Industry">
            <div class="q-pa-md">
              <q-option-group @change="filterFunction" :options="options1" type="checkbox" v-model="industryFilters" />
            </div>
          </q-expansion-item>
        </q-card>
      </div>
      <div class="col-sm-12 col-md-6">
        <q-chip v-for="filter in allFilters" :key="filter.type + filter.value" removable
          @remove="removeFilter(filter.type, filter.value)" color="primary" text-color="white" :label="filter.label"
          :title="filter.label" />
        <q-card flat bordered class="q-pa-md">
          <div class="text-grey text-bold q-mb-md">Jobs</div>
          <div v-if="filteredJobs.length === 0" class="text-color">No matching jobs found.</div>
          <div v-for="(item) in filteredJobs" :key="item.heading">
            <q-separator />
            <div class="row q-mt-md">
              <q-avatar class="q-mt-md">
                <q-img :src="item.logo" />
              </q-avatar>
              <div class="q-ml-md">
                <div class="color">{{ item.heading }}</div>
                <div class="text-color">{{ item.subh }}</div>
                <div class="text-color">{{ item.thridh }}</div>
                <div class="text-color">{{ item.country }}</div>
                <div class="text-color q-mb-md">{{ item.industry }}</div>
              </div>
            </div>
          </div>
        </q-card>
      </div>
      <div class="col-sm-12 col-md-3">
        <mange-job />
      </div>
    </div>
  </q-page>
</template>


<script>
import { defineComponent, ref } from "vue";
import MangeJob from 'src/components/Mange-job.vue'

export default defineComponent({
  components: {
    MangeJob
  },
  data() {
    return {
      selectedFilter: null,
      selectedFilterLabel: "",
      company: {
        name: 'Nodesol',
        owner: 'Amer SAhib'
      },
      jobs: [
        {
          logo: "logo.png",
          heading: " Agricultural Product Grader Sorter",
          subh: "Roob LLC",
          thridh: "On-Site",
          industry: 'Hardware and equipment',
          country: 'Pakistan'
        },
        {
          logo: "logo.png",
          heading: " Logging Tractor Operator",
          subh: "Rutherford, Jast and Hickle",
          thridh: "Remote",
          industry: 'Hardware and equipment',
          country: 'Chania'
        },
        {
          logo: "logo.png",
          heading: "Food Service Manager",
          subh: "O'Reilly and Sons",
          thridh: "Remote",
          industry: 'Artificial intelligence',
          country: 'Pakistan'
        },
        {
          logo: "logo.png",
          heading: " Log Grader and Scaler",
          subh: "Connelly and Sons",
          thridh: "Hybrid",
          industry: 'Data services',
          country: 'India'

        },
        {
          logo: "logo.png",
          heading: " Log Grader and Scaler",
          subh: "Connelly and Sons",
          thridh: "Hybrid",
          industry: 'Energy',
          country: 'Chania'
        },
        {
          logo: "logo.png",
          heading: " Bookbinder",
          subh: "Stehr-Hamill",
          thridh: "On-Site",
          industry: 'Energy',
          country: 'Pakistan'
        },
        {
          logo: "logo.png",
          heading: " Copy Machine Operator",
          subh: "Dibbert-Lindgren",
          thridh: "Remote",
          industry: 'Energy',
          country: 'America'

        },
        {
          logo: "logo.png",
          heading: " Grinder OR Polisher",
          subh: "Simonis, Kulas and Beier",
          thridh: "On-site",
          industry: 'Gaming',
          country: 'America'
        },
        {
          logo: "logo.png",
          heading: " Pile-Driver Operator",
          subh: "Crona LLC",
          thridh: "Remote",
          industry: 'Gaming',
          country: 'Chania'
        },
        {
          logo: "logo.png",
          heading: "Geological Sample Test Technician",
          subh: "Stehr-Hamill",
          thridh: "On-site",
          industry: 'Gaming',
          country: 'Pakistan'
        },
        {
          logo: "logo.png",
          heading: "Electric Motor Repairer",
          subh: "Gerlach, Oberbrunner and Dickens",
          thridh: "Hybrid",
          industry: 'Gaming',
          country: 'India'
        },
        {
          logo: "logo.png",
          heading: "Farmworker",
          subh: "Ratke PLC",
          thridh: "Remote",
          industry: 'Business services',
          country: 'America'
        },
        {
          logo: "logo.png",
          heading: "Electronics Engineering Technician",
          subh: "Rau-Gusikowski",
          thridh: "On-Site",
          industry: 'Business services',
          country: 'America'
        },
        {
          logo: "logo.png",
          heading: "Materials Engineer",
          subh: "Gusikowski Ltd",
          thridh: "Remote",
          industry: 'Artificial intelligence',
          country: 'America'
        },
        {
          logo: "logo.png",
          heading: "Surveying and Mapping Technician",
          subh: "Bogisich, Schaefer and Carroll",
          thridh: "Hybrid",
          industry: 'Artificial intelligence',
          country: 'America'
        },
        {
          logo: "logo.png",
          heading: "Grinding Machine Operator",
          subh: "Mante-Halvorson",
          thridh: "on-site",
          industry: 'Artificial intelligence',
          country: 'India'
        },
        {
          logo: "logo.png",
          heading: "Highway Patrol Pilot",
          subh: "Hintz Group",
          thridh: "Hybrid",
          industry: 'Business services',
          country: 'Pakistan'
        },
        {
          logo: "logo.png",
          heading: "Wellhead Pumper",
          subh: "Wellhead Pumper",
          thridh: "Remote",
          industry: 'Business services',
          country: 'Pakistan'
        },
        {
          logo: "logo.png",
          heading: "Material Moving Worker",
          subh: "Marvin, Hansen and Roberts",
          thridh: "On-Site",
          industry: 'Business services',
          country: 'India'
        },
        {
          logo: "logo.png",
          heading: "Refractory Materials Repairer",
          subh: "Kohler PLC",
          thridh: "Remote",
          industry: 'Creative services',
          country: 'India'
        },
        {
          logo: "logo.png",
          heading: "Manager Tactical Operations",
          subh: "Von-Davis",
          thridh: "On-Site",
          industry: 'Creative services',
          country: 'Pakistan'
        },
      ],
      jobTypeFilters: ref([]),
      countryFilters: ref([]),
      industryFilters: ref([]),
      options: [
        { label: "On-Site", type: 'jobtype', value: "on-site" },
        { label: "Remote", type: 'jobtype', value: "remote" },
        { label: "Hybrid", type: 'jobtype', value: "hybrid" },
      ],
      options2: [
        { label: "Pakistan", type: 'country', value: "pakistan" },
        { label: "America", type: 'country', value: "america" },
        { label: "Chania", type: 'country', value: "chania" },
        { label: "India", type: 'country', value: "india" },

      ],
      options1: [
        { label: "Artificial intelligence", value: "artificial intelligence" },
        { label: "Business services", value: "business services" },
        { label: "consumer products and services", value: "consumer products and services" },
        { label: "Energy", value: "energy" },
        { label: "Gaming", value: "gaming" },
        { label: "Hardware and equipment", value: "hardware and equipment" },
        { label: "Creative services", value: "creative services" },
      ],
    };
  },
  computed: {
    allFilters() {
      const filters = [];
      filters.push(...this.jobTypeFilters.map(value => ({ type: 'jobType', value, label: value })));
      filters.push(...this.countryFilters.map(value => ({ type: 'country', value, label: value })));
      filters.push(...this.industryFilters.map(value => ({ type: 'industry', value, label: value })));
      return filters;
    },
    filteredJobs() {
      return this.jobs.filter((job) =>
        this.filterByJobType(job) &&
        this.filterByCountry(job) &&
        this.filterByIndustry(job)
      );
    },
  },
  methods: {
    filterByJobType(job) {
      return this.jobTypeFilters.length === 0 || this.jobTypeFilters.includes(job.thridh.toLowerCase());
    },
    filterByCountry(job) {
      return this.countryFilters.length === 0 || this.countryFilters.includes(job.country.toLowerCase());
    },
    filterByIndustry(job) {
      return this.industryFilters.length === 0 || this.industryFilters.includes(job.industry.toLowerCase());
    },
    removeFilter(filterType, filterValue) {
      if (filterType === 'jobType') {
        this.jobTypeFilters = this.jobTypeFilters.filter(filter => filter !== filterValue);
      } else if (filterType === 'country') {
        this.countryFilters = this.countryFilters.filter(filter => filter !== filterValue);
      } else if (filterType === 'industry') {
        this.industryFilters = this.industryFilters.filter(filter => filter !== filterValue);
      }
      this.filterFunction();
    },
  },
});
</script>

<style>
.color {
  color: #828282;
  font-size: 22px;
  font-weight: 500;
}

.text-color {
  color: #828282;
  font-weight: 500;
}
</style>
