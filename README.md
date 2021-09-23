# SQL Server Reporting Services in Docker

creates a fresh install of SSRS in a container

https://hub.docker.com/r/roflinnds/mssql-ssrs-windows-developer

## Run it

This sample originally used mssql-server-windows-developer as a parent image and accepts all the commands listed there:

https://github.com/Microsoft/mssql-docker/tree/master/windows/mssql-server-windows-developer

This image no longer exists and it now uses roflinnds/mssql-server-windows-developer which uses the original Microsoft github code plus additional updates.

In addtion it accepts two more env variables: </br>

- **ssrs_user**: Name of a new admin user that will be created to login to report server
- **ssrs_password**: Sets the password for the admin user

Do not use the PWs listed in the example.  Come up with your own!!

example:

```
docker run -d -p 1433:1433 -p 8080:8080 -v C:/temp/:C:/temp/ -e sa_password=sa123#45678#pw -e ACCEPT_EULA=Y -e ssrs_user=SSRSAdmin -e ssrs_password=ssrs123#45678#pw --memory 6048mb mssql-ssrs-windows-developer:2017-1.0
```

then access SSRS at http://localhost:8080/reports/browse/ and login using ssrs_user (SSRSAdmin)

## Tips

- **-p 8080:8080** to access report manager in browser
- **--memory 6048mb** to bump RAM

## Disclaimers

SSRS is defintely not supported in containers..

## Credits

- [Complete automated configuration of SQL Server 2017 Reporting Services - Sven Aelterman](https://svenaelterman.wordpress.com/2018/01/03/complete-automated-configuration-of-sql-server-2017-reporting-services/)

## License

MIT license. See the [LICENSE file](LICENSE) for more details.
