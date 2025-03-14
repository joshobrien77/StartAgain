# Day 3: Start Again

So, I rolled in this morning with this week starting to take a toll. It’s not like I haven’t been working 40+ hour weeks for the past 8 months or so, but honestly, that work was taking about 20% of my capacity. Prior to that, the stress of being unemployed and apparently unemployable was taking its own type of toll.

But last night, I got back to the hotel, worked out (part of my plan to survive 100% travel for the foreseeable future), and then just crashed. My Garmin watch says I got more recovery than I’ve had in months, but today did not feel that way.

So, that out of the way, I rolled in today having to talk to one of my people about my understanding of Packer and, in general, build systems and pipelines. Barry is always there for me to tell me I’m dumb, or thankfully in this case, that I’m on the right track. We also just talked about life and caught up, but that's another thing.

What he helped me validate is that the whole Packer build system on nested virtualization is a solved issue, and most of the use cases are around running pipelines that use a cloud VM as an ephemeral build server. 

## The Day's Focus

When I logged in today, I focused on getting a new Ubuntu 22.04 (considered the most stable Packer platform from what I’ve been reading) VM up and running. I only focused on KVM and QEMU and the tests I needed to validate that they worked. Honestly, that part was just too simple. From there, I took a snapshot of the VM to undo whatever chaos I was about to initiate.

Yesterday, I threw together a quick and dirty shell script to install and configure all the build requirements for our Packer images. So, I tossed that on the new system and ran it... and KVM and QEMU still worked. Right off the bat, it felt good to make progress and know that the last two days weren’t a waste. 

Then it was on to cloning the repo, making the local changes that I had mocked up yesterday, and... QEMU crashes. Well, shit.

## Troubleshooting

To be fair, this wasn’t a big deal. About 3 minutes of tailing logs and reading errors, and I realized that our Packer image called for 64GB of RAM, but our VM had 16. About 10 minutes of Googling and talking to my manager about the implications of moving the Packer QEMU build requirement to 8GB, and we were back on track. The Packer build started, downloaded the base image, and booted... then hung indefinitely at "waiting for SSH to start."

## Core Purpose of the Packer Refactor

At this point, I should state that the core purpose of the Packer refactor exercise I am undertaking is twofold (threefold, if I’m honest with myself):

1. It’s to get me familiar with some of the nuances of building hardware in the AI world.
2. To refactor some complexity out of the image, such as private SSH keys being embedded, as we are moving to post-image build solutions for automation and customization. It’s also about making the image build process as simple and self-contained as possible so it can be managed better as we scale. (It is already a complex image for reasons.)
3. The to-be-honest-with-myself part is for the team to evaluate how capable I really am. I was honest that I’ve been a pointy-haired boss for the better part of 9 years, and while I understand the concepts, I’m pretty rusty when it comes to configuring on the keyboard.

## Lessons Learned

Okay, with all that said, I spent way too much time beating my head against the wall trying to figure out how to get SSH to communicate right with the Packer build. But I did learn a few things:

1. I learned how Packer HCL2 flows through variables. I may be exaggerating, but I don’t think so when I say that you can have 500+ `VARx.pkr.hcl` files, and the primary `pkr.hcl` config will parse them in file system order, as if you did an `ls -l`. This is a PITA when you have at least 4 of them, plus variables in the `main.pkr.hcl`, and about 50 scripts that are called when you’re trying to debug something you didn’t write.

In the end, I took another approach and pulled the Packer:MAAS official repo for Ubuntu builds. When I ran a build against that, it worked right out of the gate. Now, I know my build environment is not the issue. I know my core understanding of Packer is sound. And now I have a config that is the base of our own config to work backward from.

## Wrap-Up

With that, I talked to the boss about SLURM, our network design for our next non-blocking AI fabric, and how QoS will apply or not apply on a non-blocking, credit-based DMA fabric. Then I called it a day.

In the morning, I fly by to Wyoming and pick up where today left off remotely until Monday night when I fly back out. See you on Day 4: Start Again.
