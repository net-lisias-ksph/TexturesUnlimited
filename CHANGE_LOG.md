# Textures Unlimited :: Change Log

* 2020-0301: 1.5.10.25 (Shadowmage) for KSP 1.9
	+ Update for KSP 1.9
	+ Fix issues with TU/* shaders with some of the stock normal maps
	+ Add keyword driven support for BC5 normal maps ('keyword=TU_BC5_NRM')
* 2020-0209: 1.5.9.24 (Shadowmage) for KSP 1.8
	+ recompile and update for KSP 1.8
	+ update Unity editor and project to 2019.2.2f1; match KSP version
	+ fix icon-shader clipping; incorrect default coords specified in the shader itself
	+ add basic albedo color multiplication to the icon shaders, and update the default _Multiplier parameter to 2.25
	+ recompile icon shader bundle, include .manifest file for info on what it contains
* 2019-0804: 1.5.8.23 (Shadowmange) for KSP 1.7.2
	+ FIX - KSPTextureSwitch - Grabbing child-part transforms in the editor.
	+ FIX - KSPTextureSwitch - Recoloring not applied to symmetry counterparts in editor.
	+ FIX - KSPTextureSwitch - Not using 'default colors' specified in a texture-set, and always persisting colors from the first applied set.
	+ FIX - TextureSet - Allow parsing of either float or byte notation in COLORS blocks.
	+ CHANGE - Change default behavior for texture-sets to 'create new material'.  Previous behavior was to 're-use existing material' which caused absolute messes with keywords and other shader parameters, as previous values were not cleared from the material during set switches.
		- Default mode for TEXTURE_SET is 'create'.  Default mode for MODEL_SHADER is 'update' (unchanged).
		- This will have an impact on any configurations that were intentionally using the previous default 'update' behavior.  They will need to be explicitly updated to state that they should continue to use that behavior, by adding a 'mode = update' line to the MATERIAL blocks.
		- This may also have a negative impact on patches targeting existing materials that had non-default values specified for such as 'specular' or 'hardness', as these values will no longer carry over from the original material and must be explicitly specified in the texture-set configuration.
		- An error will be logged anytime a texture-set is loaded that does not specify its mode.
	+ CHANGE - Move over to using the in-game settings screens for settings that are configurable at run-time.  Custom editor-reflections, custom reflection resolution, and a few other settings are now available from in-game.  Debug/logging options are still driven by the config-file based system.
	+ CHANGE - Add a new Reflection Probe to the VAB/SPH to fix the incorrectly baked stock environment maps.
		- Can be enabled/disabled in the in-game options.  Default is enabled.
		- Resolution can be adjusted in the in-game options.  Default is 512x.
	+ NEW FEATURE - Recoloring GUI - Add 'detail' multiplier slider to allow for user to control the amount of extracted detail that is used.
		- This requires proper use of the 'normalization' system for proper detail extraction.
		- Default is 100%, GUI slider goes from 0-500%, but can use manually typed values up to 999%.
	+ NEW FEATURE - Preset Color Groups (Palettes in recoloring UI).  Config defined groups of colors that can be selected to limit the # of displayed colors in the recoloring UI.  These preset-color-groups can be themed, or setup for specific mods, etc.
		- Currently there is no limitation on which palettes are available for any part/section.  If a palette is defined, it may be selected.
		- In the future there will be a method to specify the default and available palettes for any given recolorable section.
	+ CHANGE - Adjust a few of the preset colors to more closely match their intended shades.  Notably this includes the 'stock' colors.
	+ CHANGE - Added a few new stock color presets that reflect the commonly used stock colors from the original textures.
* 2019-0622: 1.4.8.22 (Shadowmange) for KSP 1.7.2
	+ Recompile for KSP 1.7.2
	+ CHANGE - Disable TU's 'Reflection Manager', and use the stock Reflection Probes.  If you find reflections are not working in your game, enable the stock reflection settings in the in-game options menu.
	+ CHANGE - On ModuleManager reload, clear all existing data.  Should fix issues of TU throwing errors during MM database reloads, and will actually allow for reloading the database to pick up changes to TU configs.
	+ CHANGE - Remove graphics API check and warning.  As the stock reflection system is in use, no longer care what API is used.
	+ KNOWN ISSUE - Stock skybox (stars) no longer present in reflections.  Stock issue with their reflection system.
	+ KNOWN ISSUE - Scatterer no longer present in reflections.  Seems to be caused by changes to stock code regarding skyboxes, but may also be due to the recent Scatterer overhaul (or both?).
* 2019-0414: 1.4.7.21 (Shadowmange) for KSP 1.7
	+ Recompile for KSP 1.7
* 2019-0306: 1.3.6.20 (Shadowmange) for KSP 1.6
	+ Add several functions available for external mod integration to swap texture sets or reload existing textures on model changes.
	+ First use of new build script for this repository, so please make note of any issues with packaging.
* 2019-0219: 1.3.5.19 (Shadowmange) for KSP 1.6
	+ Fix shader bundle Windows-OpenGL compatibility
* 2019-0216: 1.3.4.18 (Shadowmange) for KSP 1.6 PRE-RELEASE
	+ Recompile Plugin for KSP 1.6
	+ Recompile shaders to fix mixing issues with recoloring normalization.
* 2018-1105: 1.2.3.17 (Shadowmange) for KSP 1.5
	+ FIX - Clean up an issue with parsing for color values.
	+ FIX - Many fixes for WIP - TUPartVariant module (stock PartVariant integration)
* 2018-1028: 1.2.2.16 (Shadowmange) for KSP 1.5 PRE-RELEASE
	+ Updated and recompiled for KSP 1.5
		- Compatible with stock PBR shader - adds in-flight reflections
		- Still does not work properly under DX9
		- Should be mostly backwards compatible with existing config sets
	+ New Shaders Available - See the wiki for details ( https://github.com/shadowmage45/TexturesUnlimited/wiki )
		- Minimized shader variant count -- only Metallic, Specular, and Legacy exist, along with their transparent counterparts.
		- New recoloring system implemented, usable from all shaders - See wiki for details
		- Minor updates to subsurface scattering implementation, usable from all shaders - See wiki for details
	+ CHANGE - Add a selection of new Icon Shaders that fix rendering issues on DX11/OpenGL for stock parts
		- Also include configs to apply these shaders to most (all?) stock parts (based on the original shader name used in the material).
	+ CHANGE - Add ability for MATERIAL blocks to specify a render-queue for that material.  Use 'renderQueue = XXXX' inside of the block to specify the value.
	+ CHANGE - Add ability for MATERIAL blocks to specify texture scale and offsets (applied to all textures equally).
		- 'textureScale = 1,1'
		- 'textureOffset = 1,1'
	+ CHANGE - Allow for 'modelShader=XXXX' syntax to be used in KSPTextureSwitch to inform the module to look for its texture-set data from a KSP_MODEL_SHADER config source.
	+ CHANGE - Include a new stand-alone redistributable for AssetBundle model loading, using the '.kbm' file extension.  TU will continue to load and process '.smf' asset-bundle models as it did before.
		- The main difference between these two is that .kbm models will not support TU shaders, and is intended for distribution by mods that only need model-loading functionality.
	+ CHANGE - Add more error logging features on failed texture set, material, model, and texture lookups.  Debug information should be more useful and contain more reference data to help track down the issue.
	+ CHANGE - Updates/changes to config layout for the mod.
		- REFLECTION_CONFIG and UV_EXPORT configs moved inside of root TEXTURES_UNLIMITED node and all have been moved into a single file.
		- Reflections are now enabled by default as they are needed for the stock reflective shaders.  They can still be patched to disable them if desired for whatever reason.
	+ CHANGE - Update the debug 'dump world data' function to include a ton more data on transforms, materials, and shaders.
	+ FIX - Icon shaders will no longer use 'sharedMaterial' when being applied - fixes issues of icon shaders being copied back onto the source part.
	+ CHANGE - Color specifications in shader property blocks or for use in preset colors can now be specified in one of the following formats:
		- hex - #FF80AAF8  (leading # is mandatory)
		- float - 1.0,0.5,1.0,0.9725  (use of decimal is mandatory -- one is specified as '1.0' and not '1')
		- byte - 255,128,255,247
* 2018-0913: 1.1.2.15 (Shadowmange) for KSP 1.4.5
	+ Update .version file and repackage for KSP 1.4.5 compatibility.
	+ No other changes.
* 2018-0605: 1.1.2.14 (Shadowmange) for KSP 1.4.3
	+ Recompile vs. KSP 1.4.3 libs - update .version file accordingly
	+ Finalize the DX11 'fix'; auto-enabled whenever DX11 or DX9 are detected
	+ Remove graphics API warning for DX11 (still warns when DX9 is used)
	+ Add ability to override recoloring data through PROPERTY blocks (special-case exceptions)
* 2018-0506: 1.1.2.14a (Shadowmange) for KSP 1.3.1 PRE-RELEASE
	+ TESTING RELEASE
	+ FIX - Add alternate rendering routine that can be used with DX9/DX11, slightly more overhead, but removes issues of inverted cubemap faces.
		- Can be activated in the debug menu, or through config file, see patch example below
			- DOES NOT FIX DX9 CUBEMAP BLURRING ISSUES
		- version file not updated, nor has AVC target; pure testing release
	+ still warns when starting about DX9/DX11
	+ 'alternate rendering' mode must be enabled either manually in debug menu or with a patch (see below)
		- Patch to enable alternate rendering mode:
```
@REFLECTION_CONFIG[default]
{
    %directXFix = true
}
```
* 2018-0421: 1.1.1.13 (Shadowmange) for KSP 1.3.1
	+ FIX - Shader replacement on models using stock TEXTURE= for texture replacement should no longer null-ref.  This was caused by incomplete texture-set definitions leaving 'empty' texture slots on the model.
	+ FIX - Check for null materials/shaders on stock parts when doing shader and material adjustments.
	+ FIX - Transparent material render-queue sorting.  Transparent materials such as flags should now render properly after being adjusted by TU.
	+ CHANGE - Add a new partmodule that handles the stock fairings.  See #40 for more info.
	+ CHANGE - Add shader properties to control texture scale and texture offset.  See #49 for more info.
* 2018-0322: 1.1.0.12 (Shadowmange) for KSP 1.3.1
	+ No changelog provided
* 2018-0121: 1.0.0.8 (Shadowmange) for KSP 1.3.1
	+ FIX - Symmetry handling of parts using KSPTextureSwitch module
	+ FIX - Incorrect URL specified in .version file
* 2017-1220: 1.0.0.7 (Shadowmange) for KSP 1.3.1
	+ FIX - Revert some unintended changes to shader property names
	+ FIX - The other half of the part-hierarchy issues in the editor when using KSPTextureSwitch
	+ FIX - Recoloring GUI config parameters not loading properly for width/height
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