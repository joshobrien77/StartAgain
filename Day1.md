# Day 1: Starting My New Consulting Gig

Today, March 11, 2025, I showed up at my new consulting gig. I could say a lot about how I got here, but that's not the point of these posts.

First off, today I woke up in Las Vegas, where I will be spending the majority of my next three months. After that, who knows? But I am going to make the most of these three months.

## Onboarding

9 AM started with onboarding with this client. They are an AI infrastructure company with big plans and a unique value proposition. Onboarding was great, but nothing too deep to dive into here. Lots of interesting things from the IT management side to talk about later, maybe.

Around 11 AM, my manager gave me my first tasks:

1. Generate your keys.
2. Get logged into GitHub.
3. Upload your public key into the repo.
4. Get into the Infra Repository on GitHub, find the root Packer image, and start understanding it.

### The Packer Challenge

So, here’s the deal:

1. I haven’t deployed a Packer image or written config for it in over 8 years.
2. I now know exactly what my team at Sauce Labs felt like on their first day when we were like, "Deploy your own creds in Ansible, get familiar with the platform for the next 5 days, and you're on call starting Friday."

I still think that approach is 100% the right way to deal with mid/senior-tier staff, but HOLY SHIT, it's a lot to come in cold to a new environment with just your experience and dive right in!

### Startup Life

I should mention, this is a startup, and a lot of what I’ll be doing is helping them build out the systems that will enable them to scale from hundreds to thousands of systems quickly.

For that reason, a lot of today was asking questions like, “Where are your build servers for Packer?” only to be met with, “Build server?” Or, “What do you use as your virtual environment on OSX?” (They issued me an amazing brand new Apple M3 Max.) To be told by my manager and peer, "We’re on x86 systems running Linux..." 

So, I reached into my 8 years of OSX experience from Sauce Labs and got some of my tooling going, including iTerm2, VSCode, Canonical Multipass, and various other quality-of-life tools installed. Then it was off to the races.

### Cloning the Repo and Getting Started

I cloned the repo for the Infra Packer tools, spun up an Ubuntu 20.04 VM, did a quick and dirty manual install of the build tools required for Packer, remembered how to clone private repos in Linux, and got my keys pushed to all the needed places. All of this after my manager said, “This should take you about 4 hours to restructure the Packer config with external requirements, such as private keys, into an atomic standalone build that can be run from anywhere with a clone and build command.”

So, he was right about most of it. I stayed at my desk until almost 7 PM tonight, determined to walk away with a refreshed knowledge of Packer and a big chunk of the requirements resolved. And you know what? It almost worked.

After hours of refactoring my pre- and post-SSH scripts, re-running `packer validate` about 1000 times, linting, Googling, and GPTing my way through the solution... the image started to build!!! Then it failed because Multipass does not support nested QEMU virtualization on Mac...

### Wrapping Up Day 1

So, with that, I wrapped up the first day. I got a beer, some wings, came back to the hotel, worked out for 30 minutes, and then wrote this. In 10 hours or less, I'll be back at it. On Day 2, we will build a build server on Proxmox, test the Packer config, and maybe start writing a short pipeline.

This is going to be a wild and amazing 90 days.
