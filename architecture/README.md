# MeghMukt architecture

```mermaid
flowchart LR
    A["Example, live search or upload"] --> B["Prepare Green, Red and NIR"]
    B --> C["Detect clouds and shadows"]
    B --> D["Align and colour-match optional reference"]
    C --> E["Build nine-channel input"]
    D --> E
    E --> F["MeghGAN tiled inference"]
    G["Offline training and checkpoint"] --> F
    F --> H["Reconstruction and confidence"]
    H --> I["PNG and GeoTIFF"]
```

MeghGAN learns a correction over a reference-assisted starting image using an attention U-Net and a PatchGAN discriminator during training. The dashboard blends overlapping tile predictions. PyTorch runs the models, Rasterio handles spatial alignment and GeoTIFFs, OpenCV supports mask processing, Earth Search provides the Sentinel-2 archive, and Streamlit serves the UI.
