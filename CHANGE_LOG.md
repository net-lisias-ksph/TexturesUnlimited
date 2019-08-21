# Textures Unlimited :: Change Log

* 2017-1217: 1.0.0.6 (Shadowmange) for KSP 1.3.1
	+ FIX - Recoloring GUI will only display the part-action 'Open Recoloring GUI' button if there is _something_ to recolor on the part.
	+ FIX - KSPTextureSwitch (and recoloring system) will no longer effect children parts in the editor.
	+ FIX - Symmetry part handling for KSPTextureSwitch / SSTUTextureSwitch modules
	+ CHANGE - Add ability to specify a flat color to use for a texture slot.
	+ CHANGE - Add configuration fields for Recoloring GUI width/height to general config file.
	+ CHANGE - Add an invert-alpha toggle to the stock replacement PBR shader.
	+ CHANGE - SSTU/Masked shader -- add Emissive support
* 2017-1203: 1.0.0.5 (Shadowmange) for KSP 1.3.1
	+ FIX - Error that could result in explosions due to reflection probe collider when reverting to launch.  Reflection probe creation is now delayed from when the event is fired until the next Update() tick.
	+ CHANGE - Property name for _Metallic multiplier to _Metal in SSTU/PBR/Metallic shader.  Apparently Unity has some internal conflicts with the _Metallic property name, where it refuses to default the property to any value but '0'.
	+ CHANGE - Combine scenery-near and scenery-far render passes into a single pass; the loss of depth-resolution will rarely if ever be visible in the low-resolution reflection texture, but -might- result in apparent z-fighting in distant geometry, and/or apparent out-of-order rendering.
	+ CHANGE - Reflection probe texture updates are now amortized over 32 frames, up from 20.  Each pass of each cubemap face is now rendered on its own frame (3 passes per face * 6 faces = 18 frames), as well as the Unity internal reflection probe updates (14 frames).  Should result in slightly higher FPS and more consistent frame timing.
	+ CHANGE - Add keyword support at the plugin/config level.  These are specified through PROPERTY blocks, with 'name = keyword', and 'keyword = FEATURE_TO_ACTIVATE'.
		- Currently only supports enabling of keywords.
		- Keyword-variants must be built into the shader before they can be used.  A list of keyword-variants will be published on the wiki in the documentation for each specific shader.
	+ CHANGE - Add 'tinting' mode to the recoloring shaders (Masked + PBR version).  This is enabled with the keyword 'TINTING_MODE';  the default (no keywords activated) is to use the existing codepath.
			- UNTESTED
* 2017-1202: 1.0.0.5-pre (Shadowmange) for KSP 1.3.1 PRE-RELEASE
	+ FIX - Error that could result in explosions due to reflection probe collider when reverting to launch.  Reflection probe creation is now delayed from when the event is fired until the next Update() tick.
	+ CHANGE - Property name for _Metallic multiplier to _Metal in SSTU/PBR/Metallic shader.  Apparently Unity has some internal conflicts with the _Metallic property name, where it refuses to default the property to any value but '0'.
	+ CHANGE - Combine scenery-near and scenery-far render passes into a single pass; the loss of depth-resolution will rarely if ever be visible in the low-resolution reflection texture, but -might- result in apparent z-fighting in distant geometry, and/or apparent out-of-order rendering.
	+ CHANGE - Reflection probe texture updates are now amortized over 32 frames, up from 20.  Each pass of each cubemap face is now rendered on its own frame (3 passes per face * 6 faces = 18 frames), as well as the Unity internal reflection probe updates (14 frames).  Should result in slightly higher FPS and more consistent frame timing.
	+ CHANGE - Add keyword support at the plugin/config level.  These are specified through PROPERTY blocks, with 'name = keyword', and 'keyword = FEATURE_TO_ACTIVATE'.
		- Currently only supports enabling of keywords.
		- Keyword-variants must be built into the shader before they can be used.  A list of keyword-variants will be published on the wiki in the documentation for each specific shader.
	+ CHANGE - Add 'tinting' mode to the recoloring shaders (Masked + PBR version).  This is enabled with the keyword 'TINTING_MODE';  the default (no keywords activated) is to use the existing codepath.
			- UNTESTED
	+ CHANGE - Only a single reflection probe is ever created/used.  Should result in better performance, and fewer visual artifacts with multiple vessels on screen.  However, any non-actively-controlled vessels may have 'incorrect' reflections.  Will be addressing this a bit more in depth in the future.
* 2017-1125: 1.0.0.4 (Shadowmange) for KSP 1.3.1
	+ Move to 'official release' status.
	+ FIX - #8 - Camera positioning / atmosphere reflection capture
	+ FIX - #12 - Editor skybox not captured in reflections
	+ FIX - #18 - Remove 'Texture' from being appended to all section names in texture switch module.
	+ FIX - #19 - Launch clamps/debris causing reflection probe problems.
	+ CHANGE - Add more debugging utilities.  These can be enabled through the config file, but are disabled by default.
	+ CHANGE - Ninja-patch to remove some debug spam.  If you downloaded in the first 5 mins, you might want to re-download.
* 2017-1120: 0.9.0.3 (Shadowmange) for KSP 1.3.1 PRE-RELEASE
	+ CHANGE - Add _Smoothness and _Metallic property setters to shaders.  These can be used in combination with default textures to facilitate simple material setups. (SSTU/PBR/Metallic and SSTU/PBR/StockMetallicBumped)
	+ CHANGE - Add SSTU/PBR/Solar shader.  Uses industry standard PBR SubSurfaceScattering to simulate backlighting on objects, using a _Thickness texture to determine how much light is transmitted through the object.
	+ FIX - Error that would cause KSP to null-ref when using the stock texture-replacement mechanics in MODEL nodes within PART configs.
	+ CHANGE - Add preliminary implementation of UV-map exporting utility.  Not yet fully functional, has some issues with some stock models that will need to be corrected.
* 2017-1116: 0.9.0.2 (Shadowmange) for KSP 1.3.1 PRE-RELEASE
	+ FIX - Error with reflection-sphere colliders not being deleted properly that could result in explosions in certain staging situations.
	+ CHANGE - remove duplicate/unused field from texture-switch module.
* 2017-1111: 0.9.0.1 (Shadowmange) for KSP 1.3.1 PRE-RELEASE
	+ Initial Release
