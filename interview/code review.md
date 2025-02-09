As a technical project manager, code review is one of my duties. I also spend time improving my code - review skills. First, it's important to understand why we conduct code reviews. We don't just want our features to run smoothly; we also aim to make our code more elegant and easier to maintain. So, code review helps our team write high - quality code.

Before starting a code review, I recommend that my colleagues do the following:

1. Ensure that the required logic runs well. If the code can't meet the requirements and make the features work properly, there's no point in proceeding with the code review.
2. Use software to track their code. This software can detect duplicate code, and they should fix these issues on their own.

During the code review, we often encounter some problems. For junior developers, they may make some mistakes. For example, they might query the database in a loop. Suppose you only want to get data by ID, but a junior developer queries the database every time in the loop. We'd suggest that they collect all the IDs in a list and then query the database just once. This can make the program run more smoothly and reduce the response time.

In our project, we also use `ThreadLocal`. Some junior developers forget to close the `ThreadLocal`, which can cause some garbage - collection (GC) issues in the project. So, one key thing we check is whether colleagues close the `ThreadLocal`.

When we notice that colleagues use a lot of `if - else` code blocks, we suggest they use design patterns like the strategy pattern or the template pattern. This can make the code more elegant and improve the developers' skills.

I also learned from my own experience during code reviews. At first, I only pointed out problems and said negative things. Sometimes, my colleagues felt frustrated because I was always highlighting the negatives. When I realized this, I knew I had to change. Now, when doing a code review, I first mention positive aspects of my colleagues' work. For example, when they complete a feature, it shows they've put in a lot of effort, which is really admirable. Then, I point out the problematic parts to help them improve.

Finally, I write a document to summarize the common problems that occur during our development projects. The three problems mentioned above are what I've summarized. I always recommend new colleagues to read this document, which can help our team reduce the occurrence of these problems.