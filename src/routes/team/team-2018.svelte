<svelte:head>
  <title>Team - 2018</title>
</svelte:head>

<script context="module">
  export async function preload() {
    const res = await this.fetch('./Data/2018Team.json');
    const datas = await res.json();
    return { datas };
  }
</script>

<script>
  import TeamComponent from '../../components/TeamComponent.svelte';

  export let datas;
</script>

<div class="main-title">OUR TEAM <br> 2018-2019</div>

<section class="card-list">
  {#each datas as data (data.id)} 
    <TeamComponent imgSrc={data.imgSrc} name={data.name} role={data.role}
    gitLink={data.gitlink} />
  {/each}
</section>

<style>
  .main-title {
    font-size: 3rem;
    font-weight: bold;
    text-align: center;
    padding-bottom: 1rem;
    border-bottom: 2px solid #ff8c00;
  }

  .card-list {
    display:grid;
    grid-template-columns: repeat(2,1fr);
    gap:7rem 3rem;
  }

  @media (max-width:700px) {
    .main-title {
      font-size:2.5rem;
    }
    .card-list {
      grid-template-columns: 1fr;
      gap:2rem 1rem;
    }
  }
</style>
