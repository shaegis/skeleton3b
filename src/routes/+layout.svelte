<script lang="ts">
	import '../app.css';
    import { AppBar } from '@skeletonlabs/skeleton-svelte';
    import { Navigation } from '@skeletonlabs/skeleton-svelte';
    // Icons
    import IconBack from 'lucide-svelte/icons/arrow-left';
    import IconSignup from 'lucide-svelte/icons/user-plus';
    import IconLogin from 'lucide-svelte/icons/log-in';
    import IconLogout from 'lucide-svelte/icons/log-out';
    import IconHome from 'lucide-svelte/icons/house';
    import IconProgress from 'lucide-svelte/icons/notebook-pen';
    import IconScale from 'lucide-svelte/icons/ruler';
    import IconSettings from 'lucide-svelte/icons/settings';

	let { children } = $props();
    let hrefExample = '#';
</script>

<div class="flex flex-col h-screen">
    <AppBar>
        {#snippet lead()}
            <IconBack size={24} />
            <!-- If subDir, then show name of subDir. -->
            <div class="pl-4">Charting Up</div>
        {/snippet}
        {#snippet trail()}
            <IconSignup size={20} />
            <IconLogin size={20} />
            <IconLogout size={20} />
        {/snippet}
    </AppBar>
    
    <div class="flex flex-1">
        <!-- Only when Lon-In case. If Not, Do NOT show Rail. -->
        <Navigation.Rail>
            {#snippet header()}
                <Navigation.Tile label="Home" href={hrefExample} tilte="Home">
                    <IconHome />
                </Navigation.Tile>
            {/snippet}
            {#snippet tiles()}
                <Navigation.Tile id="0" label="Progress" href={hrefExample}>
                    <IconProgress />
                </Navigation.Tile>
                <Navigation.Tile id="1" label="Scale" href={hrefExample}>
                    <IconScale />
                </Navigation.Tile>
            {/snippet}
            {#snippet footer()}
                <Navigation.Tile label="Settings" href="/settings" tilte="settings">
                    <IconSettings />
                </Navigation.Tile>
            {/snippet}
        </Navigation.Rail>

        <!-- Content -->
        <div class="flex-1 overflow-auto p-4">
            <div class="prose">
                {@render children()}
            </div>
        </div>
    </div>
</div>
