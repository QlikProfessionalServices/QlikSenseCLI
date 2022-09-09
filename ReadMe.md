# QlikSenseCLI
## About

QlikSenseCLI is PowerShell module to interface with the Qlik Sense QRS APIs.
Objects retrieved from the QRS APIs are cast to DotNet object types.

QlikSenseCLI is procedurally generated from the OpenAPI Specification.

While each version of the module will predominantly be forwards & backwards compatible with previous version of Qlik Sense. 

A new version of the module will be release with each major release of Qlik Sense Enterprise containing all of the changes in the OpenAPI specification. 

The Version number of the QlikSenseCLI will relate to the Version of the OpenAPI schema in Qlik Sense.

Each release comes in two variants.
net45 & netstandard2.0

the net45 can be used by Windows PowerShell 4+ 
the netstandard2.0 can be used by PowerShell 5 and PowerShell 7+ (on Windows/MacOSx/Linux)

Issues can be reported via the GitHub Repository [Issues](https://github.com/QlikProfessionalServices/QlikSenseCLI/issues) 

Further information around the QRS API's can be found in the [OpenAPI](https://help.qlik.com/en-US/sense-developer/APIs/RepositoryServiceAPI/index.html) specification

## Installation
```PowerShell
Get-PackageProvider -Name NuGet -ForceBootstrap

# Install for all users, requires admin rights
Install-Module QlikSenseCLI

# Install for current user
Install-Module QlikSenseCLI -Scope CurrentUser
```

```PowerShell
# Once Installed you can import the Module
Import-Module QlikSenseCLI

# Then to Connect to Qlik Sense you can use one of the following with the Optional Parameters

# Current User
Connect-QlikSense [[-Hostname] <string>] [[-VirtualProxy] <string>] [[-TrustAllCertificates]]
    
# Specified Credentials
Connect-QlikSense [[-Hostname] <string>] [[-VirtualProxy] <string>] [[-Credential] <NetworkCredential>] [[-TrustAllCertificates]]  
    
# Qlik Client Certificate
Connect-QlikSense [[-Hostname] <string>] [[-Username] <string>] [[-Certificate] <X509Certificate2>][[-TrustAllCertificates]]  
```

### Connection Examples
```PowerShell
# Connect to local host as current user
Connect-QlikSense

# Connect to local host as current user on specific virtual proxy
Connect-QlikSense -VirtualProxy "MyVP" -TrustAllCertificates

# Connect to Remote host on specific Virtual proxy as the current user
Connect-QlikSense -Hostname "MySenseServer" -VirtualProxy "MyVP" -TrustAllCertificates
```

```PowerShell
# Connect to Local host with Specified Credentials
$Credentials = Get-Credential
Connect-QlikSense -Credential $Credentials -TrustAllCertificates

# Connect to Remote host on with Specified Credentials on specific Virtual proxy 
$Credentials = Get-Credential
Connect-QlikSense -Hostname "MySenseServer" -VirtualProxy "MyVP" -Credential $Credentials  -TrustAllCertificates
```

```PowerShell
# Connect to Local host on with QlikClient Certificate as Specified User
$QlikClientCertificate = Get-ChildItem Cert:\CurrentUser\My\ | ? { $_.Subject -eq "CN=QlikClient" }
Connect-QlikSense -Certificate $QlikClientCertificate -Username "Domain\User" -TrustAllCertificates

# Connect to Remote host on with QlikClient Certificate as Specified User
$QlikClientCertificate = Get-ChildItem Cert:\CurrentUser\My\ | ? { $_.Subject -eq "CN=QlikClient" }
Connect-QlikSense -Hostname "MySenseServer" -Certificate $QlikClientCertificate -Username "Domain\User" -TrustAllCertificates
```



### TO DO
Usage examples Coming soon!