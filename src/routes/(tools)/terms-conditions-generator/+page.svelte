<script lang="ts">
	import Intro from '$lib/Intro.svelte';

	export let data;

	// start
	let companyName = '';
	let websiteName = '';
	let websiteUrl = '';
	let email = '';
	let showTerms = true; // A variable to control the visibility of the h2 and Copy button

	let termsAndPolicy = '';

	function handleSubmit() {
		// Capture the user's input
		companyName = companyName.trim();
		websiteName = websiteName.trim();
		websiteUrl = websiteUrl.trim();

		const companyNameBold = `<strong>${companyName}</strong>`;

		// Generate the terms and policy content
		termsAndPolicy = `
      <strong>Terms and Conditions</strong>

      This agreement ("Agreement") is entered into between ${companyNameBold} and you, the user of ${websiteName} (${websiteUrl}). By accessing and using ${websiteUrl}, you agree to be bound by the terms and conditions set forth in this Agreement.

      ...

      **Privacy Policy**

      We respect your privacy. Our Privacy Policy explains how we collect, use, and protect your personal information when you use our services. Please read it carefully.

      - Company Name: ${companyNameBold}
      - Website Name: ${websiteName}
      - Website URL: ${websiteUrl}

      ...
    `;
		console.log(companyName);

		showTerms = false;
	}
</script>

<Intro heading={data.meta.title} description={data.meta.description} />

<div class=" bg-[#323A49] mt-2 w-1/2 container mx-auto py-8 flex flex-col items-center">
	<h1 class="text-3xl comp font-semibold mb-4 tw-text-red">Company Information</h1>
	<form on:submit={handleSubmit} class="space-y-4">
		<div class="flex flex-col">
			<label for="companyName" class="text-lg text-white">Company Name:</label>
			<input
				type="text"
				id="companyName"
				bind:value={companyName}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
			/>
		</div>
		<div class="flex flex-col">
			<label for="websiteName" class="text-lg text-white">Website Name:</label>
			<input
				type="text"
				id="websiteName"
				bind:value={websiteName}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
			/>
		</div>
		<div class="flex flex-col">
			<label for="websiteUrl" class="text-lg text-white">Website URL:</label>
			<input
				type="text"
				id="websiteUrl"
				bind:value={websiteUrl}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
				required
			/>
		</div>
		<div class="flex flex-col">
			<label for="email" class="text-lg text-white">Enter your Email</label>
			<input
				type="email"
				id="email"
				bind:value={email}
				class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
				placeholder="john.doe@company.com"
				required
			/>
		</div>
		<button
			type="submit"
			class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
		>
			Generate My Terms & Conditions
			<svg
				class="w-3.5 h-3.5 ml-2"
				aria-hidden="true"
				xmlns="http://www.w3.org/2000/svg"
				fill="none"
				viewBox="0 0 14 10"
			>
				<path
					stroke="currentColor"
					stroke-linecap="round"
					stroke-linejoin="round"
					stroke-width="2"
					d="M1 5h12m0 0L9 1m4 4L9 9"
				/>
			</svg>
		</button>
	</form>
</div>

<div class=" result w-1/2 content flex flex-col items-center justify-center mx-auto mt-8">
	{#if !showTerms}
			<button
				type="button"
				class="text-gray-900 bg-white border border-gray-300 focus:outline-none hover:bg-gray-100 focus:ring-4 focus:ring-gray-200 font-medium rounded-full text-sm px-5 py-2.5 mr-2 mb-2 dark:bg-gray-800 dark:text-white dark:border-gray-600 dark:hover:bg-gray-700 dark:hover:border-gray-600 dark:focus:ring-gray-700"
				>Copy</button>
				{/if}
		{#if showTerms}
			<h2>Terms & Conditions Will go here</h2>
			{/if}
			<div class="">{@html termsAndPolicy}</div>
</div>

<style>
	.content {
		padding: 20px;
		background-color: lightgray;
	}
	.comp {
		color: white;
	}
</style>
