<template>
  <input
    class="text-3xl py-2 px-4 rounded-xl w-full mt-8 text-gray-800 bg-gray-100"
    type="text"
    placeholder="16桁の伝票番号を入力してください"
    v-model="track"
  />
  <button @click="insertTrack">検索</button>
  <p>{{ trackInfo.number }}</p>
  <p>{{ trackInfo.itemType }}</p>
  <p>{{ trackInfo.companyNameJP }}</p>
  <p>
    {{
      trackInfo.delivered === true
        ? "配達完了"
        : trackInfo.errors.map((data) => data.message)
    }}
  </p>
  <!-- <div>{{ trackStatusList }}</div> -->
  <ul
    class="w-full flex justify-around"
    v-for="list in trackStatusList"
    v-bind:key="list.status"
  >
    <li>{{ list.placeName }}</li>
    <li>{{ list.status }}</li>
    <li>{{ list.placeCode }}</li>
    <li>{{ list.dateTime }}</li>
  </ul>
</template>

<script lang="ts">
import { ref, defineComponent } from "vue";
import format from "date-fns/format";
// const newInputValue = ref("429582062593");
// console.log(newInputValue);

// const res = await fetch(
//   `https://staging.trackingjp.work/api/v2/tracking/${newInputValue.value}`
// );
// const data = await res.json();

export default defineComponent({
  name: "TrackData",
  setup: () => {
    const track = ref("");
    const trackInfo = ref();
    const trackStatusList = ref([]);

    console.log(track, trackInfo);
    async function insertTrack(): Promise<void> {
      try {
        const res = await fetch(
          `https://staging.trackingjp.work/api/v2/tracking/${track.value}`
        );
        const data = await res.json();
        trackInfo.value = data;
        trackStatusList.value = data.statusList;
        console.log(trackInfo.value, trackStatusList.value);
      } catch (error) {
        console.log(error);
      }
    }
    return { track, trackInfo, trackStatusList, insertTrack, format };
  },
});
</script>
