# THREE.js-PathTracing-Renderer
Real-time PathTracing with global illumination and progressive rendering, all on top of the Three.js WebGL framework.

<h2>LIVE DEMOS</h2>

* [Geometry Showcase Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Geometry_Showcase.html) demonstrating some primitive shapes for ray tracing.  

* [Ocean and Sky Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Ocean_And_Sky_Rendering.html) mixes ray tracing with ray marching and models an enormous calm ocean underneath a realistic physical sky. Now has more photo-realistic procedural clouds!

* [Billiard Table Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Billiard_Table.html) shows support for loading image textures (i.e. .jpg .png) to be used for materials. The billiard table cloth and two types of wood textures are demonstrated.

* [Cornell Box Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Cornell_Box.html) This demo renders the famous old Cornell Box, but at 30-60 FPS - even on mobile!

For comparison, here is a real photograph of the original Cornell Box vs. a rendering with the three.js PathTracer:

![](readme-Images/measured.jpg) ![](readme-Images/CornellBox-Render0.png)

<br>

* [Volumetric Rendering Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Volumetric_Rendering.html) renders objects inside a volume of dust/fog/etc..  Notice the cool volumetric caustics from the glass sphere on the left, rendered almost instantly!

* [Terrain Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Terrain_Rendering.html) combines traditional raytracing with raymarching to render stunning outdoor environments in real time!  Land is procedurally generated, can be altered with simple parameters. Total number of triangles processed for these worlds: 2! (for screen size quad) :-)

* [Arctic Circle Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Arctic_Circle.html) I was experimenting with my ray marching engine and what types of environments I could get out of it by just altering some parameters.  When the scene first opens, it's almost like you're transported to the far north! The time of year for this demo is summer - notice how the sun never quite sets below the horizon.

* [Planet Demo (W.I.P.)](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Planet_Rendering.html) takes raymarching and raytracing to the extreme and renders an entire Earth-like planet with physically-based atmosphere!  Still a work in progress, the terrain is procedurely generated.  Although the mountains/lakes are too repetitious (W.I.P.), this simulation demonstrates the power of path tracing: you can hover above the planet at high orbit (5000 Km altitude), then drop all the way down and land your camera right on top of a single rock or single lake water wave (1 meter). All planet/atmosphere measurements are to scale.  The level of detail possible with raytracing is extraordinary!

* [Quadric Geometry Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Quadric_Geometry_Showcase.html) showing different quadric (mathematical) ray tracing shapes.

* [Water Rendering Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Water_Rendering.html) Renders photo-realistic water and simulates waves at 30-60 FPS. No triangle meshes are needed, as opposed to other traditional engines/renderers. The water surface is achieved through ray marching.

<h3>BVH Acceleration Structure Demos </h3>

* [BVH Point Light Source Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/BVH_Point_Light_Source.html) Demonstrates the use of a point light to illuminate the famous Stanford Bunny (30,000+ triangles!).  Normally a dark scene like this with a very bright small light would be very noisy, but thanks to randomized direct light targeting, the image converges almost instantly!

* [BVH Spot Light Source Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/BVH_Spot_Light_Source.html) A similar scene but this time a bright spotlight in the air is aimed at the Stanford Bunny, making him the star of the scene!  The spotlight is made out of dark metal on the outside and a reflective metal on the inside.  Notice the light falloff on the checkered floor.

* [Animated BVH Model Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/BVH_Animated_Model.html) not only loads and renders a 15,000+ triangle GLTF model with correct PBR materials (albedo, emmisive, metallicRoughness, and normal maps), but it also translates and rotates the entire model and its BVH structure in real time!  Loading and ray tracing bone animations for rigged models is still under investigation, but getting rigid models to move, rotate, and scale arbitrarily was a huge step forward for the pathtracing game engine!

* [HDRI Environment Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/HDRI_Environment.html) shows how to load an equi-rectangular HDRI map to use as the scene's surrounding environment.  This demo also uses the optimized BVH accelerator to load the famous Stanford Dragon model consisting of 100,000 triangles and renders the scene in real-time!  I also added a material and color picker so you can instantly change the dragon's material type (glass, metal, ceramic) as well as its material color without missing a beat! *Note: please allow 5-10 seconds to download the large HDR image*

* [BVH Visualizer Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/BVH_Visualizer.html) Lets you peek under the hood of the BVH acceleration structure and see how the various axis-aligned bounding boxes are built all the way from the large surrounding root node box (level 0), to the small leaf node boxes (level 14+), to the individual triangles of the model that are contained within those leaf node boxes.  This demo loads the famous Stanford Dragon (100,000 triangles!) and renders it as a purple light source inside yellow glass bounding boxes of its BVH.<br>

* [GLTF Viewer Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Gltf_Viewer.html) This cool viewer not only loads models in glTF format, but also uses three.js' RGBE.Loader to load an equi-rectangular HDR image as the background and for global lighting. Many thanks to github user [n2k3](https://github.com/n2k3) for his awesome contributions to this viewer!  He implemented a slick loading animation as well as a GUI panel that allows you to change the sun angle, sun intensity, sun color, hdr intensity, and hdr exposure. <br>

<h3>Constructive Solid Geometry(CSG) Demos</h3>

![](readme-Images/tron_MAGIlibrary2_web1.jpg)

