---
title: "Project Management"
description: "A JVM application for project managers to manage projects and teams, keep track of tasks and calculate the critical tasks and the expected duration of a project."
layout: post

media-folder: "ProjectManagement"
featured: "ft.jpg"
skills: [Algorithms, Java, Kotlin, Scala, Unit Testing, Leader, Collaboration,]
---
*Application built with **Java**, **Kotlin** and **Scala**.*

*Application and source code available on <a href="https://github.com/abdullahibneat/ProjectManagement">GitHub</a>.*

Project Management was an application build as part of the JVM Programming Languages course at University. The aim was to introduce us to programming languages designed to run on the JVM and encourage remote group collaboration during the Coronavirus lockdown.

![{{ post.title }}](https://i.imgur.com/s3H5G29.png)

The requirements were as follows:

1. Use Java to create a desktop application with a graphical user interface which enables project managers
to set up projects and manage teams and record progress on tasks.
2. Create domain and entity classes that create an object-oriented structure supporting the Java GUI
application. These classes should be implemented in Kotlin.
3. Implement persistence for the project, team and task data, which makes it possible to save this data. You should use Lambda expressions to manage the collections of data. This should be implemented in Kotlin.
4. Implement an object-oriented component in Kotlin that can calculate the duration and finishing date of a project (based on its critical path) when provided with a project object. Integrate the critical path component into the project management process, so that when a project is edited, the critical path is automatically calculated and the duration and finishing date are updated.
5. Implement a critical path algorithm using a functional approach in Scala. Ideally, it should be possible to choose whether the object-oriented or functional implementation should be used at run-time.

As the member of the team with the most programming experience, I was selected as the lead developer. Responsibilities included:

- Create an initial codebase and maintain the project on GitHub;
- Overseeing the project, ensuring that tasks were completed on time;
- Organize regular meetings with my colleagues to schedule tasks for the day/week;
- Help out whenever someone was struggling, providing pseudocode or fixing bugs

With responsibilities shared among us, I began setting up a project to support Java, Kotlin and Scala. To make setting up easier for my peers, I used Maven as the dependency manager.

My task was to produce the critical path finding algorithm in Kotlin and Scala. For the former, an object-oriented approach was used, with the process similar to the one described in [this video](https://www.youtube.com/watch?app=desktop&v=0Lo4zsB-bjE). The main reason for choosing this implementation is the extra information that it produces: the output of this algorithm can tell which tasks are in the critical path, which tasks can be delayed without affecting the project, and the expected duration of the entire project.

![{{ post.title }}](https://i.imgur.com/XjPnfgS.png)

Because two implementations are necessary, an interface was created to make it easy to call either of the two implementations from the GUI.

```
public interface CriticalPath {
    Task[] findCriticalPath(Set<Task> tasks);
    Map<Task, CriticalCalculations> forwardBackwardPass(Set<Task> tasks);
}
```

<details style="margin-top: 1rem; border: 1px solid #aaa; border-radius: 4px; padding: .5em .5em 0">
	<summary style="font-weight: bold; margin: -.5em -.5em 0; padding: .5em">Click here to read more about the algorithm</summary>
	<div style="margin: .5rem">

	<p style="font-style: normal">The algorithm uses a while loop to iterate over all tasks and stops once all the tasks’ critical values have been computed. Because the forward and backward pass have very minor differences, and otherwise share the same code, they have been merged into a single function, <code>forwardBackwardPass</code>, and controlled using the forwardPass boolean.</p>
	<p>The following happens for each task in the forward pass:</p>
	<ul>
	<li>
		it first checks that in the forward pass, all previous tasks’ early values have been calculated
		<ul style="margin-left: 1.5rem">
			<li>if this is not the case, the while loop skips this task and proceeds to the next task</li>
			<li>If this is the first iteration, it finds the starting task</li>
		</ul>
	</li>
	<li>
		It then computes the critical early values for this task
		<ul style="margin-left: 1.5rem">
			<li>
				From the list of previous tasks, find the task that is expected to finish last.
				<ul style="margin-left: 1.5rem">
				<li>If this is a starting task, early start is set to 1, since this task can begin on day 1 of the project.</li>
				</ul>
			</li>
			<li>Add 1 to get the current task’s early start day</li>
			<li>
				Add the task’s duration to the early start and subtract 1 to get the early finish
				<ul style="margin-left: 1.5rem">
				<li>For example, task B has a duration of 2 days, and depends on A. The early finish of A is day 3. So B can start on day 4, and because it lasts 2 days, it can be worked on day 4 and 5 (i.e. 4 + 2 – 1 = 5.)</li>
				</ul>
			</li>
			<li>Add this tasks’ critical values to the map</li>
		</ul>
	</li>
	</ul>
	<p>Once all tasks have had their early start and early finish computed, the <code>forwardPass</code> boolean is set to false. This starts the backward pass:</p>
	<ul>
	<li>
		First check that for the current task, all the next task’s late values have been calculated
		<ul style="margin-left: 1.5rem">
			<li>If this is not the case, proceed to the next task</li>
			<li>If this is the first iteration, it will try to find the end task</li>
		</ul>
	</li>
	<li>
		It then computes the late values for this task
		<ul style="margin-left: 1.5rem">
			<li>
				From the list of successor tasks, find the task which starts the earliest
				<ul style="margin-left: 1.5rem">
				<li>If this is an end task, late finish is set to the highest early finish that is present in the map</li>
				</ul>
			</li>
			<li>
				Subtract 1 and the lag to find the early finish value for the current task
				<ul style="margin-left: 1.5rem">
				<li>E.g. if task B has two successors with early finish values of 6 and 7, take the value of 6 and subtract 1 to get 5 (meaning this task must end on day 5 for the successor task to begin on day 6)</li>
				</ul>
			</li>
			<li>Subtract the current task’s duration and add 1 to get the late start</li>
			<li>
				To get the float, subtract early finish from late finish
				<ul style="margin-left: 1.5rem">
				<li>A float of 0 indicates that this task cannot be delayed at all, implying this is a critical task. Non-critical tasks can be started a bit later without delaying the project.</li>
				</ul>
			</li>
		</ul>
	</li>
	<li>Update the map with these early values</li>
	</ul>
	<p>Once all tasks’ late values have been computed, return the map of tasks to their critical values, ending the algorithm.</p>

<!-- The algorithm uses a while loop to iterate over all tasks and stops once all the tasks’ critical values have been computed. Because the forward and backward pass have very minor differences, and otherwise share the same code, they have been merged into a single function, `forwardBackwardPass`, and controlled using the forwardPass boolean.

The following happens for each task in the forward pass:

-	it first checks that in the forward pass, all previous tasks’ early values have been calculated
	-	if this is not the case, the while loop skips this task and proceeds to the next task
	-	If this is the first iteration, it finds the starting task
-	It then computes the critical early values for this task
	-	From the list of previous tasks, find the task that is expected to finish last.
		-	If this is a starting task, early start is set to 1, since this task can begin on day 1 of the project.
	-	Add 1 to get the current task’s early start day
	-	Add the task’s duration to the early start and subtract 1 to get the early finish
		-	For example, task B has a duration of 2 days, and depends on A. The early finish of A is day 3. So B can start on day 4, and because it lasts 2 days, it can be worked on day 4 and 5 (i.e. 4 + 2 – 1 = 5.)
	-	Add this tasks’ critical values to the map

Once all tasks have had their early start and early finish computed, the `forwardPass` boolean is set to false. This starts the backward pass:

- First check that for the current task, all the next task’s late values have been calculated
	- If this is not the case, proceed to the next task
	- If this is the first iteration, it will try to find the end task
-	It then computes the late values for this task
	-	From the list of successor tasks, find the task which starts the earliest
		-	If this is an end task, late finish is set to the highest early finish that is present in the map
	-	Subtract 1 and the lag to find the early finish value for the current task
		-	E.g. if task B has two successors with early finish values of 6 and 7, take the value of 6 and subtract 1 to get 5 (meaning this task must end on day 5 for the successor task to begin on day 6)
	-	Subtract the current task’s duration and add 1 to get the late start
	-	To get the float, subtract early finish from late finish
		-	A float of 0 indicates that this task cannot be delayed at all, implying this is a critical task. Non-critical tasks can be started a bit later without delaying the project.
-	Update the map with these early values

Once all tasks’ late values have been computed, return the map of tasks to their critical values, ending the algorithm. -->

	</div>
</details>

This function is then called from the `findCriticalPath` method implemented by my colleague Harvind, where he finds the path from the starting task to the end task which contain all the critical paths.

Next, I worked on the Scala implementation. I decided to follow a pure functional approach, with no side effects, meaning I had to use recursion to avoid for and while loops. The logic took many attempts to get the correct results, this is mainly due to my inexperience with recursion. However, this process helped me developing a better understanding of recursive problems, and I feel more confident now.

![{{ post.title }}](https://i.imgur.com/VGMUuwo.png)

Comparing the performance against the Kotlin implementation, I noticed that some nodes were re-computed multiple times. This is because using a functional approach, I cannot store intermediate results to a variable that can be accessed by all recursive calls, as this would cause a side effect. Perhaps a better solution could have been to use a more dynamic approach, with the recursive calls storing intermediate values to a variable shared with all recursive calls.

Because of the single-threaded nature of this program, no additional issues would arise with such an implementation, however moving to a multi-threaded approach could cause race issues when multiple threads try to access or update the variable at the same time.

Overall, the algorithm works successfully and is capable of identifying a critical path correctly. During testing I found some issues, which I was able to debug and fix. Perhaps the Scala implementation could be optimized as detailed in the previous paragraph.

In regards to the coursework as a whole, most features work correctly and do have unit tests to ensure nothing breaks when refactoring or adding code. The only exceptions are persistence and the GUI. Regarding persistence, the lack of tests meant we weren’t aware of a minor bug in the code until functionality was implemented into the GUI. More specifically, when creating a new team through the interface, the JSON file would not update automatically. Upon further inspection I found out that the “save()” method was not called when creating a new team object.

On the upside, the persistence logic has been abstracted away from other parts of the program, by automatically updating the JSON file whenever a Project or Team object is instantiated and updated. This meant that other members of the group who weren’t working on persistence would not have to worry about when and how to update persistence (for example, Ed worked on the GUI but not on persistence), this was all taken care of in the background.

The GUI was built using the form editor by my colleague Ed; however, the code is quite messy, and does not adhere to the proper naming conventions expected in Java. For instance, most variables begin with an uppercase letter, something that is generally reserved for classes. Additionally, the code is not properly commented, and it’s sometimes hard to identify what a block of code does and what’s the logic behind it. This caused an issue when launching the interface for the first time, when a “data.json” is empty or does not exists. It would cause a null pointer exception, but due to us using IntelliJ’s form editor, the error was vague and would simply point to the first line of the file. After some debugging I found out that a panel was created inside a loop that iterated based on the contents of “data.json”, however when it’s empty/does not exists, the panel would not be created, essentially adding a null panel to the interface. The fix was to move the panel creation outside the loop.

A further issue with the GUI was that error messages would not be displayed. For example, adding a duplicated member to a team would throw an exception, but the GUI would just close the dialog without displaying useful messages. Following the demonstration, we added try/catch statements to catch errors and display relevant error messages to the user. This was mostly a painless process since, when throwing exceptions, we also defined custom error messages, so a simple dialog that prints the exception’s message was enough to solve this issue.

Due to the pandemic, we thought it was a good idea to use the git versioning system and host the code on GitHub to allow for easier collaboration and code sharing. Each of us had their own branch, working on a particular aspect of the project, and later we would merge the code into the master branch to combine everyone’s code. I have previous experience with git, so I’m familiar with the concept of committing code regularly with clear, concise commit messages.

However, my colleagues had little to no experience with this, so sometimes they would include multiple changes across a number of files in a single commit. This is something that could be improved in future projects and would be of great benefit in the workplace when working on a large codebase with dedicated members checking merge requests.

Additionally, my previous experiences with Git were limited to individual projects. Through this coursework, I learnt how to collaborate with others, how to fix any code conflicts, how to create pull requests for review by other members, and how to merge all our branches into a single “master” branch.

Generally speaking, version control did work successfully, and we were able to work on this project remotely, as a group, very well.