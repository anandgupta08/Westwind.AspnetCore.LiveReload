# Live Reload WebServer Dotnet Tool

This is a self-contained Web Server for serving static HTML and loose Razor files that automatically includes Live Reload functionality. 

Change to a folder with Web files, and launch `LiveReloadServer` to serve files in that folder. You can make changes to static files and see the changes reflected.

Live Reload Web Server for static and loose Razor files. Use it to host a local folder as a Web site and automatically refresh page content as content is changed. It's a quick and easy way to 'run' a local folder with Web content as a local Web site and make interactive changes to it.

You can also use this 'generic' server behind a live Web Server by using installing the main project as a Web application.

## Installation
You can install this server as a .NET Tool using Dotnet SDK Tool installation:

```powershell
dotnet install -g LiveReloadServer
```

To use it, navigate to a folder that you want to serve HTTP files out of:

```ps
# will serve files out of https://localhost:5200
LiveReloadServer
```

### Launching the Web Server
You can use the command line to customize how the server runs. By default files are served out of the current directory but you can override the `WebRoot` folder.

Use commandlines to customize:

```ps
LiveReloadServer --WebRoot "c:/temp/My Web Site" --port 5200 --useSsl False
```

There are a number of Configuration options available:


```text
Live Reload Server
------------------
(c) Rick Strahl, West Wind Technologies, 2019

Static and Razor File Service with Live Reload for changed content.

Syntax:
-------
LiveReloadServer  <options>

Commandline options (optional):

--WebRoot            <path>  (current Path if not provided)
--Port               5200*
--UseSsl             True*|False
--LiveReloadEnabled  True*|False
--RazorEnabled       True*|False
--OpenBrowser        True*|False
--DefaultFiles       ""index.html,default.htm,default.html""

Live Reload options:

--LiveReload.ClientFileExtensions   "".cshtml,.css,.js,.htm,.html,.ts""
--LiveReload ServerRefreshTimeout   3000,
--LiveReload.WebSocketUrl:          ""/__livereload""

Configuration options can be specified in:

* Environment Variables with a `LiveReloadServer` prefix. Example: 'LiveReloadServer_Port'
* Command Line options as shown above

Examples:
---------
LiveReload --WebRoot ""c:\temp\My Site"" --port 5500 --useSsl false

$env:LiveReload_Port 5500
LiveReload
```

You can also use Environment variables to set these save options by using a `LiveReloadServer_` prefix:

```ps
$env:LiveReload_Port 5500
LiveReload
```
## Static Files
The Web Server automatically serves all static files and Live Reload is automatically enabled unless explicitly turned off. Making a change to any static file causes the current HTML page loaded in the browser to be reloaded.

## Razor Files
You can also use 'loose Razor Files' in the designated folder, which means you can use `.cshtml` Razor Pages with this server. All of the base .NET Core and ASP.NET Core API are supported, but you currently **cannot load custom packages or assemblies**. This tooling is meant to allow you to create 'semi-dynamic' content that can do simple things displays dates, read cookies do simple calcs, but not meant to run a full business application.
