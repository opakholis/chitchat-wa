<script lang="ts">
	let phoneNumber = '';

	const onSubmit = () => {
		window.location.href = `https://wa.me/${phoneNumber}`;
	};
</script>

<div class="flex justify-center items-center h-full">
	<div class="space-y-4 bg-slate-50 p-8 rounded-md shadow-lg w-full max-w-md">
		<h1 class="font-semibold text-center text-lg text-slate-800">
			WhatsApp 에 채팅
		</h1>
		<p class="text-center text-slate-600">
			채팅하기 전에 번호를 저장하는 데 지쳤습니까?
		</p>

		<form on:submit|once={onSubmit}>
			<input
				type="tel"
				bind:value={phoneNumber}
				placeholder="전화번호"
				class="w-full border border-slate-300 rounded-md p-2"
			/>
			<button
				type="submit"
				disabled={!phoneNumber}
				class="w-full py-2 px-4 bg-violet-600 text-white rounded-md mt-4 disabled:bg-violet-400"
				>갑시다!</button
			>
		</form>
	</div>
</div>
