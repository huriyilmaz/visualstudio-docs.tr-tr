---
title: Docker Compose derleme ayarları
author: ghogen
description: Visual Studio 'Nun bir Docker Compose uygulamasını nasıl oluşturup yürüttüleceğini özelleştirmek için Docker Compose derleme özelliklerini nasıl düzenleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 0a27535e9c07f87391b3cdfd8440578e36feee9e
ms.sourcegitcommit: d577818d3d8e365baa55c6108fa8159c46ed8b43
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97846820"
---
# <a name="docker-compose-build-properties"></a>Docker Compose derleme özellikleri

[Kapsayıcı araçları derleme özellikleri](container-msbuild-properties.md)bölümünde açıklanan tek Docker projelerini denetleyen özelliklere ek olarak, MSBuild 'in çözümünüzü oluşturmak için kullandığı Docker Compose özelliklerini ayarlayarak Visual Studio 'nun Docker Compose projelerinizi nasıl derlemediğini de özelleştirebilirsiniz. Ayrıca, Docker Compose yapılandırma dosyalarında dosya etiketlerini ayarlayarak Visual Studio hata ayıklayıcının Docker Compose uygulamalarınızı nasıl yürüttüğünde da denetleyebilirsiniz.

## <a name="how-to-set-the-msbuild-properties"></a>MSBuild özelliklerini ayarlama

Bir özelliğin değerini ayarlamak için proje dosyasını düzenleyin. Docker Compose özellikler için, bu proje dosyası bir sonraki bölümdeki tabloda aksi belirtilmedikçe. dcproj uzantılı bir uzantıdır. Örneğin, hata ayıklamaya başladığınızda tarayıcıyı başlatmak için belirtmek istediğinizi varsayalım. `DockerLaunchAction`. Dcproj proje dosyasındaki özelliğini aşağıdaki gibi ayarlayabilirsiniz.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Özellik ayarını varolan bir `PropertyGroup` öğeye ekleyebilirsiniz, yoksa yeni bir `PropertyGroup` öğe oluşturun.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose MSBuild özellikleri

Aşağıdaki tabloda Docker Compose projeleri için kullanılabilen MSBuild özellikleri gösterilmektedir.

| Özellik adı | Konum | Açıklama | Varsayılan değer  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Tüm komutlar için docker-compose.exe gönderilmek üzere, noktalı virgülle ayrılmış bir listede ek oluşturma dosyaları belirtir. Docker-Compose proje dosyasından (dcproj) göreli yollara izin verilir.|-|
|DockerComposeBaseFilePath|dcproj|Docker-Compose dosyalarının dosya adlarının ilk kısmını *. yıml* uzantısı olmadan belirtir. Örneğin: <br>1. DockerComposeBaseFilePath = null/tanımsız: *Docker-Compose* taban dosya yolunu kullanın ve dosyalar *Docker-Compose. yml* ve *Docker-Compose. override. yml* olarak adlandırılır<br>2. DockerComposeBaseFilePath = *mydockercompose*: dosyalar *mydockercompose. yml* ve *mydockercompose. override. yml* olarak adlandırılacak<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: dosyalar bir düzey yukarı kalacak. |Docker-Compose|
|DockerComposeBuildArguments|dcproj|Komuta geçirilecek ek parametreleri belirtir `docker-compose build` . Örneğin, `--parallel --pull` |
|DockerComposeDownArguments|dcproj|Komuta geçirilecek ek parametreleri belirtir `docker-compose down` . Örneğin, `--timeout 500`|-|  
|DockerComposeProjectPath|csproj veya vbproj|Docker-Compose projesi (dcproj) dosyasının göreli yolu. Docker-Compose. yıml dosyasında depolanan ilişkili görüntü derleme ayarlarını bulmak için hizmet projesini yayımlarken bu özelliği ayarlayın.|-|
|DockerComposeUpArguments|dcproj|Komuta geçirilecek ek parametreleri belirtir `docker-compose up` . Örneğin, `--timeout 500`|-|
|DockerDevelopmentMode|dcproj| "Konak oluşturma" iyileştirmesi ("hızlı mod" hata ayıklama) etkin olup olmadığını denetler.  İzin verilen değerler **hızlı** ve **normal**. | Hızlı |
|DockerLaunchAction| dcproj | F5 veya CTRL + F5 üzerinde gerçekleştirilecek başlatma eylemini belirtir.  İzin verilen değerler None, LaunchBrowser ve LaunchWCFTestClient 'Tur|Hiçbiri|
|DockerLaunchBrowser| dcproj | Tarayıcının başlatılıp başlatılmayacağını belirtir. DockerLaunchAction belirtilmişse yoksayıldı. | Yanlış |
|DockerServiceName| dcproj|DockerLaunchAction veya DockerLaunchBrowser belirtilmişse DockerServiceName, başlatılacak hizmetin adıdır.  Bu özelliği kullanarak, bir Docker-Compose dosyasının başvurmasına yönelik olabilecek çok sayıda projeden hangisini başlatılacağı belirlenir.|-|
|DockerServiceUrl 'Si| dcproj | Tarayıcı başlatılırken kullanılacak URL.  Geçerli değiştirme belirteçleri şunlardır "{Serviceıpaddress}", "{ServicePort}" ve "{Scheme}".  Örneğin: {Scheme}: ı{serviceipaddress}: {ServicePort}|-|
|DockerTargetOS| dcproj | Docker görüntüsü oluşturulurken kullanılan hedef işletim sistemi.|-|

