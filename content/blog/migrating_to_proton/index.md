---
date: '2026-02-14T13:31:00+02:00'
title: Migrating to Proton
summary: "How to limit our dependency on US big tech companies."
author: ["Wilbert van Dolleweerd"]
draft: true
categories: ["blog"]
tags: ["Proton"]
---
# Preface

{{< callout >}}
  This is still very much a work in progress. Feel free to [contact me](mailto:wilbert@arentheym.com) if you have any remarks.
{{< /callout >}}

For years and years, I am using a [Google Workspace](https://workspace.google.com) account linked to my own domain. When Google started it around 2006 as 
*Google Apps for Your Domain*, I was one of the first to get an account. Google had a deal that meant that you could get a free account where you could 
create up to 50 users. Later on when Google started to make it a commercial service all those accounts got grandfathered in 
a free account for life. 

Quite the deal where I make extensive use of the following services:

<ul>
  <li>Gmail</li>
  <li>Google drive to share documents</li>
  <li>Google calendar</li>
  <li>Google docs as an Office replacement</li>
</ul>

However, nowadays I'm wondering if this is actually such a good deal.

First of all,

> "If you are not paying for it, you're not the customer; you're the product being sold."<br>
> — <cite> Andrew Lewis [^1]</cite>

Basically, all my data is being harvested and used by Google for their own purposes. When I was a bit younger (and maybe a bit more naive) I
tended not to see this as a big problem. But nowadays this does not sit well with me.

Second, we have seen large geopolital changes in the United States with the election and later re-election of Donald Trump. The U.S. is swiftly moving 
towards authoritarianism. Trump sees everything as a zero-sum, win-lose game. For him to win means that someone else has to lose. 
In his view, it is perfectly acceptable to use all means necessary to create that win.

A prime example is the [cancellation of the email address of the International Criminal Courts chief prosecutor.](https://nltimes.nl/2025/05/20/microsofts-icc-email-block-triggers-dutch-concerns-dependence-us-tech)
The International Criminal Court is being targeted by U.S. sanctions. And don't even get me started on the so-called ['The Hague Invasion Act'.](https://www.hrw.org/news/2002/08/03/us-hague-invasion-act-becomes-law)

This means that it is not out of the question that Europeans will face disruption of U.S. online services due to a political conflict with the U.S.

Finally, the U.S. has created the [CLOUD act](https://wire.com/en/blog/cloud-act-eu-data-sovereignty) in 2018. It a nutshell, it 
compels U.S.-based technology companies to provide data requested by law enforcement, regardless of whether that data is stored domestically or abroad. 

I think that Europe should get less dependent on U.S. big tech. And as a techie, I can start doing that myself. 


## Proton

Enter Proton, a Swiss based [email service](https://proton.me/mail) with a focus on privacy. Depending on what subscription you use, they also offer 
additional services such as a [calendar](https://proton.me/calendar), [VPN](https://protonvpn.com/), a [cloud drive](https://proton.me/drive), 
[Proton Docs](https://proton.me/drive/docs) and even a [password manager.](https://proton.me/pass) 

Proton Mail is [GDPR compliant.](https://proton.me/support/is-proton-mail-gdpr-compliant) Proton is subject to Swiss law, not foreign law. 
They cannot be forced to act on foreign legal requests directly; all requests must go through Swiss authorities.

Due to zero-access encryption, Proton cannot turn over the content of emails, files, or calendar events.

However, it is not a free for all. Proton can be compelled by the Swiss courts in case of a criminal investigation to 
log specific IP addresses or metadata for a particular user. But lets say that I put a lot of more faith in the Swiss
authorities versus the current U.S. based law enforcement agencies.

## The migration plan (for now)

This will take time, a lot of time. To get an idea of what I have to do, I came up with the following plan.

- [ ] Acquire a new personal domain (hosted by a suitable provider in Europe).
- [ ] Buy a Proton subscription (I still have to decide what fits my usecase).
- [ ] Link the new domain to the Proton subscription so Proton handles the mail for my domain.
- [ ] Create a new forward rule for mail still being received on my old domain to send it to my new mail address.
- [ ] Start using my new email address for my personal communication.
- [ ] Create a new reply rule for my old email to notify people that they should starting using the new email address.
- [ ] Migrate all my existing calendar events to the new calendar.
- [ ] Migrate all my existing Google Doc files to Proton Docs.
- [ ] Migrate my existing passwords from 1Password to the Proton provided password manager (I'm actually quite happy with 1Password which is Canadian based so I first want to evaluate the Proton password manager).
- [ ] Update password accounts that use my old email address to start using the new address.
- [ ] Let my old domain and mail co-exist with the new one for at least a year. This way, mail that is only sent once a year (my taxes) is still forwarded to me.
- [ ] Finally, kill my old domain and Google Workspace account.

For now, nothing of this list has been achieved. I plan to update this blog entry whenever I reach another (mini) milestone. I'll keep you posted!

[^1]: [Online comment made by Andrew Lewis and amplified by the resharing of Tim O'Reilly](https://x.com/andlewis/status/24380177712)



