---
layout: post
title: 'Code Comments: The Good, the Bad, and the Ugly'
author: Vladas Maier
tags: comments
---

Code comments, those tiny snippets of text embedded in the vast area of code, are both a blessing and a curse for developers. They serve as a guide, translator, and sometimes spoiler of your codebase. In this post, we embark on an expedition to explore the depths of code comments and uncover the good, the bad, and the ugly aspects of these annotations. Buckle up guys.

P.S. We have a special guest today - [DALL-E](https://openai.com/blog/dall-e/).

<a href="https://labs.openai.com/s/3oqvESK4MAujH8rgD95jNqZp"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-3oqvESK4MAujH8rgD95jNqZp/image.webp"></a>

### *The Good*

#### Clarity & Understanding

Think of code comments as glowing torches in the labyrinth of code. A well-placed comment can shed light on complex algorithms, nested loops, or unclear functions, making them accessible to both seasoned developers and newjoiners. These comments become invaluable guides that shorten the learning curve and make code maintenance easier.

<a href="https://labs.openai.com/s/mqwtZYXKtSXCiJzZwqR5YBUU"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-mqwtZYXKtSXCiJzZwqR5YBUU/image.webp"></a>

#### Documentation

Now think of code comments as historical scrolls that record the epic history of your codebase. They detail the “why", “what” and “how” behind [LOC](https://en.wikipedia.org/wiki/Source_lines_of_code), providing a map for navigating the complex terrain of large and complicated projects. Whether you're dealing with legacy code or collaborating with a distributed team, these comments become vital for knowledge sharing and maintaining consistency in your codebase.

<a href="https://labs.openai.com/s/308B8NVbDcrZOMUpOZ64M2fD"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-308B8NVbDcrZOMUpOZ64M2fD/image.webp"></a>

I went through a debugging hell once because I simply did not understand why the code is not working but everything seemed fine (as always). After hours of debugging, I found a comment: *"Do not use hyphens in the application ID"*. I felt mad, relieved and happy at the same time. Mad because I wasted hours of debugging and the solution did not even affect the code so I was right that the code was fine ;) Relieved because I finally found the solution. Happy because a fellow developer who probably also wasted hours of debugging as well left this comment for future developers. I think this is a good example of how comments can help you.

#### TODOs

TODO comments are your virtual sticky notes that remind you of tasks waiting to be done. They serve as a marker for future improvements, feature enhancements or bug fixes. Without it, it's like walking through a house with peeling paint and a leaking roof without thinking about making repairs. TODOs are your friendly reminders that keep the codebase tidy and organized.

<a href="https://labs.openai.com/s/ThlcZYCZ0zRbt2M5Ti2FtjoQ"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-ThlcZYCZ0zRbt2M5Ti2FtjoQ/image.webp"></a>

You might be wondering what this guy is talking about. TODOs are the worst thing you can have in the codebase as developers tend to ignore them and these comments end up staying in the codebase forever.

You bring up a valid point. While TODOs can be valuable in theory, their effectiveness in practice can vary widely. In some cases, TODOs may indeed be ignored or forgotten, and they can accumulate in the codebase, leading to clutter and reduced code quality. Here are some additional insights to consider:

- **Overuse of TODOs**
  
  Sometimes, developers tend to use TODOs liberally for various minor tasks or code improvements. Over time, this can lead to a backlog of TODOs that never get addressed, resulting in a less effective practice.

- **Lack of Follow-Up Actions**

  TODOs are only beneficial if there is a process in place to ensure they are regularly reviewed and addressed. If developers and teams do not actively manage their TODOs, they can become a source of neglect.

- **Task Management Tools**

  In some cases, using dedicated task management tools or project management software might be more effective for tracking and prioritizing tasks, as they offer better accountability and visibility into the progress of tasks.

