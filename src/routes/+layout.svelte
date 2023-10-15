<script>
    import '../app.scss'
</script>

<header>
    <div class="container-fluid"><nav>
        <ul>
            <li><strong>CrabbyDisk.net</strong></li>
            <li><a href="/">About me</a></li>
            <li><a href="/projects">Projects</a></li>
            <li><a href="/compare">Compare prices (pre-alpha)</a></li>
        </ul>
      </nav>
    </div>
</header>

<main>
    <slot />
</main>

<footer>
    <p>This is a footer, remind me that I need to put something here.</p>
</footer>