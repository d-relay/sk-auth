<script context="module">
  import { dev } from "$app/env";
  import { session } from "$app/stores";
  import SVG from "$lib/icons/SVG.svelte";
  import { google, twitch, reddit, facebook, twitter } from "$lib/icons/index";
  import clsx from "clsx";

  export const hydrate = dev;
</script>

<svelte:head>
  <title>Profile | SvelteKitAuth</title>
</svelte:head>

<h1 class={clsx("mb-4")}>Your Profile</h1>

<div class={clsx("flex", "flex-col")}>
  <p class={clsx("text-lg", "mb-2")}>Connections</p>

  <div
    class={clsx(
      "grid",
      "grid-cols-2",
      "sm:grid-cols-3",
      "md:grid-cols-4",
      "lg:grid-cols-6",
      "gap-4",
      "mb-6",
    )}
  >
    <div class={clsx("flex", "items-center", "space-x-4")}>
      <SVG icon={twitch} />
      <div class={clsx("flex", "flex-col", "items-start", "space-y-1")}>
        {#if $session.user.connections.twitch}
          <p class={clsx("font-bold")}>Signed in as:</p>
          {$session.user.connections.twitch.display_name}
        {:else}
          <p class={clsx("font-bold")}>Not signed in</p>
          <a
            href="/api/auth/signin/google"
            class={clsx(
              "text-xs",
              "md:text-sm",
              "py-1",
              "px-2",
              "border-gray-400",
              "rounded",
              "hover:no-underline",
              "border",
              "hover:bg-gray-100",
              "transition-colors",
              "items-center",
            )}
          >
            Connect
          </a>
        {/if}
      </div>
    </div>
    <div class={clsx("flex", "items-center", "space-x-4")}>
      <SVG icon={google} />
      <div class={clsx("flex", "flex-col", "items-start", "space-y-1")}>
        {#if $session.user.connections.google}
          <p class={clsx("font-bold")}>Signed in as:</p>
          {$session.user.connections.google.name}
        {:else}
          <p class={clsx("font-bold")}>Not signed in</p>
          <a
            href="/api/auth/signin/google"
            class={clsx(
              "text-xs",
              "md:text-sm",
              "py-1",
              "px-2",
              "border-gray-400",
              "rounded",
              "hover:no-underline",
              "border",
              "hover:bg-gray-100",
              "transition-colors",
              "items-center",
            )}
          >
            Connect
          </a>
        {/if}
      </div>
    </div>
    <div class={clsx("flex", "items-center", "space-x-4")}>
      <SVG icon={facebook} />
      <div class={clsx("flex", "flex-col", "items-start", "space-y-1")}>
        {#if $session.user.connections.facebook}
          <p class={clsx("font-bold")}>Signed in as:</p>
          {$session.user.connections.facebook.name}
        {:else}
          <p class={clsx("font-bold")}>Not signed in</p>
          <a
            href="/api/auth/signin/facebook"
            class={clsx(
              "text-xs",
              "md:text-sm",
              "py-1",
              "px-2",
              "border-gray-400",
              "rounded",
              "hover:no-underline",
              "border",
              "hover:bg-gray-100",
              "transition-colors",
              "items-center",
            )}
          >
            Connect
          </a>
        {/if}
      </div>
    </div>
    <div class={clsx("flex", "items-center", "space-x-4")}>
      <SVG icon={reddit} />
      <div class={clsx("flex", "flex-col", "items-start", "space-y-1")}>
        {#if $session.user.connections.reddit}
          <p class={clsx("font-bold")}>Signed in as:</p>
          {$session.user.connections.reddit.name}
        {:else}
          <p class={clsx("font-bold")}>Not signed in</p>
          <a
            href="/api/auth/signin/reddit"
            class={clsx(
              "text-xs",
              "md:text-sm",
              "py-1",
              "px-2",
              "border-gray-400",
              "rounded",
              "hover:no-underline",
              "border",
              "hover:bg-gray-100",
              "transition-colors",
              "items-center",
            )}
          >
            Connect
          </a>
        {/if}
      </div>
    </div>
    <div class={clsx("flex", "items-center", "space-x-4")}>
      <SVG icon={twitter} />
      <div class={clsx("flex", "flex-col", "items-start", "space-y-1")}>
        {#if $session.user.connections.twitter}
          <p class={clsx("font-bold")}>Signed in as:</p>

          {$session.user.connections.twitter.name}
        {:else}
          <p class={clsx("font-bold")}>Not signed in</p>
          <div
            class={clsx(
              "text-xs",
              "md:text-sm",
              "py-1",
              "px-2",
              "border-gray-400",
              "rounded",
              "hover:no-underline",
              "border",
              "hover:bg-gray-100",
              "transition-colors",
              "items-center",
              "cursor-not-allowed",
              "inline-block",
            )}
          >
            Connect
          </div>
        {/if}
      </div>
    </div>
  </div>

  <p class={clsx("text-lg", "mb-2")}>Session</p>
  <pre
    class={clsx(
      "bg-gray-100",
      "whitespace-pre-wrap",
      "p-3",
    )}>
    <code>{JSON.stringify($session, null, 2)}</code>
  </pre>
</div>
