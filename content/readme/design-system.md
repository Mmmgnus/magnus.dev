---
title: "Design system"
date: 2021-01-06T18:22:00+02:00
draft: true
---
# What is a design system?
A design system is a set of interconnected patterns and *share practices* coherently organized to achieve the purpose of digital products. Patterns are the repeating elements that we combine to create an interface: things like user flows, interactions, buttons, text fields, icons, colors, typography, microcopy. Practices are *how* we choose to create, capture, share and use those patterns, particularly when working in a team.

The *purpose* of the product shapes the design patterns it adopts.

The choice of design patterns is influenced by many factors. Some of them come from the *domain* the product belongs to, and from its core functionality: those are *functional patterns*. To use trading and market analysis software, for instance, you'd need to be accustomed to task bars, data fields, grids, charts and data visualization tools. For an online learning site, it could be articles, videos, discussion threads, progress indicators and interactive activities. An e-commerce site would most likely include a product display, list filters, shopping carts and a checkout.

The *ethos* of a product (or the brand, depending on your definition of a brand) also forms patterns which together shape how a product is perceived; *Perceptual patterns*. This like tone of voice, typography, color choices, iconography styles, spacing and layout, specific shapes, interactions, animations and sounds. Without perceptual patterns you wouldn't feel that much difference between products from within the same domain, which have similar functionality.

* Functional patterns (button, field ...)
* Perceptual patterns (the typography, color, shape, animation on the button)
* User flow patterns (such as completion of forms with errors and success messages)
* domain-oriented design pattern (like learning patterns for EdTech systems, and e-commerce patterns)
* Persuasive UX patterns

# Shared language
A shared language should be established before you think about interfaces, by discussing, vetting and documenting our language decisions. This idea could be applied to describing high-level concepts as well as the day-to-day language we use to talk about design decisions. Having a shared language would mean that we have the same approach to naming interface elements and defining design patterns, or that the same names are used in design files and front-end architecture. But that might not be enough. It's not only about developing a shared language — we need also to develop a *shared use of language*. It's not enough to have a shared understanding of the term *button*. People must also know why and how to use a button, in what contexts, and the purpose a button can serve. Designers and front-end developers should have this knowledge, but it helps if people from other disciplines (content, marketing, product management) have same idea too.

# Pattern libraries
A design system consists not only of pattens, but also *techniques* and *practices* for creating, capturing, sharing and evolving those patterns. A pattern library is a tool to collect, store and share your design patterns, along with the principles and guidelines for how to use them.

A pattern library doesn't guarantee a more cohesive and consistent design. It might help to correct small inconsistencies or make a codebase more robust, but a tool alone will have very little impact on the user experience.

A living pattern library is associated with better collaboration. Yet you might end up in a situation where only a small group of people uses it, or there might be too many disconnected patterns as a result of a lack of communication between the teams. When up-to-date, a pattern library is a glossary for the share language. But that doesn't mean there isn't still room for interpretation, It's the discussions *around* the interpretation which are often the key to a pattern library's success or failure.

Without a foundation of a coherent design system that integrates the patterns *and* practices, its impact will be limited. When a pattern library is used to support a solid design language foundation, it becomes a powerful design and collaboration tool. Until then, it's a collection of modules on a web page.

## Effective Design system
The effectiveness of a design system can be measured by how well its different parts work together to help achieve the purpose of the product. For example if the interface is confusing and people don't achieve their goal, then the design language is not effective. If it take too long to build a new area of the site because patterns have to be recreated from scratch every time, then we know our practices can be improved.

A design system can be considered effective when it combines cost-effectiveness in the design process, and efficiency and satisfaction of the user experience in relation to the product's purpose.

# Shared purpose
One of the most important qualities systems have is how they're connected and organised: subsystems are aggregated into larger systems, which in turn form part of something larger. No system exists in isolation. Your design system might have smaller subsystems within it: editorial rules to control the layout of the page; or it might include a method for scaling your logo responsively in a certain way. At the same time, it is also part of other larger systems: your product, your team, your company culture.

In highly effective systems, we see that subsystems are connected and aligned toward a share purpose: a design approach is mirrored in the front-end architecture; design pattern follow the guiding principles; the pattern language is applied consistently in design, code and the pattern library. We see harmony in the way those systems function: they workflow is more efficient, and the user experiences they generate feel more meaningful and coherent.

# Identifying problems
When there are gaps, it's also easy to see them. A fragmented design system leads to a fragmented user experience, full of conflicting messages. We want the user to sign up for our newsletter, but we also want them to check out our latest products. We want them to progress through the steps, but we also need to make sure they rate each recipe. "Sequence" is used to preview the steps in on area of the site; in another, it is suddenly a tabbed navigation. The interface is full of various shades of the same color and multiple version of the same button. The team's productivity is also affected: making the tiniest change is time-consuming and fiddly because of the confusing, tangled up code. Designers spend their time copying pixels and reinventing solutions to the same problems, instead of understanding and solving real user needs.

