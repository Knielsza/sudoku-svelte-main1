<script lang="ts">
  import Button from "./Button.svelte"
  import { sample1, sample2 } from "./samples.json"
  import { cells, solved } from "./stores"

  const setSample = (numArray: number[]) => {
    cells.setArray(numArray)
    $solved = false
  }
</script>

<div class="btn-box">
  <div class="btn-wrapper">
    <Button variant="primary" on:click={() => setSample(sample1.flat())}>
      BOARD 1
    </Button>
  </div>
  <div class="btn-wrapper">
    <Button variant="primary" on:click={() => setSample(sample2.flat())}>
      BOARD 2
    </Button>
  </div>
</div>

<style lang="scss">
  .btn-box {
    display: flex;
    justify-content: center;
    margin-top: 20px;
    color: wheat;
  }
  .btn-wrapper {
    margin-left: 10px;
    margin-right: 10px;
  }
</style>
