<script setup>
import _ from "lodash";
import Movie from "./components/Movie.vue";
import { ref, computed } from "vue";
const movies = [
  {
    imdb_id: "tt7074886",
    title: "The Front Runner",
    description:
      "In 1987, U.S. Senator Gary Hart's presidential campaign is derailed when he's caught in a scandalous love affair.",
    release: "2018-08-31",
    duration: 113,
    poster:
      "https://m.media-amazon.com/images/M/MV5BMTcyNTAxOTg4NV5BMl5BanBnXkFtZTgwMTMwNjQ2NjM@._V1_QL75_UX380_CR0,7,380,562_.jpg",
    tags: ["Biography", "Drama", "History"],
  },
  {
    imdb_id: "tt6348138",
    title: "Missing Link",
    description:
      "Mr. Link recruits explorer Sir Lionel Frost to help find his long-lost relatives in the fabled valley of Shangri-La. Along with adventurer Adelina Fortnight, this trio of explorers travel the world to help their new friend.",
    release: "2019-04-04",
    duration: 93,
    poster:
      "https://m.media-amazon.com/images/M/MV5BMWFmNWZmZWYtMWM3OC00YTYyLWIxNDMtOTRjNzhiYWQ0MDIwXkEyXkFqcGdeQXVyODk2NDQ3MTA@._V1_QL75_UX380_CR0,1,380,562_.jpg",
    tags: ["Animation", "Adventure", "Comedy"],
  },
  {
    imdb_id: "tt8206668",
    title: "Bad Education",
    description:
      "The beloved superintendent of New York's Roslyn school district and his staff, friends and relatives become the prime suspects in the unfolding of the single largest public school embezzlement scandal in American history.",
    release: "2019-10-08",
    duration: 108,
    poster:
      "https://m.media-amazon.com/images/M/MV5BYmE2NDNlMDktOTA5YS00ZmYyLWE1ZjUtN2QzZGIzNzI1MGVmXkEyXkFqcGdeQXVyODE5NzE3OTE@._V1_QL75_UX380_CR0,0,380,562_.jpg",
    tags: ["Biography", "Comedy", "Crime"],
  },
  {
    imdb_id: "tt3272066",
    title: "Reminiscence",
    description:
      "Nick Bannister, a private investigator of the mind, navigates the alluring world of the past when his life is changed by new client Mae. A simple case becomes an obsession after she disappears and he fights to learn the truth about her.",
    release: "2021-08-11",
    duration: 146,
    poster:
      "https://m.media-amazon.com/images/M/MV5BODBkMTNmMmQtYTNlMy00OTRhLWE5MzgtYTZlMTUyYzY1MzkzXkEyXkFqcGdeQXVyNjY1MTg4Mzc@._V1_QL75_UX380_CR0,0,380,562_.jpg",
    tags: ["Mystery", "Romance", "Sci-Fi"],
  },
  {
    imdb_id: "tt14458442",
    title: "The Son",
    description:
      "Peter has his busy life with new partner Beth and their baby thrown into disarray when his ex-wife Kate turns up with their teenage son, Nicholas.",
    release: "2022-07-09",
    duration: 123,
    poster:
      "https://m.media-amazon.com/images/M/MV5BNDZiY2Y0MTgtYjRjMS00ZTE0LTg3NzYtY2VlYzEwYjI2NWY5XkEyXkFqcGdeQXVyMTQyODg5MjQw._V1_QL75_UX380_CR0,0,380,562_.jpg",
    tags: ["Drama"],
  },
  {
    imdb_id: "tt1485796",
    title: "The Greatest Showman",
    description:
      "Celebrates the birth of show business and tells of a visionary who rose from nothing to create a spectacle that became a worldwide sensation.",
    release: "2017-09-20",
    duration: 105,
    poster:
      "https://m.media-amazon.com/images/M/MV5BMjI1NDYzNzY2Ml5BMl5BanBnXkFtZTgwODQwODczNTM@._V1_QL75_UY562_CR2,0,380,562_.jpg",
    tags: ["Biography", "Drama", "Musical"],
  },
  {
    imdb_id: "tt3315342",
    title: "Logan",
    description:
      "In a future where mutants are nearly extinct, an elderly and weary Logan leads a quiet life. But when Laura, a mutant child pursued by scientists, comes to him for help, he must get her to safety.",
    release: "2017-02-17",
    duration: 137,
    poster:
      "https://m.media-amazon.com/images/M/MV5BYzc5MTU4N2EtYTkyMi00NjdhLTg3NWEtMTY4OTEyMzJhZTAzXkEyXkFqcGdeQXVyNjc1NTYyMjg@._V1_QL75_UX380_CR0,4,380,562_.jpg",
    tags: ["Action", "Drama", "Sci-Fi"],
  },
  {
    imdb_id: "tt3332064",
    title: "Pan",
    description:
      "Twelve-year-old orphan Peter is spirited away to the magical world of Neverland, where he finds both fun and danger, and ultimately discovers his destiny: to become the hero who will be forever known as Peter Pan.",
    release: "2015-08-20",
    duration: 141,
    poster:
      "https://m.media-amazon.com/images/M/MV5BMzk2MDg5MDczMl5BMl5BanBnXkFtZTgwNTE2NjYyNjE@._V1_QL75_UX380_CR0,0,380,562_.jpg",
    tags: ["Action", "Adventure", "Comedy"],
  },
  {
    imdb_id: "tt1083452",
    title: "Eddie the Eagle",
    description:
      "The story of Eddie Edwards, the notoriously tenacious British underdog ski jumper who charmed the world at the 1988 Winter Olympics.",
    release: "2015-12-12",
    duration: 106,
    poster:
      "https://m.media-amazon.com/images/M/MV5BMTUxOTc5MTU1NF5BMl5BanBnXkFtZTgwODYyNTA1NzE@._V1_QL75_UX380_CR0,1,380,562_.jpg",
    tags: ["Adventure", "Biography", "Comedy"],
  },
];

const availableTags = Array.from(
  new Set(movies.flatMap((movie) => movie.tags))
);

const selectedTag = ref("");

const filteredMovies = computed(() => {
  if (!selectedTag.value) {
    return movies;
  } else {
    return movies.filter((movie) => movie.tags.includes(selectedTag.value));
  }
});


</script>

<template>
  <div style="display: flex; flex-direction: column">
    <!-- in this section you can select the category of the movie -->
    <div style="background-color: #d7edff">
      <p style="font-size: xx-large; color: brown; text-align: center">
        in this section you can select the category of the movie
      </p>
      <label for="tagFilter">Filter by Tag: </label>
      <select v-model="selectedTag" id="tagFilter">
        <option value="">All</option>
        <option v-for="tag in availableTags" :key="tag" :value="tag">
          {{ tag }}
        </option>
      </select>

      <ul
        style="
          display: flex;
          flex-wrap: wrap;
          margin: 5px;
          list-style: none;
          width: 100%;
        "
      >
        <Movie v-for="(item, i) in filteredMovies" :key="i" :info="item" />
      </ul>
    </div>

    <!-- in this section you can see all movies -->
    <div style="background-color: #f3ffd151; width: 100%">
      <p style="font-size: xx-large; color: brown; text-align: center">
        in this section you can see all movies
      </p>
      <ul
        style="
          display: flex;
          flex-wrap: wrap;
          margin: 5px;
          list-style: none;
          width: 100%;"
      >
        <Movie v-for="(item, i) in movies" :key="i" :info="item" />
      </ul>
    </div>
  </div>
</template>
