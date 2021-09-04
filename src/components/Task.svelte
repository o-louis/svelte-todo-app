<script>
  export let id;
  export let name;
  export let completed = false;

  import { createEventDispatcher } from 'svelte';

  const dispatch = createEventDispatcher();

  function deleteTask() {
    dispatch('delete', { id });
  }
</script>

<li class:completed={completed}>
  <label>
    <input type=checkbox bind:checked={completed}>{name}
  </label>
  <button class="delete" on:click={deleteTask}><img src="https://s2.svgbox.net/hero-outline.svg?ic=trash&color=fff" width="28" height="28" alt="delete button"></button>
</li>

<style>
  li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    transition: all 0.30s ease-in-out;
    box-shadow: 0 20px 30px 0 rgba(1, 1, 1, 0.07);
    border-radius: .75rem;
    color: #0d0d0d;
    padding: 1.25rem;
    font-size: 1rem;
    font-weight: 600;
    letter-spacing: .03rem;
    animation:fadeIn .5s linear;
    background-color: #fff;
    margin-bottom: 5px;
    position: relative;
    border-right: 0px solid lightgray;
    letter-spacing: -.015rem;
    will-change: transform;
    margin: 1rem 0;
    border-right: 55px solid red;
    cursor: pointer;
  }
  li.completed label {
    text-decoration: line-through;
    opacity: 0.5;
  }

  input { 
    display: none;
  }

  .delete {
    position: absolute;
    right: -42px;
    background: none;
    border: none;
    outline: 0;
    line-height: .85rem;
    font-size: 1.5rem;  
    cursor: pointer;
  }
  .delete:hover {
    opacity: .75;
  }

  @keyframes fadeIn{
    0% {
      opacity:0;
      margin-top: -50px;
    }
    50% {
      opacity:0;
    }
    100% {
      opacity:1;
      margin-top: 0px;
    }
  }
</style>