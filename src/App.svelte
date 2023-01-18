<script lang="ts">
  import Board from "./Board.svelte"
  import ButtonBox from "./ButtonBox.svelte"
  import SampleButtonBox from "./SampleButtonBox.svelte"
  import Title from "./Title.svelte"
</script>

<main class="main">
  <Title>SudokuSvelte</Title>
  <div class="container">
    <Board />
    <ButtonBox />
    <SampleButtonBox />
  </div>
</main>

<style lang="scss">
  .main {
    padding: 30px 10px 80px;
  }
  .container {
    max-width: 500px;
    margin-left: auto;
    margin-right: auto;
    border-radius: 10px;
  }
</style>
