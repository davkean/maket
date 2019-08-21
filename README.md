# maket

This repository shows an example of controlling NuGet package versions at the repository level, while at the same time ensuring that projects only opt into packages that they want.

Packages are opt'd in as normal via a `<PackageReference>` [in each project]((https://github.com/davkean/maket/blob/master/Library2/Library2.csproj#L12)) just without a version:

``` XML
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" />
  </ItemGroup>
```

Package versions across the repository (or solution) are then controlled by the `<PackageReference Update=""/>` constructs (new for MSBuild 15) inside of [Directory.Build.targets](https://github.com/davkean/maket/blob/master/Directory.Build.targets):

``` XML
  <ItemGroup>
    <PackageReference Update="Newtonsoft.Json" Version="10.0.1"/>
    <PackageReference Update="EntityFramework" Version="6.1.2"/>  
  </ItemGroup>
```

This says, "if a project has Newtonsoft.Json or EntityFramework in their list of packages, update them to this version".


You can read more information about Directory.Build.props/Directory.Build.targets in [Customize your build](https://docs.microsoft.com/en-us/visualstudio/msbuild/customize-your-build).
