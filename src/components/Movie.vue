<script setup>

defineProps({
  info: Object,
});

</script>

<template>
  <li
    style="padding: 5px; margin: 5px; background-color: #dfe7e7; display: flex; width:30%; border: 2px solid #50011e;"
  >
    <div style="position: relative; width: 40%; height: 100%">
      <img
        style="
          position: absolute;
          left: 0;
          right: 0;
          bottom: 0;
          top: 0;
          object-fit: fill;
          width: 100%;
          height: 100%;
        "
        :src="info.poster"
        alt="Movie Poster"
      />
    </div>
    <div style="width: 60%; padding-left: 10px">
      <p>
        <span style="font-weight: bold; color: #50011e"> Title: </span
        >{{ info.title }}
      </p>
      <p>
        <span style="font-weight: bold; color: #50011e">Description: </span>
        {{ info.description }}
      </p>
      <p>
        <span style="font-weight: bold; color: #50011e">Duration: </span


        >{{ info.duration }}
      </p>
      <p>
        <span style="font-weight: bold; color: #50011e">Release: </span
        >{{ info.release }}
      </p>


      <p>
        <span style="font-weight: bold; color: #50011e">Release: </span>
        {{ new Date(info.release).getFullYear() }}
      </p>


      <p>
        <span style="font-weight: bold; color: #50011e">Tags: </span
        >{{ info.tags.join(", ") }}
      </p>
    </div>
  </li>
</template>
