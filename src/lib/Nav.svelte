<script lang="ts">
	import { page } from '$app/stores';
	import { slide } from 'svelte/transition';

	let isOpen = false;
</script>

<nav class="bg-gray-800">
	<div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8">
		<div class="relative flex items-center justify-between h-16">
			<div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
				<!-- Mobile menu button-->
				<button
					type="button"
					class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white hover:bg-gray-700 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
					aria-controls="mobile-menu"
					aria-expanded={isOpen}
					on:click={() => (isOpen = !isOpen)}
				>
					<span class="sr-only">Open main menu</span>
					<!--
            Icon when menu is closed.

            Heroicon name: outline/menu

            Menu open: "hidden", Menu closed: "block"
          -->
					<svg
						class="{isOpen ? 'hidden' : 'block'} h-6 w-6"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="2"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
					</svg>
					<!--
            Icon when menu is open.

            Heroicon name: outline/x

            Menu open: "block", Menu closed: "hidden"
          -->
					<svg
						class="{isOpen ? 'block' : 'hidden'} h-6 w-6"
						xmlns="http://www.w3.org/2000/svg"
						fill="none"
						viewBox="0 0 24 24"
						stroke-width="2"
						stroke="currentColor"
						aria-hidden="true"
					>
						<path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
					</svg>
				</button>
			</div>
			<div class="flex-1 flex items-center justify-center sm:items-stretch sm:justify-start">
				<div class="flex-shrink-0 flex items-center">
					<!-- <img
						class="block lg:hidden h-8 w-auto"
						src="https://tailwindui.com/img/logos/workflow-mark-indigo-500.svg"
						alt="Workflow"
					/>
					<img
						class="hidden lg:block h-8 w-auto"
						src="https://tailwindui.com/img/logos/workflow-logo-indigo-500-mark-white-text.svg"
						alt="Workflow"
					/> -->
				</div>
				<div class="hidden sm:block sm:ml-6">
					<div class="flex space-x-16">
						<!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
						<a
							href="/"
							class="{$page.url.pathname === '/'
								? `bg-gray-900 text-white`
								: `text-gray-300 hover:bg-gray-700 hover:text-white`} px-3 py-2 rounded-md text-sm font-medium"
							aria-current="page">Home</a
						>
						<a
							href="/fonts"
							class="{$page.url.pathname.startsWith('/fonts')
								? `bg-gray-900 text-white`
								: `text-gray-300 hover:bg-gray-700 hover:text-white`} px-3 py-2 rounded-md text-sm font-medium"
							aria-current="page">Fonts</a
						>

						<a
							href="/colors"
							class="{$page.url.pathname.startsWith('/colors')
								? `bg-gray-900 text-white`
								: `text-gray-300 hover:bg-gray-700 hover:text-white`} px-3 py-2 rounded-md text-sm font-medium"
							>Colors</a
						>
					</div>
				</div>
			</div>
		</div>
	</div>

	<!-- Mobile menu, show/hide based on menu state. -->
	{#if isOpen}
		<div class="sm:hidden" id="mobile-menu" transition:slide>
			<div class="px-2 pt-2 pb-3 space-y-1">
				<!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
				<a
					href="/"
					class="{$page.url.pathname === '/'
						? `bg-gray-900 text-white`
						: `text-gray-300 hover:bg-gray-700 hover:text-white`} block px-3 py-2 rounded-md text-base font-medium"
					aria-current="page">Home</a
				>
				<a
					href="/fonts"
					class="{$page.url.pathname.startsWith('/fonts')
						? `bg-gray-900 text-white`
						: `text-gray-300 hover:bg-gray-700 hover:text-white`} block px-3 py-2 rounded-md text-base font-medium"
					aria-current="page">Fonts</a
				>

				<a
					href="/colors"
					class="{$page.url.pathname.startsWith('/colors')
						? `bg-gray-900 text-white`
						: `text-gray-300 hover:bg-gray-700 hover:text-white`} block px-3 py-2 rounded-md text-base font-medium"
					>Colors</a
				>
			</div>
		</div>
	{/if}
</nav>
