# maket

This repository shows an example of controlling NuGet package versions at the repository level, while at the same time ensuring that projects only opt into packages that they want.

Package versions are controlled in [Directory.Build.targets](https://github.com/davkean/maket/blob/master/Directory.Build.targets):

``` XML
  <ItemGroup>
    <PackageReference Update="Newtonsoft.Json" Version="10.0.1"/>
    <PackageReference Update="EntityFramework" Version="6.1.2"/>
  </ItemGroup>
```

Projects can [individually opt into packages](https://github.com/davkean/maket/blob/master/Library2/Library2.csproj#L12) simply via a normal package reference just without a version:

``` XML
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" />    
  </ItemGroup>
```