- **Documentation & Collaboration**

  Encouraging a culture of thorough documentation and open communication can be a more effective way to address improvements and pending tasks. This approach may involve using project management or issue tracking tools where tasks are discussed, assigned, and tracked collaboratively.

In summary, while TODOs can be a helpful way to flag areas for improvement or pending tasks, they are most effective when incorporated into a broader process of task management and follow-up. It's essential for development teams to establish best practices for handling TODOs to ensure they are not ignored and left to accumulate in the codebase.

So I will still leave TODOs in *"The Good"* part, because I think that TODOs are a good thing if used properly.


### *The Bad*

#### Outdated & Irrelevant Comments

Comments can quickly become outdated as the code evolves. These outdated comments can mislead developers and cause confusion. It is important to regularly update or remove such comments. In the ever-evolving landscape of software development, change is the only constant. As your codebase changes, old comments can remain like relics from a bygone era. These once-helpful notes can become misleading, misleading developers and plunging them into a maze of confusion, wasting time and effort to understand the connection between the code and the comments.

Keeping comments up to date is a responsibility akin to tending a garden - neglect them and they become overgrown and unmanageable. But how do you ensure these outdated comments stay relevant?

<a href="https://labs.openai.com/s/ketMSEx16n6Ok2h9ZRuYzTOf"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-ketMSEx16n6Ok2h9ZRuYzTOf/image.webp"></a>

One approach is to conduct regular code reviews and treat comments as seriously as the code. During these reviews, you can search your codebase, identify outdated comments, and either update them with the latest information or properly remove them. This approach not only keeps your codebase organized, but also promotes respect for the importance of accurate and up-to-date documentation.

Another technique is to use automated tools (linters) that can flag outdated comments for you.


#### Redundancy

Some developers tend to write comments that simply duplicate the functionality of the code. Redundant comments clutter the code base without adding value and should be avoided.

Redundant comments echo through your codebase like echoes in a canyon, adding nothing but noise. They are clearly reminiscent of the old saying “less is more”. So why do developers fall into the trap of over-explaining their code?

<a href="https://labs.openai.com/s/ertdb4IllmsRFoyqfzzbGUuc"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-ertdb4IllmsRFoyqfzzbGUuc/image.webp"></a>

One reason is the fear of darkness. In their quest for clarity, developers may believe it is necessary to repeat the purpose of the code in plain English. However, it is important to remember that the code should be reasonably self-explanatory. If you find yourself writing comments that reflect the functionality of the code, stop and think again.

A more effective approach is to focus on the “why” rather than the “what”. Instead of repeating what the code does, explain why it does it. Share insights into design decisions, possible side effects, or the reasons for a particular approach. This not only eliminates redundancy, but also increases the value of your comments and improves the reader's understanding of the purpose of your code.

Remember that in the world of clean code, less verbosity often leads to more elegance and readability.

#### Overcommenting

Overcommenting code can be counterproductive. Excessive comments can make the code harder to read and maintain. It's important to find a balance between clarity and detail. The line between informative comments and an overwhelming flood of comments is thinner than you think. The appeal of providing absolute clarity can lead some developers into the abyss of exaggerated commentary.

When you're dealing with code that seems to be annotated to the last breath, you'll notice that every line of code has a paragraph-long explanation attached to it. While the intention is noble – to make the code crystal clear – the result can be quite the opposite.

Imagine trying to enjoy a meal while your dining partner explains the origins, history and culinary intricacies of each dish in great detail. The experience transforms from a delicious meal into an academic lecture. Likewise, overcommented code can turn a simple reading task into a laborious undertaking.

<a href="https://labs.openai.com/s/mp6E4IO91C05tA8ISxgGgGAK"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-mp6E4IO91C05tA8ISxgGgGAK/image.webp"></a>

