<!-- route for this component is /guides/hello -->

<script context="module"> // need module in order to fetch data
  export async function load(context) { // load is a sveltekit function, context gives us access to fetch.. can destructure ({fetch})
    // const res = await context.fetch('https://jsonplaceholder.typicode.com/posts') <- for fetching from external endpoint
    const res = await context.fetch('/guides.json') // our endpoint. if named abc.json.js, endpoint is /guides.abc.json
    const {guides} = await res.json() //sending back an object so need to destructure
    if (res.ok) {
      console.log(guides)
      return {
        props: {
          // guides: guides
          guides: guides 
        }
      }
    }

    return { // this is passed to either the default error.svelte component in .svelte-kit/runtime/components
             // or is passed into the custom __error.svelte in /routes
      status: res.status,
      error: new Error('Could not fetch the guides')
    }
  }
</script>


<script>
  export let guides
</script>


<div class="guides">
    <ul>
        {#each guides as guide}
          <li>
            <a sveltekit:prefetch href={`/guides/${guide.id}`} >{guide.title}</a> 
            <!-- this makes a network request on hover without routing to the guide page -->
          </li>
        {/each}
    </ul>
</div>

<style>
    .guides {
      margin-top: 20px;
    }
    ul {
      list-style-type: none;
      padding: 0;
    }
    a {
      display: inline-block;
      margin-top: 10px;
      padding: 10px;
      border: 1px dotted rgba(255,255,255,0.2);
    }
  </style>