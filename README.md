# MessagePack for CLI

## What is it?

This is MessagePack serialization/deserialization for CLI (Common Language Infrastructure) implementations such as .NET Framework, Silverlight, Mono (including Moonlight.)
This library can be used from ALL CLS compliant languages such as C#, F#, Visual Basic, Iron Pyhton, Iron Ruby, PowerShell, C++/CLI or so.

## Usage

```c#
var serializer = MessagePackSerializer<T>.Create();
serializer.Pack(stream, obj);
var unpackedObject = serializer.Unpack(stream);
```

```vb
Dim serializer = MessagePackSerializer(Of T).Create()
serializer.Pack(stream, obj)
Dim unpackedObject = serializer.Unpack(stream)
```

## Features

* Fast and interoperable binary format serialization with simple API.
* Generating pre-compiled assembly for rapid start up.
* Flexible MessagePackObject which represents MessagePack type system naturally.

## Documentation

See [wiki](https://github.com/msgpack/msgpack-cli/wiki)

## Installation

* You can get binary drops from NuGet (currently, pre-release only).
  * There are NO distribution packages other than NuGet, so you have to build your own drops for Mono.

## How to build

### For .NET Framework

1. Install recent Windows SDK (at least, .NET Framework 4 Client Profile and MSBuild is needed.) <br/>
   Or install Visual Studio or Visual Studio Express.
    1. If you want to build unit test assemblies, install NuGet and then restore NUnit packages.
2. Run:

    msbuild MsgPack.sln

  Or (for .NET 3.5 drops, Silverlight 4 drops, and Silverlight 5 drops):

    msbuild MsgPack.compats.sln

  Or (for Windows Phone 7.1 drops):

    msbuild MsgPack.wp7.sln

Or open one of above solution files in your IDE and run build command in it.

### For Mono

Open MsgPack.mono.sln with MonoDevelop and then click **Build** menu item.
(Of cource, you can build via xbuild.)

### For Unity

* Build: use xbuild

```
$ xbuild xbuild MsgPack.compats.sln
```

* Put `MsgPack.dll` to you Unity project
(about `Plugins` or `Libs` directory)

```
cp bin/net35-client/MsgPack.dll $UNITY_PROJECT/Assets/
```

* Create `link.xml`. msgpack-cli needs System.Linq but mscorlib has't it.

```xml
<linker>
  <assembly fullname="System">
    <type fullname="System.Linq" preserve="all" />
  </assembly>
</linker>
```

* Configure "Use micro mscorlib" (**REQUIRED**)
* Build your project! :sushi:

## See also

*  GitHub Page           : http://cli.msgpack.org/
*  Wiki (documentation)  : https://github.com/msgpack/msgpack-cli/wiki
*  API Reference         : http://cli.msgpack.org/doc/top.html
*  Issue tracker         : https://github.com/msgpack/msgpack-cli/issues
*  MSBuild reference     : http://msdn.microsoft.com/en-us/library/0k6kkbsd.aspx
*  Mono xbuild reference : http://www.mono-project.com/Microsoft.Build

