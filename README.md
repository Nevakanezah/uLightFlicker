# uLightFlicker: Simple flickering lights for VRChat worlds

uLightFlicker is a Unity package whose sole contents are the uLightFlicker Udon graph, meant for use in creating VRChat worlds.
Attaching uLightFlicker to any gameObject with a Light component causes that light source to rapidly change its intensity, 
creating a flickering effect that ranges from smooth candlelight all the way to an aggressive strobe useful for electrical sparks.

This project is based on the work of Steve Streeting's "LightFlickerEffect" C# code.

## DISCLAIMER & REQUIREMENTS:
This package acts during onUpdate and lateUpdate events, and requires a dynamic(or mixed) light to operate.
Is that performant? Hell no, but we're here for A E S T H E T I C.
This project is also intended for use in VRChat worlds, requriring the VRCWorld gameObject & whatever associated
packages VRC uses to run Udon. See: https://vcc.docs.vrchat.com/ for additional details.

## CONFIG:
uLightFlicker has three settings:
  (Float) minIntensity - The minimum light intensity
  (Float) maxIntensity - The maximum light intensity
  (Int) smoothing      - How smoothly the light level changes. This is clamped to a value of 1 or higher.

I recommend the following settings for the gameObject you're attaching this to:
- Only one Light component
- The light component has to be either "Dynamic" or "Mixed." This does nothing on baked-only light sources.
  I'm partial to mixed lighting, as this can provide more consistent brightness than minIntensity alone seems to provide.
- This should work on any light component with an "intensity" parameter,
  but point lights, spotlights, and maybe directional lights will probably work best.
- I recommend that your light component does not cast shadows, as this is even worse for performance.

## HOW TO USE THIS PACKAGE:
1. Download the unity package and import it to your project
2. Select a gameObject in your scene with an attached light component
3. Add a new Udon Behaviour component to that gameObject
4. Drag and drop the uLightFlicker udon graph into the new Udon Behaviour component.
   uLightFlicker automatically identifies the first Light component on its gameObject parent in order to operate.
5. Set your desired parameters for uLightFlicker
6. That's it.
