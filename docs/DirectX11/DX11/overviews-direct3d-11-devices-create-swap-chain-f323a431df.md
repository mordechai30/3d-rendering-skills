Source: [https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-create-swap-chain](<https://learn.microsoft.com/en-us/windows/win32/direct3d11/overviews-direct3d-11-devices-create-swap-chain>)

# How To: Create a Swap Chain

This topic show how to create a swap chain that encapsulates two or more buffers that are used for rendering and display. They usually contain a front buffer that is presented to the display device and a back buffer that serves as the render target. After the immediate context is done rendering to the back buffer, the swap chain presents the back buffer by swapping the two buffers.

The swap chain defines several rendering characteristics including:

-   The size of the render area.
-   The display refresh rate.
-   The display mode.
-   The surface format.

Define the characteristics of the swap chain by filling in a [**DXGI\_SWAP\_CHAIN\_DESC**](/windows/desktop/api/dxgi/ns-dxgi-dxgi_swap_chain_desc) structure and initializing an [**IDXGISwapChain**](/windows/desktop/api/dxgi/nn-dxgi-idxgiswapchain) interface. Initialize a swap chain by calling [**IDXGIFactory::CreateSwapChain**](/windows/desktop/api/dxgi/nf-dxgi-idxgifactory-createswapchain) or [**D3D11CreateDeviceAndSwapChain**](./nf-d3d11-d3d11createdeviceandswapchain-5744e33d11.md).

## Create a device and a swap chain

To initialize a device and swap chain, use one of the following two functions:

-   Use the [**D3D11CreateDeviceAndSwapChain**](./nf-d3d11-d3d11createdeviceandswapchain-5744e33d11.md) function when you want to initialize the swap chain at the same time as device initialization. This usually is the easiest option.

-   Use the [**D3D11CreateDevice**](./nf-d3d11-d3d11createdevice-fbcd3f07e1.md) function when you have already created a swap chain using [**IDXGIFactory::CreateSwapChain**](/windows/desktop/api/dxgi/nf-dxgi-idxgifactory-createswapchain).

## Related topics

<dl> <dt>

[Devices](./overviews-direct3d-11-devices-8464b8d294.md)
</dt> <dt>

[How to Use Direct3D 11](./how-to-use-direct3d-11-112ea0ccbf.md)
</dt> </dl>