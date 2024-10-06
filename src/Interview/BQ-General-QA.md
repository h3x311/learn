
## conclusion 
- On top of that
- Overall, I believe 

## connected words
- jog thoughts
- its not just about xx !!!!
- its deeper
- if necessary
## Situation
- When I joined my previous company
- At my last job
- In my previous role
- our company/team 
- During a project I worked on
- In a previous project
- In a previous role
- I once had to 
- I once worked with a colleague who had strong opinions 
- Early in my career, 
- A few months ago

## Problem in FE stituation
- Code style / issues  代码样式 / 问题
- Tests — missing cases, bugs, etc  测试 — 缺失的 case、bug 等
- Accessibility  可及性
- Performance issues  性能问题
- framework misuse / opportunities to learn  框架滥用 / 学习机会
- issues with data fetching / changing  数据获取 / 更改问题
- responsive design issues  响应式设计问题
- design mismatches  设计不匹配
- For React, basically every use of useEffect should be examined and attempts should be made to remove them unless absolutely necessary  对于 React，基本上应该检查每次使用 useEffect，除非绝对必要，否则应该尝试删除它们。

## BQ考查的重点是啥?
- Problem-solving skills
- Communication abilities
- Teamwork
- Adaptability
- Conflict resolution
- Among other essential soft skills

## Task
- I was assigned to a project that used the Go programming language, which I hadn't worked with before.
- As a software engineer on the team, my task was to identify the root cause of the issue and implement a solution as quickly as possible to minimize the impact on our users and the company's revenue. 
- We needed to ensure the stability and reliability of the platform while maintaining a positive user experience.

## Action

- By attending agile training sessions and workshops. 
- I also took the time to read up on agile best practices and learn from experienced agile practitioners within the company. 
- I collaborated closely with my team lead and colleagues to improve our agile processes. 
- I realized that I needed to adjust my approach, so I began practicing simplifying complex ideas and using analogies to make my explanations more accessible.
- To tackle this issue, I first analyzed the error logs and user reports to gather as much information as possible about the circumstances surrounding the failures. 
- I then set up a testing environment that mimicked the production system, allowing me to reproduce the issue without affecting real users.


## Action
- What I did was to arrange a quick meeting with all relevant product and engineering stakeholders to co-prioritize and assign the appropriate resources to support this project.
- I listed the features requested from every team and worked with all the relevant stakeholders to identify each feature's contribution to business objectives, while also roughly estimating the engineering effort for each one.
- This helped us to deprioritize features that had very high engineering effort but little contribution to the objectives.
- For projects that were not realistically possible to achieve within the timelines, we were able to negotiate for more engineering resources to delegate these feature work to.
- After that, to ensure my own timelines were met, I broke down my features into smaller tasks and planned them into daily and weekly milestones, reviewing my progress regularly with the team.

## Problem solving- FE
- In recent years, the product was showing its age – developer experience was not great and the website performance was poor. Initial loading speed was over 3 seconds and the conversion rate was around 0.8%.
- I was tasked with improving the performance and conversion of the website.
### Action
#### Problem Identification
- Conversion is tied to performance and UX.
- Website performance has been on a gradual decline over the past few years.
- UX hasn't been looked at in a while.
#### Information gathering 
- Looked at nature of bugs in the past year, categorized them according to their root causes to identify hotspots and major problematic areas.
- Gathered feedback from team regarding areas of improvements.
- Brainstorming session with the team to think of ways to improve.
- In order to improve, firstly we need to know how we are doing.
- Double checked that our performance and conversion tracking was working correctly.
- Started tracking new metrics from Lighthouse and Core Web Vitals.
- Worked with Data Scientists to come up with dashboards for performance and conversion and gained some insights:
- Mobile users had lower conversion rates as compared to desktop.
- Identified that some countries had lower conversion rates.
- Worked with UX Designers and UX Researchers to identify problems in the end-to-end shopping experience on the website.
- UI elements were too spaced apart and required a lot of scrolling which affected bounce rate because some users didn't bother scrolling.
#### Solution brainstorming
##### User Interface
- Server side rendering is crucial for its performance and SEO benefits. Made choices around good performance.
- Next.js: A few of our developers have experience with React and Next.js as a meta framework for building SSR applications was rapidly rising in popularity. We really desired the fast initial load and app-like behavior that Next.js provided.
- Svelte: Reactive model was appealing and the programming model easier to understand as compared to React's, however the ecosystem is small and there aren't that many libraries.
##### Styling: 
- The stylesheet was getting very bloated due to many classes being added over the years and being hard to remove.
- Tailwind CSS: Tailwind CSS was among the hottest CSS methodologies and its atomic CSS approach scales well for growing code bases.
- Styled Components: CSS-in-JS was something we were also looking at, but Styled Components was tied to React and runtime style injection was bad for performance.
#####  Performance-centric mindset. 
-  Read many performance case studies on web.dev and engineering blogs of other e-commerce companies, gathered a list of important performance techniques and processes:
- Set performance budget for each page (under 300kb).
- Run performance benchmarks before merging Pull Requests.
- Lazy loading of non-critical components Lazy load below-the-fold contents.
- Split JavaScript on page level instead of a single bundle (handled by Next.js).
##### Use WebP format for images.
- Host images on a CDN instead Adaptive loading of images so that mobile devices load a smaller image Consolidated duplicate JavaScript libraries (data-fns and moment.js), switched to lodash-es, removed all usages of jQuery - Looked at data to identify less used features and removed them from the code, reducing JS size on the product details pages by 200+kb.
##### Search Engine Optimization (SEO)
- Used SEO tools like Ahrefs to continuously monitor SEO.
- Worked with the marketing team to ensure marketing copy included important keywords as shown by Ahrefs.
- Adjusted page URLs to include SEO keywords
##### User Experience improvements
- Single page checkout experience as opposed to two-page checkout to reduce clicking.
- Reduced height of many UI elements.
- Fixed checkout button that wouldn't be missed.
##### Payment improvements
- Analyzed Stripe checkout and implemented country-specific address fields.
- Initially only had one available payment method: credit card. Got the help of Data Scientists to evaluate the popularity of new payment methods and whether they were worth adding. We later added PayPal, Google Pay, and Apple Pay payment methods as well.
##### Solution evaluation
- View and Rendering: Chose Next.js because it is backed by Vercel and has the largest community of all. React is also the most popular UI library out there and also easiest to hire jobs for.
##### Monitoring and adjustment
- Rolled out the new website behind an A/B test while monitoring the performance and conversion rates over a period of 2 months.
- Countries which previously saw lower conversion rates experienced nearly 50% improvements in conversion rates.
### result
- Lighthouse score has improved to 92.
- Loading speed has improved to 1.5 seconds
- Conversion has improved to 2.5%
- Developer velocity has improved in the recent survey and it is now easier to hire people into the team because more people know React over other frameworks.

