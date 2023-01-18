<script lang="ts">
    export let top: number = 60;
    export let left: number = 60;
    let grabbed: boolean = false;

    function onGrab() {
        grabbed = true;
    }
    function offGrab() {
        grabbed = false;
    }
    function onDrag(e: { movementX: number; movementY: number }) {
        if (grabbed) {
            [top, left] = [top + e.movementY, left + e.movementX];
        }
    }
</script>

<svelte:window on:mousemove={onDrag} on:mouseup={offGrab} />
<div
    class="frame flex flex-col drop-shadow-2xl rounded-xl overflow-hidden text-white"
    style="left: {left}px; top: {top}px"
>
    <div class="bar w-full cursor-move bg-[#484848dd]" on:mousedown={onGrab}>
        <div class="m-1 flex flex-row items-center">
            <div class="decobtn bg-red-600" />
            <div class="decobtn bg-yellow-400" />
            <div class="decobtn bg-green-500" />
        </div>
    </div>
    <div class="output w-full mb-1 text-right text-5xl font-thin">
        <span class="mr-3">12345</span>
    </div>
    <div class="input">
        <div class="row w-full flex flex-row items-center">
            <div class="key flex items-center justify-center bg-[#484848dd]">
                <span>C</span>
            </div>
            <div
                class="key flex items-center justify-center bg-[#484848dd] text-xs"
            >
                <span>+/-</span>
            </div>
            <div class="key flex items-center justify-center bg-[#484848dd]">
                <span>%</span>
            </div>
            <div class="key flex items-center justify-center bg-[#ff9f0bee]">
                <span>÷</span>
            </div>
        </div>
        <div class="row w-full flex flex-row items-center">
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>7</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>8</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>9</span>
            </div>
            <div class="key flex items-center justify-center bg-[#ff9f0bee]">
                <span>*</span>
            </div>
        </div>
        <div class="row w-full flex flex-row items-center">
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>4</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>5</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>6</span>
            </div>
            <div class="key flex items-center justify-center bg-[#ff9f0bee]">
                <span>-</span>
            </div>
        </div>
        <div class="row w-full flex flex-row items-center">
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>1</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>2</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>3</span>
            </div>
            <div class="key flex items-center justify-center bg-[#ff9f0bee]">
                <span>+</span>
            </div>
        </div>
        <div class="row w-full flex flex-row items-center">
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>00</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>0</span>
            </div>
            <div class="key flex items-center justify-center bg-[#717171dd]">
                <span>.</span>
            </div>
            <div class="key flex items-center justify-center bg-[#ff9d0bee]">
                <span>=</span>
            </div>
        </div>
    </div>
</div>

<style>
    .key {
        flex: 1 1 0px;
        border: solid rgba(0, 0, 0, 0.25);
        border-width: 1px 1px;
        height: 45px;
    }
    .decobtn {
        margin: 4px;
        width: 11px;
        height: 11px;
        border-radius: 50%;
    }
    .frame {
        width: 215px;
        height: 300px;
        position: absolute;
        background: #424242ee;
    }
</style>
