Calm Blueprints: Overview
As we briefly discussed earlier, Blueprints are recipes for applications. Now let’s take a little time to explore what those recipes typically contain.

The eleven main components of a Calm Blueprint are:

Application Profiles
Services
Substrates
Application Profile Actions
System Defined Profile Actions
Custom Profile Actions
Service Actions
System Defined Service Actions
Custom Service Actions
Package Install/Uninstall
VM Pre-create/Post-create
Let’s go over each of these in a little more detail.

Calm Blueprint Canvas
Calm Blueprint Canvas
Calm Blueprint Canvas

Application Profiles (number 1 in the image above) expose simple choices to your end users. These choices are often about where an application should run (AHV or AWS), but they can also be used for ‘t-shirt’ sizing (small or large), or a combination of the two (small AHV or large AHV or small AWS). You, as an IT operator or developer, should have a good grasp of the underlying differences of these choices, while abstracting that complexity from your end users.

Services (number 2 in the image) are logical entities exposed by an IP, which span all application profiles, and are managed by Calm. End users and services communicate amongst each other over a network via their exposed IPs and ports. Services are typically deployed based on a disk image that is managed by Prism Central. Take a moment to think back to previous lessons, and to the Image Management topic that we discussed. Services in Calm are one reason why it’s important to understand how to work with images in Prism Central.

Substrates (number 3 in the image) are a combination of the underlying cloud and the virtual machine instance. When the desired cloud is selected in the Calm UI, all of the fields required for creating a virtual machine instance on that particular cloud are displayed — the combination of all these fields make up a substrate. Substrates do not span application profiles, so it’s considered a best practice to name substrates as a combination of the service name and app profile name (DB_AHV or DB_AWS or DB_Small or DB_Large).

Calm Application Profiles and Actions
Calm Application Profiles and Actions
Calm Application Profiles and Actions

Application Profile Actions (or Profile Actions for short, number 4 in the image above) are a set of operations that you can run on your application. For example, when launching a blueprint, the ‘Create’ action is run. If your application is not needed for a period of time, you could then run the ‘Stop’ action to gracefully stop your application. When you’re ready to resume work, running the ‘Start’ action will bring the app back up. There are two different types of profile actions, system defined profile actions and custom profile actions.

System Defined Profile Actions (5 in the image) are automatically created by Calm in every blueprint and underlying application. Since these are created for you, you cannot directly edit the tasks or the order of tasks within the canvas. However there are ways to control the order of operations, called Dependencies.

Custom Profile Actions (6 in the image) are created by the blueprint developer, and should be added whenever you need to expose a set of operations to the end user. Common custom profile actions are ‘Upgrade’, ‘Scale In’, and ‘Scale Out’. Since the actions are custom, individual tasks can be manually added in any order desired by the developer.

Calm Service Actions
Calm Service Actions
Calm Service Actions

Service Actions (7 in the image above) are a set of operations to be run on an individual service. As we discussed earlier, services span application profiles, so their actions (and the operations underlying those actions) do as well. If you create a service action in the ‘AHV’ profile, the same service action will be available in the ‘AWS’ profile. As with profile actions, there are also two different types of service actions: system-defined service actions and custom service actions.

System Defined Service Actions (8 in the image) are automatically created by Calm in every blueprint and underlying application. While these actions cannot be individually invoked, they are called when the corresponding profile action is run. For instance, any operations placed under the ‘Stop’ service action will be run when an end user invokes the ‘Stop’ profile action.

Custom Service Actions (9 in the image) are created by the blueprint developer, and should be added for any repeatable operations within the blueprint, like a function definition in a programming language. For instance, during both the ‘Create’ and ‘Upgrade’ profile actions, the ‘App’ service should pull new code from a source code control repository. Rather than maintaining two separate tasks that perform the same set of operations, you could create a single custom service action which is then referenced in both the ‘Create’ and ‘Upgrade’ actions.

Package Install/Uninstall (10 in the image) are operations which are run during the ‘Create’ or ‘Delete’ profile actions. In other words, they are operations that run when a user first launches a blueprint, or finally deletes the entire application. Package Install and Uninstall are unique to each application profile, which means your tasks or the task contents can vary depending upon the underlying cloud or the app’s ‘t-shirt’ size.

VM Pre-create/Post-delete (11 in the image) are operations which are run before the substrate is created, or after it is deleted. A common use case for this is to make an API call into an IP Address Management (IPAM) system to get an IP for a to-be-created VM. Since other operations described so far are run after the substrate has already been created, VM pre-create is necessary if a property of your substrate relies on a 3rd party system.

Additional Optional Reading
Calm Terminology, Actions, and Dependencies

Blueprint Overview

## Multi VM Blueprints

A multi-VM blueprint is a framework that you can use to create an instance, provision, and launch applications that require multiple VMs. Just like single VM blueprints, you can define the underlying infrastructure of the VMs, application details, and actions that are carried out on a blueprint until the termination of the application.

And, once again, you can choose which infrastructure to leverage when creating a multi-VM blueprint, with Nutanix, VMware, AWS, Azure, and GCP available as options.

Creating a Multi-VM Blueprint
Creating a multi-VM blueprint is a little more involved than a single VM blueprint. The process involves 6 major tasks, which are:

Adding a service
Configuring the VM, package, and service for your provider
Setting up service dependencies
Adding and configuring an application profile
(Optional) Adding and configuring scale out and scale in
Creating an action
Multi-VM blueprints are discussed in much more detail in the next lesson, but it’s helpful for you to have an overview of them now.

Now we come to the end of this lesson. Before we move on, let’s quickly recap some of the highlights of this lesson.

Blueprints are essentially recipes for applications. These recipes encompass application architecture and Infrastructure choices, provisioning and deployment steps, application binaries, command steps, monitoring endpoints, remediation steps, licensing and monetization, and policies. Every time a Blueprint is executed it results in an application.

Calm uses Services, Packages, Substrates, Deployments, and Application Profiles as building blocks for a blueprint. Together they fully define applications. By encoding these into a blueprint, Calm can understand the application as a whole and properly automate its lifecycle.

Blueprints are also incredibly important. The ability to turn an application into a repeatable, automated blueprint offer enterprises a number of benefits: greater agility while minimizing human error; broader self-service capabilities while allowing IT to retain centralized control; the ability to modernize app development by pairing Calm with a certified Kubernetes solution; and the ability to automate provisioning across multi-cloud architectures from a single management interface.

You can create two types of blueprints: single-VM and multi-VM. A single-VM blueprint is a framework that you can use to create an instance, provision, and launch applicati
ons that require a single VM. A multi-VM blueprint is a framework for applications that require multiple VMs.

Blueprints can be downloaded, uploaded, viewed, configured, edited, deleted, published, unpublished, and launched. Publishing, unpublishing, and deleting blueprints involves using the Marketplace Manager, which is what determines whether or not your blueprints are available to users of the Nutanix Marketplace.

If you’re comfortable with these concepts, you’ll find yourself in a good position to delve deeper into Calm. So, in the next lesson, we’ll explore blueprints even further, by discussing multi-VM blueprints and how you can use them for more complex, sophisticated automation tasks.