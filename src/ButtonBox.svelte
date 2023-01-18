<script lang="ts">
  import Button from "./Button.svelte"
  import { cells, cellsIsEmpty, solved, time } from "./stores"
  import { solve, SolveStatus } from "sudoku-solver-ts"

  const invokeSolve = () => {
    const startTime = performance.now()
    const result = solve($cells.map((cell) => cell.num))
    $time = performance.now() - startTime
    if (result.success) {
      cells.setSolvedArray(result.solution)
      $solved = true
    } else {
      switch (result.status) {
        case SolveStatus.duplicated:
          alert("Powtarzają się")
          break
        case SolveStatus.noEmpty:
          alert("")
          break
        case SolveStatus.unsolvable:
          alert("U did it wrong")
          break
        default:
          alert("Bad input")
          break
      }
    }
  }

  const reset = () => {
    cells.reset()
    $solved = false
  }

  const undo = () => {
    cells.undo()
    $solved = false
  }
</script>

<div class="btn-box">
  <div class="btn-wrapper">
    {#if !$solved}
      <Button variant="primary" on:click={invokeSolve} disabled={$cellsIsEmpty}>
        END
      </Button>
    {:else}
      <Button variant="primary" on:click={undo}>Erase Board</Button>
    {/if}
  </div>
  <div class="btn-wrapper">
    <Button variant="secondary" on:click={reset} disabled={$cellsIsEmpty}>
      RESET
    </Button>
  </div>
</div>

<style lang="scss">
  .btn-box {
    display: flex;
    justify-content: center;
    margin-top: 20px;
  }
  .btn-wrapper {
    margin-left: 10px;
    margin-right: 10px;
  }
</style>
