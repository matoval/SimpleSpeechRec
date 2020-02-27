<script>
import { onMount } from 'svelte';
let menu = false;
let isMobile = false;

function toggleMenu() {
  menu = !menu;
}

onMount(() => {
  resizing();
})

function resizing() {
  console.log("resize");
  console.log(document.body.clientWidth);
  if(document.body.clientWidth < 600) {
    isMobile = true;
    console.log(isMobile);
  } 
  else {
    isMobile = false;
    console.log(isMobile);
  }
}

window.addEventListener("resize", resizing);

</script>

<main on:resize="{resizing}">
  <div class="topbar">
    <div class="graphic">
      <img class="HP-glasses" src="HP-glasses.svg" alt="glasses">
    </div>
    <div class="logo">
      <h1 class="page-title">Cast a Spell</h1>
    </div>
    {#if !isMobile}
    <div class="nav">
      <ul>
        <li><button>Nav1</button></li>
        <li><button>Nav1</button></li>
        <li><button>Nav1</button></li>
        <li><button>Nav1</button></li>
      </ul>
    </div>
    {:else if isMobile}
    <div class="mobile-nav">
      <button class="open-menu" on:click="{toggleMenu}">&#9776</button>
      {#if menu}
        <ul>
          <li><button>Nav1</button></li>
          <li><button>Nav1</button></li>
          <li><button>Nav1</button></li>
          <li><button>Nav1</button></li>
        </ul>
      {/if}
    </div>
    {/if}
  </div>
	
</main>

<style>
  .topbar {
    width: 100vw;
    background-color: var(--primary);
    position: fixed;
    top: 0;
    display: flex;
    justify-content: space-between;
  }

  .page-title {
    padding: 5px;
    margin: 0 auto;
    color: var(--light-font);
  }

  .nav {
    margin-right: 25px;
  }

  button {
    border-radius: 5px;
    border: none;
    cursor: pointer;
  }

  .nav li {
    color: var(--light-font);
    list-style: none;
    float: left;
    padding: 5px 15px;
  }

  .mobile-nav ul {
    position: fixed;
    padding: 5px;
    right: 10px;
    top: 30px;
    list-style: none;
    display: flex;
    flex-direction: column;
    background-color: var(--primary);
    border-radius: 0 0 5px 5px;
  }

  .mobile-nav li {
    padding: 8px;
    color: var(--light-font);
  }

  .open-menu {
    position: fixed;
    right: 0;
    border: none;
    width: 35px;
    color: var(--light-font);
    background-color: var(--secondary);
    margin: 5px;
  }
  .HP-glasses {
    height: 15px;
    width: auto;
    margin: 25px 5px;
  }

  .graphic {
    height: 60px;
  }

  @media only screen and (max-device-width: 600px) {
    
  } 
	
</style>