## <a name="example"></a>Örnek

Docker Compose dosyalarının konumunu `DockerComposeBaseFilePath` göreli bir yol olarak değiştirirseniz, yapı bağlamının çözüm klasörüne başvurması için değiştirildiğinden da emin olmanız gerekir. Örneğin, Docker oluşturma dosyanız *Dockercomposefiles* adlı bir klasörgerekliyse Docker Compose dosyası Build bağlamını ".." ya da ".. olarak ayarlanmalıdır. çözüm klasörüne göreli olduğu yere bağlı olarak.

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

*Mydockercompose. yıml* dosyası, derleme bağlamı çözüm klasörünün göreli yoluna (Bu durumda) ayarlanmış olarak şöyle görünmelidir `..` .

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
> DockerComposeBuildArguments, DockerComposeDownArguments ve DockerComposeUpArguments, Visual Studio 2019 sürüm 16,3 ' de yenidir.

## <a name="docker-compose-file-labels"></a>Docker Compose dosya etiketleri

Ayrıca, *Docker-Compose. yıml* dosyanızdaki aynı dizinde *Docker-Compose. vs. Debug. Yıml* ( **hata ayıklama** yapılandırması için) veya *Docker-Compose. vs. Release. yıml* ( **Sürüm** yapılandırması için) adlı bir dosya yerleştirerek belirli ayarları geçersiz kılabilirsiniz.  Bu dosyada ayarları aşağıdaki gibi belirtebilirsiniz:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Yukarıdaki örnekte olduğu gibi, değerlerin etrafında çift tırnak işareti kullanın ve ters eğik çizgiyi yollarda ters eğik çizgi için kaçış karakteri olarak kullanın.

|Etiket adı|Açıklama|
|----------|-----------|
|com. Microsoft. VisualStudio. debugayıklanan. Arguments|Hata ayıklama başlatılırken programa geçirilen bağımsız değişkenler. .NET Core uygulamaları için, bu bağımsız değişkenler genellikle NuGet paketleri için ek arama yollarıdır ve ardından projenin çıkış derlemesinin yoludur.|
|com. Microsoft. VisualStudio. debugayıklanan. killprogram|Bu komut, kapsayıcının içinde çalışan hata ayıklanan programı durdurmak için kullanılır (gerektiğinde).|
|com. Microsoft. VisualStudio. debugayıklanan. program|Hata ayıklama başlatılırken program başlatıldı. .NET Core uygulamaları için bu ayar genellikle **DotNet**' dir.|
|com. Microsoft. VisualStudio. debugayıklanan. WorkingDirectory|Hata ayıklama başlatılırken başlangıç dizini olarak kullanılan dizin. Bu ayar genellikle Linux kapsayıcıları için */App* veya Windows kapsayıcıları için *c:\app* ' dir.|

## <a name="customize-the-app-startup-process"></a>Uygulama başlatma işlemini özelleştirme

Ayarını kullanarak uygulamanızı başlatmadan önce bir komut veya özel betik çalıştırabilir `entrypoint` ve yapılandırmaya bağımlı hale getirebilirsiniz. Örneğin, serbest bırakma modunda değil, yalnızca **hata ayıklama** modunda bir sertifika ayarlamanız gerekirse `update-ca-certificates` , aşağıdaki kodu yalnızca *Docker-Compose. vs. Debug. yml* içine ekleyebilirsiniz: 

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

*Docker-Compose. vs. Release. yıml* veya *Docker-Compose. vs. Debug. yıml* ' yi atlarsanız, Visual Studio varsayılan ayarlara göre bir tane oluşturur.

## <a name="next-steps"></a>Sonraki adımlar

MSBuild özellikleri hakkında genel bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[Kapsayıcı araçları derleme özellikleri](container-msbuild-properties.md)

[Kapsayıcı araçları başlatma ayarları](container-launch-settings.md)

[MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
