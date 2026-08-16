Project Description

This project demonstrates the design, visualization, and analysis of arectangular aperture horn antenna using MATLAB Antenna Toolbox. The hornantenna is simulated to study its geometry, three-dimensional radiationpattern, S11 response, and its use as the feed element of a reflectorantenna.

Horn antennas are directional microwave antennas commonly used in radarsystems, satellite communication, microwave links, antenna measurements,and as feeds for parabolic reflector antennas.

Requirements

MATLAB

Antenna Toolbox

RF Toolbox / RF plotting support for S-parameter visualization

MATLAB Code

% Create a rectangular horn antenna object
myHorn = horn;

% Manually set antenna dimensions
myHorn.FlareWidth = 0.1;
myHorn.FlareHeight = 7;
myHorn.Length = 15;

% Display horn antenna geometry
figure;
show(myHorn);
title('Aperture Horn Antenna Geometry');

% Plot the 3D radiation pattern at 10 GHz
figure;
pattern(myHorn, 10e9);
title('3D Radiation Pattern at 10 GHz');

% Define frequency range from 8 GHz to 12 GHz
freqRange = linspace(8e9, 12e9, 41);

% Calculate and plot S-parameters
figure;
s = sparameters(myHorn, freqRange);
rfplot(s);
grid on;
title('S11 (Return Loss) vs Frequency');

% Use horn antenna as a feed for a reflector
myDish = reflector;
myDish.Exciter = myHorn;
myDish.GroundPlaneRadius = 0.5;

% Display reflector antenna
figure;
show(myDish);

 S11 / Reflection Coefficient
S11 tells us how much of the incident signal is reflected at the antennainput.
S11(dB) = 20 log₁₀|Γ|
A more negative S11 generally means better matching.
 S11 Approximate Interpretation

 Return Loss

Return loss is conventionally:

RL = -20 log₁₀|Γ|

Therefore, if:

S11 = -10 dB

then:

Return Loss = +10 dB

Although S11 and return loss are often casually used interchangeably inantenna plots, the sign convention is technically different.

A horn antenna is a flared waveguide antenna in which the cross-sectional area of the waveguide gradually increases toward the aperture.

The flaring provides a smoother transition between:
Rectangular Waveguide
        ↓
    Flared Section
        ↓
      Aperture
        ↓
Free-Space Radiation

   
