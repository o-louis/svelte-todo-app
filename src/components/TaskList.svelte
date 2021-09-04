<script>
  let className;
  export { className as class };
</script>

<ul class={className}>
  <slot></slot>
</ul>

<style>
  ul {
    list-style-type: none;
    padding-left: 0;
    margin: 30px 0;
  }
</style>