# Day 2: Start Again

As with many things in my career, today was a lesson in something amazing, something disappointing, and lots of learning.

I am not at liberty to talk about what was amazing yet, but it's cool.

## The Disappointing Part

The disappointing part was that I expected to come in, jump onto our Proxmox cluster, fire up a VM from our gold image, and knock down the Packer refactor I was working on. Yeah, not so much.

There isn't a ton to talk about other than I learned **a LOT** about KVM and QEMU, Packer, and I relearned a lot of fundamentals around SSH, Linux commands, and debugging.

At the end of the day, I had come to a clear conclusion: I needed to talk to some of my people and validate my thoughts on virtualizing Packer build systems. I think the problems I’ve been beating my head against are tied to:

1. A nested virtualization bug.
2. Something awry in our gold image concerning KVM/QEMU.
3. That I am a total moron who somehow forgot that Packer has to run on big dedicated hardware (I refuse to believe this one… not that I am not a moron, but that this is not a solved pipeline issue involving nested virtualization).

So, I walked away today with a pounding headache, feeling like I had slid backward, even though I know I made forward progress.

## Moving Forward

I have a request in for either server hardware in the morning or, if that is not possible, a NUC from IT, which they told me they have if I need it. I also had a chat with ChatGPT right at the end of my day, where we discussed what a nested virtualization config would look like in Proxmox for Packer. But even it recommended I give up and just use hardware… but I refuse.

So, I’ll get in early in the morning and build a one-off VM and see if I can get Packer to build an image from it.

See you on Day 3: Start Again.
