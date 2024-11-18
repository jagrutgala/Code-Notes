# Hangfire

Hangfire is a C# Nuget Library that allows you to un background threads and jobs. It is a very easy to use. It also allows you to run recurring jobs easily using cron syntax for setup.

Hangfire requires a persistent storage for keeping track of the background tasks & jobs. You can connect any sql server of your choice.

## Background Server

Hangfire Server part is responsible for background job processing. The Server does not depend on ASP.NET and can be started anywhere, from a console application to Microsoft Azure Worker Role. Single API for all applications is exposed through the BackgroundJobServer class:
```cs
using (var server = new BackgroundJobServer())
{
    // Application code.
    // Lastly stop application from closing, so BackgroundJobServer can do its thing.
    Console.ReadLine();
}
```


> **Helpful links**
>
> Docs: [https://docs.hangfire.io/en/latest/getting-started/index.html](https://docs.hangfire.io/en/latest/getting-started/index.html)
> Example (Console Application): [https://karolmemo.com/2020/11/26/background-automation-tasks-in-net-sample-console-application-using-hangfire/](https://karolmemo.com/2020/11/26/background-automation-tasks-in-net-sample-console-application-using-hangfire/)
> Example (Asp.Net Application): [https://karolmemo.com/2020/12/22/background-automation-tasks-in-net-core-sample-web-application-using-hangfire/](https://karolmemo.com/2020/12/22/background-automation-tasks-in-net-core-sample-web-application-using-hangfire/)
> Useful resource for Crontab: [https://crontab.guru](https://crontab.guru)


## Background Jobs

In Hangfire using the `BackgroundJob` class we can create or schedule tasks to be run in a background process.

**BackgroundJob methods:**

- **Enqueue**: Using the Enqueue method we can add a function to be processed and run in the background process. It returns a jobId that can be used to update, cancel that job or invoke a callback on completion of it.
    ```cs
    var jobId = BackgroundJob.Enqueue(
        () => Console.WriteLine("Fire-and-forget!")
    );
    ```

- **Schedule**: Using the Schedule method we can add a function to be processed and run in the background process after a scheduled delay. It returns a jobId that can be used to update, cancel that job or invoke a callback on completion of it.
    ```cs
    var jobId = BackgroundJob.Schedule(
        () => Console.WriteLine("Delayed!"),
        TimeSpan.FromDays(7)
    );
    ```

- **ContinueJobWith**: Using the ContinueJobWith method we can invoke a method as a callback after the completion of a job.
    ```cs
    BackgroundJob.ContinueJobWith(
        jobId,
        () => Console.WriteLine("Continuation!")
    );
    ```

## Recurring Jobs

In Hangfire using the `RecurringJob` class we can create and schedule tasks to be run in a background process recurringly at the specified interval.

**RecurringJob methods:**

- **AddOrUpdate**: Add a method to be run at scheduled intervals.
    ```cs
    RecurringJob.AddOrUpdate(
        "myrecurringjob",
        () => Console.WriteLine("Recurring!"),
        Cron.Daily
    );
    ```
- **RemoveIfExists**: Removes the recurring job from the schedule.
    ```cs
    RecurringJob.RemoveIfExists("some-id");
    ```

- **Trigger**: It can be used to trigger the background job manually.
    ```cs
    RecurringJob.Trigger("some-id");
    ```

## Example (Console Application)

**Step 1:** Install Hangfire

Install nuget package `Hangfire.Core` & a SQL adapter for Hangfire like `Hangfire.SqlServer`, `Hangfire.PostgreSql`, `Hangfire.Storage.SQLite`.

If you also want to configure dependency injection for your Hangfire jobs then install IoC Libs like `Hangfire.Autofac`, `Hangfire.Ninject`, `Hangfire.SimpleInjector`.

And to convert your app into an application host so that it runs indefinitely until you shut it down install `Microsoft.Extensions.Hosting`.

**Step 2:** Configure Hangfire
```cs
GlobalConfiguration.Configuration
    .SetDataCompatibilityLevel(CompatibilityLevel.Version_180)
    .UseColouredConsoleLogProvider()
    .UseSimpleAssemblyNameTypeSerializer()
    .UseRecommendedSerializerSettings()
    .UseSqlServerStorage("<ConnectionString>");
```

**Step 3:** Configure Jobs
```cs
BackgroundJob.Enqueue(() => Console.WriteLine("Hello, world!"));

var jobId = BackgroundJob.Schedule(
    () => Console.WriteLine("Delayed!"),
    TimeSpan.FromMinutes(10)
);

RecurringJob.AddOrUpdate(
    "myrecurringjob",
    () => Console.WriteLine("Good Morning!"),
    Cron.Daily
);
```

**Step 4:** Start BackgroundServer
```cs
using (var server = new BackgroundJobServer())
{
    // Simple sol to stop application from closing
    Console.ReadLine();

    // Or Run a Host Application
    Host.CreateApplicationBuilder().Build().Run();
}
```

## Example (Asp.NetCore Application)

**Step 1:** Install Hangfire

Install nuget package `Hangfire` & Asp.Net Core adapter `Hangfire.AspNetCore` & a SQL adapter for Hangfire like `Hangfire.SqlServer`, `Hangfire.PostgreSql`, `Hangfire.Storage.SQLite`.

If you also want to configure dependency injection for your Hangfire jobs then install IoC Libs like `Hangfire.Autofac`, `Hangfire.Ninject`, `Hangfire.SimpleInjector`.

And to convert your app into an application host so that it runs indefinitely until you shut it down install `Microsoft.Extensions.Hosting`.

**Step 2:** Configure Hangfire
```cs
// Add Hangfire services.
services.AddHangfire(configuration => configuration
    .SetDataCompatibilityLevel(CompatibilityLevel.Version_180)
    .UseSimpleAssemblyNameTypeSerializer()
    .UseRecommendedSerializerSettings()
    .UseSqlServerStorage(Configuration.GetConnectionString("<ConnectionString>"))
);

// Add the processing server as IHostedService
services.AddHangfireServer();

// Add framework services.
services.AddMvc();

// ...other services

// If you want Hangfire Dashboard UI (optional)
app.UseHangfireDashboard();
```

**Step 3:** Configure Jobs
```cs
// Inject using IBackgroundJobClient
ctor(IBackgroundJobClient backgroundJobs);

backgroundJobs.Enqueue(() => Console.WriteLine("Hello, world!"));

var jobId = BackgroundJob.Schedule(
    () => Console.WriteLine("Delayed!"),
    TimeSpan.FromMinutes(10)
);

RecurringJob.AddOrUpdate(
    "myrecurringjob",
    () => Console.WriteLine("Good Morning!"),
    Cron.Daily
);
```

**Step 4:** Open hangfire dashboard

When the application has started, we can open Dashboard, just add `“/hangfire”` to URL.

## Advance use-case

You can also use hangfire to run background jobs in a throttled or rate-limited manner, using the `Hangfire.Throttling` package. We can create Semaphore, Mutexes, FixedWindow, SlidingWindow, DynamicWindow Options to configure different behaviors.

> **Note**
>
> Refer: [https://docs.hangfire.io/en/latest/background-processing/throttling.html](https://docs.hangfire.io/en/latest/background-processing/throttling.html)
