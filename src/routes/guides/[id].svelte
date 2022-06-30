<script context="module"> // need module in order to fetch data
    export async function load(context) { // load is a sveltekit function, context gives us access to fetch.. can destructure ({fetch})
    const id = context.params.id // this is whatever we name the path for the individual guide: [id].svelte
    
    // const res = await context.fetch(`https://jsonplaceholder.typicode.com/posts/${id}`)
    const res = await context.fetch(`/guides/${id}.json`) // our endpoint
      const {guide} = await res.json()
      if (res.ok) {
        console.log(guide)
        return {
          props: {
            guide: guide
          }
        }
      }
  
    //   return {
    //     status: res.status,
    //     error: new Error('Could not fetch the guide')
    //   }
    return {
        status: 301,
        redirect: '/guides'
    }
    }
  </script>

<script>
    export let guide
</script>

<div class="guide">
    <h2>{guide.title}</h2>
    <p>{guide.body}</p>
</div>

<style>
    .guide {
        margin: 40px;
        padding: 10px;
        border: 1px dotted rgba(255,255,255,0.2)
     }
</style>