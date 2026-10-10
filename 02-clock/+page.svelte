<script lang=ts>
    // 300 seconds is 5 minutes
    let seconds = $state(300);

    // effect, deducts 1 from seconds var every 1000ms (which is 1 second)
    $effect(() => {
    const id = setInterval(() => seconds--, 1000);
    return () => clearInterval(id);
    // stops the clock
    });
</script>

// rounds the minute : modulo 60 to get seconds, pad start adds a 0 in beginning
<h1>{Math.floor(seconds / 60)} : {String(seconds % 60).padStart(2, '0')}</h1>