To find the right balance, you should adopt the principle of minimalism. Keep comments for the aspects that really need clarification. Focus on explaining complex algorithms, unconventional design decisions, and potential pitfalls. Keep your comments concise and ensure that they improve rather than detract from the readability of the code. Essentially, your comments should serve as subtle guides rather than overwhelming companions. The trick is to let the code speak for itself and provide valuable insights only where necessary.

### *The Ugly*

#### Unused Comments

Unused comments can haunt your codebase like neglected relics of the past. They serve no purpose and only clutter the source code. Although they may not directly affect the functionality of your code, they reduce its readability and maintainability.

<a href="https://labs.openai.com/s/ScLl5eUYdcvia0pyR2sAjOe1"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-ScLl5eUYdcvia0pyR2sAjOe1/image.webp"></a>

As a diligent developer, it's important to regularly review your codebase and remove those ghosts of past comments. Unused comments can result from outdated code, changing requirements, or the natural evolution of your project. Neglecting them can result in a cluttered codebase and cause confusion, especially among new team members trying to understand your code. To eliminate these ghosts from your code, adopt a proactive comment cleanup policy during regular code reviews. It's a straightforward but effective approach that ensures your codebase remains clean, uncluttered, and accessible to everyone who interacts with it.

#### Inappropriate Language

In the realm of coding, comments should maintain a professional and respectful tone. Using inappropriate language or adopting an unprofessional attitude can cast a shadow over your development environment. Such comments can create a hostile work atmosphere, lead to conflicts within the development team, and tarnish the overall collaboration. Ensuring that your comments uphold a respectful and constructive tone is vital for maintaining a positive and productive coding environment.

<a href="https://labs.openai.com/s/jtH8DRJNqzfXaSAdiXZf8BFS"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-jtH8DRJNqzfXaSAdiXZf8BFS/image.webp"></a>

I'm familiar with the saying, *"Criticize the code, not the developer"* but we developers all know how sensitive we can be when it comes to the code we've written.

#### Incomplete or Incoherent Comments

Incomplete or incoherent comments can be worse than having no comments at all. They create confusion and frustration. Always aim for clear, complete, and concise comments. One [code snippet](https://github.com/vlmaier/enigma/blob/main/app/src/main/java/de/yapp/enigma_test/Chat.java#L218) from a project I was part of in the past:

~~~ java
public void sendGUI(ChatItemArrayAdapter adapter, Message msg) {
    this.getMessages().add(msg);
    adapter.add(msg);
    // TODO:
}
~~~

You immediately ask yourself: "To do what exactly?" You see incomplete comments are worse than having no comments at all.

#### Lack of Updates

Ignoring comments that indicate issues or improvement opportunities can lead to serious technical debt and negatively impact the code's quality and maintainability.

You know those comments like: *"This is a workaround for a bug in the library. Remove it when the bug is fixed."* or *"This is a temporary solution. We need to find a better way to do this."* or even better *"Remove this when feature X is implemented."*

<a href="https://labs.openai.com/s/tP8L20JaNKnSqV4iDmv4PD5I"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-tP8L20JaNKnSqV4iDmv4PD5I/image.webp"></a>

And then you do `git praise` and realize that these comments are old enough to raise a family together... great.

### Conclusion

All in all, code comments are a double-edged sword. We have covered more bad and ugly than good things. Because misuse and neglect of comments can result in a cluttered, confusing, and error-prone codebase. However, when used effectively, code comments can significantly contribute to clean code practices and improve understanding of software. To maintain a healthy balance, developers should prioritize clear, concise, and timely comments and ensure that they truly add value to the codebase. When it comes to code comments, remember the saying: "It's better to have no comment than a bad comment."

<a href="https://labs.openai.com/s/g7GDG9T19RZOMSr0Qw7TZepJ"><img class="dall-e" src="https://openai-labs-public-images-prod.azureedge.net/user-EdjyOaPT5S1BTvJpIGVzvTQx/generations/generation-g7GDG9T19RZOMSr0Qw7TZepJ/image.webp"></a>

Cheers, happy coding :)