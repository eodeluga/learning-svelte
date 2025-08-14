<script lang='ts'>
  import '../app.css'
  import Header from './Header.svelte'
  
  type FormPages = {
    name: string
    dob: string
    job: string
  }
  
  type FormStep = {
    id: keyof FormPages
    question: string
    type: 'text' | 'date'
  }
  
  const formPages: FormPages = $state({
    name: '',
    dob: '',
    job: ''
  })
  
  const keys = Object.keys(formPages) as (keyof FormPages)[]
</script>

{#snippet formStep({ question, type, id }: FormStep)}
  <article>
    <div>
      <label for={id} class:error={formPages[id] === ''}>
        {question}
      </label>
      <div>
        <input 
          id={id}
          type={type}
          bind:value={formPages[id]}
          class:error={formPages[id] === ''}
        />
      </div>
    </div>
  </article>
{/snippet}

<main>
  <Header name={formPages.name}/>
  
  {#each keys as key}
    {#if key === 'name'}
      {@render formStep({
        question: 'What is your name',
        id: 'name',
        type: 'text'
      })}
    {/if}
    
    {#if key === 'dob'}
      {@render formStep({
        question: 'When were you born?',
        id: 'dob',
        type: 'date'
      })}
    {/if}
    
    {#if key === 'job'}
      {@render formStep({
        question: 'What do you do for a living?',
        id: 'job',
        type: 'text'
      })}
    {/if}
  {/each}
</main>

<style>
  label.error {
    color: red;
  }
</style>
