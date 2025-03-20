# Day 8: Start Again

It has been a few days since I have updated. First off, lots of work and learning going on. Second, the first week of travel bookended by family travel kind of wiped out my spare time. But with that, let's catch up.

## Packer  
First off, years ago I heard how horrible HashiCorp’s documentation was, and it may have been, but now I was super impressed with how clean the docs were and how quickly I was able to grok what they were saying as I dove through it all.  

There are still some oddities in Packer, like the directory structure order calls for variable files (I think I want to call my own VAR files), but it works when you understand it.

## MAAS  
It is the exact opposite doc-wise. Their docs are trash. The explanation of their commands is trash. Their logging and errors, at least on the build system side, are trash.  

They deprecated the `maas-cli`, so if you want CLI commands on, say, a build server, you need to do a full MAAS install on your build host and just not initialize it. **Dumb.**  

That said, once you get past the janky docs and no idea why stuff doesn’t work, it does its core job of **image distribution to HW and VMs (Proxmox for me)** really well. So at least for now, work through the pain.

## Proxmox  
Not much new to say here—I already love this platform. It works, it's getting better, and the cluster I am working on now is way better than my home lab one, so **bonus**.

## Pipelines  
I am starting to dig into **Jenkins**, but I can’t really say much because I don’t know much, other than the build language is called **Groovy**, which is, well, groovy.  

I have listened to my team and peers talk about **pipelines, mocks, and testing** and been pretty intimidated till now. While by no means have I arrived, I just spent the last two weeks building a **pipeline**...  

It was all **manual**. Every piece of the puzzle has to work, and you need to make it so it is reproducible. Jenkins and other tooling are the glue that ties all the pieces together. So while I don’t have an **automated** pipeline, I have a **fully reproducible manual "Pipeline"**, and now we **automate**.  

Mike Bushong has famously drilled into people:  
![The Path to Automated Networks](https://i0.wp.com/staticnat.com/wp-content/uploads/2015/10/automated-networking.png)  

I like to refer to all this as:  
**Crawl, Walk, Run, Fly, JetPlanes, Rockets, Spaceships.**  

I am about ready to start **running**.

## Key Takeaways  
The key takeaway is that **I was not as far behind as I was afraid I was**.  

I still Google a lot, and **GPT is like the best DevOps buddy I have ever met**. Using it to take a **Packer-MAAS (public repo) config** that I don’t understand and ask GPT to break it down line by line and explain it has helped me come up to speed **so much faster** than I would have otherwise.  

I think lots of folks are like, *"let it do all my work for me..."* but that’s the wrong approach.  

### The right approach:  
1. **Use it as a learning tool.**  
2. **Use it where you would use Google.** You will often get back the right answer on your first go and not have to dig through ads and random blog posts.  
3. **Use it to template work.**  
   - Gather the data and knowledge you need to do the work.  
   - Spend 10 to 45 minutes dumping that into GPT (**leave out security, names, private data, etc.**).  
   - Ask GPT for a **template** for that task—whether it's a quote to a client or a shell script.  
   - Request comments on every line and explanations for why it did what it did.  

This process will radically **reduce your typing time** and let you focus on **troubleshooting, debugging, and other work**. Plus, it ties right back into **learning**.


