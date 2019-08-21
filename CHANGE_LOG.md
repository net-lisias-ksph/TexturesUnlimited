# Textures Unlimited :: Change Log

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
