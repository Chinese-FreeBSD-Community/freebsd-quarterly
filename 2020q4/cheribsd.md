## CheriBSD ##

Link:    http://www.cheri-cpu.org  
Link:    https://github.com/CTSRD-CHERI/cheribsd  
Link:    https://www.morello-project.org  
Link:    https://morello-dist.cl.cam.ac.uk
Link:    https://developer.arm.com/architectures/cpu-architecture/a-profile/morello  

Contact: Alex Richardson <arichardson@FreeBSD.org>  
Contact: Andrew Turner <andrew@FreeBSD.org>  
Contact: Brooks Davis <brooks@FreeBSD.org>  
Contact: Edward Tomasz Napierala <trasz@FreeBSD.org>  
Contact: George Neville-Neil <gnn@FreeBSD.org>  
Contact: Jessica Clarke <jrtc27@FreeBSD.org>  
Contact: John Baldwin <jhb@FreeBSD.org>  
Contact: Robert Watson <rwatson@FreeBSD.org>  
Contact: Ruslan Bukin <br@FreeBSD.org>  

### CheriBSD Status ###

CheriBSD extends FreeBSD to implement memory protection and software
compartmentalization features supported by the CHERI instruction-set
extensions.  There are three architectural implementations of the
CHERI protection model: CHERI-MIPS, CHERI-RISC-V, and Arm's forthcoming
experimental Morello processor (due late 2021).  CheriBSD is a research
operating system with a stable baseline implementation into which
various new research features have been, or are currently being, merged:

 * Arm Morello - In October, we released a developer preview of CheriBSD
 ported to Arm's Morello architecture.  This release supports a
 dynamically linked runtime and is generally functional.  It was cut
 from a development branch and work is in progress to merge the contents
 of this branch with the CheriBSD main line.  We anticipate producing a
 new release from this branch in early 2021.

 * Kernel spatial memory safety (pure-capability kernel) - The current
 CheriBSD kernel is a hybrid C program where only pointers to userspace
 are CHERI capabilities. This ensures that the kernel follows the
 intent of the application runtime and cannot be used to defeat
 bounds on application pointers. We have developed and will soon
 merge a pure-capability kernel where all pointers in the kernel are
 appropriately bounded capabilities. This vastly reduces the opportunity
 for buffer overflows. This spatial memory safety lays the
 groundwork for future work such as device driver compartmentalization
 and kernel temporal safety.

 * Userspace heap temporal memory safety (Cornucopia) - CHERI
 capabilities provide the necessary features to enable
 robust and efficient revocation of freed pointers.  With [Cornucopia](https://www.cl.cam.ac.uk/research/security/ctsrd/pdfs/2020oakland-cornucopia.pdf)
 we have implemented a light-weight revocation framework providing
 protection from use-after-reallocation bugs with an average cost below
 2%.  We aim to bring these overheads down further over the next year and
 merge this functionality into the mainline CheriBSD.

 * Syncing with upstream FreeBSD - We spent considerable time this
 quarter catching up with FreeBSD-CURRENT.  As of the beginning of
 December, we had caught up.  Merges are currently paused while we
 work to land Morello and pure-capability kernel changes.  In the
 interim, we have performed a test merge between our tree based on
 the legacy export of the FreeBSD tree to git and the new FreeBSD
 git repository.  The process went smoothly and is expected to have
 few impacts.

 * We have been working on updating the arm64 bhyve from Politehnica
 University of Bucharest to have it committed to FreeBSD. We have been
 upstreaming initial changes to help support this.