The following section deals with different techniques in Constructive Solid Geometry(CSG) - taking one 3D mathematical shape and either adding, removing, or intersecting a second shape.

 The above image was my inspiration to embark on the years-long (and still ongoing!) journey to implement a complete library of analytically ray-traced mathematical shapes that can be rendered in realtime inside a browser.  The image is a computer screen grab from an old cinema magazine article showing how the vintage CG company MAGI made their iconic imagery for the 1982 movie, TRON.  I saw that movie in theaters when it came out (I was 9 years old, ha) and at first I thought, since it was a Disney movie, that their artists had hand-drawn all the crazy scenes and sci-fi vehicles.  As the end credits rolled though, it said 'computer imagery and animation by MAGI'.  Mind blown!  At 9 years old in the early 1980's, I hadn't seen anything like that in a movie - I couldn't even comprehend how they made all those cool scenes/vehicles inside of a computer!  The film really peaked my interest in computer graphics and nearly 40 years later, I am happy to report that my quest to be able to render all the shapes that MAGI could has been largely successful!  If you combine the right primitives with my CSG viewer demo below, you should be able to recreate most every shape that you see in the picture above, and maybe even in the movie (after I implement multiple recursion of the CSG operations!).  For those that are interested in the math, these are all quadric shapes - shapes that can be defined implicitly (i.e., a unit sphere: x2 + y2 + z2 - 1 = 0) and reduced to a quadratic equation in the ray's 't' value, which can be easily solved by a computer to quickly find the roots (t0, t1).  Using these mathematical primitives, MAGI was able to construct all the cool vehicles featured in the movie.  An interesting side note: they did not use triangles/polygon modeling like the CG industry does today - it was mainly these math shapes with pixel-perfect continuous-looking curves.  Also noteworthy is that they used ray tracing to render the final animations.  Each frame took 30 minutes to multiple hours.  Well I'm happy to say that you won't have to wait that long to see an image now - my shapes render at 30-60 FPS inside your browser, even on mobile!  ;-)  <br> 

* [Constructive Solid Geometry Viewer](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Constructive_Solid_Geometry_Viewer.html)
This viewer allows you to easily experiment with different CSG configurations while seeing the results path-traced in real time!  You can select a CSG Operation from the Operations list - Union (A+B), Difference (A-B), or Intersection (A^B).  Briefly, a 'Union' operation means that the outside of shape A is fused with the outside of shape B, creating a new single shape with a single interior volume.  A 'Difference' operation means that shape A is cut out with shape B (shape B by itself will be invisible, but its influence will be visible as a section missing from shape A where the two overlap).  An 'Intersection' operation means that wherever shape A touches shape B, a new shape/volume will be created (the two shapes *must* overlap, otherwise no new shape will be seen).  I added a detailed and fully-featured GUI menu system so that you can easily modify the CSG Operation type, both shapes' Transforms (Position, Scale, Skew, Rotation), both shapes' base geometry (Sphere, Box, Cylinder, Cone, Paraboloid, etc.), their material type (Diffuse, Transparent Refractive, Metal, ClearCoat Diffuse) and their RGB material color. I have spent hours trying various configuration possibilities, which are seemingly endless (ha)!  I hope that you too will have fun experimenting with this viewer and seeing what new shapes you can create!  <br>

