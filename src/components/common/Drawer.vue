<script setup>
import { ref, computed, watch, onWatcherCleanup, nextTick } from 'vue';

 const open = defineModel('open', { type: Boolean, default: false });

 const props = defineProps({
    side: {
        type: String,
        default: 'right',
        validator: (v) => ['left', 'right'].includes(v),
    },
    closeOnBackdrop: { type: Boolean, default: true },
    closeOnEsc: { type: Boolean, default: true },
});

 const panel = ref(null);
let lastFocused = null;

 const close = () => {
	open.value = false;
}

 const hiddenTranslate = computed(() =>
	props.side === 'right' ? 'translate-x-full' : '-translate-x-full'
);

 const onKeydown = (e) => {
	if (e.key === 'Escape' && props.closeOnEsc) close();
};

 watch(open, (isOpen) => {
	if (!isOpen) {
		lastFocused?.focus?.()
		lastFocused = null
		return
	}

 	lastFocused = document.activeElement;
	nextTick(() => panel.value?.focus());

 	document.addEventListener('keydown', onKeydown);
	document.body.style.overflow = 'hidden';

 	onWatcherCleanup(() => {
		document.removeEventListener('keydown', onKeydown);
		document.body.style.overflow = '';
	})
}, { immediate: true })
</script>

 <template>
	<Teleport to="body">
        <Transition
            enter-active-class="transition-opacity duration-300 ease-out"
            enter-from-class="opacity-0"
            leave-active-class="transition-opacity duration-200 ease-in"
            leave-to-class="opacity-0"
        >
            <div
                v-if="open"
                class="fixed inset-0 z-40 bg-black/50"
                @click="closeOnBackdrop && close()"
            />
        </Transition>

         <Transition
            enter-active-class="transition-oppacity duration-300 ease-out"
            enter-from-class="opacity-0"
            leave-active-class="transition-opacity duration-200 ease-in"
            leave-to-class="opacity-0"
        >
            <div
                v-if="open"
                ref="panel"
                tabindex="-1"
                role="dialog"
                aria-modal="true"
                :class="[
                    'fixed inset-y-0 z-50 flex w-full md:max-w-sm flex-col bg-white shadow-xl outline-none',
                    side === 'right' ? 'right-0' : 'left-0',
                ]"
            >
                <div class="flex shrink-0 items-center justify-between border-b border-gray-100">
                    <slot name="header" :close="close" />

                 </div>

                 <div class="flex-1 overflow-y-auto overscroll-contain">
                    <slot :close="close" />
                </div>
            </div>
        </Transition>
    </Teleport>
</template>