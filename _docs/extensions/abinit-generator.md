---
title: ABINIT Generator
---

Avogadro has a new interface to the open source solid-state code ABINIT, provided by one of the ABINIT developers, Prof. Matthieu Verstraete

![][1]

[1]: ../images/abinit-generator/media_1340329424336.png

Start with a crystal structure — here a clay mineral from the new Avogadro crystal library.

![][2]

[2]: ../images/abinit-generator/media_1340329441585.png

Open up the Abinit input generator under the Extensions menu

![][3]

[3]: ../images/abinit-generator/media_1340331425028.png

Most common options for Abinit are available here, with a text preview (highlighted in red) generated as you change options above.

![][4]

[4]: ../images/abinit-generator/media_1340331450497.png

The input generator allows you to (1) pick the type of coordinates: real-space Cartesians or reduced coordinates and (2) pick the type of geometry optimization (if any).

![][5]

[5]: ../images/abinit-generator/media_1340331470946.png

Another important option is setting the occupation scheme (1) and SCF options (2) and (3).

![][6]

[6]: ../images/abinit-generator/media_1340331539150.png

Finally, when finished, you can click the “Compute” button (not pictured) if Abinit is available locally on your computer, or “Generate” to save the input file for submission to a remote queue.

![][7]

[7]: ../images/abinit-generator/media_1340331503702.png

Save the input file and you‘re finished!
