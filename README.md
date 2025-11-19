# Vulkan_Triangle
A minimal Vulkan project that renders a single triangle using a fully manual graphics pipeline.
Includes instance & device setup, swapchain creation, render pass configuration, graphics pipeline setup, vertex buffers, command buffers, and synchronized drawing.

The project configures Vulkan by linking against the Vulkan SDK through VS project settings (include directories, library directories, and linking vulkan-1.lib). GLFW is used only for window creation.

All shaders were written in GLSL and then manually compiled into SPIR-V bytecode using glslc from the Vulkan SDK. The resulting .spv files (vert.spv and frag.spv) are loaded directly at runtime to create the graphics pipeline.

**Built as a learning-focused reference for understanding the core Vulkan rendering flow from scratch — no helper libraries beyond GLFW for windowing.**

# General Overview of Vulkan Rendering Pipeline

Creating this project provided deeper insight into the entire Vulkan rendering pipeline, because each stage had to be implemented explicitly and in the correct order. The application walks through each component of the API one step at a time:

createInstance() — establish the Vulkan connection

setupDebugMessenger() — enable validation layers for debugging

createSurface() — create a rendering surface with GLFW

pickPhysicalDevice() — select a suitable GPU

createLogicalDevice() — enable queues and features

createSwapChain() — configure images for presentation

createImageViews() — wrap swapchain images for rendering

createRenderPass() — define attachment formats and operations

createGraphicsPipeline() — load SPIR-V shaders and build the programmable pipeline

createFramebuffers() — bind image views to render passes

createCommandPool() — allocate command buffer storage

createCommandBuffer() — record draw commands

createSyncObjects() — ensure proper frame synchronization

Implementing each step by hand made the flow of Vulkan much clearer: how resources depend on one another, how the pipeline stages interact, and why Vulkan requires such explicit control. This repository serves as a foundational learning project and a clean reference for understanding how Vulkan actually works beneath higher-level abstractions.

