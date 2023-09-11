<template>
    <div
        id="TopNav"
        class="fixed bg-[#333333] z-30 flex items-center w-full h-[45px]"
    >
        <div
            class="flex items-center justify-between h-full w-full max-w-[1240px] mx-auto"
        >
            <div class="flex items-center gap-0 justify-start min-w-[275px]  w-full h-full">
                <div
                    class="h-full w-[100px]" 
                    :style="{
                        background: `url(${backgroundImagePath}) no-repeat  center #000000`,
                        padding: '10px',
                        backgroundOrigin:' content-box'
                    }"
                >
                    <NuxtLink to="/discover" >
                        <div class="h-full"/>
                    </NuxtLink>
                </div>
                <div class="w-[105px] h-full">
                    <button
                        @click="toHome()"
                        :class="route.fullPath === '/discover' ? 'bg-[#111111] text-[#fff]' : ''" 
                        class="flex items-center justify-center border-r border-[#000] rounded-sm px-3 py-[6px] text-[#ccc] hover:text-gray-100 h-full w-full"
                    >
                        <span class="px-2 text-[14px]">Home</span>
                    </button>
                </div>
                <div class="w-[105px] h-full">
                    <button
                        @click="toFeed()"
                        :class="route.fullPath === '/feed' ? 'bg-[#111111] text-[#fff]' : ''" 
                        class="flex items-center justify-center border-r border-[#000] rounded-sm px-3 py-[6px] text-[#ccc] hover:text-gray-100 h-full w-full"
                    >
                        <span class="px-2 text-[14px]">Feed</span>
                    </button>
                </div>
                <div class="w-[105px] h-full">
                    <button
                        :class="route.fullPath === '/you/library' ? 'bg-[#111111] text-[#fff]' : ''" 
                        class="flex items-center justify-center border-r border-[#000] rounded-sm px-3 py-[6px] text-[#ccc] hover:text-gray-100 h-full w-full"
                    >
                        <span class="px-2 text-[14px]">Library</span>
                    </button>
                </div>
            </div>
            <div class="hidden md:flex ml-2 items-center bg-[#F1F1F2] rounded-[5px] max-w-[380px] w-full">
                <input 
                    type="text" 
                    class="w-full pl-3 my-1 bg-transparent placeholder-[#838383] text-[15px] focus:outline-none"
                    placeholder="Search accounts"
                >
                <div class="px-3 py-1 flex items-center ">
                    <Icon name="mdi:magnify" color="#666666" size="20"/>
                </div>
            </div>
            <div class="flex items-center gap-0 justify-end min-w-[275px]  w-full h-full">
                <div class=" h-full">
                    <button
                        class="flex items-center justify-center rounded-sm px-3 py-[6px] text-[#ff5510] h-full w-full"
                    >
                        <span class="px-2 text-[14px]">Try Next Pro</span>
                    </button>
                </div>
                <div class="h-full">
                    <button
                        class="flex items-center justify-center rounded-sm px-3 py-[6px] text-[#ccc] hover:text-gray-100 h-full w-full "
                    >
                        <span class="px-2 text-[14px]">For Artists</span>
                    </button>
                </div>
                <div class="h-full">
                    <button
                        class="flex items-center justify-center rounded-sm px-3 py-[6px] text-[#ccc] hover:text-gray-100 h-full w-full"
                    >
                        <span class="px-2 text-[14px]">Upload</span>
                    </button>
                </div>
            </div>
            <div class="flex items-center justify-items-center h-full">
                <div class="relative h-full">
                    <div
                        @click="showMenu = !showMenu"
                        :class="showMenu?'bg-black':''"
                        class="flex items-center cursor-pointer h-full px-2.5"
                        id="MenuBtn"
                    >
                        <button 
                            class="mr-2"
                        >
                            <img 
                                class="rounded-full" 
                                width="40" 
                                src="~/assets/images/avatar.png"
                            >
                        </button>
                        <Icon class="text-[#cccccc] hover:text-gray-100" name="ic:outline-keyboard-arrow-down" size="30"/>
                    </div>

                    <div 
                        v-if="showMenu"
                        id="PopupMenu"
                        class="absolute bg-white shadow-xl border-x border-b border-[#ccc] top-[45px] "
                    >
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="material-symbols:person"  size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Profile</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="material-symbols:favorite" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Likes</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="ph:copy-simple-fill" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Playlist</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="fluent:live-24-filled" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Stations</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="mdi:account-multiple" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Following</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="mdi:account-multiple" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Who to follow</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="material-symbols:star-rate" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Try Next Pro</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="game-icons:present" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Partner offers</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="ph:waveform-bold" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Tracks</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="material-symbols:bar-chart-4-bars-rounded" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Insights</span>
                        </NuxtLink>
                        <NuxtLink
                            @click="showMenu = false" 
                            class="flex items-center justify-start py-2 px-2.5 text-[#333333] hover:bg-gray-100 cursor-pointer"
                        >
                            <Icon name="fluent:text-align-distributed-vertical-24-filled" size="20"/>
                            <span class="pl-2 font-bold text-sm whitespace-nowrap">Distribute</span>
                        </NuxtLink>
                        
                    </div>
                </div>
                <Icon class="ml-5 mr-5 text-[#cccccc] hover:text-gray-100 cursor-pointer" name="iconamoon:notification-fill" size="25"/>
                <Icon class="mr-5 text-[#cccccc] hover:text-gray-100 cursor-pointer" name="uiw:mail" size="25"/>
                <Icon class="mr-5 text-[#cccccc] hover:text-gray-100 cursor-pointer" name="fluent:more-28-filled" size="25"/>

            </div>
        </div>
    </div>
</template>

<script setup>
    import backgroundImagePath from '~/assets/images/sound-cloud-white-logo.svg'
    const route = useRoute()
    const router = useRouter()
    let showMenu = ref(false)

    onMounted(() => {
        document.addEventListener('mouseup', function(e) {
            let popupMenu = document.getElementById('PopupMenu');
            let menuBtn = document.getElementById('MenuBtn');
            if (popupMenu != null && !popupMenu.contains(e.target)&& !menuBtn.contains(e.target)) {
                showMenu.value = false
            }
        });
    })

    const toHome = () => {
        try {
            router.push('/discover')
        } catch (error) {
            console.log(error)
        }
    }
    const toFeed = () => {
        try {
            router.push('/feed')
        } catch (error) {
            console.log(error)
        }
    }
</script>
