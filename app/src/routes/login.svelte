<script context="module">
  import { dev } from "$app/env";
  import clsx from "clsx";

  export const hydrate = dev;
</script>

<script>
  import SVG from "$lib/icons/SVG.svelte";
  import { google, twitch, facebook, reddit, twitter } from "$lib/icons/index";

  const links = [
    { name: "Twitch", icon: twitch, href: "/api/auth/signin/twitch" },
    { name: "Google", icon: google, href: "/api/auth/signin/google" },
    { name: "Facebook", icon: facebook, href: "/api/auth/signin/facebook" },
    { name: "Reddit", icon: reddit, href: "/api/auth/signin/reddit" },
  ];
</script>

<svelte:head>
  <title>Login | SvelteKitAuth</title>
</svelte:head>

<h1>Welcome to SvelteKitAuth</h1>

<section
  class={clsx(
    "flex",
    "items-center",
    "flex-col",
    "mt-4",
    "sm:mt-8",
    "md:mt-16",
    "shadow",
    "py-8",
    "sm:py-16",
    "md:py-32",
    "px-8",
    "sm:px-16 md:px-32 self-center",
  )}
>
  <h1 class={clsx("text-xl", "md:text-2xl")}>Login</h1>
  <hr class={clsx("my-3", "border-gray-400", "w-full")} />
  <p class={clsx("text-sm", "md:text-base", "text-gray-400", "max-w-lg")}>
    Login with one of the configured social providers to test the social login.
  </p>

  <br />

  <div class={clsx("flex", "flex-col", "justify-items-stretch", "space-y-4")}>
    {#each links as link}
      <a
        href={link.href}
        class={clsx(
          "text-sm",
          "md:text-base",
          "inline-flex",
          "space-x-4",
          "py-2",
          "px-4",
          "border-gray-400",
          "rounded",
          "hover:no-underline",
          "border",
          "hover:bg-gray-100",
          "transition-colors",
          "items-center",
        )}
      >
        <SVG icon={link.icon} />
        <span>Sign in with {link.name}</span>
      </a>
    {/each}

    <p class={clsx("text-gray-600", "text-center", "border-gray-400", "border-b", "pb-2")}>
      Coming soon.
    </p>

    <br />

    <p class={clsx("text-sm", "md:text-base", "text-orange-400", "max-w-lg")}>
      We will never share your identity with anyone else.
    </p>

    <div
      class={clsx(
        "text-sm",
        "md:text-base",
        "inline-flex",
        "space-x-4",
        "py-2",
        "px-4",
        "border-gray-400",
        "rounded",
        "hover:no-underline",
        "border",
        "hover:bg-gray-100",
        "transition-colors",
        "items-center",
        "text-gray-500",
        "cursor-not-allowed",
      )}
    >
      <SVG icon={twitter} />
      <span>Sign in with Twitter</span>
    </div>
  </div>
</section>
