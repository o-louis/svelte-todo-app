<script>
  export let label;
  export let forID;
  export let value;
</script>

<div>
  <input type=text id={forID} bind:value={value} placeholder={label}>
</div>

<style>
  div {
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 100%;
    box-sizing: border-box;
    padding: 1.5rem;
    align-self: flex-start;
    text-transform: uppercase;
    box-shadow: 0 -10px 10px 0 rgba(1, 1, 1, 0.05);
  }
  
  input{
    box-sizing: border-box;
    font-size: 1rem;
    background: transparent;
    width: calc(100% - 3rem - 5px);
    border: none;
    color: white;
  }

  input:focus {
    outline: 0;
    border-color: white;
  }
</style>