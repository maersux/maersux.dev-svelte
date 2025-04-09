<script lang="ts">
  import github from './svg/github.svelte';
  import twitch from './svg/twitch.svelte';

  type Social = {
    platform: 'github' | 'twitch';
    username: string;
    component: typeof github | typeof twitch;
  };

  const socials: Social[] = [
    { platform: 'github', username: 'maersux', component: github },
    { platform: 'twitch', username: 'maersux', component: twitch },
  ];
</script>


<div class="socials">
  {#each socials as { platform, username, component: SocialComponent } (platform)}
    <SocialComponent {username} />
  {/each}
</div>

<style>
    div.socials {
        display: flex;
        gap: 1rem;
    }
</style>