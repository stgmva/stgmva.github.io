---
layout: page
title: "Everything Is On Fire"
subheadline: "Fixing A Broken Mailserver"
teaser: ""
author: Morgan
categories:
  - tech
image:
    title: http://imgur.com/8HYmOEt.jpg
    homepage: http://imgur.com/8HYmOEt.jpg
    thumb: http://imgur.com/8HYmOEt.jpg
    caption:
    caption_url:
breadcrumb: true
---

### Some Background

For two years now I've been managing my own email server built on [Mailinabox](https://mailinabox.email/). I first built out the box in the wake of the Snowden revelations. It occurred to me that while Gmail does offer state-of-the-art encryption on their data at rest, it was entirely possible that Google would be subject to [NSLs](https://en.wikipedia.org/wiki/National_security_letter) and definitely even mass data collection.

Of course, email never really was designed for security, and unless you're using PGP on every message it's possible for **anyone** listening on the wire to intercept messages as they come and go. Despite this, I felt it was best to decentralize myself - and thus remove as much of my digital identity from Google as possible.

If one's threat model is a nation state actor there is no perfect defense against that, but it is possible to minimize the attack surface or at least make it a bit more difficult to be attacked or surveilled by being removed from as many centralized systems as possible. Thus, Mailinabox.

### The First Cracks Appear

Everything was working perfectly until a few months ago - the build of my box predated Mailinbox's [LetsEncrypt](https://letsencrypt.org/) integration, so I used an SSL cert issued by Comodo, and later WoSign. It was time to get myself moved off those options and on to LetsEncrypt (and in the wake of news of misdeeds by both Comodo and [WoSign](https://blog.mozilla.org/security/2016/10/24/distrusting-new-wosign-and-startcom-certificates/) that was a good decision), however my box was being stubborn. Even if I SFTP'd into the machine and removed the existing certs, I couldn't get any new certs to apply.

Digging around the [Mailinabox support forums](https://discourse.mailinabox.email/), I found the proper script to invoke:

```
./management/ssl_certificates.py --force
```

After that the LetsEncrypt cert was successfully applied, but weird stuff started happening to the server. Where once the status pages would show me all was well, I started getting failures instead. Despite the Status Checks page failing, the box was fully functional.

> I let the box continue to run until today - when it finally broke on me.

Once a LetsEncrypt certificate is issued, Mailinabox is _supposed_ to automatically renew the cert every 90 days. Today, my original LetsEncrypt cert expired. First warning was my phone telling me over and over again that it couldn't connect to the mail server.

### Everything Is On Fire

I was unable to get new emails on my phone, and my desktop machine was making similar complaints.

First step was to go out to the box's admin page in an attempt to issue a new cert from the TLS console. In the interest of security, Mailinabox deployments enforce [HTTP Strict Transport Security](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security) (HSTS), which enforces SSL after you visit an encrypted site for the first time. HSTS is there to prevent a user from being exposed to [downgrade attacks](https://en.wikipedia.org/wiki/Downgrade_attack). In this case, with an expired certificate it prevented me from initiating a web connection with the site at all.

Next step was to SSH into the server and attempt the ssl_certificates.py script again - foiled! I got an error and it wouldn't run. The server was telling me it had issues with OpenSSL - this was likely the result of my messing around with the server months earlier trying to force it to get a LetsEncrypt manually.

I _hoped_ that an update would fix it, but unfortunately it did not. Just attempting to run the update to Mailinabox v0.21C didn't work. Again I was encountering errors regarging OpenSSL.

> Time to build a new box

At this point I figured the only resolution was to build out a new box and attempt to migrate/recover all my data. Fortunately there is a guide on how to do that [here.](https://mailinabox.email/maintenance.html#moving-boxes)

First I ran a manual backup.

```
cd mailinabox
sudo management/backup.py
```

By default Mailinabox does daily backups, but it was best to have a totally up-to-date backup. I also went into Mail, Contacts, and Calendar on my local machine and exported everything I had, just in case I was unable to restore from the backup on to the new box.

Then it was time to get the backup off the machine, so I fired up FileZilla and SFTP'd into the box. Per the Mailinabox instructions it's neccessary to only grab _/home/user-data/backup/secret_key.txt_ and _/home/user-data/backup/encrypted_, but I opted to backup the entire _/user-data/_ folder.

![](http://imgur.com/td2P77x.jpg)

I then got started spinning up a new server with [DigitalOcean](https://www.digitalocean.com/). It was necessary to rename my old droplet to _box.missourivalleyambulance.com_ to _box.missourivalleyambulance.com.old_. I was able to get the new box up and running quickly, including the Mailinabox install. The setup for this is actually down to a single curl command.

```
curl -s https://mailinabox.email/setup.sh | sudo bash
```

After the box was set up and fully configured, I went over to GoDaddy to set up the new IP address. One thing that's brilliant about Mailinabox is that it hosts its DNS - so the only thing needed on the registrar's end are the nameserver addresses.

Then it was time to SFTP into the new box, upload the _/user-data/backup/encrypted/_ folder, rename the existing _/user-data/_ folder to _/user-data-old/_ and run the restore command.

```
cd mailinabox/home
export PASSPHRASE=$(cat secret_key.txt)
sudo -E duplicity restore file:///home/backups/encrypted /home/user-data/
```

A quick server reboot, and the box was back to its original configuration.

### The Fire Extinguished

The timing for this failure was quite good actually. My domain was up for renewal with GoDaddy, expiring on 2/10. Since I was doing all this work with rebuilding the server today, I took the time go get my domain transferred over to [Hover.](https://www.hover.com/) I'm just a few hours into being a Hover customer, but so far I'm pretty impressed. Their site offers step-by-step guides for how to get a domain released from GoDaddy and prepped for transfer to Hover. From the time I initiated the transfer until it was complete was just under an hour. Hover even automatically copied over all the nameserver glue records, so there was no fighting with those trying to get DNS working correctly with the mailserver.

It's funny - when I first got this mail server up and running 2 years ago it took me ages to get everything configured correctly. The whole process took me weeks. The largest barrier was getting the old Comodo SSL cert & DNS up and running correctly as I had no idea what I was doing. Today I experienced an unexpected failure of my mailserver, requiring a total rebuild. I was able to get it all resolved within a few hours. The largest parts of the rebuild today was just waiting for all _/user-data/_ directory information to transfer from one server to another, and waiting for DNS records to propagate after moving the server to a new IP address.

---
<p align="right">Typed on ErgoDox Test Board</p
