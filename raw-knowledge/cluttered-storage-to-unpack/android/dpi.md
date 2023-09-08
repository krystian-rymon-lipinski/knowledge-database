#status/3-freezer 
#tech-area/android 

Pixel density

To convert pixels (px) to density-independent pixels (dp) and vice versa, you need to know the screen density or dots per inch (DPI) of the device. The conversion between px and dp is based on the following formula:

makefileCopy code

`dp = px / (DPI / 160) px = dp * (DPI / 160)`

Where:

- `px` is the dimension in pixels.
- `dp` is the dimension in density-independent pixels.
- `DPI` is the screen density in dots per inch.

The key concept here is the factor `DPI / 160`, which is often referred to as the "density factor" or "density scale." It represents the scaling factor needed to convert between pixels and density-independent pixels for a specific screen density.

---

Compose definiuje stałą:

```kotlin
val screenDensity = LocalDensity.current.density
```