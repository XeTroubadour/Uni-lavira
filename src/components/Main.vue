<script>
import Title from './sections/Title.vue'
import Abstract from './sections/Abstract.vue'
import Markdown from './sections/Markdown.vue'
import BibTeX from './sections/BibTeX.vue'
import Video from './sections/Video.vue'
import Table from './sections/Table.vue'

export default {
  components: {
    Title,
    Abstract,
    Markdown,
    BibTeX,
    Video,
    Table,
  }
}
</script>

<template>
  <Title/>
  <Video/>
  <Abstract/>
  <Markdown/>
  <Table/>
  <BibTeX/>
</template>
