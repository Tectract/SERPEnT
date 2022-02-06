# SERPEnT
SERPEnT - Surface Extrapolation by Reverse-Plotting of Energy Trajectories


SERPEnT is a tool that allows for programmatic generation of equilibrium crystal surfaces shapes (ECS shapes) and equilibrium surface energy shapes (SES shapes) according to classical "Wulff Construction Theory". Crystal surface shapes can be generated by specifying an array of directional vectors and their corresponding surface energy parameters (as real numbers). Surface energy shapes can be generated automatically for most shapes but they need manual adjustment.


Here is an example list of the adjustable parameters for the surface energy shapes:

***cuboctahedron surface energy param example***

22    % number of Bezier spatial divisions

0.6   % ANISOTROPY or "bubbliness"

0.4   % inner pointiness

1.8   % extra pointiness

1.1   % facetPush

13.5  % cornerPush

1.1   % edgePush

.95   % edgePush1

1.13  % bezPush


Surface energy shapes are currently generated using bezier surfaces, but one goal of this project is to upgrade this component so they use NURBS curved surfaces instead, so that less parameters can be used to control the generation of surface energy shapes, and so that they can be programmed to more naturally follow theorized surface energy shapes which have no sharp edges or "jump discontinuities". In my dissertation I positted that although crystal surface energy shapes are non-unique, they are constrained to be normal to all planes and perpendicular to all edges and vertices.

For more information on how crystal surface energy is evaluated, please refer to "[Characterization, Modeling, and Simulation of Multiscale Directed-Assembly Systems](http://www.unm.edu/~reason/RAM_dissertation_final.pdf)", Molecke 2011, pages 16-46.

SERPEnT is a collection of MATLAB scripts, currently. They will eventually be translated to C++ and/or other languages. This tool should allow generation of arbitrary crystal surface shapes and surface energy shapes, which can be used to calculate anistropic crystal interactional energies with external particles, or inside of a solid crystal, due to intermolecular forces. 

