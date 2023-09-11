<template>
    <MainLayout>
        <div class="pt-[80px] pr-[30px] w-full max-w-[820px] border-r border-[#f2f2f2]">
            <div class="w-full ">
                <div class="flex flex-col h-[318px] mb-[34px] border-b">
                    <div class="mb-6">
                        <span class="text-2xl font-thin text-[#333333]">Recently Played</span>
                    </div>
                    <RecentlyPlayed>

                    </RecentlyPlayed>
                </div>
                <div class="flex flex-col h-[318px] mb-[34px] border-b">
                    <div class="mb-6">
                        <span class="text-2xl font-thin text-[#333333]">Charts: Top 50</span>
                    </div>
                    <RecentlyPlayed>

                    </RecentlyPlayed>
                </div>
                <div class="flex flex-col h-[318px] mb-[34px] border-b">
                    <div class="mb-6">
                        <span class="text-2xl font-thin text-[#333333]">More of what you like</span>
                    </div>
                    <RecentlyPlayed>

                    </RecentlyPlayed>
                </div>
                <div class="flex flex-col h-[318px] mb-[34px] border-b">
                    <div class="mb-6">
                        <span class="text-2xl font-thin text-[#333333]">More of what you like</span>
                    </div>
                    <RecentlyPlayed>

                    </RecentlyPlayed>
                </div>
                <div class="flex flex-col h-[318px] mb-[34px] border-b">
                    <div class="mb-6">
                        <span class="text-2xl font-thin text-[#333333]">More of what you like</span>
                    </div>
                    <RecentlyPlayed>

                    </RecentlyPlayed>
                </div>
                <div class="flex flex-col h-[318px] mb-[34px] border-b">
                    <div class="mb-6">
                        <span class="text-2xl font-thin text-[#333333]">More of what you like</span>
                    </div>
                    <RecentlyPlayed>

                    </RecentlyPlayed>
                </div>
                
            </div>
        </div>
        <div class="pt-[80px] w-[420px] h-full relative ">
            <div id="playDiv" class="h-[1000px] w-full max-w-[420px] top-0 ">
                <div class="h-[1000px] mb-[34px] border-b">
                    ABCD
                </div>
            </div>
        </div>
    </MainLayout>
</template>

<script setup>
    import MainLayout from '@/layouts/MainLayout.vue'
    onMounted(() => {
        let playDiv = document.getElementById("playDiv");
        document.addEventListener('scroll', function(e) {
            let maxY = window.scrollY + window.innerHeight
            if ((maxY) > playDiv.offsetHeight && (playDiv.offsetHeight) > window.innerHeight) {
                playDiv.classList.add("fixed", "top-[-"+ playDiv.offsetHeight +"px]");
            }
            else {
                playDiv.classList.remove("fixed", "top-[-"+ playDiv.offsetHeight +"px]");
            }
        });
    })

</script>
