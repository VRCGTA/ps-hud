<script lang="ts">
  import { fade } from 'svelte/transition';
  import MoneyHudStore from '../stores/moneyHudStore'
</script>

<div id="money-container">
  {#if $MoneyHudStore.showCash}
    <div transition:fade|local="{{duration: 1000}}">
      <p><span id="sign">𝕍&nbsp;</span><span id="money">{Number($MoneyHudStore.cash).toLocaleString()}</span></p>
    </div>
  {/if}
  {#if $MoneyHudStore.showBank}
    <div transition:fade|local="{{duration: 1000}}">
      <p><span id="sign">𝕍&nbsp;</span><span id="bank">{Number($MoneyHudStore.bank).toLocaleString()}</span></p>
    </div>
  {/if}
  {#if $MoneyHudStore.showUpdate}
    <div transition:fade|local="{{duration: 1000}}">
      {#if $MoneyHudStore.plus}
        <p id="money"><span id="plus">+&nbsp;</span><span id="money">{Number($MoneyHudStore.amount).toLocaleString()}</span></p>
      {:else if $MoneyHudStore.minus}
        <p id="minus"><span id="minus">-&nbsp;</span><span id="money">{Number($MoneyHudStore.amount).toLocaleString()}</span></p>
      {/if}
    </div>
  {/if}
</div>

<style>
  #money-container {
    position: absolute;
    right: 2vw;
    top: 5vh;
    font-weight: 400;
    font-size: 40px;
  }

  #sign, #bank {
    font-family: 'Pricedown Bl', sans-serif;
    text-align: right;
    color: #00ac31;
    text-shadow: -1px -1px 0 rgba(0,0,0, 0.7), 1px -1px 0 rgba(0,0,0, 0.7), -1px 1px 0 rgba(0,0,0, 0.7), 1px 1px 0 rgba(0,0,0, 0.7);
  }

  #plus {
    font-size: 50px;
    font-family: 'Pricedown Bl', sans-serif;
    text-align: right;
    color: #00ac31;
    text-shadow: -1px -1px 0 rgba(0,0,0, 0.7), 1px -1px 0 rgba(0,0,0, 0.7), -1px 1px 0 rgba(0,0,0, 0.7), 1px 1px 0 rgba(0,0,0, 0.7);
  }

  #minus {
    font-size: 50px;
    font-family: 'Pricedown Bl', sans-serif;
    text-align: right;
    color: #ac0000;
    text-shadow: -1px -1px 0 rgba(0,0,0, 0.7), 1px -1px 0 rgba(0,0,0, 0.7), -1px 1px 0 rgba(0,0,0, 0.7), 1px 1px 0 rgba(0,0,0, 0.7);
  }

  #money {
    font-family: 'Pricedown Bl', sans-serif;
    text-align: right;
    color: #ffffff;
    text-shadow: -1px -1px 0 rgba(0,0,0, 0.7), 1px -1px 0 rgba(0,0,0, 0.7), -1px 1px 0 rgba(0,0,0, 0.7), 1px 1px 0 rgba(0,0,0, 0.7);
  }
</style>