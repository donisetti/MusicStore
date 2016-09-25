## Running with Docker Compose

 * `docker build -t sqlserver:2016 -f .\docker\mssql-server-2016-express\Dockerfile .\docker\mssql-server-2016-express\.`
 * `docker-compose -f .\src\MusicStore\docker-compose.yml up`
 * Open a browser and open `http://<ip-of-vm-running-docker>:5000/`

## Demo script

 1. $Env:DOCKER_HOST = "vm-ip:2375"
 2. Get-Content .\docker\dotnet\Dockerfile | docker build -t microsoft/dotnet:1.0.0-preview2-windowsservercore-sdk -
 3. Get-Content .\docker\mssql-server-2016-express\Dockerfile | docker build -t sqlserver:2016 -
 4. docker build -t musicstore -f .\src\MusicStore\Dockerfile .\src\MusicStore\.
 5. .\start.ps1
 6. open http://vm-ip:5000/ in browser

# MusicStore application

AppVeyor: [![AppVeyor](https://ci.appveyor.com/api/projects/status/ja8a7j6jscj7k3xa/branch/dev?svg=true)](https://ci.appveyor.com/project/aspnetci/MusicStore/branch/dev)

Travis:   [![Travis](https://travis-ci.org/aspnet/MusicStore.svg?branch=dev)](https://travis-ci.org/aspnet/MusicStore)

This project is part of ASP.NET Core. You can find samples, documentation and getting started instructions for ASP.NET Core at the [Home](https://github.com/aspnet/home) repo.

## Run the application on Helios:
* If you have Visual Studio 2015
	1. Open MusicStore.sln in Visual Studio 2015 and run the individual applications on `IIS Express`.
* If you don't have Visual Studio 2015
	1. Open a command prompt and execute `cd \src\MusicStore\`.
	2. Execute `dnu restore`.
	3. Execute `Helios.cmd` to launch the app on IISExpress from command line (Application started at URL **http://localhost:5001/**).
	   
**NOTE:** App and tests require Visual Studio 2015 LocalDB on the machine to run.

## Run on WebListener/Kestrel:
* Open a command prompt and cd `\src\MusicStore\`.
* **[WebListener]:**
	4. Run `dnx . web` (Application started at URL **http://localhost:5002/**).
* **[Kestrel]:**
	5. Run `dnx . kestrel` (Application started at URL **http://localhost:5004/**).
* **[CustomHost]:**
	6. Run `dnx . run` (This hosts the app in a console application - Application started at URL **http://localhost:5003/**).

## To run the sample on Mac/Mono:
* Follow the instructions at the [Home](https://github.com/aspnet/Home) repository to install Mono and DNVM on Mac OS X.
* Open a command prompt and execute `cd \src\MusicStore\`.
* Execute `dnu restore`.
* Try `dnx . kestrel` to run the application.

**NOTE:** Since on Mono SQL client is not available the sample uses an InMemoryStore to run the application. So the changes that you make will not be persisted.

### Deploy on Heroku
To deploy MusicStore on Heroku, click the button below:

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

###NTLM authentication
More information at [src/MusicStore/StartupNtlmAuthentication.cs](src/MusicStore/StartupNtlmAuthentication.cs).

###OpenIdConnect authentication
More information at [src/MusicStore/StartupOpenIdConnect.cs](src/MusicStore/StartupOpenIdConnect.cs).
