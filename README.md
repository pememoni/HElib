HElib
=====

***August 2019:*** Improved noise management in HElib.
Better and more robust bootstrapping algorithm.
Ubuntu 18.04 Docker image with HElib and its dependencies. 
See install instructions in [DOCKER_USAGE.md](DOCKER_USAGE.md)

***July 2019:*** Added new bootstrapping and PGFFT tests.

***June 2019:*** Added implementation of PGFFT to replace Armadillo for FFTs in
the CKKS scheme. See comments in `PGFFT.h` for more information.

***May 2019:*** CKKS bug fixes and fixed compiler warnings.

***April 2019:*** Moved the HElib repository on github from shaih/HElib to
HomEnc/HElib. Introduced HElib-specific exceptions, replaced C `assert`, NTL
Error and `std::exception` to use HElib-specific assertions that throw the new
exceptions. See comments in `assertions.h` and `exceptions.h` for usage
information.

***March 2019:*** Introduced new test framework (google test), documented in
[TESTS.md](TESTS.md). Previous framework will be deprecated. Added a cmake
build script for building HElib and dependencies, documented in
[INSTALL.md](INSTALL.md). Added an example program, see `example program`.

***January 2019:*** Multiple changes: CKKS support, new modulus-chain
implementation, better noise management, etc. Documented in
[changes.md](changes.md)

***March 2018:*** Re-implementation of homomorphic linear transformations,
featuring speedups of 15x to 75x.

***Dec 2017-Jan 2018:*** Added some routines for addition/multiplication and
comparisons of integers in binary representation, and for homomorphic table
lookup. See the supported interfaces in `binaryArith.h`, `binaryCompare.h`,
and `tableLookup.h`. Some examples are in `Test_binaryArith.cpp`,
`Test_binaryCompare.cpp`, and `Test_tableLookup.cpp`.

The inputs and outputs to the new routines are logically vectors of Ctxt objects
(one Ctxt per bit in the binary representation). These vectors are wrapped by
the new `CtPtrs` wrapper (see `CtPtrs.h` and the underlying `PtrsVector.h` and
`PtrsMatrix.h`).  Hence the same logic will work for any type of input that can
be mapped logically to arrays of `Ctxt`s, as long as one can wrap them with the
same wrapper class. In particular, we implemented wrappers for
`std::vector<Ctxt>`, `std::vector<Ctxt*>`, `NTL::Vec<Ctxt>` and
`NTL::Vec<Ctxt*>`.

-----------------------------------------------------------------------------
HElib is a software library that implements [homomorphic encryption][6] (HE).
Currently available is an implementation of the
[Brakerski-Gentry-Vaikuntanathan][1] (BGV) scheme, along with many
optimizations to make homomorphic evaluation runs faster, focusing mostly on
effective use of the [Smart-Vercauteren][2] ciphertext packing techniques and
the [Gentry-Halevi-Smart][3] optimizations. See [this report][7] for a
description of a few of the algorithms using in this library. Starting
December 2014, the library also includes [bootstrapping][8].

At its present state, this library is mostly meant for researchers working on
HE and its uses. Also currently it is fairly low-level, and is best thought of
as "assembly language for HE". That is, it provides low-level routines (set,
add, multiply, shift, etc.), with as much access to optimizations as we can
give. Hopefully in time we will be able to provide higher-level routines.

This library is written in C++ and uses the [NTL mathematical library][4]
(version 10.0.0 or higher). As of March 2015, it also supports multi-threading.
HElib is distributed under the terms of the [Apache License v2.0][5].
For more information see the [GitHub Pages][9].

  [1]: http://eprint.iacr.org/2011/277       "BGV12"
  [2]: http://eprint.iacr.org/2011/133       "SV11"
  [3]: http://eprint.iacr.org/2012/099       "GHS12"
  [4]: http://www.shoup.net/ntl/             "NTL"
  [5]: http://www.apache.org/licenses/LICENSE-2.0  "Apache-v2.0"
  [6]: http://en.wikipedia.org/wiki/Homomorphic_encryption "Homomorphic encryption"
  [7]: http://eprint.iacr.org/2014/106       "algorithms"
  [8]: http://eprint.iacr.org/2014/873       "bootstrapping"
  [9]: https://github.com/homenc/HElib       "GitHubPages"
