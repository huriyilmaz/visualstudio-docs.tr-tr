---
title: Visual Studio Konteyner Araçları Docker Oluşturma yapı ayarları
author: ghogen
description: Konteyner Araçları oluşturma sürecine genel bakış
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 85cb8745a14439cfb09036a1bc96e6bd0fa15ae4
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988511"
---
# <a name="docker-compose-build-properties"></a>Docker Oluşturma yapı özellikleri

[Konteyner Araçları yapı özellikleri](container-msbuild-properties.md)açıklanan tek tek Docker projelerini kontrol eden özelliklere ek olarak, VISUAL Studio'nun, MSBuild'in çözümünüzü oluşturmak için kullandığı Docker Compose özelliklerini ayarlayarak Docker Compose projelerinizi nasıl oluşturduğunu da özelleştirebilirsiniz. Ayrıca, Docker Compose yapılandırma dosyalarında dosya etiketleri ayarlayarak Visual Studio hata ayıklama aracının Docker Compose uygulamalarınızı nasıl çalıştırdığını da denetleyebilirsiniz.

## <a name="how-to-set-the-msbuild-properties"></a>MSBuild özellikleri nasıl ayarlanır?

Bir özelliğin değerini ayarlamak için proje dosyasını edin. Docker Compose özellikleri için, bir sonraki bölümdeki tabloda aksi belirtilmedikçe, bu proje dosyası .dcproj uzantılı dosyadır. Örneğin, hata ayıklamaya başladığınızda tarayıcıyı başlatmak için belirtmek istediğinizi varsayalım. .dcproj `DockerLaunchAction` proje dosyasındaki özelliği aşağıdaki gibi ayarlayabilirsiniz.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Özellik ayarını varolan `PropertyGroup` bir öğeye ekleyebilirsiniz veya yoksa yeni `PropertyGroup` bir öğe oluşturabilirsiniz.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose MSBuild özellikleri

Aşağıdaki tablo, Docker Compose projeleri için kullanılabilir MSBuild özelliklerini gösterir.

| Özellik adı | Konum | Açıklama | Varsayılan değer  |
|---------------|----------|-------------|----------------|
|EkComposeFilePaths|dcproj|Tüm komutlar için docker-compose.exe'ye gönderilecek yarı sütunlu sınırlı bir listede ki ek dosyaları belirtir. Docker-compose proje dosyasından (dcproj) göreli yollara izin verilir.|-|
|DockerComposeBaseFilePath|dcproj|*.yml* uzantısı olmadan docker-compose dosyalarının dosya adlarının ilk bölümünü belirtir. Örnek: <br>1. DockerComposeBaseFilePath = null/undefined: temel dosya yolu *docker-compose*kullanın ve dosyaları *docker-compose.yml* ve *docker-compose.override.yml* adlı olacaktır<br>2. DockerComposeBaseFilePath = *mydockercompose*: dosyaları *mydockercompose.yml* ve *mydockercompose.override.yml* adlı olacaktır<br> 3. DockerComposeBaseFilePath = *. \mydockercompose*: dosyalar bir seviye kadar olacaktır. |docker-compose|
|DockerComposeBuildArguments|dcproj|Komuta geçmek için ekstra parametreleri `docker-compose build` belirtir. Örneğin, `--parallel --pull` |
|DockerComposeDownBağımsız Değişkenler|dcproj|Komuta geçmek için ekstra parametreleri `docker-compose down` belirtir. Örneğin, `--timeout 500`|-|  
|DockerComposeProjectPath|csproj veya vbproj|Docker-comproject (dcproj) dosyasına göreli yol. Docker-compose.yml dosyasında depolanan ilişkili görüntü oluşturma ayarlarını bulmak için hizmet projesini yayımlarken bu özelliği ayarlayın.|-|
|DockerComposeUpArguments|dcproj|Komuta geçmek için ekstra parametreleri `docker-compose up` belirtir. Örneğin, `--timeout 500`|-|
|DockerDevelopmentMode|dcproj| "Ev sahibi" optimizasyonu ("Hızlı Mod" hata ayıklama) etkin olup olmadığını denetler.  İzin verilen değerler **Hızlı** ve **Düzenli'dir.** | Hızlı |
|DockerLaunchAction| dcproj | F5 veya Ctrl+F5 üzerinde gerçekleştirmek için başlatma eylemini belirtir.  İzin verilen değerler Yok, LaunchBrowser ve LaunchWCFTestClient'dır|None|
|DockerLaunchBrowser| dcproj | Tarayıcıyı başlatıp başlatmayacağını gösterir. DockerLaunchAction belirtilirse yoksayılır. | False |
|DockerServiceName| dcproj|DockerLaunchAction veya DockerLaunchBrowser belirtilmişse, DockerServiceName başlatılması gereken hizmetin adıdır.  Docker-compose dosyasının başlatılacak olası birçok projeden hangisinin başlatılacak olabileceğini belirlemek için bu özelliği kullanın.|-|
|DockerServiceUrl| dcproj | Tarayıcıyı başlatırken kullanılacak URL.  Geçerli yedek belirteçler "{ServiceIPAddress}", "{ServicePort}" ve "{Scheme}" dır.  Örneğin: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Docker görüntüsünü oluştururken kullanılan hedef işletim sistemi.|-|

