<template>
    <div>
        <div id="view_container">
            <div id="canvas_block">
                <canvas id="c" tabindex="0" resize></canvas>
            </div>
            <div id="renderContainer"/>
        </div>
    </div>
</template>

<script>
import BareViewManager from "../../3DuF/src/app/view/bareViewManager"
import Registry from "../../3DuF/src/app/core/registry"
import Examples from "../../3DuF/src/app/examples/jsonExamples"

    export default {
       mounted() {
        let viewManager = new BareViewManager();

        Registry.viewManager = viewManager;

        viewManager.loadDeviceFromJSON(JSON.parse(Examples.example2));
        viewManager.updateGrid();
        Registry.currentDevice.updateView();

        window.dev = Registry.currentDevice;
        window.Registry = Registry;

        window.view = Registry.viewManager.view;
       }
    }
</script>

<style lang="scss" scoped>
#view-container {
    width: 100%;
    height: 100%;
}
</style>