# How to start?
## Purpose and values
One of the first things we'd do is try to understand who our users are, their goals, needs and motivations. __Keep it simple__. Express the purpose in a single sentence. The purpose is the core of the product, and it should inform design and development decisions. The team should recognise that purpose and believe in it — It shouldn't feel forced.

Another important element is the *ethos* that captures the values and spirit we try to portray through the site.

## Design principles
To make sure the purpose of the product is expressed clearly through everything we do, we would need to establish a few grounding principles and values. They might be discussed informally or written as a manifesto — what's important is that the people involved in the creation of the product agree on those values and commit to them.

For example, everyone on the ten-minute cooking recipe site team understand the value of time. They are motivated by having a time limit on the recipes, and as a result they all strive to make interactions on the site short, simple, fast and smooth.
This principle will be expressed not only through design patterns, but the performance of the site , it tone of voice, and even how the team operates.

These principles might not necessarily be official or even written down. But having an agreement and awareness in the team on what they are is essential to keep everyone's effort and priorities in sync. It can also help with decision-making: from which feature to build first and which approach to use, to working out UX flows, or how buttons should look and the choice of typeface.

Having clarity on the purpose is paramount because all other decisions should be shaped by it, even if indirectly.

Depending on the company, the principles can be more focused on the brand, the team culture, or the design process. The principles at Pinterest are more brand-focused ("Lucid", "Animated", "Unbreakable"), whereas at the UK's Government Digital Service (GDS) they're directed more at how the team operates ("Do less," "Iterate. Then iterate again").

Larger companies might have separate sets of principles for the user experience, the brand and the design system. While this work for some, others can find that having multiple sets of guidelines can contribute to a design system's fragmentation.

Approaches to design principles are unique to every company and can take many forms. Principles can be overarching or more granular, temporary, or long-lasting. What matters is how effective they are at unifying design thinking and distributing creative direction in the team. *Design principles are share guidelines that capture the essence of what good design menas for the team, and advice on how to achieve it*; in other words , agreed criteria for what constitutes good design in your organisation and for your product.

### What effective guidelines have in common
#### 1. They're authentic and genuine
Principles like: "Simple. Useful. Enjoyable" isn't very helpful.   They are ubiquitous and we hear them everywhere. These qualities  can be interpreted in a variety of ways. What would make them more helpful is knowing exactly what those words mean to your team and your product. What does *innovative* entail? When is a design considered *useful*? Good design principles define qualities the can be interpreted in different ways, and ground them in the context of a specific product.

#### 2. They're practical and actionable
A principle should offer practical guidance on how to solve a design problem within the context of a specific product. Try thinking of them not as something what should merely sound good, but something that offers *actionable advice*. Imagine a new person joined your team and you've been asked to share five things that are most important when designing for your project.

If you tell them "We like things to be delightful here. Make it delightful!" It's probably not going to help them do they job. You'd need to define what delight means and share practical examples of what delight looks like in the context of your interface. 

But even the best-worded principles can still be interpreted in different ways. Nothing can make principle more practical that pairing it with a real-life example to show how it can be applied in practice.

#### 3. They have a point of view
Design is shaped by the choices we make. Should this page be more visually alive? Is it appropriate to be more playful or more serious here? Can we justify making this module more usable at the cost of making it less flexible?

By achieving some things we often have to say no to others. Good design principles help to work out priority and balance, even if they are conflicting factors to consider.

__Example__: "Clarity. Efficiency. Consistency. Beauty" It's emphasised that they must be applied in the priority order above. Beauty should not be promoted over efficiency or consistency, and clarity should always come first. Ranking the principles in this way communicates to the team what should make priority when making design decisions.

It can be useful to acknowledge the conflicting values and suggest how to find a balance. One of the early design principles at Medium was "Direction over Choice". This principle was often referred to while the team was designing the Medium editor. They purposely traded a variety of formatting options for guidance and direction to allow people to focus on writing.

Good principles don't try to be everything for everyone. They have a voice and actively encourage a designer to take a perspective.

"A design system should have guidelines for: perspective, point of view, extending creative direction to everyone that decides to build something with the design system. That stuff should be baked in. Otherwise, we all might as well use Material Design and call it a day." — Dan Mall, "Researching Design Systems"

#### 4. They're relatable and memorable
If no one can remember them, chances are they can be improved. To be memorable, the principles must be in constant use. They should be referred to in everyday conversations, included in presentations and design critiques, displayed where they can be seen.

It also helps not to have too many of them. Human memory is limited and remembering more than four things at a time can be hard. 3-5 is recommended.

The team at Spotify came up with the acronym TUNE (tone, usable, necessary, emotive) to make their design principles more memorable.

### Defining your principles
* Start with the purpose
* Find shared themes
* Focus on the right audience
* Test and evolve your principles

## Behaviors and functional patterns
We'd work out some of the key behaviors we want to encourage or enable in our users that will help them achieve their goals. For example:

* We want to enable people to achieve good results in under ten minutes. This means that we'll need to present the recipes in a few simple steps. The steps should be short, clear and focused. Perhaps we could have a timer on each step, to make sure we keep the ten-minute promise.

