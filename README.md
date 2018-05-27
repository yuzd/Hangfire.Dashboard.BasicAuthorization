Hangfire.Dashboard.BasicAuthorization for .netcore
================================

Some authorization filters for Hangfire's Dashboard.

Installation
-------------

This library is available as a NuGet Package:

```
Install-Package Hangfire.Dashboard.BasicAuthorization
```

Usage
------

## Basic authentication

```csharp
using Hangfire.Dashboard;

public void Configure(IApplicationBuilder app)
{
	app.UseHangfireServer();
	app.UseHangfireDashboard("/hangfire",new DashboardOptions
	{
		Authorization = new[] { new BasicAuthAuthorizationFilter(new BasicAuthAuthorizationFilterOptions
		{
			RequireSsl = false,
			SslRedirect = false,
			LoginCaseSensitive = true,
			Users = new []
			{
				new BasicAuthAuthorizationUser
				{
					Login = "admin",
					PasswordClear =  "test"
				} 
			}

		}) }
	});
}
```

