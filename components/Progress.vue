<template>
    <div>
   <div class="progress">
            <div
                class="progress-bar progress-bar-striped progress-bar-animated"
                :class="{'bg-success':currentItem==12}"
                role="progressbar"
                :style="{width: progress + '%'}"
                aria-valuenow="50"
                aria-valuemin="0"
                aria-valuemax="120"
            >
                <span style=" text-align: center;"> {{currentItem}}/12</span>    
            </div>
        </div>
        <br><br>
    </div>
</template>

<script>
import {eventBus} from "../main"
    export default {
        data() {
            return {
                currentItem: 0,
                progress: 0,
            }
        },
        created(){
            eventBus.$on("progressBarUpdated", (productListCount)=>{
                this.currentItem = productListCount;
                this.progress  = productListCount * (100/12);
                
            })
        }
        
    }
</script>

