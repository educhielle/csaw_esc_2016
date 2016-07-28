Challenge Description (ESC 2016)
================================

The theme of this year's competition is **control flow integrity** and **memory corruption** for embedded processors. For more than a decade, memory safety violations on control data remain a prominent threat to the security of embedded systems. Yet, embedded systems are often overlooked in the design of mitigation techniques both at the compiler level as well as the hardware itself. An important observation is that software level modifications, implemented inside the compiler, attempt to protect the security of the system at the same abstraction layer as the software exploitation itself. Hence, from a security perspective, protection methods at lower abstraction levels, such as the SoC hardware, are more desirable and effective, since they afford better guarantees against evasion. 

Today, most mobile and IoT devices are based on embedded SoCs, and improving their security would have a direct impact to the privacy of the users. Towards this goals, this year's challenge invites participating teams to *design, implement and demonstrate* mitigation techniques against control flow violations and memory integrity corruptions, using **hardware modifications** (with minimal area and performance impact) together with potential compiler support. In more details, acceptable solutions to the challenge must be based on hardware level trust, and new hardware modules and structures, while allowing necessary compiler level enhancements to complement these hardware changes. Solutions that focus primarily only on compiler enhancements, *without demonstrating adequate synergy of both hardware and software*, would not receive full consideration at the ESC competition finals. Competitive solutions to the challenge need to use novel mitigations as much as possible, and avoid reusing previously published solutions or already known techniques. The best solutions need to impact the area and performance of the SoC as little as possible.

Qualification Phase
-------------------

The 2016 challenge is divided in two phases: the **qualification phase** and the **final phase**. For the qualification phase, participating teams are asked to develop a set of *software level exploits* for the **OpenRISC** embedded processor ISA. Specifically, teams are asked to develop, implement and test vulnerable C/C++ programs for OpenRISC Linux, as well as write the corresponding *software exploits* that subvert memory integrity and control flow, in order to execute arbitrary code of the attackers' choice, escalate privileges, hide attack evidence, leak sensitive memory data, attack a different process/thread in the OS, inject code, execute CO-OP, JOP and ROP payloads etc. Evaluation will take into account the *diversity* and *complexity* of the attack vectors/exploits, including but not limited to stack smashing, heap smashing, function pointer clobbering, data pointer corruptions, virtual pointer smashing, exception pointer hijacking, `longjmp` buffer corruption, integer overflows etc. 

Teams are asked to provide actual **working implementations** of their vulnerable programs and exploits (including Makefiles and testing instructions) on at least **two (2)** different attack vectors that demonstrate *novelty*, *effectiveness*, *efficiency*, while at the same time allow powerful *post-exploitation payloads*. The teams should describe the details of their exploits in their **qualification report** (including a description of why each exploit works on OpenRISC), as well as how they intend to protect against different attack vectors by **modifying the OpenRISC hardware** and the **compiler** (if needed to complement the hardware enhancements). The proposed components and the new functionality of the protection modules should also be described in sufficient detail in the report. Qualification phase submissions, and the implemented software exploits, will be evaluated by a team of experts for correctness, impact, realistic payload effects (e.g., opening a shell, leaking memory data etc.) and practicality (e.g., how easy is it to launch the attack, does it always work even though standard protections such as ASLR or canaries are in place, etc). 

Final Phase
-----------

The **10 best** submissions will qualify to the final phase that requires **implementing** the proposed mitigation techniques at the RTL of the OpenRISC processor on a DE0-nano FPGA, using Verilog HDL. Finalists should primarily address the hardware layer and can add C/C++ compiler modifications only if this is necessary to complement a hardware protection mechanism. The definitive goal is to *mitigate as many exploitation categories as possible*, from a pool of vulnerable programs and actual exploits, collected during the qualification phase. Evaluation of the finalists will be a combination of positive points, awarded to the implemented mitigations, as well as negative points, lost when the exploits implemented during the qualification phase, are mitigated by other teams during the final phase.

Specifically, **positive points** will be awarded based on the following criteria:
 
1. The **universality** of the solution in terms of how many different exploitation categories/attack vectors are mitigated at the same time, while minimizing the hardware & compiler level modifications (15%).
2. The *relative weight* of each exploitation category (i.e. not all exploitations are equally powerful/practical). These weights will be provided after the qualification phase ends and affect the points distribution for 'universality'.
3. The **robustness** of the developed mitigations and how easy it could be for attackers to bypass it (20%).
4. The **efficiency** of the mitigation techniques in terms of runtime memory overhead, hardware area overhead, performance impact etc. (15%).
5. The **quality** and **elaboration** of the final report submitted through the HotCRP registration system, which should also report experimental results on the impact of the proposed mitigation (in terms of area, performance etc.) to the OpenRISC SoC (20%). 
6. The **correctness** of the implementation and live demonstration at the finals (using a DE0-nano), under the given attack vectors (30%).

In addition, each team will receive **negative points** for their developed exploits during the qualification phase, which will be proportional to the number of other teams that mitigate these particular exploits at the finals. This means that all teams should *judiciously develop their qualification phase exploits* to prevent mitigation by other teams at the finals. The maximum number of negative points can be up to 18% of the maximum positive points.


All deliverables in both the qualification and final phase (developed files, programs, exploits, etc.), are *should work out of the box* by just typing a simple command (like `make <target>`), and need to be accompanied by *simple step by step instructions* on how the organizers and judges can verify each deliverable under a standard OpenRISC environment. The entire demonstration framework that includes the FPGA implementations of the OpenRISC hardware and the compilation of the attacks before and after the mitigation is applied, will be a responsibility of each team. Moreover, the framework should allow the judges and organizers to be able to *provide new exploits on the fly*, for testing the developed mitigations on the day of the finals. **Extra credit** (up to 5%) will be given if the proposed mitigations can resist *previously unseen exploits*.

The evaluation of the finalists based on the above criteria will be the responsibility of a panel of **industry expert judges**. Teams are encouraged to start investigating the challenge as early as possible. During the day of the finals, each team should be able to answer the questions posed by the judges, in addition to *demonstrating live the correctness and effectiveness* of their mitigations on a DE0-nano FPGA. Furthermore, the finalists should prepare a **PowerPoint presentation** and a **poster** of their work, to present on the day of the finals, which complements the submitted **final report**. 
