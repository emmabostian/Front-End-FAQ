# Performance   

**What is the best way to reduce my image file size?** 

>At minimum: use [ImageOptim](https://imageoptim.com/). It can significantly reduce the size of images while preserving visual quality. Windows and Linux [alternatives](https://imageoptim.com/versions.html) are also available.

>More specifically: run your JPEGs through [MozJPEG](https://github.com/mozilla/mozjpeg0) (q=80 or lower is fine for web content) and consider [Progressive JPEG](http://cloudinary.com/blog/progressive_jpegs_and_green_martians) support, PNGs through [pngquant](https://pngquant.org/) and SVGs through [SVGO](https://github.com/svg/svgo). Explicitly strip out metadata (--strip for pngquant) to avoid bloat. Instead of crazy huge animated GIFs, deliver [H.264](https://en.wikipedia.org/wiki/H.264/MPEG-4_AVC) videos (or [WebM](https://www.webmproject.org/) for Chrome, Firefox and Opera)! If you can’t at least use [Giflossy](https://github.com/pornel/giflossy). If you can spare the extra CPU cycles, need higher-than-web-average quality and are okay with slow encode times: try [Guetzli](https://research.googleblog.com/2017/03/announcing-guetzli-new-open-source-jpeg.html).

From the excellent [images.guide](https://images.guide/). <br/><br/>

**What is the best format for performant images? PNG? JPG? SVG?**  
> It's between SVG and JPG. It really depends on how much detail and color variation the image has. If it's a simple vector graphic (_Something like a logo or icon_) you should safely be able to go with SVG. This can be under 1k - 5k in size. If the image is more like a photo with a considerable amount of detail and colors I would go with JPG. You should only feel compelled to reach for PNG if the file has transparency.