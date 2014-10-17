---
layout: default
title: SourceForge Blog
---

# SourceForge Blog

` I noticed some recent activity in your Avogadro project. We're looking for projects to highlight in our Community Blog (https://sourceforge.net/community/blog/). Want to answer a few questions about your software so we can write about your project?`

` First, what's your name, and where are you from?`

I'm Geoff Hutchison, an assistant professor in chemistry at the University of Pittsburgh.

` Can you briefly explain what a molecular editor is and what it does? How does Avogadro differ from the other dozen or more molecular editors out there? What makes it unique?`

Avogadro allows you to interactively build and edit molecular models on your screen. That is, you can see in 3D, the shape and structure of chemistry. Want a protein? Want to see a gold surface? Want to build the next great cancer treatment?

Well, I had to laugh about the "dozen or more molecular editors," because that's really not true. There are probably hundreds of molecular viewer programs, but very few which let you build new molecules or edit existing chemical data. The vast majority of those are commercial -- some even cost upwards of $10,000 per seat.

What really makes Avogadro unique is that we've tried to make the most intuitive program for building chemical systems -- molecules, proteins, crystals, nanotubes, whatever. And we've made everything modular -- almost everything is a plugin. So you can easily add or change functionality.

We want Avogadro to be flexible and scale from educational use to advanced research.

` What motivated you to create the software? How long have you been working on it? What tools did you use to built the application, and why did you choose those particular tools?`

I was motivated because I didn't really see any truly great tools to create molecular models. For my research, it's the critical first step of doing computational chemistry simulations -- you need the molecular data!

While some early planning and minor coding started in early 2006, Donald Curtis and myself wiped the slate clean and really began "for real" at the start of 2007. The project got a big help with a Google Summer of Code project from Marcus Hanwell, who has now become a lead developer.

For tools, we've heavily leveraged C++ and the Qt user interface toolkit. This allows us to have releases on Windows, Mac, and Linux simultaneously. Qt has also really helped out with multi-threading our interface -- most of the chemistry simulation occurs in the background on multi-core machines, which makes the interface much smoother.

The chemistry side is largely handled by the Open Babel toolkit, since it handles scores of chemistry file formats and data types. (I'm also the lead developer for Open Babel, so it was a natural choice!

` Why did you decide to put it up on SourceForge.net? How have you let people know about it? Do you know about any specific cases where people are using it for something interesting?`

SourceForge.net was the natural choice -- many people come here to find open source projects and it has helped us host much of the project administration functions. SourceForge has also helped us "get out the word," with a Community Choice Award nomination. We try to publicize Avogadro at chemistry conferences, chemical mailing lists, the "chemical blogspace," and through word of mouth. Marcus has also really helped to get out the word through the Qt and KDE communities. It's been adopted by the KDE-Edu project for chemistry visualization.

Interesting uses? Avogadro has gained use for a lot of university teaching. I've seen website referrals from Thailand, and we have over a dozen useful language translations.

Scientifically, I know it's gaining use. We will shortly have our first journal cover, and there's a blog posting about using Avogadro to visualize molecular databases for drug leads.

` Is there any especially useful capability users might overlook? What's a cool tip for people who use the software?`

One of the coolest features, in my mind, is the "auto-optimization" tool. This lets you optimize the geometry of a molecule as you edit or manipulate it. Think of it as running an interactive chemistry simulation. Pull an atom, and the molecule will respond. Drag a molecule around, and you can see others move in response. It's like a little video game.

Cool tips? If you're drawing a molecule, you can switch elements from carbon to nitrogen by just typing the atom symbol (i.e., "n" for nitrogen). You can also move things around with the arrow keys. I hardly have to use the mouse.

` What's coming up in future versions? How frequently do you expect to make releases? Do you need help on the project? With what? And what's the best way for people who want to help to get in touch?`

This Friday, October 23rd, we're releasing Avogadro 1.0, in honor of its namesake. Avogadro's number is 6.02x10^23, so chemists often celebrate Oct. 23rd as "Mole Day". <http://en.wikipedia.org/wiki/Mole_Day>

We expect fairly regular bug-fix releases, and anticipate a major feature release (e.g., version 1.2) every year. Our hope is that the Python scripting interface and plugin framework will also make it easy for people to add features and extend Avogadro between releases.

We'd love to have more contributors! Right now, there are probably 15-20 people, and the more, the better. We could use help with documentation and tutorials (particularly for education), translations, OpenGL rendering optimization, GLSL shaders... We've got a list on our wiki actually: "How you can help" <http://avogadro.openmolecules.net/wiki/Get_Involved>

Of course people can always contact us on the avogadro-devel @ lists.sourceforge.net mailing list.

` Finally, is there anything you'd like our SourceForge.net developers to know, that we could do to improve the site?`

It would be great if you could connect tracker items to Git or SVN commits.

