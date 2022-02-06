# SERPEnT
SERPEnT - Surface Extrapolation by Reverse-Plotting of Energy Trajectories


SERPEnT is a tool that allows for programmatic generation of equilibrium crystal surfaces shapes (ECS shapes) and equilibrium surface energy shapes (SES shapes) according to classical "Wulff Construction Theory". Crystal surface shapes can be generated by specifying an array of directional vectors and their corresponding surface energy parameters (as real numbers). Surface energy shapes can be generated automatically for most shapes but they need manual adjustment.

.

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

.

Here is an example of the surface energy params that specify a cuboctahedron equilibrium crystal shape:

divisor = 10;     % use a divisor here to cure (irrational-number rounding) tolerance errors (RAM)

a=1/divisor;

a1=1.156/divisor;

WulffECS = [

0	0	1	a       255   255   102   % light yellow

0	0      -1	a       255   255   102

0	1	0	a       255   255   102

0      -1	0	a       255   255   102

1	0	0	a       255   255   102

-1	0	0	a       255   255   102

1	1	1	a1       226   226   0    % medium yellow

-1	1	1	a1       226   226   0

1	-1	1	a1       226   226   0

-1	-1	1	a1       226   226   0

1	1	-1	a1       226   226   0

-1	1	-1	a1       226   226   0

1	-1	-1	a1       226   226   0

-1	-1	-1	a1       226   226   0

];

So in this example, a cuboctahedron is characterized by two sets of planes, the simple cubic faces and the corner facets. The corner facets are set to have a surface energy that is 1.156 times the unitized surface energy of the cubic facets. So the facet surface energies are specified in a ratio with a chosen surface energy unitized to 1, usually I chose the planar surface or set of surfaces that lies closest to the origin to unitize as the basis for the surface energy ratios, so the other surface energies for facets which are further from the origin would have real values greater than 1, but this is not a strict requirement for the tool to work.

So each line in the ECS input array has a real directional vector in 3D-space, a real energy param, which in this example is a for the cubic faces and a1 for the corner facets, and 3 integers for RGB color.

There is a divisor param to help cure rounding errors related to computation of the edge and vertex locations. If 10 doesn't work, try 100. If 100 doesn't work, try 1000.

Surface energy shapes are currently generated using bezier surfaces, but one goal of this project is to upgrade this component so they use NURBS curved surfaces instead, so that less parameters can be used to control the generation of surface energy shapes, and so that they can be programmed to more naturally follow theorized surface energy shapes which have no sharp edges or "jump discontinuities". The Wulff shape is the convex
inner shape bounded by all tangents to an outer surface energy shape (SES). In my dissertation I positted that although crystal surface energy shapes are non-unique, they are constrained to be normal to all planes (by the Wulff contruction theory) AND ALSO perpendicular to all edges and vertices.

For more information on how crystal surface energy is evaluated, please refer to "[Characterization, Modeling, and Simulation of Multiscale Directed-Assembly Systems](http://www.unm.edu/~reason/RAM_dissertation_final.pdf)", Molecke 2011, pages 16-46.

SERPEnT is a collection of MATLAB scripts, currently. They will eventually be translated to C++ and/or other languages. This tool should allow generation of arbitrary crystal surface shapes and surface energy shapes, which can be used to calculate anistropic crystal interactional energies with external particles, or inside of a solid crystal, due to intermolecular forces. 

