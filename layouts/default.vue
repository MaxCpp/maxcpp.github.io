<template>
    <div class="page-wrapper" :class="{'is-mobile': isMobile}">
<!--        <Header/>-->
        <aside class="page-wrapper__aside">
            <Menu/>
        </aside>
        <main class="page-wrapper__main">
            <slot/>
        </main>

<!--		<a href="#" class="btn-up" :class="{'btn-up_showed': isScrolled}">-->
<!--			<IconButtonUp/>-->
<!--		</a>-->

	</div>
</template>

<script>
import {useStore} from "~/stores/store.js";

export default {
	name: 'default',
    // setup() {
    //     const store = useStore();
    //     const { $helpers } = useNuxtApp();
    //
    //     if (process.client) {
    //         store.isMobile = $helpers.detectMobile();
    //     }
    //
    //     return {
    //         isMobile: store.isMobile
    //     }
    // },
	data() {
		return {
            isMobile: false,
			isScrolled: false
		};
	},
	mounted() {
		window.addEventListener('scroll', this.handleScroll);
	},
	methods: {
		handleScroll() {
			this.isScrolled = window.scrollY >= window.innerHeight / 2;
		}
	},
};
</script>

<style lang="scss">
.page-wrapper {
    display: flex;

    &__aside {
        max-width: 280px;
        padding: 10px;
    }
    
    &__main {
        padding: 50px 36px;
    }
}
main {
    width: 100%;
	//min-height:calc(100vh - 400px);
}
</style>
