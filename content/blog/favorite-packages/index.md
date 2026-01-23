---
date: '2025-07-29T11:39:05+02:00'
title: 'Favorite tooling / Nuget packages'
summary: "My list of recommended NuGet packages and tools."
weight: 20
author: ["Wilbert van Dolleweerd"]
draft: false
categories: ["blog"]
tags: ["NuGet", ".NET tool"]
ShowToc: true
TocOpen: false
---
# Don't reinvent the wheel
An important skill as a software developer is knowing when to build something yourself and when to pull
in a external dependency. This is a delicate balance. 

When you pull in a dependency you need to ask yourself: 
*"What if this package would disappear tomorrow?"*.
Worst case would be that from now on you need to support it yourself. Plan accordingly - maybe add an abstraction to make 
it easier to replace the dependency in the future.

On the other hand, deciding to write everything yourself might be a interesting intellectual challenge but your customer who is
paying the bill will probably be less impressed :money_with_wings:

During the course of multiple projects and solving problems, you will encounter lots of tools and packages. People might recommend them to 
you or they are considered to be a de facto standard within your community.  

## My selection criteria
These criteria are subjective - it is what I consider to be important. These are not hard rules. 

- I prefer open source over commercial. I don't dismiss commercial software but all things being equal, open source would have my preference.
- [Libraries over frameworks](https://www.youtube.com/watch?v=-NQUSbhqTLs). Frameworks tend to force you in a specific way of working while 
  with libraries you can pick what to use. Having said, sometimes you cannot avoid a framework.
- Packages/tools that are actively maintained are a plus.
- For a commercial project, I tend to avoid the more 'viral' [GPL-like](https://en.wikipedia.org/wiki/GNU_General_Public_License) licenses. Not 
  because I personally dislike these licenses but because they are usually not accepted by customers/our organisation.

## Show me the list
This is my list of useful tools and Nuget packages that I use on a regular basis in 
projects (both my own and at work). I will update this list to keep it current and I can refer other people 
to it. The description in *italics* means that it is lifted directly from the project website.

### Syntactic sugar / patterns
Syntactic sugar refers to features that can be used to simply existing syntax for accomplishing a task. Patterns are a well-known defined way to 
solve common problems. 

- [OneOf](https://github.com/mcintyre321/OneOf/) - provides F# style discriminated unions.
- [Dunet](https://github.com/domn1995/dunet) - similar to OneOf, but with source generators.
- [FluentResults](https://github.com/altmann/FluentResults) - return a result object instead of an exception.
- [Vogen](https://www.nuget.org/packages/Vogen/) - *"is a semi-opinionated library which is a Source Generator to generate value objects."*
- [NodaTime](https://nodatime.org/) - if you have to write functionality that will span timezones, use this library. No exceptions.
- [Flurl](https://flurl.dev/) - an elegant way to build URLs & set query params
- [UnitsNet](https://github.com/angularsen/UnitsNet) - *"add strongly typed quantities to your code and get merrily on with your life."*
- [SmartEnums](https://github.com/ardalis/SmartEnum) - if you prefer Java style enums that can have behaviour. 
- [Comparers](https://github.com/StephenCleary/Comparers) - can't be bothered with all the boilerplate code for writing comparers? Use this.
- [Mapster](https://mapperly.riok.app/) - *"a .NET source generator for generating object mappings. No runtime reflection."*
- [Stateless](https://github.com/dotnet-state-machine/stateless) - *"create state machines and lightweight state machine-based workflows directly in .NET code."*
- [Polly](https://github.com/App-vNext/Polly) - *"Polly is a .NET resilience and transient-fault-handling library that allows developers to express resilience strategies such as Retry, Circuit Breaker, Hedging, Timeout, Rate Limiter and Fallback in a fluent and thread-safe manner."*
- [FluentValidation](https://docs.fluentvalidation.net/en/latest/) - *"is a .NET library for building strongly-typed validation rules."*
- [Reactive Extensions for .NET](https://github.com/dotnet/reactive) - *"a library for event-driven programming with a composable, declarative model."*
- [FastCloner](https://github.com/lofcz/FastCloner) - *"Fast cloning library, supporting anything from .NET 4.6 to modern .NET 8+. Implements both deep and shallow cloning."*
- [CliWrap](https://github.com/Tyrrrz/CliWrap) - *"a library for interacting with external command-line interfaces."*
- [TickerQ](https://github.com/Arcenox-co/TickerQ) - *"a fast, reflection-free background task scheduler for .NET"*

### Testing
All tools related to testing.

- [xUnit](https://github.com/xunit/xunit) - I simply prefer xUnit over NUnit.
- [xUnit.SkippableFact](https://github.com/AArnott/Xunit.SkippableFact) - Let's you skip certain tests based on conditions.
- [NSubstitute](https://nsubstitute.github.io/) - *"Mock, stub, fake, spy, test double? Strict or loose? Nah, just substitute for the type you need!"*
- [Autofixture](https://github.com/AutoFixture/AutoFixture) - *"is designed to make Test-Driven Development more productive and unit tests more refactoring-safe. It does so by removing the need for hand-coding anonymous variables as part of a test's Fixture Setup phase."*
- [Autofixture.Xunit2](https://www.nuget.org/packages/AutoFixture.Xunit2) - *"offers integrations with most major .NET testing frameworks."*
- [Autofixture.AutoNSubstitute](https://www.nuget.org/packages/AutoFixture.AutoNSubstitute) - *"offers integations with most major .NET mocking libraries."* 
- [FluentAssertions](https://fluentassertions.com/) - *"Fluent Assertions is a very extensive set of extension methods that allow you to more naturally specify the expected outcome of a TDD or BDD-style unit tests."*
>[!NOTE]
>Since version 8, Fluent Assertions requires a commercial license.
- [FluentAssertions.OneOf](https://github.com/Resultful/FluentAssertions.Resultful) - *"improves the usage of [OneOf](https://github.com/mcintyre321/OneOf/) to allow easier unit testing."*
- [Bogus](https://github.com/bchavez/Bogus) - easily create fake data for your tests.
- [MELT](https://github.com/alefranz/MELT) - *"MELT is a free, open-source, testing library for the .NET Standard Microsoft Extensions Logging library. It is a solution to easily test logs."*
- [ArchUnitNET](https://github.com/TNG/ArchUnitNET) - express & verify your architecture as unit tests.
- [bUnit](https://bunit.dev/) - *"is a testing library for Blazor Components."*
- [Mailpit](https://github.com/axllent/mailpit) - *"email testing for developers"*

### Userinterface
Looking for things to spice up your userinterface?

- [Phospor](https://phosphoricons.com/) - *"is a flexible icon family for interfaces, diagrams, presentations — whatever, really."*
- [Iconify](https://iconify.design/) - over 200.000 open source vector icons.
- [Spectre.Console](https://spectreconsole.net/) - *"a .NET library that makes it easier to create beautiful console applications."*
- [Apache ECharts](https://echarts.apache.org/en/index.html) - *"An Open Source JavaScript Visualization Library"*
- [MudBlazor](https://mudblazor.com/) - A Blazor component library.
- [MVVM Toolkit](https://learn.microsoft.com/nl-nl/dotnet/communitytoolkit/mvvm/) - *"A fast, modular, platform-agnostic MVVM library."*
- [AvaloniaUI](https://avaloniaui.net/) - *"The open-source WPF successor for .NET developers building beautiful, cross-platform applications."*
- [SukiUI](https://kikipoulet.github.io/SukiUI/) - A desktop theme for AvaloniaUI
- [LiveCharts2](https://livecharts.dev/) - Almost all software needs a chart
- [Bootswatch](https://bootswatch.com/) - *"Free themes for Bootstrap. Simply download a CSS file and replace the one in Bootstrap."* 

### Logging / Performance
Logging and performance related tooling.

- [Serilog](https://serilog.net/) - *"provides diagnostic logging to files, the console, and elsewhere."*
- [SerilogTracing](https://github.com/serilog-tracing/serilog-tracing) - *"a minimal tracing system that integrates Serilog with .NET's `System.Diagnostics.Activity`"*
- [SerilogAnalyzer](https://github.com/Suchiman/SerilogAnalyzer) - *"Roslyn-based analysis for code using the Serilog logging library. Checks for common mistakes and usage problems."*
- [BenchmarkDotNet](https://github.com/dotnet/BenchmarkDotNet) - *"helps you to transform methods into benchmarks, track their performance, and share reproducible measurement experiments."* 

### Build / install related
Everything related to your build process and installer.

- [NukeBuild](https://nuke.build/) - Hate YAML build flows? Why not use Nuke.Build to create a build locally?
- [GitVersion](https://gitversion.net/) - Use your Git version history to determine a semantic version number.
>[!CAUTION]
>Beware that GitVersion needs access to your entire Git history. Some build systems only check out the latest commit to speed up the git clone.
>See the [requirements](https://gitversion.net/docs/reference/requirements) for more information.
- [Wix](https://www.firegiant.com/wixtoolset/) - If you need to write an MSI-based installer.
- [Dotnet outdated](https://github.com/dotnet-outdated/dotnet-outdated) - find out if your dependencies need updating.
- [CSharpier](https://csharpier.com/) - *"is an opinionated code formatter for c# and Xml."*
- [Banned API Analyzer](https://www.nuget.org/packages/Microsoft.CodeAnalysis.BannedApiAnalyzers/) - prevent the usage of certain classes/methods in your code.
- [Velopack](https://github.com/velopack/velopack) - *"Velopack is an installation and auto-update framework for cross-platform applications."*

### Network stuff / messaging
All things related to networking and/or messaging.

- [YARP](https://github.com/dotnet/yarp) - a reverse proxy server.
- [mitmproxy](https://mitmproxy.org/) - *"a free and open source interactive HTTPS proxy."*
- [FastEndPoints](https://fast-endpoints.com/) - *"a developer friendly alternative to Minimal APIs & MVC."*
- [MassTransit](https://masstransit.io/) - *"the trusted messaging framework powering mission-critical applications in more than 100 countries across industries like finance, government, logistics, healthcare, and technology"*
- [Wolverine](https://wolverinefx.net/) - *"The messaging and web development framework that gets out of your way"*
- [Brighter](https://github.com/BrighterCommand/Brighter) - *"a framework for building messaging app with .NET and C#"*
- [Darker](https://github.com/BrighterCommand/Darker) - *"The query-side counterpart of Brighter."*
- [MessagePack](https://msgpack.org/) - *"an efficient binary serialization format."*
- [EasyNetQ](https://easynetq.com/) - *"the leading client API for RabbitMQ on .NET"*
- [MQTT Explorer](https://mqtt-explorer.com/) - *"An all-round MQTT client that provides a structured topic overview"*
- [AsyncAPI](https://www.asyncapi.com/en) - *"Open-Source tools to easily build and maintain your event-driven architecture. All powered by the AsyncAPI specification, the industry standard for defining asynchronous APIs."*
- [Scalar](https://scalar.com/) - *"Create world-class API Docs with a built-in interactive playground"*
- [Mosquitto](https://mosquitto.org/) - *"an open source message broker that implements the MQTT protocol versions 5.0, 3.1.1 and 3.1."*
- [NGrok](https://ngrok.com/) - API gateway. Makes it possible to locally test your webhooks.


### Databases
Everything related to data access.

- [SQLite EF Core Database Provider](https://learn.microsoft.com/en-us/ef/core/providers/sqlite/?tabs=dotnet-core-cli) - Use EF Core with SQLite.
- [Npgsql Entity Framework Core Provider](https://www.npgsql.org/efcore/?tabs=onconfiguring) - Use EF Core with PostgreSQL.
- [EntityFramework.Exceptions](https://github.com/Giorgi/EntityFramework.Exceptions) - *"Handle database errors easily when working with Entity Framework Core. Supports SQLServer, PostgreSQL, SQLite, Oracle and MySql."*
- [EFCore.CheckConstraints](https://github.com/efcore/EFCore.CheckConstraints) - *"Check constraints for Entity Framework Core"*

### Reporting
Sometimes you still need a printed report.

- [QuestPDF](https://www.questpdf.com/) - *"Generate and manipulate PDF documents in your .NET applications"*