Naturally, the design details will change as we work on the site, but those key behaviors would remain the same. Those behaviors will inform the *core functional modules* and *interactions* of the site: ingredient thumbnails, recipe cards step sequence, timer.

## Aesthetics and perceptual patterns
Around the same time, we'd need to work out how we want to be perceived by someone using the site. Are we simple and down-to-earth or glamours and sophisticated? Are we serious or playful? What are the aesthetics that capture the personality and ethos we want to portray through the interface? 

## Shared language
Alongside this process we will be making language decisions by choosing to refer to concepts in certain ways. What is a "recipe"? What do we mean by "steps"? The words we choose will influence how the team thinks. And indirectly, they will shape the design.

# Functional patterns
Functional patterns are the tangible building blocks of the interface. Their purpose is to enable or encourage certain user behavior.

Functional patterns can be simple or they can combine to create more complex patterns.

As the product evolves, so do the patterns. We might start allowing our users to rate the recipes, and the rating display will become part of the recipe card. Or we might decide that the layout of the card can be improved, or that we need to introduce a compact version of the card. We test and iterate the patterns to try to make them work better to achieve their purpose; that is, encouraging the behaviors more effectively.

Articulating the purpose of the patterns early in the design process can help prevent duplication as the product grows.

When a pattern is not defined and shared in the team, you start recreating it to accomplish similar goals: another promotional module, another news feed, another set och sharing links, another dropdown. Before you know it, you end up with 30 different product displays and pop-over menus.

Patterns are the physical embodiment of the behaviors we're trying to encourage or enable though the interface. Their execution, content, interactions and presentation can change.
But the core behaviours they're designed to encourage remain relatively stable, as they stem from the purpose of your product and the idea of how it works. Being conscious of the purpose of your key patterns can help you understand how your system works and prevent it from fragmenting as it evolves.

__NOTE: Patterns != components (https://medium.com/eightshapes-llc/patterns-components-2ce778cbe4e8)__

## Defining Function patterns
Some techniques to define function patterns:

### Create a pattern map
To see how your patterns fit into a bigger picture, try to map some of your core modules to sections of a user journey. Thinks about what each section is for and what behaviors it's designed to encourage. Focus on the big picture: understand the parts of the system and how they work together. For FutureLearn, it was primarily focused on three areas: discovering content, learning on a course, and achieving a goal.

Keeping this map in my mind helped me to think in *families of patterns joined by a share purpose*, rather that individual pages.

### Conduct an interface inventory
The interface inventory process, described by Brad Frost, has become a popular way to start modularizing an interface. Print out the screens of your interface on paper or collect them in Keynote or Powerpoint. You then separate out various components either by cutting them out or pasting them in Keynote.

You end up with a collection of parts which can be grouped into categories: navigation, forms, tabs, buttons, lists and so on. Going through this process allows you to see duplicated patterns and identify problem areas that need attention.

This should be done regularly!

### View patterns as actions
To understand the purpose of a pattern, try to focusing on what it does rather than what you think it is. In other words, try to find an action that best describes the behavior a pattern is design for. Describing a pattern with a verb rather than a noun can help you to broaden potential use cases for a pattern and define its purpose more accurately.

Example: A simple module to promote an online course. If you try to describe what it is, you might refer to it as "Image header" or "Course banner". But by describing a pattern in this way, you  could be making it too specific to its presentation or content. You might end up limiting its use to a particular context. If you define it in terms of actions like "Promote a course", "Discover a course" and "Encourage people to join". By focusing the action, you connect pattern with behavior and keep it open for various use cases. What else can this pattern promote? An online discussion? A new event? We named the module "Billboard" to reflect its action-focused, promotional function.

### Draw a pattern's content structure
To get a shared understanding of how a pattern works, draw its structure: the core types of content a module needs to be effective.

Draw it like a sketch or wireframe. This is a sketch focused specifically on the content structure of a module, and the hierarchy and grouping of the elements.

Once you have a shared understanding of a pattern's structure, it's easier to make sure that the way the module is designed is reflected in the markup. A designer can work on the visual explorations, while a developer can start putting together a prototype. Designer understand how much they can push a pattern visually before it becomes something different. Developers know the reasons for the design choices and don't get unexpected designs thrown to them over the wall.

Breaking down similar modules and drawing their structures allows us to see if they could be unified into one pattern, and to design that pattern in a way that works in all use cases.

### Place patterns on a scale
Try placing smilier patterns on a scale, in relation to one another. For example, there could be a few promotional patterns in your system, with varying degrees of intensity.

Placing pattern on a scale help make sure they're used appropriately and don't compete for attention across the system. It also helps prevent modules being recreated needlessly, since you can see when you already have a module at the same "volume".

### Treat content as a hypothesis

# Perceptual Patterns
Examples of perceptual patterns in digital products includes:
- Tone of voice 
- Typography
- Color palette
- Layout
- Illustrations and iconography style
- Shapes and textures
- Spacing
- Imagery
- Interactions or animations

And all the specific ways in which those elements are combined and used in an interface.

( Hoppar över denna bit tills vidare )

# Shared Language












