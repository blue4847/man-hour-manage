/* eslint-disable vue/require-default-prop */ /* eslint-disable
vue/require-default-prop */
<template>
  <table>
    <thead>
      <tr>
        <th colspan="3">
          <v-layout column>
            <v-flex>{{ header.title }}</v-flex>
            <v-flex>{{ header.projectCd }}</v-flex>
          </v-layout>
        </th>
      </tr>
      <tr>
        <th>work1</th>
        <th>work2</th>
        <th>work3</th>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="(dailyData, idx) of dailyWorkTimeList"
        :key="idx"
      >
        <td>{{ dailyData.work1Str }}</td>
        <td>{{ dailyData.work2Str }}</td>
        <td>{{ dailyData.work3Str }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import MockData from "@/js/mock/ProjectTableData";
import ProjectMonthlyWorkTime from "@/js/mhm/timetable/monthly/ProjectMonthlyWorkTime.js";

export default {
  props: {
    projectData: {
      type: Object,
      default: new ProjectMonthlyWorkTime({})
    }
  },
  data: () => ({
    restProjectData: {}
  }),
  computed: {
    dailyWorkTimeList() {
      return this.projectData.dailyWorkTimeList;
    },
    header() {
      return this.projectData.header;
    }
  },
  created() {
    this.restProjectData = MockData;
  }
};
</script>

<style scoped>
table thead th {
  border-bottom: 1px solid darkgray;
  height: 25px;
}

table tbody td {
  border-bottom: 1px solid darkgray;
  height: 25px;
}
</style>
