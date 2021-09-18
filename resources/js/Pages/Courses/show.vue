<template>
  <app-layout title="show course">
    <template #header>
      <h2 class="font-semibold text-xl text-gray-800 leading-tight">
        Course : {{ course.title }}
      </h2>
    </template>
    <div class="py-3">
      <div class="text-base text-gray-900 px-3">
        Episode {{ this.index + 1 }} :
        {{ course.videos[this.index].title }}
      </div>
      <div class="mx-8 my-3">
        <iframe
          class="w-full h-screen"
          src="https://www.youtube.com/embed/SlX03hcCayE"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
          allowfullscreen
        ></iframe>
      </div>
      <div class="my-5 mx-8 text-gray-600">
        Description : {{ course.videos[this.index].description }}
      </div>
      <div>
        <ul
          class="mx-5"
          v-for="(episode, x) in course.videos"
          :key="episode.id"
        >
          <li
            class="
              bg-gray-200
              p-3
              rounded
              border-2
              flex
              justify-between
              items-center
              mb-3
            "
          >
            <div>
              <span>Ep n° {{ x + 1 }}: - {{ episode.title }} </span>
              <button
                class="
                  text-green-600
                  py-2
                  px-4
                  focus:text-red-500
                  cursor-pointer
                "
                @click="watchEpisode(x)"
              >
                Watch
              </button>
            </div>
           <progress-button :video-id='episode.id'/>
          </li>
        </ul>
      </div>
    </div>
  </app-layout>
</template>

<script>
import axios from 'axios';
import AppLayout from "./../../Layouts/AppLayout";
import ProgressButton from './PrgressButton';

export default {
  components: {
    AppLayout,
    ProgressButton
  },
 
  props: ["course"],
  data() {
    return {
      index: 0,
    };
  },
  methods: {
    watchEpisode(x) {
      this.index = x;
      window.scrollTo({
        top: 0,
        left: 0,
        behavior: "smooth",
      });
    }
  },
};
</script>

<style></style>
