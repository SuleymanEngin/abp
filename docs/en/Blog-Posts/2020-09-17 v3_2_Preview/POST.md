# ABP Framework 3.2 RC with the new Blazor UI

We are extremely excited today to release the ABP Framework (and the ABP Commercial, as always) version `3.2.0-rc.1` (Release Candidate). This release includes an early preview version of the **Blazor UI** for the ABP.IO Platform.

## The Blazor UI

While the Blazor UI should be considered as **experimental** for now, it is possible to develop your application today.

### Fundamental Services

Currently implemented some important framework features;

* **Authentication** through the MVC backend using the OpenId Connect authorization code flow. So, all the current login options (login, register, forgot password, external/social logins...) are supported.
* **Authorization**, using the ABP Framework **permissions** as well as the standard authorization system.
* **Localization** just works like the MVC UI.
* **Basic Theme** with top main menu.
* **Dynamic C# HTTP API proxies**, so you can directly consume your backend API by injecting the application service interfaces.
* Some other **fundamental services** like ISettingProvider, IFeatureChecker, ICurrentUser

Also, the standard .net services are already available, like caching, logging, validation and much more. Since the ABP Framework is layered itself, all the non MVC UI related features are already available.

### Pre-Built Modules

And some modules have been implemented;

* **Identity** module is pre-installed and provides user**, role and permission management**.
* **Profile management** page is implemented to allow to change password and personal settings.

### About the Blazorise Library

We've selected the [Blazorise](https://blazorise.com/) as a fundamental UI library for the Blazor UI. It already support different HTML/CSS frameworks and significantly increases the developer productivity.

We also have a good news: **[Mladen Macanović](https://github.com/stsrki)**, the creator of the Blazorise, is **joining to the core ABP Framework team** in the next weeks. We are excited to work with him to bring the power of these two successfully projects together.

### The Tutorial

We are currently in progress of updating the web application development tutorial for the Blazor UI. Follow the [@abpframework](https://twitter.com/abpframework) Twitter account to get informed once it's done.

### Get started with the Blazor UI

If you want to try the Blazor UI today, follow the instructions below.

First, install the the latest [ABP CLI](https://docs.abp.io/en/abp/latest/CLI) preview version:

````bash
dotnet tool update Volo.Abp.Cli -g --version 3.2.0-rc.1
````

Then you can create a new solution using the *abp new* command:

````bash
abp new AbpBlazorDemo -u blazor
````

> See the ABP CLI documentation for the additional options, like MongoDB database or separated authentication server.

Open the generated solution using the latest Visual Studio 2019. You will see a solution structure like the picture below:

TODO

* Run the `.DbMigrator` project to create the database and seed the initial data.
* Run the `HttpApi.Host` project for the server side.
* Run the `.Blazor` project to start the Blazor UI.

Use `admin` as the username as `1q2w3E*` as the password to login to the application.

TODO

## What's New with the ABP Framework 3.2

Beside the Blazor UI, there are a lot of issues have been closed with [the milestone 3.2](https://github.com/abpframework/abp/milestone/39?closed=1). I will highlight some of the major features and changes released with this version.

### MongoDB ACID Transactions

[MongoDB integration](https://docs.abp.io/en/abp/latest/MongoDB) now supports multi-document transactions that comes with the MongoDB 4.x.

> Transactions are disabled for automated integration tests coming with the application startup template, since the Mongo2Go library (we use in the test projects) has a problem with the transactions. We've sent a [Pull Request](https://github.com/Mongo2Go/Mongo2Go/pull/101) to fix it and will enable the transactions again when they merge & release it.
>
> If you are upgrading an existing solution and using MongoDB, please disable transactions for the test projects by following the [Unit Of Work](https://docs.abp.io/en/abp/latest/Unit-Of-Work) documentation.

### Kafka Integration for the Distributed Event Bus

ABP Framework's [distributed event system](https://docs.abp.io/en/abp/latest/Distributed-Event-Bus) has been [integrated to RabbitMQ](https://docs.abp.io/en/abp/latest/Distributed-Event-Bus-RabbitMQ-Integration) before. By the version 3.2, it has a Kafka integration package, named [Volo.Abp.EventBus.Kafka](https://www.nuget.org/packages/Volo.Abp.EventBus.Kafka).

See the [Kafka integration documentation](https://docs.abp.io/en/abp/latest/Distributed-Event-Bus-Kafka-Integration) to learn how to install and configure it.

### Host Features

TODO

### AbpHttpClientBuilderOptions

TODO

### Account Module: Profile Management Page Extensions

TODO

### ABP Build Command

We are using **mono repository** approach and the [abp repository](https://github.com/abpframework/abp) has tens of solutions and hundreds of projects (the framework, modules, tooling, templates...) with all of them are referencing to each other.

It gets a significant time to build the whole repository for every Git push. To **optimize** this process, we've created the **abp build** command in the [ABP CLI](https://docs.abp.io/en/abp/latest/CLI):

````bash
abp build
````

We will use this command to build the abp repository or a solution inside it. However it is available to everyone in case of need.

> **Most of the people will not need it**. If you need it, see the [ABP CLI](https://docs.abp.io/en/abp/latest/CLI) document to learn all the details and options.

### Other Features, Improvements and Changes

* Introduced the `DynamicRangeAttribute` that can be used to determine the range values on runtime, just like the `DynamicStringLengthAttribute` was introduced before.
* Improved the feature management modal for multi-tenant applications to group features on the UI and show hierarchically.
* Added `--skip-cli-version-check` option to ABP CLI to improve the performance by bypassing the online version check.
* Angular UI now redirect to MVC UI (the authentication server side) for profile management page, if the authorization code flow is used (which is the default).
* Improvements and optimizations for the [Angular service proxy generation](https://blog.abp.io/abp/Introducing-the-Angular-Service-Proxy-Generation).

And a lot of minor improvements and bug fixes. You can see [the milestone 3.2](https://github.com/abpframework/abp/milestone/39?closed=1) for all issues & PRs closed with this version.