<template>
    <div class="container mx-auto p-10">
        <div class="flex flex-col justify-center items-center text-center">
            <div class="font-bold pb-10">
                <h1 class="text-3xl text-base-content">Testimonial</h1>
            </div>
        </div>

        <div class="mx-auto max-w-4xl">
            <swiper
                :modules="modules"
                :slides-per-view="3"
                :space-between="10"
                :loop="true"
                :pagination="{ clickable: true }"
                :scrollbar="{ draggable: true }"
                :centeredSlides="true"
                :grabCursor="true"
                @swiper="onSwiper"
                @slideChange="onSlideChange"
            >
                <swiper-slide
                    v-for="(testimonial, index) in testimonials"
                    :key="index"
                    ><div class="card h-56 bg-primary-content text-primary shadow-xl">
                        <div class="card-body">
                            <h2 class="card-title flex-1">{{ testimonial.isi }}</h2>
                            <div class="flex flex-col justify-center pt-4">
                                <div>
                                    {{ testimonial.nama }}
                                </div>
                                <div>
                                    {{ testimonial.profesi }}
                                </div>
                            </div>
                        </div>
                    </div></swiper-slide
                >
            </swiper>
        </div>
    </div>
</template>

<script>
import { ref, onMounted } from "vue";
import Api from "../../api";
import { Pagination, Scrollbar, A11y } from "swiper/modules";
import { Swiper, SwiperSlide } from "swiper/vue";
import "swiper/css";
import "swiper/css/pagination";

export default {
    components: {
        Swiper,
        SwiperSlide,
    },
    setup() {
        const testimonials = ref([]);

        const fetchDataTesti = async () => {
            try {
                const response = await Api.get("/api/testimonials");
                testimonials.value = response.data;
            } catch (error) {
                console.error("Error fetching testimonials:", error);
            }
        };

        const onSwiper = (swiper) => {
            console.log(swiper);
        };

        const onSlideChange = () => {
            console.log("slide change");
        };

        onMounted(() => {
            fetchDataTesti();
        });

        const modules = [Pagination, Scrollbar, A11y];

        return {
            testimonials,
            onSwiper,
            onSlideChange,
            modules,
        };
    },
};
</script>
