---
title: Visual Studio Kapsayıcı araçları derleme özellikleri
author: ghogen
description: Visual Studio kapsayıcı projesi oluşturup çalıştırma şeklini özelleştirmek için kapsayıcı araçları derleme özelliklerini nasıl düzenleyeceğinizi öğrenin.
ms.author: ghogen
ms.date: 06/06/2019
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: b284296e4f7bc0f2d641e3094717f95161aef2d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045027"
---
# <a name="container-tools-build-properties"></a>Kapsayıcı araçları derleme özellikleri

Visual Studio, projenizi oluşturmak için MSBuild tarafından kullanılan özellikleri ayarlayarak kapsayıcı projelerinizi nasıl derleyerek özelleştirebilirsiniz. örneğin, dockerfile adını değiştirebilir, görüntüleriniz için etiketler ve etiketler belirtebilir, docker komutlarına geçirilen ek bağımsız değişkenleri sağlayabilir ve Visual Studio kapsayıcı ortamının dışında oluşturma gibi belirli performans iyileştirmeleri yapıp getirmediğini kontrol edebilirsiniz. Ayrıca, başlatılacak yürütülebilir dosyanın adı ve sağlanacak komut satırı bağımsız değişkenleri gibi hata ayıklama özelliklerini de ayarlayabilirsiniz.

Bir özelliğin değerini ayarlamak için proje dosyasını düzenleyin. Örneğin, Dockerfile adlı dosyanın *Mydockerfile* olduğunu varsayalım. `DockerfileFile`Proje dosyasındaki özelliğini aşağıdaki gibi ayarlayabilirsiniz.

```xml
<PropertyGroup>
   <DockerfileFile>MyDockerfile</DockerfileFile>
</PropertyGroup>
```

Özellik ayarını varolan bir `PropertyGroup` öğeye ekleyebilirsiniz, yoksa yeni bir `PropertyGroup` öğe oluşturun.

