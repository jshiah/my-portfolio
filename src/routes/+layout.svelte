<script>
    import { page } from '$app/stores';
    // import '../style.css'; // Import global CSS

    let pages = [
        { url: './', title: 'Home' },
        { url: './projects', title: 'Projects' },
        { url: './contact', title: 'Contact' },
        { url: './resume', title: 'Resume' },
        { url: 'https://github.com/jshiah', title: 'GitHub' } 
    ];
</script>



<nav>
    {#each pages as p}
        <a href={p.url} class:current={'.' + $page.route.id === p.url} target={ p.url.startsWith("http") ? "_blank" : null }>
            {p.title}
        </a>
    {/each}
</nav>


<slot />


<style>
    nav ul {
        display: contents; 
    }

    nav li {
        display: contents; 
    }

    nav {
        --border-color: oklch(50% 10% 200 / 40%); /* Define the semi-transparent border color */
        display: flex; 
        margin-bottom: 1em; 
        border-bottom-color: var(--border-color);
        /* border-bottom: 1px solid oklch(80% 3% 200);  */
    }

    nav a {
        flex: 1; 
        text-decoration: none; 
        color: inherit; 
        text-align: center; 
        padding: 0.5em; 
    }

    nav a.current {
        border-bottom: 0.4em solid oklch(80% 3% 200); 
        padding-bottom: 0.1em; 
    }

    nav a:hover {
        border-bottom: 0.4em solid var(--color-accent); 
        background-color: color-mix(in oklch, var(--color-accent), canvas 85%);
        /* background-color: oklch(from var(--color-accent) 95% 5% h);  */
    }
</style>