<template>
  <li
    class="
            flex
            justify-between
            items-center
            p-3
            pl-6
            cursor-pointer
            transition
            duration-300
            hover:bg-gray-50
          "
  >
    <div>
      <router-link
        :to="{ name: 'song', params: { id: song.docId } }"
        class="font-bold block text-gray-600"
        >{{ song.modifiedName }}</router-link
      >
      <span class="text-gray-500 text-sm"
        >Uploaded by {{ song.displayName }}</span
      >
    </div>

    <div class="text-gray-600 text-lg">
      <router-link
        custom
        :to="{ name: 'song', params: { id: song.docId }, hash: '#comments' }"
        v-slot="{ navigate }"
      >
        <span class="comments" @click="navigate">
          <i class="fa fa-comments text-gray-600"></i>
          {{ song.commentCount }}
        </span>
      </router-link>
    </div>
  </li>
</template>

<script>
  import { ref, toRefs } from 'vue';

  export default {
    name: 'SongItem',
    props: {
      song: { type: Object, required: true },
    },
    setup(props) {
      const { song } = toRefs(props);
    },
  };
</script>

<style></style>