aşağıdaki tabloda kapsayıcı projeleri için kullanılabilen MSBuild özellikleri gösterilmektedir. NuGet paketi sürümü [Microsoft. VisualStudio. Azure. Containers. Tools. Targets](https://www.nuget.org/packages/Microsoft.VisualStudio.Azure.Containers.Tools.Targets/)için geçerlidir.

| Özellik adı | Açıklama | Varsayılan değer  | NuGet paketi sürümü|
|---------------|-------------|----------------|----------------------|
| ContainerDevelopmentMode | "Konak oluşturma" iyileştirmesi ("hızlı mod" hata ayıklama) etkin olup olmadığını denetler.  İzin verilen değerler **hızlı** ve **normal**. | Hızlı |1.0.1872750 veya daha yeni|
| ContainerVsDbgPath | VSDBG hata ayıklayıcısı için yol. | `%USERPROFILE%\vsdbg\vs2017u5` |1.0.1985401 veya daha yeni|
| DockerDebuggeeArguments | Hata ayıklarken, hata ayıklayıcı, bu bağımsız değişkenleri başlatılan yürütülebilir dosyaya iletmektir. | ASP.NET .NET Framework projelerine uygulanamaz |1.7.8 veya daha yeni|
| DockerDebuggeeProgram | Hata ayıklarken, hata ayıklayıcıda bu çalıştırılabiliri başlatması istendi. | .net Core projeleri için: dotnet, ASP.NET .NET Framework projeleri: uygulanamaz (ııs her zaman kullanılır) |1.7.8 veya daha yeni|
| DockerDebuggeeKillProgram | Bu komut, bir kapsayıcıda çalışan işlemi sonlandırmak için kullanılır. | ASP.NET .NET Framework projelerine uygulanamaz |1.7.8 veya daha yeni|
| Dockerdebuggeeworkingdizini | Hata ayıklarken, hata ayıklayıcının bu yolu çalışma dizini olarak kullanması talimatı verilir. | c:\app (Windows) veya/app (Linux) |1.7.8 veya daha yeni|
| DockerDefaultTargetOS | Docker görüntüsü oluşturulurken kullanılan varsayılan hedef işletim sistemi. | Visual Studio tarafından ayarlanır. |1.0.1985401 veya daha yeni|
| Dockerımagelabels | Docker görüntüsüne uygulanan varsayılan etiket kümesi. | com. Microsoft. Created-By = Visual-Studio; com. Microsoft. Visual-Studio. Project-Name = $ (MSBuildProjectName) |1.5.4 veya daha yeni|
| Dockerfastmodeprojectbağlamadizini|**Hızlı modda**, bu özellik proje çıktı dizininin çalışan kapsayıcıya birim bağlı olduğunu denetler.|c:\app (Windows) veya/app (Linux)|1.9.2 veya daha yeni|
| DockerfileBuildArguments | [Docker Build](https://docs.docker.com/engine/reference/commandline/build/) komutuna ek bağımsız değişkenler geçirildi. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileContext | Docker görüntüsü oluşturulurken kullanılan varsayılan bağlam, Dockerfile ile ilişkili bir yol olarak. | Visual Studio tarafından ayarlanır. |1.0.1872750 veya daha yeni|
| DockerfileFastModeStage | Görüntü hata ayıklama modunda oluşturulurken kullanılacak Dockerfile aşaması (yani, hedef). | Dockerfile 'da bulunan ilk aşama (temel) |
| DockerfileFile | Projenin kapsayıcısını derlemek/çalıştırmak için kullanılacak varsayılan Dockerfile öğesini açıklar. Bu bir yol da olabilir. | Dockerfile |1.0.1872750 veya daha yeni|
| DockerfileRunArguments | [Docker Run](https://docs.docker.com/engine/reference/commandline/run/) komutuna ek bağımsız değişkenler geçirildi. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileRunEnvironmentFiles | Docker çalıştırması sırasında uygulanan ortam dosyalarının noktalı virgülle ayrılmış listesi. | Geçerli değildir. |1.0.1872750 veya daha yeni|
| DockerfileTag | Docker görüntüsü oluşturulurken kullanılacak etiket. Hata ayıklama sırasında, etikete bir ":d ev" eklenir. | Aşağıdaki kurallarla alfasayısal olmayan karakterleri gerçekleştirdikten sonra bütünleştirilmiş kod adı: <br/> Sonuç etiketi tümü sayısal ise, "görüntü" bir ön ek olarak eklenir (örneğin, image2314) <br/> Sonuç etiketi boş bir dizeyse, etiket olarak "görüntü" kullanılır. |1.0.1872750 veya daha yeni|

## <a name="example"></a>Örnek

Aşağıdaki proje dosyası bu ayarlardan bazılarının örneklerini gösterir.

```xml
 <Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UserSecretsId>feae72bf-2368-4487-b6c6-546c19338cb1</UserSecretsId>
    <DockerDefaultTargetOS>Linux</DockerDefaultTargetOS>
    <!-- In CI/CD scenarios, you might need to change the context. By default, Visual Studio uses the
         folder above the Dockerfile. The path is relative to the Dockerfile, so here the context is
         set to the same folder as the Dockerfile. -->
    <DockerfileContext>.</DockerfileContext>
    <!-- Set `docker run` arguments to mount a volume -->
    <DockerfileRunArguments>-v $(pwd)/host-folder:/container-folder:ro</DockerfileRunArguments>
    <!-- Set `docker build` arguments to add a custom tag -->
    <DockerfileBuildArguments>-t contoso/front-end:v2.0</DockerfileBuildArguments>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.VisualStudio.Azure.Containers.Tools.Targets" Version="1.10.6" />
  </ItemGroup>

</Project>
```

## <a name="next-steps"></a>Sonraki adımlar

MSBuild özellikler hakkında daha fazla bilgi için bkz. [MSBuild properties](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[Docker Compose derleme özellikleri](docker-compose-properties.md)

[Kapsayıcı araçları başlatma ayarları](container-launch-settings.md)

[MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