All of the following 4 demos feature a large dark glass sculpture in the center of the room, which shows Ellipsoid vs. Sphere CSG. <br>
Along the back wall, a study in Box vs. Sphere CSG: [CSG_Museum Demo #1](https://erichlof.github.io/THREE.js-PathTracing-Renderer/CSG_Museum_1.html) <br>
Along the right wall, a glass-encased monolith, and a study in Sphere vs. Cylinder CSG: [CSG_Museum Demo #2](https://erichlof.github.io/THREE.js-PathTracing-Renderer/CSG_Museum_2.html) <br>
Along the wall behind the camera, a study in Ellipsoid vs. Sphere CSG: [CSG_Museum Demo #3](https://erichlof.github.io/THREE.js-PathTracing-Renderer/CSG_Museum_3.html) <br>
Along the left wall, a study in Box vs. Cone CSG: [CSG_Museum Demo #4](https://erichlof.github.io/THREE.js-PathTracing-Renderer/CSG_Museum_4.html) <br>

Important note! - There is a hidden Easter Egg in one of these 4 Museum demo rooms.  Happy hunting!

<h3>Materials Demos</h3>

* [Switching Materials Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Switching_Materials.html)
This demo showcases different surface material possibilities. The materials that are feautured are: Diffuse (matte wall paint/chalk), Refractive (glass/water), Specular (aluminum/gold), ClearCoat (billiard ball, plastic, porcelain), Car clearCoat (painted metal with clear coat), Translucent (skin/balloons, etc.), and shiny SubSurface scattering (polished Jade/wax/marble, etc.) <br>

* [Material Roughness Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Material_Roughness.html)
Demonstrates increasing levels of roughness on different materials.  From left to right, roughness on the left sphere is set at 0.0, then 0.1, 0.2, 0.3 etc., all the way to the max: 1.0 roughness on the right sphere. The demo starts out with a clearcoat cyan plastic-like material, but you can choose different material presets from the selection menu, as well as change the material color in realtime.  I have researched and improved the importance sampling of specular lobes for various amounts of roughness, which results in very fast convergence, especially with smoother to medium-rough materials.  Try all the presets for yourself! <br>
<br>

<h3> Real-Time Transformation of Primitive Geometry</h3>

* [Transforming Quadric Geometry Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Transforming_Quadric_Geometry_Showcase.html) Using the game engine version of the three.js path tracer, this demo shows how to create multiple objects (a bunch of 'THREE.Object3d()'s, each with its own transform) on the JavaScript side when initializing three.js, and then send the objects over to the GPU for realtime pathtracing.  The nice thing about having my pathtracer sitting on top of three.js is that I can use its built-in transformations such as Translate, Rotate, and Scale.  Since these shapes are mathematical (all quadrics), I also included clipping parameters so you can have partial shapes and can even animate the cutting process! *Note: this demo may take several seconds to compile* <br> <br>

* <h3>Classic Scenes / Ray Tracing History</h3>

<img src="https://github.com/erichlof/THREE.js-PathTracing-Renderer/blob/gh-pages/readme-Images/4-Figure7-1.png" width=30% height=30%>

Arthur Appel is credited with the first formal mention of Ray Tracing (raycasting and shadow rays, shown above) in his 1968 paper [Some Techniques for Shading Machine Renderings of Solids](https://docs.google.com/viewer?url=https%3A%2F%2Fohiostate.pressbooks.pub%2Fapp%2Fuploads%2Fsites%2F45%2F2017%2F09%2Fshading-appel.pdf) while working at IBM Research (TJW Center).  Mr. Appel used this new technique to help visualize machine parts and architectural concepts on printed paper in black and white.  The scene data was sent to an IBM 1627 (Calcomp) digital plotter that cleverly used text characters (like '+') with different spacing and brightness to differentiate the various shading of sides of a 3D model under a virtual light source.  Here are a few examples of Mr. Appel's digital plot renderings from his 1968 paper:

<img src="https://github.com/erichlof/THREE.js-PathTracing-Renderer/blob/gh-pages/readme-Images/2-Figure2-1.png" width=20% height=20%> <img src="https://github.com/erichlof/THREE.js-PathTracing-Renderer/blob/gh-pages/readme-Images/4-Figure3-1.png" width=70% height=70%>

Until now (2021), actual photos of Arthur Appel were not publicly available (none can be found with a thorough internet search).  All that was known was that he was working at IBM Research (TJW Center) at the time he wrote this seminal 1968 paper.  I really wanted to see what Mr. Appel looked like, and to share and celebrate his image and contributions to the field of Ray Tracing and Rendering.  With a little hesitation at first, I reached out to the IBM Corporate Archives in New York to see if they might have any remaining employee portraits of Arthur Appel.  I'm so glad I did, because I met (via email) a wonderful IBM Archive employee, Max Campbell, who kindly searched the entire archives and found 2 rarely-seen photos of Mr. Appel.  Since these images are copyrighted by IBM (and NOT a part of my repo's CC License), Max also kindly and graciously helped me to obtain permission from IBM to share these historic photos of the man who started it all!  Click on the images to see the full resolution photos:

<img src="https://github.com/erichlof/THREE.js-PathTracing-Renderer/blob/gh-pages/readme-Images/1982_December_Arthur%20Appel_IBM%20Research%20Magazine.png" width=20% height=20%> <br>
Arthur Appel, from the IBM Research Employee Gallery, ca. 1982
Reprint Courtesy of IBM Corporation © <br>

<img src="https://github.com/erichlof/THREE.js-PathTracing-Renderer/blob/gh-pages/readme-Images/1983_December_Arthur%20Appel_IBM%20Research%20Magazine.png" width=20% height=20%> <br>
Arthur Appel demonstrating display architecture, from IBM Research Magazine ca. 1983
Reprint Courtesy of IBM Corporation © <br>

Many thanks to Max Campbell at IBM Research Archives for locating these rare photos and helping me to obtain permission to share them with everyone who is interested in ray tracing!  It is so nice to be able to finally put a face with the name of one of my ray tracing heroes, Arthur Appel.  Thank you Mr. Appel for your historic contributions to field of Computer Graphics! <br>
<br>


![](readme-Images/Whitted_1979.jpg)

While working at Bell Labs and writing his now-famous paper [An Improved Illumination Model for Shaded Display](http://artis.imag.fr/Members/David.Roger/whitted.pdf), J. Turner Whitted created an iconic ray traced scene which showcased his novel methods for producing more realistic images with a computer. Beginning work in 1978, he rendered a handful of scenes featuring spheres and planes with various materials and reflectivity, so that these images would be included in his paper (which would be published in June 1980).  Then for an upcoming SIGGRAPH conference submission, Whitted decided to create an animated sequence of individual rendered images.  Thus the first ever ray traced animation was born!  This style of putting together single frames of pre-rendered images would continue through a great lineage of movies such as Tron, Toy Story, Cars, all the way to current animated feature films.     

[Vintage 1979 Video: 'The Compleat Angler' by J. Turner Whitted](https://youtu.be/0KrCh5qD9Ho)

Although this movie appears as a smooth animation, it took around 45 minutes to render each individual frame back in 1979!  Fast forward to today and using WebGL 2.0 and the parallel processing power of GPUs, here is the same iconic scene rendered at 60 times a second in your browser! : <br>
* [The Compleat Angler demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Classic_Scene_Whitted_TheCompleatAngler.html) <br>

Thank you Dr. Whitted for your pioneering computer graphics work and for helping to start the rendered animation industry!  <br> 
<br>

In 1986 James T. Kajiya published his famous paper [The Rendering Equation](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.63.1402), in which he presented an elegant and profound unifying integral equation for rendering.  Since the equation is infinitely recursive and hopelessly multidimensional, he suggests using Monte Carlo integration (sampling and averaging) in order to converge on a solution.  Thus Monte Carlo path tracing was born, which this repo follows very closely.  At the end of his paper he included a sample rendered image that demonstrates global illumination through Monte Carlo path tracing:

![](readme-Images/kajiya.jpg)

And here is the same scene from 1986, rendered in real-time: <br>
* [The Rendering Equation Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Classic_Scene_Kajiya_TheRenderingEquation.html) <br>
<br>

* <h4>Bi-Directional Path Tracing</h4> In December of 1997, Eric Veach wrote a seminal PhD thesis paper on methods for light transport http://graphics.stanford.edu/papers/veach_thesis/  In Chapter 10, entitled Bi-Directional Path Tracing, Veach outlines a novel way to deal with difficult path tracing scenarios with hidden light sources (i.e. cove lighting, recessed lighting, spotlights, etc.).  Instead of just shooting rays from the camera like we normally do, we also shoot rays from the light sources, and then later join the camera paths to the light paths.  Although his full method is difficult to implement on GPUs because of memory storage requirements, I took the basic idea and applied it to real-time path tracing of his classic test scene with hidden light sources.  For reference, here is a rendering made by Veach for his 1997 paper:

![](readme-Images/Veach-BiDirectional.jpg)

And here is the same room rendered in real-time by the three.js path tracer: <br>
* [Bi-Directional PathTracing Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Bi-Directional_PathTracing.html) <br>

The following classic scene rendering comes from later in the same paper by Veach.  This scene is intentionally difficult to converge because there is no direct light, only indirect light hitting the walls and ceiling from a crack in the doorway.  Further complicating things is the fact that caustics must be captured by the glass teapot on the coffee table, without being able to directly connect with the light source.

![](readme-Images/Veach-DifficultLighting.jpg)

And here is that scene rendered in real-time by the three.js path tracer: Try pressing 'E' and 'R' to open and close the door! <br>
* [Difficult Lighting Classic Test Scene Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Bi-Directional_Difficult_Lighting.html) <br>

I only had the above images to go on - there are no scene dimensions specifications that I am aware of.  However, I feel that I have captured the essence and purpose of his test scene rooms.  I think Veach would be interested to know that his scenes, which probably took several minutes if not hours to render back in the 1990's, are now rendering real-time in a web browser! :-D

For more intuition and a direct comparison between regular path tracing and bi-directional path tracing, here is the old Cornell Box scene again but this time there is a blocker panel that blocks almost all of the light source in the ceiling.  The naive approach is just to path trace normally and hope that the camera rays will be lucky enough to find the light source:
* [Naive Approach to Blocked Light Source](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Compare_Uni-Directional_Approach.html) As we can painfully see, we will have to wait a long time to get a decent image!
Enter Bi-Directional path tracing to the rescue!:
* [Bi-Directional Approach to Blocked Light Source](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Compare_Bi-Directional_Approach.html) Like magic, the difficult scene comes into focus - in real-time! <br> <br> <br>

<h3>Game Engine path tracer for Desktop and Mobile</h3>

Before I got into this world of path tracing, I was a 3D game programmer (and still am, although path tracing is consuming most of my coding time!).  My first game was way back in 1998, using OpenGL 1 and the C language, back when these new things called graphics cards were all the rage! [my old Binary Brotherz page](https://web.archive.org/web/20010405004141/http://www.binarybrotherz.com/games.html)  Although using OpenGL back then and WebGL today was/is cool, I always wanted more in terms of lighting, shadows, reflections, diffuse color sharing, etc., in my game engines that I just couldn't get from rasterizing graphics APIs.  Well, fast forward to 2019 and NVidia is releasing graphics cards dedicated to real-time ray tracing!  I couldn't have imagined this back in the 90's! However, at the time I'm writing this, NVidia is only doing specular ray tracing as a bonus feature on top of the old rasterization technique. I wanted to see if I could 'overclock' my full path tracer's convergence so that you could see the beautiful light effects in real time, being able to possibly move a game character or 1st-person camera through a path-traced dynamic game environment at 30-60 fps, even on mobile.  If you're willing to sacrifice some ultimate physical reality (like perfect converged reflected/refracted caustics), then you can have this!: <br>

* [Future Game Engine PathTracer Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/GameEngine_PathTracer.html)<br>
To my knowledge, this is just about as fast as I can push the path tracing engine and WebGL in general, and still retain good lighting, accurate reflections, and almost instant image convergence.  As computers get faster, this will be the heart of future game rendering engines - a simple path tracer that is just around 500 to 1000 lines of code, is easy to maintain and debug, and which gives photo-realistic real-time results! I already have some ideas for some simple 3d games that can use this technology.  I'll keep you posted! <br>
<br>

<h2>PATH TRACED GAMES</h2>

*Update: 1/21/2021* 

In 1986 when I was 13 years old and on my Commodore 64 (I know, I'm old), Geoff Crammond released his masterpiece, The Sentinel.  This iconic game featured true 3D filled polygons (an amazing feat running on underpowered 80's hardware!) and had a haunting look and atmosphere like no other before it (or after).  This was the first game that I played that truly immersed me, surrounding the player from all angles with its sterile, other-worldly environment.  I've always wanted to pay homage to my favorite game of all time, while maybe adding some of my personal path tracing touch to it.  So it is with much joy that I present, The Sentinel: 2nd Look.  This fully path traced remake contains a random landscape generator (which I had to figure out from looking at the classic over several months), an added day cycle, pixel-perfect raytraced shadows on the terrain and game objects, object self-shadowing, and true raytraced reflections on the white/black connector panels of the landscape.  <br>
<br>
Creating this remake forced me to figure out how to make a dynamic top-level BVH over many moving, rotating game objects/models, each with their own unique BVHs for their own triangle geometry.  I'm happy to report that not only does my new system work, it can completely rebuild and update the whole top-level BVH in a split second, allowing for more complex, path traced dynamic game environments!  As of now, this project is a W.I.P. (gameplay and game logic to be added soon), but I just wanted to share this passion project of mine, as well as the technical major step forward (in BVH technology) that will allow a wider range of real time games and applications to be path traced right inside your browser!
<br><br>

* [The Sentinel: 2nd Look (W.I.P.) game](https://erichlof.github.io/TheSentinel-2nd-Look/TheSentinel_2nd_Look.html) on Desktop, click to capture Mouse
* [The Sentinel: 2nd Look project](https://github.com/erichlof/TheSentinel-2nd-Look) <br>

*Update: 12/18/2020*
- Continuing my series of path traced games for desktop and mobile, I happily present: Path Traced Pong!  The iconic game of Pong holds a special place in my heart as it was my first computer game experience as a 6 year old in 1979, played on my brand new Atari 2600!  My version of Pong brings the classic into 3D, and is played inside the CG-famous 'Cornell Box'.  Path Traced Pong features real time raytraced reflections, soft shadows, transparency, dynamic light sources, and path traced global illumination.  As with AntiGravity Pool, I made a dedicated repository for just this new game. I must say, once you start playing, it's hard to stop!  I didn't realize how addictive it would become!<br><br>

* [Path Traced Pong game](https://erichlof.github.io/PathTracedPong/Path_Traced_Pong.html) on Desktop, click to capture Mouse
* [Path Traced Pong project](https://github.com/erichlof/PathTracedPong) <br>

*Update: 5/24/2019*
- I am pleased to announce the first ever path traced game for desktop and mobile: AntiGravity Pool!  If you've ever played American 8-ball before, then you already know how to play - except that gravity has been shut off! LOL. I tried to imagaine how our distant future descendants would enjoy the game of billiards while in the HoloDeck.  Warping the 2D classic pool table into a 3D cube presents some unique and interesting challenges for the player.  AntiGravity Pool features real-time raytraced reflections, soft shadows, and path traced global illumination from 8 light sources (which is challenging for path tracers).  Since it uses a physics engine and various custom components, I decided to create a dedicated repository for just this new game. Be sure to check it out!<br>

* [AntiGravity Pool game](https://erichlof.github.io/AntiGravity-Pool/AntiGravityPool.html) on Desktop, press SPACEBAR to shoot! :)
* [AntiGravity Pool project](https://github.com/erichlof/AntiGravity-Pool) <br><br>


<br>
<br>
A random sample rendering from the three.js pathtracing renderer as it was back in 2015!
<br>

![](readme-Images/threejsPathTracing.png)


<h2>FEATURES</h2>

* Real-time interactive Path Tracing at 30-60 FPS in your browser - even on your smartphone! ( What?! )
* First-Person camera navigation through the 3D scene.
* When camera is still, switches to progressive rendering mode and converges on a highest quality photo-realistic result!
* The accumulated render image will converge at around 500-3,000 samples (lower for simple scenes, higher for complex scenes).
* My custom randomized Direct Light targeting now makes images render/converge almost instantly!
* Both Uni-Directional (normal) and Bi-Directional path tracing approaches available for different lighting situations.
* Support for: Spheres, Planes, Discs, Quads, Triangles, and quadrics such as Cylinders, Cones, Ellipsoids, Paraboloids, Hyperboloids, Capsules, and Rings/Torii. Parametric/procedural surfaces (i.e. terrain, clouds, waves, etc.) are handled through Raymarching.
* Constructive Solid Geometry(CSG) allows you to combine 2 shapes using operations like addition, subtraction, and overlap.
* Support for loading models in .gltf and .glb formats
* BVH (Bounding Volume Hierarchy) greatly speeds up rendering of triangle models in gltf/glb format (tested up to 800,000 triangles!)
* Current material options: Metallic (mirrors, gold, etc.), Transparent (glass, water, etc.), Diffuse(matte, chalk, etc), ClearCoat(cars, plastic, polished wood, billiard balls, etc.), Translucent (skin, leaves, cloth, etc.), Subsurface w/ shiny coat (jelly beans, cherries, teeth, polished Jade, etc.)
* Solid transparent objects (i.e. glass tables, glass sculptures, tanks filled with water or other fluid, etc) now obey the Beer-Lambert law for ray color/energy attenuation.
* Support for PBR materials on models in gltf format (albedo diffuse, emissive, metallicRoughness, and normal maps)        
* Diffuse/Matte objects use Monte Carlo integration (a random process, hence the visual noise) to sample the unit-hemisphere oriented around the normal of the ray-object hitpoint and collects any light that is being received.  This is the key-difference between path tracing and simple old-fashioned ray tracing.  This is what produces realistic global illumination effects such as color bleeding/sharing between diffuse objects and refractive caustics from specular/glass/water objects.
* Camera has Depth of Field with real-time adjustable Focal Distance and Aperture Size settings for a still-photography or cinematic look.
* SuperSampling gives beautiful, clean Anti-Aliasing (no jagged edges!)


<h3>Experimental Works in Progress (W.I.P.)</h3>

The following demos show what I have been experimenting with most recently.  They might not work 100% and might have small visual artifacts that I am trying to fix.  I just wanted to share some more possible areas in the world of path tracing! :-) <br>

Some pretty interesting shapes can be obtained by deforming objects and/or warping the ray space (position and direction) around these objects.  This demo applies a twist warp to the spheres and mirror box and randomizes the positional space of the top purple sphere, creating an acceptable representation of a little cloud. <br>

* [Ray/Object Warping Demo](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Ray_Warping.html)<br>

When rendering/raytracing Terrain, you can either raymarch a Perlin noise texture (as I have demonstrated in the above Terrain_Rendering and Planet_Rendering demos), or you can just load in a large pre-existing triangle terrain mesh and raytrace it in the traditional way.  Both have their advantages and disadvantages. However, if you want to go the classical raytracing route, to make the land contours a little more convincing, there needs to be a *lot* of triangles!  The following WIP preview demo uses the BVH acceleration structure to load in and quickly render a huge terrain mesh consisting of no less than 734,464 triangles!  It really pushes my BVH code to the max - we're pretty near a million triangles here, pathtracing in WebGL!  For now I just stuck a checker texture across the terrain and the environment is simply a large skylight dome.  But the good news is that it doesn't crash the browser, and it runs slightly above 20 fps even on my humble laptop - it's amazing that all of this is happening inside a browser webpage!  Note: because of the large BVH data set that needs to be built at startup, this demo might take a few seconds to compile - please be patient, it's worth the wait! ;-) <br>

* [BVH Large Terrain Demo (W.I.P.)](https://erichlof.github.io/THREE.js-PathTracing-Renderer/BVH_Terrain.html) *Note: due to the large data set, it might take a few seconds or more to load and compile*<br>

Inspired by an older Shadertoy demo by user koiava that I came across - https://www.shadertoy.com/view/MtBSzd - I noticed that my mobile device didn't have any problems when trying that particular demo with 1000 triangles.  I copied / edited / optimized the traversal code and then, I did the unthinkable (for me anyway) - I sent down over 2 million triangles to the engine to be raytraced, then raytraced yet again for the reflection/shadow ray pass (so effectively 4,200,000 triangles in a single frame, and .... my Samsung 9 still runs at nearly 60 fps!  It didn't even blink an eye.  Compilation takes maybe 1 second.  I couldn't believe what I was seeing at first. <br>
<br>
![](readme-Images/Grid_on_Mobile.png)

* [Grid Acceleration Demo (W.I.P.)](https://erichlof.github.io/THREE.js-PathTracing-Renderer/Grid_Acceleration.html) <br>

A technical note about what you are seeing: The data arrives to the fragment shader through a 1024x1024 heightmap texture (I randomly chose a DinoIsland.png heightmap, but it can be anything, even a realtime video texture).  The acceleration structure handles sampling the texture and stepping the ray through each sample cell.  The number of cells is up to you.  At first I tried 32x32 cells, and each cell is a square, and each of the 4 corners of that square is a vertex that is used by 2 triangles sandwiched together back-to-back.  So to get the number of triangles that you must raytrace, you take 32 cells width times 32 cells height and remember that each square cell contains 2 triangles, so multiply all that times 2, so 32Wx32Hx2t  which is 2048 triangles representing the polygon heightmap.  Now 2048 triangles sounds like a lot, and it is for raytracing, but the result mesh looks like an old-school low-poly terrain - it is not detailed enough.  On a whim, I tried a resolution of 1024, so each little texel of the 1024x1024 source texture image has its own quad cell, and 2 triangles for every one of those quad cells.  So now we have 1024x1024x2, or 2,097,152 triangles every frame!  And since the grid looks up the texture to get the triangle vertices every frame, you can animate the height/depth of the displacement as well as even play an HD video (saved as textures) with an embossed-effect on the terrain in real time!    
     Oddly, it turns out that my Mobile device (a Samsung S9) trounces my laptop at this demo.  The humble old laptop achieves maybe 20fps, whereas the newer smartphone rocks at 60fps. It may have to do with the cheap integrated graphics of my laptop, but in any case, this is a true testament to the power of modern smartphone GPUs!  



<h2>Updates</h2>

* May 2nd, 2021: My first attempt at a de-noiser!  Well actually, it's more of a 'noise-smoother', but it still makes a big difference! In 2021 you may have seen some of NVIDIA'S demos/partnered games that use their real-time A.I. deep-learning denoising technology. Games like 'Minecraft RTX', 'Quake RTX', and the 'Marbles' demo feature this proprietary denoiser, which is basically magic.  I really don't understand how it accepts such raw, incomplete, noisy input and produces a cleaned, refined image at 1080p.  Even if my humble attempt at a de-noiser will never approach NVIDIA'S level of sophistication, their technology and latest games and demos served as inspiration to try my hand at it for this project here.  I am happy to report that the initial results are promising! If you take a look at the Geometry_Showcase Demo, Quadric_Geometry_Showcase Demo, Cornell_Box Demo, and Billiard_Table Demo in particular and drag the camera around with your mouse, you'll notice that the moving, rotating image is much less noisy and when the camera does come to a full stop, the image converges almost instantly!  A little technical note on this new denoising feature: if you take a look at Screen_Output_Fragment.glsl in the 'shaders' folder, you'll see that I have added a simple 9x9 box blur filter that averages the current center pixel with its immediate neighbor pixels, only if we say it's ok to blur inside the demo's path tracing fragment shader. Specifically, if it is a Diffuse (DIFF) surface or the diffuse portion of a clear coated diffuse surface (COAT), then it is allowed to blur with its neighbors,  which greatly helps convergence speed on surfaces like room walls, floors,  and ceilings. However, if it is a smooth mirror or glass specular surface, or it lies on the boundary edge between 2 pixels with greatly different reported intersection data, like the corner of a room where the surface normals change abruptly, or the boundaries between different scene objects,  or an abrupt color change (like 2 differently colored squares of a checkerboard texture), then the blur filter is disabled for that pixel and thus it remains razor sharp.  I have found that with some minor tweaks you can get the best of both worlds; sharp edges where it counts, and blurred,  softened noise on diffuse surfaces where all we care about is the general final blended color anyway. In order to differentiate between edges and non-edge flat smooth areas, I employ the handy GLSL built-in functions, dFdx() and dFdy(). These derivative functions allow you to peek at the current pixel's immediate neighbors both vertically and horizontally to compare their ray's intersection results like surface normals, surface color, and object IDs. If any of these are too different past a threshold, an edge is recorded, and later when the box blur filter is applied, it will avoid these noted edges. This is called edge detection and is an absolute necessity for even the most basic denoiser like mine. NVIDIA'S denoiser takes this pixel averaging/smoothing to a whole other magical level by training A.I. software on noisy input images vs. their fully cleaned-up path traced resulting counterpart images. Although I'll probably never understand how they do this, I am quite pleased with my humble first attempt. I think you'll agree that even this basic addition to the Three.js PathTracing Renderer makes a big difference in smoothness and convergence speed, especially when the image is moving or dynamic! :-D

* March 4th, 2021: Improved and optimized my CSG (Constructive Solid Geometry) library routines and added a new CSG Viewer demo to showcase the new features!  Over 4 years ago I initially created my CSG_Museum_1-4 rooms to demonstrate my then-limited command of CSG operations and rendering techniques.  Now in 2021 I decided to go back and revisit my understanding of and approach to Constructive Solid Geometry in order to possibly improve/optimize the routines as well as fill in any missing gaps in my knowledge of the subject.  I'm happy to report that not only do I now have a better grasp of CSG, I was able to spot and fix imperfections in my original algorithms and also increase the speed and efficiency of the 3 cardinal CSG operations.  The result is pixel-perfect beautiful custom 3D shapes (perfect mathematical curves, no triangle tessellation!) and everything is running at 30-60 fps, even on mobile!  To demonstrate the renderer's new and improved CSG capabilities, I decided to create a CSG Viewer demo that lets users easily try out the various CSG operations as well as manipulate both shape A and shape B (their shape type, 3D transforms, and material properties).  Once I got comfortable with composing matrices for shape A and shape B, I was able to hook their manipulation to the helpful dat.gui GUI system.  This browser-friendly menu system allows for intuitive and detailed control over the CSG objects in the scene.  At some point I might go back and see if I can apply my newly-gained knowledge to the old 4 CSG_Museum demo rooms.  Part of the reason there are 4 individual museum rooms instead of 1 is that my old algorithms had a lot of unnecessary 'if' statematents and boolean checks in the fragment shader, which GPUs don't like - it wouldn't compile all 4 rooms' objects at once. So I had to split them up into individual demos.  It would be nice to have all the CSG objects under 1 roof, literally!  At any rate, the new and improved CSG techniques are nicely showcased in the new CSG Viewer.  Being able to quickly mix, match, combine, and cut 3D shapes and volumes in this manner is truly powerful.  And having all of these new shapes path-traced in real time is the cherry on top!

* January 21st, 2021: New W.I.P. path traced game with new BVH technology! I am happy to present my fully path traced remake of the 1986 classic 'The Sentinel' by Geoff Crammond: it's called 'The Sentinel: 2nd Look'.  As stated above in the games section, 'The Sentinel' is my all-time favorite game for several reasons.  First, as a 13-year-old back in 1986 playing on my Commodore 64, 'The Sentinel' was the first true 3D filled polygon game on my Commodore 64 that I had ever seen.  Experiencing Geoff Crammond's worlds changed how I viewed computer games and in my opinion, his unique creation rose above what it meant to be a computer game back in the 80's (the age of coin-op arcades), even rising to the level of high art.  I don't know how Geoff Crammond got the brilliant idea to create this haunting, immersive game world, but its feel and imagery have stuck with me all these years.  I've always wanted to pay homage to this iconic game by bringing it to the modern era with a 30 fps framerate (the original played like a slideshow, understandably!), as well as maybe add my own path tracing touch and technology to it.  From the start, a major hurdle to overcome was being able to support many arbitrarily positioned/rotated dynamic game objects, each with their own personal BVH for their own triangle geometry.  The solution was to create a dynamic over-arching top-level BVH that contains all the bounding boxes of all the possible game objects.  I call it a 'BVH for the BVHs'! ;-) This top-level BVH contains all the objects' bounding volumes and pointers to their individual movement/rotation matrix transform data, and can be updated once every frame if needed, allowing for more complex, dynamic game environments to be path traced in real time.  I had been thinking about doing this for years, but working on this 'Sentinel' passion project kind of forced me to come up with a solution that could work inside the browser on commodity hardware.  Technically speaking, the new top-level BVH is created as a set of Vector4 uniforms to be quickly fed into the GPU (once every frame if needed).  Another set of Matrix4 uniforms contains the inverse matrix transform data for each game object and can also be written to on every frame if needed.  When the top-level BVH is traversed, the viewing ray is tested against the over-arching BVH to see if it hits a leaf, which in this case is a game object.  The ray then gets pointed to the real-time inverse matrix transform data for that leaf object, so it can be transformed into the objects local space.  Finally, it is tested against that particular object's own personal triangle BVH, which resides as a static data texture that was built upon game start-up and does not change during the lifetime of the application.  This last part operates like all of my other, older BVH demos on this repo.  The new part is the adding of the top-level dynamic BVH over all the 'regular', static model triangle-BVHs.  As of now, 'The Sentinel: 2nd Look' is a W.I.P. (gameplay to be added soon), but I just had to share the exciting news of the new dynamic top-level BVH, which opens the door to a lot more games and applications that can be path traced in real time inside your browser!  More updates coming soon! :)

* December 18th, 2020: The 'Games' section above has a new game: Path Traced Pong!  Continuing the series of real-time path traced games for any device with a browser (including mobile!), Path Traced Pong brings the iconic game of Pong into 3D, played inside the CG-famous Cornell Box.  Throughout my journey into 3D graphics, starting with C and OpenGL 1.0 under Windows 98, I have made now 3 versions of this game.  The first version was back in 1999, the second version was with a young three.js around late 2013, and now in 2020, Path Traced Pong uses the latest version of three.js and features real-time path traced global illumination with raytraced reflections, soft shadows, and dynamic light sources.  It is fun to play on desktop, but even more fun is when you're on the go, you can play it on your phone!  Each demo in this repo, and more currently, each new game that I try to program, presents me with new and interesting challenges, especially when trying to path trace a fast-paced game on any commodity hardware.  I learned a little more about successfully rendering dynamic, quick-moving game objects, as well as more efficiently sampling dynamic light sources (such as the bright white game ball as it bounces against the room walls).  My first 2 older versions featured basic network multiplayer over Sockets - in the future it would be nice to add WebSockets capability to these path traced games.  This would bring exciting new possibilities as players would not only be able to play a quick game online together, they would experience real time path traced game worlds!  I have more ideas for other simple, yet fun, 3D games that would benefit from this technology.  As always, I'll keep you posted! :)  



<h2>TODO</h2>

* For simple scenes without gltf models, instead of scene description hard-coded in the path tracing shader, let the scene be defined using familiar Three.js mesh creation commands (3/4/21 made progress in this area with my new CSG_Viewer demo - taught me how to create and manipulate object matrices like Three.js does)
* Figure out how to save pathtraced results into texture maps to be used for lightmaps (optimized baked lighting for static geometry)
* Dynamic Scene description/BVH rigged model animation streamed real-time to the GPU path tracer (1/21/21 made progress in this area by working on my new game The Sentinel: 2nd Look.  Featues a dynamic top-level BVH that can change and update itself every animation frame)<br>


<h2>ABOUT</h2>

* This began as a port of Kevin Beason's brilliant 'smallPT' ("small PathTracer") over to the Three.js WebGL framework.  http://www.kevinbeason.com/smallpt/  Kevin's original 'smallPT' only supports spheres of various sizes and is meant to render offline, saving the image to a PPM text file (not real-time). I have so far added features such as real-time progressive rendering on any device with a browser, FirstPerson Camera controls with Depth of Field, more Ray-Primitive object intersection support (such as planes, triangles, quadrics, CSG shapes, etc.), loading and rendering glTF triangle models, static and dynamic GPU BVH acceleration structures, and support for additional materials like ClearCoat and SubSurface. <br>

More examples, features, and content to come!