## Collaboration/help with team member

In a previous project, I had a team member who was frequently late in delivering their assigned tasks. This affected our overall progress and deadlines. 

Instead of getting upset, I approached them privately to understand the reason for the delays. They were struggling with some personal issues and felt overwhelmed. I offered my support and suggested breaking tasks into smaller, manageable parts. 

This approach helped them get back on track, and our teamwork improved significantly.

## Adaptability/learn quickly/personal


When I joined my previous company, I was assigned to a project that used the Go programming language, which I hadn't worked with before. 

To get up to speed quickly, I dedicated my evenings and weekends to studying the language. 

I started with online tutorials and official documentation, then moved on to sample projects on GitHub to understand real-world implementation. 

In addition, I sought guidance from my colleagues who had experience with Go. 

Within two weeks, I became proficient enough to start contributing to the project effectively.

## Communication skills/feedback/I am wrong
I believe constructive criticism is an essential part of personal and professional growth. 

When I receive feedback, I make sure to listen carefully and consider the points being made. 

I then use the feedback to improve my skills and performance. For example, during a code review, a senior developer pointed out that my code was difficult to read due to inconsistent formatting. 

I took their feedback to heart, researched best practices for code formatting, and started implementing those practices in my work. 

As a result, my code became more readable and easier to maintain.

## Problem solving/big problem

When faced with a complex issue in my code, I first try to understand the problem by reproducing it and gathering as much information as possible. I then break the problem down into smaller, manageable parts and tackle each part systematically. 

For example, when I encountered a performance issue in an application, I used profiling tools to identify the bottleneck and then applied optimization techniques to improve the performance. 

By addressing the issue step by step, I was able to resolve it efficiently and effectively.

When I'm unsure of how to proceed or solve a problem, I start by researching and gathering information to expand my understanding of the issue. If necessary, I consult with my peers or supervisors to seek their input or guidance. For example, when I was tasked with implementing a feature using a technology I was unfamiliar with, I began by studying the documentation and online resources. I also reached out to a colleague who had experience with the technology to ask for their advice. By leveraging both self-learning and collaboration, I was able to successfully implement the feature and expand my skillset.

- leverage my ability to solve complex problems

## Time management

I use a combination of tools and strategies to manage my workload and prioritize tasks when working on multiple projects. 

I maintain a task list, which I update regularly, and allocate time for each project based on its priority and deadlines. 

I also utilize project management tools, like Trello or Jira, to track progress and coordinate with team members. 

In addition, I periodically review my priorities and adjust my focus as needed to ensure all projects are progressing as planned.

## Problem solving2

During a critical phase of a project, I encountered a complex issue where the application would crash under specific conditions. 

To resolve it, I first reproduced the issue and examined the error logs to gather relevant information. I then isolated the problematic code and conducted a thorough code review to identify potential causes. 

After identifying the root cause, I developed a solution, tested it thoroughly, and deployed the fix. This systematic approach helped me resolve the issue and prevented further crashes.


## Conflict 

Once, a product manager requested a feature that would have caused significant performance issues in our application. 

I carefully analyzed the request and gathered data to support my concerns. I then met with the product manager to discuss the technical limitations and presented my findings. 

We collaborated to find an alternative solution that met the business needs while preserving the application's performance. 

By maintaining open communication and working together, we were able to satisfy the project requirements without compromising the system's performance.

Technical details..

## Work life balance

To maintain a healthy work-life balance, I set clear boundaries between my work and personal life. During demanding projects, I make sure to prioritize tasks and allocate time for both work and personal activities. For instance, I schedule regular breaks and dedicate time for hobbies and exercise to recharge. By doing this, I maintain my focus and productivity at work while also ensuring my well-being.

## Reverse QA
![TFuiG7test](https://cdn.jsdelivr.net/gh/h3x311/upic@main/LC3/2024/TFuiG7test.png)
- "What are some of the challenges you expect the person in this position to face?"
- Can you describe a typical day or week for a developer in your team?" / "Can you walk me through the process of a typical project