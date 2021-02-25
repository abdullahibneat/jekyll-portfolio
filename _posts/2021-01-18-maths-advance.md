---
title: "Maths Advance"
description: "A subscription platform for GCSE grade students to solve unique, tailor-made challenging maths questions along with video explanations to boost their grade and achieve better results."
layout: post

media-folder: "MathsAdvance"
featured: "ft.jpg"
skills: [Full stack, React, NodeJS, MongoDB, GraphQL, DevOps, Stripe]
---
*Front-end written in **React**, API developed in **NodeJS** and served through **GraphQL** using **MongoDB** as the database.*

*Application available live at <a href="https://mathsadvance.co.uk">https://mathsadvance.co.uk</a>.*

I was approached by George, the client for this project, to produce a subscription platform where GCSE maths students can practise challenging questions to boost their grade. As a maths teacher he wrote many tailor-made questions over time and was looking to build a platform to share his resources with other students, teachers and schools.

![{{ post.title }}](https://i.imgur.com/ucrWPez.jpg)

Initially, the client attempted at building the website themselves using WiX, but the design was not appealing and usability from a user perspective was limited.

After receiving the requirements and understanding the desired layout of the "questions" page, I began working on a modern design to suit the high-quality content that will be available to users. Crucially, it was important for navigation between topics, sub-topics and questions to be close to each other to allow easy and quick transitioning between different topics.

![{{ post.title }}](https://i.imgur.com/Dt7IK6s.jpg)

An admin area was also added to aid the creation of questions. Different features were implemented to help with the management of questions, such us drag-and-drop to change the order of items and a toggle to hide work-in-progress sections of the website.

Each question includes different options to restrict visibility to paying subscribers and to display additional icons from the main screens, such as calculator questions, exam questions and difficulty level. Moreover, the Dropbox API was implemented to better integrate with the client's workflow, such as linking to video solutions by simply selecting the resource from an existing Dropbox library.

![{{ post.title }}](https://i.imgur.com/R2PQRzN.jpg)

Extensibility was important as the client requested for extra features during development. For example, adding extra fields to the question editing page display further details to the user in the "questions" page. Reusable components helped with  accommodating extra requests and eased their development.

To allow for payment processing, the Stripe platform was decided as the best fit for the client's needs. The API was implemented in the backend to ensure correct and secure processing, with automated emails sent out once a subscription is successful by registering a webhook. The Stripe Customer portal was also used to allow users to manage their subscription anytime directly from the website.

The final step of this project was to deploy both backend and frontend. Both codebases are stored on GitHub and actions have been set up to automatically deploy the code after commits are pushed in the master branches.

With this project I was able to apply the skills I learnt over the past year on full stack deployment, with the added benefit of learning email delivery, payment processing and webhooks along the way. More importantly, this project was the key to discover and unlock the full potential of my abilities, feeling more confident on producing robust and reliable code to tackle complex tasks.

![{{ post.title }}](https://i.imgur.com/hc3PMc6.jpg)

Working alongside George was very important to ensure the final product meets his needs and to clear up any ambiguities in his requests. Not only did this shorten development time, but also saved time when it came down to writing code and kept the focus on the most important tasks for the website. Overall, the project was a success and the client is happy with the result:

<div style="margin-top: 2rem; padding: 1.5rem 2rem; border-radius: 2rem; background: #f5f5f5">
<blockquote>
It was my pleasure to have you doing the coding Abdullah. I think it's fair to say it would have never got off the ground without your help.
</blockquote>
<cite style="display: block; font-style: italic; margin-top: 1rem;">
<b>George Bowman</b><br>
Founder, Maths Advance.
</cite>
</div>