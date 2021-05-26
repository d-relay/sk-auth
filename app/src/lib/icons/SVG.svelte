<script>
  export let icon;
  export let width = 24;
  export let height = 24;
</script>

<svg
  fill="currentColor"
  {width}
  {height}
  viewBox={icon.viewBox}
  aria-labelledby={icon.name}
  role="presentation"
  class={icon.class}
>{@html icon.src}</svg>
