<script lang="ts">
	const title = 'WhatsApp 에 채팅';
	const description = '채팅하기 전에 번호를 저장하는 데 지쳤습니까?';

	let phone = '';

	const onSubmit = () => {
		// TODO: nice to have if we adding more dial code
		const dialCode = '+62'.replace(/^\+/gi, '');

		// validate that we only accept numbers
		const number = `${dialCode}${phone
			?.replace(/[^0-9]/gi, '')
			.replace(new RegExp(`^0|^${dialCode}`, 'gi'), '')}`;

		window.location.href = `https://wa.me/${number}`;
	};
</script>

<svelte:head>
	<title>{title}</title>
	<meta name="description" content={description} />
</svelte:head>

<div class="flex justify-center items-center h-full">
	<div class="space-y-4 bg-slate-50 p-8 rounded-md shadow-lg w-full max-w-md">
		<h1 class="font-semibold text-center text-lg text-slate-800">
			{title}
		</h1>
		<p class="text-center text-slate-600">
			{description}
		</p>

		<form on:submit|preventDefault={onSubmit}>
			<input
				type="tel"
				aria-label="Phone number"
				placeholder="전화번호"
				bind:value={phone}
				class="w-full border border-slate-300 rounded-md p-2"
			/>
			<button
				type="submit"
				aria-label="Start chat"
				disabled={!phone}
				class="w-full py-2 px-4 bg-violet-600 text-white rounded-md mt-4 disabled:bg-violet-400"
				>갑시다!</button
			>
		</form>
	</div>
</div>
