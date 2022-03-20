<script context="module">
  export const load = async ({ fetch }) => {
    const res = await fetch("https://countries.trevorblades.com/", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify({
        query: `{
                  countries {
                    name
                    emoji
                  }  
                }`,
      }),
    });

    const { data } = await res.json();

    return {
      props: {
        data,
      },
    };
  };
</script>

<script>
  export let data;
</script>

<h1>Countries</h1>

{#each data.countries as { name, emoji }}
  <p>
    {emoji}
    {name}
  </p>
{/each}
