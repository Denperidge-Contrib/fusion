<script lang="ts">
	import type { Item } from '$lib/api/model';
	import { ArrowUpIcon, ArrowLeftIcon, ArrowRightIcon } from 'lucide-svelte';
	import ItemActionBase from './ItemActionBase.svelte';
	import ItemActionBookmark from './ItemActionBookmark.svelte';
	import ItemActionUnread from './ItemActionUnread.svelte';
	import ItemActionVisitLink from './ItemActionVisitLink.svelte';
	import { Separator } from './ui/separator';

	interface Props {
		data: Item;
		fixed?: boolean;
	}

	let { data, fixed = true }: Props = $props();

	function handleScrollTop(e: Event) {
		e.preventDefault();
		document.body.scrollIntoView({ behavior: 'smooth' });
	}

	function previousItem(e: Event) {
		
	}

	function nextItem(e: Event) {
		console.log(e);
	}
</script>

<div class="{fixed ? 'fixed' : ''} bottom-2 left-0 right-0">
	<div
		class="flex flex-row justify-center items-center gap-2 rounded-full border shadow w-fit mx-auto bg-background px-6 py-2"
	>
		<ItemActionUnread {data} />
		<Separator orientation="vertical" class="h-5" />
		<ItemActionBookmark {data} />
		<Separator orientation="vertical" class="h-5" />
		<ItemActionVisitLink {data} />
		<Separator orientation="vertical" class="h-5" />
		<ItemActionBase fn={handleScrollTop} tooltip="Back to Top" icon={ArrowUpIcon} />
		<Separator orientation="vertical" class="h-5" />
		<ItemActionBase fn={previousItem} tooltip="Previous item" icon={ArrowLeftIcon} />
		<ItemActionBase fn={nextItem} tooltip="Next item" icon={ArrowRightIcon} />
	
	</div>
</div>
