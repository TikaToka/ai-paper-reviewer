| Algorithm 1 Resolution scaling |
| --- |
| 1: Input: Input image Xo, binary watermark w 2: Output: Watermarked image Xw 3: Model: Watermark Encoder E(.) trained on the resolution of u x v |
| 4: h, w ← Size(x。) 5: x⌀ ← x。/127.5 - 1 // normalize to range [-1, 1] 6: X⌀ ← interpolate(xo, (u, v)) 7: r ← E(x'。) - x' // resi dual image 8: r ← interpolate(r', (h, w)) 9: Xw ← clamp(x。 + r, -1, 1) 10: Xw ← Xw X 127.5 + 127.5 |
