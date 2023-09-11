<template>
    <div class="flex-1">
        <div id="imageSlider" class="image-slider h-full">
            <!-- <button v-if="currentIndex > 0" class="slider-button" @click="slidePrev">Back</button> -->
            <button v-if="currentIndex > 0" class="slider-button" @click="slidePrev">
                <Icon class="mr-1" name="material-symbols:arrow-back-ios-new-rounded"  size="20"/>
            </button>
            <div class="image-container h-full" :style="{ transform: `translateX(${slidePosition}px)` }">
                <div id="imageContainer" class="flex flex-col min-w-[192px] pr-[20px]" v-for="(image, index) in images" :key="index">
                    <div class="relative" @mouseenter="showDiv(index)" @mouseleave="hideDiv(index)">
                        <img class="cursor-pointer" @click="toDetail" :src="image" alt="Image"/>
                        <div v-if="hoveredIndex === index" class="absolute align-middle items-center justify-center text-[#ff5500] top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
                            <Icon @click="play(123)" class="cursor-pointer" name="material-symbols:play-circle-rounded"  size="70"/>
                        </div>
                    </div>
                    <NuxtLink to="/#" class="text-left mt-2 text-sm text-[#333333] font-thin">Hao Ởi</NuxtLink>
                    <span class="text-left text-xs text-[#999999] font-thin">Lucin3x</span>
                    <div
                        class="flex items-center justify-center cursor-pointer mt-0.5"
                    >
                    <!-- <button class="flex items-center text-[#333] align-middle border border-[#e5e5e5] hover:border-[#cccccc] px-2 rounded leading-2" value="">
                            <Icon class="mr-1" name="material-symbols:person-add-outline"  size="20"/>
                            Follow
                    </button> -->
                    </div>
                </div>
            </div>
            <!-- <button v-if="currentIndex < images.length - 4" class="slider-button" @click="slideNext">Next</button> -->
            <button v-if="currentIndex < images.length - 4" class="slider-button" @click="slideNext">
                <Icon class="mr-1" name="material-symbols:arrow-forward-ios-rounded"  size="20"/>
            </button>
          </div>
    </div>
</template>

<script>
import songImagePath from '~/assets/images/song-avatar.jpg'

export default {
  data() {
    return {
      images: [
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        songImagePath,
        // Add more image URLs here
      ],
      slidePosition: 0,
      elementWidth: 0,
      slideWidth: 0,
      currentIndex: 0,
      hoveredIndex: null,
    };
  },
  mounted() {
    this.elementWidth = document.getElementById('imageContainer').offsetWidth; // Display 4 images at a time
    this.slideWidth = document.getElementById('imageSlider').offsetWidth; // Display 4 images at a time
  },
  methods: {
    slideNext() {
        if (this.currentIndex + 4 < this.images.length) {
            this.currentIndex = this.currentIndex + 4;
            if (this.currentIndex + 4 >= this.images.length) {
                this.slidePosition = -this.elementWidth * this.images.length + this.slideWidth +20;
                this.currentIndex = this.images.length - 4;
            }
            else {
                this.slidePosition = -this.elementWidth * this.currentIndex + ((this.slideWidth - (this.elementWidth * 4) + 20) / 2);
            }
        }
    },
    slidePrev() {
        if (this.currentIndex > 0) {
            this.currentIndex = this.currentIndex - 4;
            if (this.currentIndex < 0) {
                this.slidePosition = 0;
                this.currentIndex = 0;
            }
            else {
                this.slidePosition = -this.elementWidth * this.currentIndex + ((this.slideWidth - (this.elementWidth * 4) + 20) / 2);
            }
        }
    },
    toDetail() {
          try {
                useRouter().push('/#')
          } catch (error) {
              console.log(error)
          }
    },
    showDiv(index) {
      this.hoveredIndex = index;
    },
    hideDiv(index) {
      this.hoveredIndex = null;
    },
    play(songId) {
      console.log(songId);
    },
  },
};
</script>

<style scoped>
.image-slider {
  overflow: hidden;
  position: relative;
  text-align: center;
}

.image-container {
  display: flex;
  transition: transform .6s ease-in-out 0s;
}

.slider-button {
  position: absolute;
  top: 34%;
  transform: translateY(-50%);
  padding: 10px;
  background-color: #fff;
  color: #333;
  border: 1px solid #cccccc;
  border-radius: 3px;
  cursor: pointer;
  z-index: 1;
}
.slider-button:hover {
  border: 1px solid #ff5500;
  color: #ff5500;
}
.slider-button:first-child {
  left: 0.5%;
}

.slider-button:last-child {
  right:  0.5%;
}

img {
    width: 100%;
    overflow:hidden;
}
</style>