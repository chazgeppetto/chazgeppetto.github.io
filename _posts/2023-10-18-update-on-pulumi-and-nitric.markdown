---
layout: post
author: Josh
date: 2023-10-18
title: Update on Pulumi and Nitric
---

Hiya readers! Josh here - I wanted to share a quick update on our latest.

The most recent [post from Chaz](/2023/10/05/streamlining-cloud-development-with-pulumi-and-nitric/) discussed our introduction to some very promising platforms for cloud development. [Pulumi](https://www.pulumi.com/) manages infrastructure-as-code, and [Nitric](https://nitric.io/) provides an abstraction layer that lets us focus on domain logic and business problems instead of studying the idiosyncracies of various cloud providers. It's really looking like a powerful 1-2 punch!

## Getting Started with Nitric

Chaz alluded to some bumps in the road, which evidently were largely the result of our local dev environment. After floundering a bit on my own, I finally reached out to the [Nitric Discord community](https://discord.com/channels/955259353043173427/955259353043173430), and these folks are awesome! If, like me, you're taking Nitric for a test spin, definitely drop in to say hello, and don't hesitate to ask for help. There are some extremely responsive and helpful community members ready and willing to share their expertise.

## TL;DR Solutions

A few of the problems we solved:

### Error initializing Docker client: protocol not available

This looks to have been unique to Docker on Windows, and required a bit of bespoke logic in the Nitric providers code. Dave and company were able to quickly triage and resolve with an RC that has since been merged to the `develop` branch. If you've got the latest version of Nitric, you likely won't run into this.

### Unrecognized resource type (Check): docker:index/image:Image

Another corner case, related to Pulumi Docker plugin version. A quick version bump via `pulumi plugin install resource docker 4.4.3` and we were back in business.

### AccessDeniedException on AWS

I ran into a handful of access issues along the way, all of which I was able to resolve by updating permissions on the AWS IAM principal I had set up for Pulumi. It wasn't super clear to me what Pulumi needed at the outset, so I chipped away until I successfully stood up a "Hello World" AWS Lamda Function. It's entrely possible I missed a critical section of Getting Started docs, but all's well that ends well.

## Onward!

Having cleared the hurdles to getting a basic cloud deployment out the door, Chaz and I can regroup and focus on building some cool new POCs and maybe even a full-fledged product or two. Stay tuned! 😉

Cheers,
Josh
