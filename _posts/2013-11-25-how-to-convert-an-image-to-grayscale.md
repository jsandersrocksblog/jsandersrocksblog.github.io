I ran across an issue where I wanted to convert an Image in a Windows Store app&#160; to grayscale and could not find a great example.&#160; So… here is one for you to try!

<pre class="code"><span style="background: white; color: black;"> </span><span style="background: white; color: blue;">private async </span><span style="background: white; color: rgb(43, 145, 175);">Task </span><span style="background: white; color: black;">imageToGrayscale(</span><span style="background: white; color: rgb(43, 145, 175);">Image </span><span style="background: white; color: black;">src, </span><span style="background: white; color: rgb(43, 145, 175);">Image </span><span style="background: white; color: black;">dest)
        {
            </span><span style="background: white; color: rgb(43, 145, 175);">RenderTargetBitmap </span><span style="background: white; color: black;">renderTargetBitmap = </span><span style="background: white; color: blue;">new </span><span style="background: white; color: rgb(43, 145, 175);">RenderTargetBitmap</span><span style="background: white; color: black;">();
            </span><span style="background: white; color: green;">//Get existing src pixels in a Byte[] (always is BRGA formate
            </span><span style="background: white; color: blue;">await </span><span style="background: white; color: black;">renderTargetBitmap.RenderAsync(src);
            </span><span style="background: white; color: rgb(43, 145, 175);">IBuffer </span><span style="background: white; color: black;">pixelSrc = </span><span style="background: white; color: blue;">await </span><span style="background: white; color: black;">renderTargetBitmap.GetPixelsAsync();
            </span><span style="background: white; color: rgb(43, 145, 175);">Byte</span><span style="background: white; color: black;">[] destBytes = </span><span style="background: white; color: blue;">new </span><span style="background: white; color: rgb(43, 145, 175);">Byte</span><span style="background: white; color: black;">[pixelSrc.Length];
            </span><span style="background: white; color: blue;">for </span><span style="background: white; color: black;">(</span><span style="background: white; color: blue;">int </span><span style="background: white; color: black;">i = 0; i &lt; pixelSrc.Length; i += 4)
            {
                </span><span style="background: white; color: blue;">double </span><span style="background: white; color: black;">b = (</span><span style="background: white; color: blue;">double</span><span style="background: white; color: black;">)pixelSrc.GetByte((</span><span style="background: white; color: blue;">uint</span><span style="background: white; color: black;">)i) / 255.0;
                </span><span style="background: white; color: blue;">double </span><span style="background: white; color: black;">g = (</span><span style="background: white; color: blue;">double</span><span style="background: white; color: black;">)pixelSrc.GetByte((</span><span style="background: white; color: blue;">uint</span><span style="background: white; color: black;">)i+1) / 255.0;
                </span><span style="background: white; color: blue;">double </span><span style="background: white; color: black;">r = (</span><span style="background: white; color: blue;">double</span><span style="background: white; color: black;">)pixelSrc.GetByte((</span><span style="background: white; color: blue;">uint</span><span style="background: white; color: black;">)i+2) / 255.0;
                </span><span style="background: white; color: blue;">byte </span><span style="background: white; color: black;">a = pixelSrc.GetByte((</span><span style="background: white; color: blue;">uint</span><span style="background: white; color: black;">)i + 3);
                </span><span style="background: white; color: blue;">double </span><span style="background: white; color: black;">e = (0.21 * r + 0.71 * g + 0.07 * b) * 255;
                </span><span style="background: white; color: blue;">byte </span><span style="background: white; color: black;">f = </span><span style="background: white; color: rgb(43, 145, 175);">Convert</span><span style="background: white; color: black;">.ToByte(e);
                destBytes[i] = f;
                destBytes[i + 1] = f;
                destBytes[i + 2] = f;
                destBytes[i + 3] = a;
            }
            </span><span style="background: white; color: rgb(43, 145, 175);">WriteableBitmap </span><span style="background: white; color: black;">destWB = </span><span style="background: white; color: blue;">new </span><span style="background: white; color: rgb(43, 145, 175);">WriteableBitmap</span><span style="background: white; color: black;">(renderTargetBitmap.PixelWidth, renderTargetBitmap.PixelHeight);
            </span><span style="background: white; color: blue;">using </span><span style="background: white; color: black;">(</span><span style="background: white; color: rgb(43, 145, 175);">Stream </span><span style="background: white; color: black;">pixelStream = destWB.PixelBuffer.AsStream()) {
                pixelStream.Seek(0, </span><span style="background: white; color: rgb(43, 145, 175);">SeekOrigin</span><span style="background: white; color: black;">.Begin);
                pixelStream.Write(destBytes, 0, destBytes.Length);
                destWB.Invalidate();
            }
            destImage.Source = destWB;
        }</span></pre>

If you like it, drop me a note of thanks!