## <a name="example"></a>Örnek

Docker'ın dosyaları oluşturan konumunu, göreceli bir `DockerComposeBaseFilePath` yola ayarlayarak değiştirirseniz, çözüm klasörüne başvurulması için yapı bağlamının değiştirilip değiştirildiğinden de emin olmanız gerekir. Örneğin, docker derleme dosyanız *DockerComposeFiles*adlı bir klasörse, docker compose dosyası yapı bağlamını ".." veya "." olarak ayarlamalıdır. /..", çözüm klasörüne göre nerede olduğuna bağlı olarak.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="15.0" Sdk="Microsoft.Docker.Sdk">
  <PropertyGroup Label="Globals">
    <ProjectVersion>2.1</ProjectVersion>
    <DockerTargetOS>Windows</DockerTargetOS>
    <ProjectGuid>154022c1-8014-4e9d-bd78-6ff46670ffa4</ProjectGuid>
    <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
    <DockerServiceUrl>{Scheme}://{ServiceIPAddress}{ServicePort}</DockerServiceUrl>
    <DockerServiceName>webapplication1</DockerServiceName>
    <DockerComposeBaseFilePath>DockerComposeFiles\mydockercompose</DockerComposeBaseFilePath>
    <AdditionalComposeFilePaths>AdditionalComposeFiles\myadditionalcompose.yml</AdditionalComposeFilePaths>
  </PropertyGroup>
  <ItemGroup>
    <None Include="DockerComposeFiles\mydockercompose.override.yml">
      <DependentUpon>DockerComposeFiles\mydockercompose.yml</DependentUpon>
    </None>
    <None Include="DockerComposeFiles\mydockercompose.yml" />
    <None Include=".dockerignore" />
  </ItemGroup>
</Project>
```

*Mydockercompose.yml* dosyası, çözüm klasörünün göreli yoluna ayarlanmış yapı bağlamıyla (bu `..`durumda) bu şekilde görünmelidir.

```yml
version: '3.4'

services:
  webapplication1:
    image: ${DOCKER_REGISTRY-}webapplication1
    build:
      context: ..
      dockerfile: WebApplication1\Dockerfile
```

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments ve DockerComposeUpArguments Visual Studio 2019 sürümü 16.3 yeni.

## <a name="docker-compose-file-labels"></a>Docker Dosya etiketleri oluşturun

*Docker-compose.vs.debug.yml* **(Hata Ayıklama** yapılandırması için) veya *docker-compose.release.yml* **(Sürüm** yapılandırması için) adlı bir dosyayı *docker-compose.yml* dosyanızla aynı dizine yerleştirerek belirli ayarları geçersiz kılabilirsiniz.  Bu dosyada, ayarları aşağıdaki gibi belirtebilirsiniz:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Önceki örnekte olduğu gibi değerlerin etrafında çift tırnak kullanın ve yollarda ters eğik çizgi için bir kaçış karakteri olarak ters eğik çizgi kullanın.

|Etiket adı|Açıklama|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Bağımsız değişkenler hata ayıklama başlarken programa geçti. .NET Core uygulamaları için bu bağımsız değişkenler genellikle Projenin çıktı derlemesine giden yolu izleyen NuGet paketleri için ek arama yollarıdır.|
|com.microsoft.visualstudio.debuggee.killprogram|Bu komut, kapsayıcının içinde çalışan hata ayıklama programını durdurmak için kullanılır (gerektiğinde).|
|com.microsoft.visualstudio.debuggee.program|Program hata ayıklama başlatılır başlattı. .NET Core uygulamaları için bu ayar genellikle **dotnet'tir.**|
|com.microsoft.visualstudio.debuggee.workingdirectory|Dizin hata ayıklama başlarken başlangıç dizini olarak kullanılır. Bu ayar genellikle Linux kapsayıcıları için */app* veya Windows kapsayıcıları için *C:\app'tir.*|

## <a name="customize-the-app-startup-process"></a>Uygulama başlatma işlemini özelleştirme

`entrypoint` Ayarı kullanarak ve yapılandırmaya bağımlı hale getirerek uygulamanızı başlatmadan önce bir komut veya özel komut dosyası çalıştırabilirsiniz. Örneğin, bir sertifikayı yalnızca **Hata Ayıklama** modunda `update-ca-certificates`çalıştırarak ayarlamanız gerekiyorsa, ancak **Sürüm** modunda değil, aşağıdaki kodu yalnızca *docker-compose.vs.debug.yml*olarak ekleyebilirsiniz:

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

*Docker-compose.vs.release.yml* veya *docker-compose.vs.debug.yml'i* atlarsanız Visual Studio varsayılan ayarlara göre bir tane oluşturur.

## <a name="next-steps"></a>Sonraki adımlar

Genel olarak MSBuild özellikleri hakkında bilgi için [MSBuild Özellikleri'ne](../msbuild/msbuild-properties.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

[Konteyner Araçları özellikleri oluşturmak](container-msbuild-properties.md)

[Konteyner Araçları başlatma ayarları](container-launch-settings.md)

[MSBuild ayrılmış ve iyi bilinen özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
