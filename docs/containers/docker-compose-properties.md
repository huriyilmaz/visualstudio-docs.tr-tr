---
title: Docker Compose ayarları oluşturma
author: ghogen
description: Bir uygulamanın nasıl Docker Compose çalıştırarak nasıl Visual Studio özelleştirmek için Docker Compose öğrenin.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-container-tools
ms.topic: reference
ms.openlocfilehash: e165f25d8f757bbf60cd7b71e9ebd9e411b98c74
ms.sourcegitcommit: 2eb12954b7b0ac9508fff11a86c54e880f3d104f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129439723"
---
# <a name="docker-compose-build-properties"></a>Docker Compose özellikleri oluşturma

[Kapsayıcı](container-msbuild-properties.md)Araçları derleme özelliklerinde açıklanan tek tek Docker projelerini denetleme özelliklerine ek olarak, çözümlerinizi derlemek için Visual Studio tarafından kullanılan Docker Compose özelliklerini ayarerek Docker Compose projelerinizi nasıl MSBuild özelleştirebilirsiniz. Yapılandırma dosyalarında dosya etiketlerini ayar Visual Studio hata ayıklayıcısının Docker Compose uygulamalarınızı nasıl Docker Compose de kontrol edin.

## <a name="how-to-set-the-msbuild-properties"></a>MSBuild ayarlama

Bir özelliğin değerini ayarlamak için proje dosyasını düzenleyin. Daha Docker Compose için, sonraki bölümde tabloda aksi belirtilmedikçe, bu proje dosyası .dcproj uzantısına sahip olan dosyadır. Örneğin, hata ayıklamaya başlarken tarayıcıyı başlatmak için belirtmek istediğinizi varsayalım. `DockerLaunchAction`.dcproj proje dosyasındaki özelliğini aşağıdaki gibi ayarlayın.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Özellik ayarını mevcut bir öğeye ekleyebilir veya yoksa yeni `PropertyGroup` bir öğe `PropertyGroup` oluşturabilirsiniz.

## <a name="docker-compose-msbuild-properties"></a>Docker Compose MSBuild özellikleri

Aşağıdaki tabloda, MSBuild projeleri için kullanılabilen Docker Compose yer alır.

| Özellik adı | Konum | Description | Varsayılan değer  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Tüm komutlar için dosya oluşturmak üzere noktalı virgülle ayrılmış bir listede ek oluşturma docker-compose.exe belirtir. docker-compose proje dosyasından (dcproj) göreli yollara izin verilir.|-|
|DockerComposeBaseFilePath|dcproj|*.yml* uzantısı olmadan docker-compose dosyalarının dosya adlarının ilk bölümünü belirtir. Örnek: <br>1. DockerComposeBaseFilePath = null/undefined: *docker-compose* temel dosya yolunu kullanın ve dosyalar *docker-compose.yml* ve *docker-compose.override.yml* olarak adlandırılmış olur.<br>2. DockerComposeBaseFilePath = *mydockercompose*: dosyalar *mydockercompose.yml* ve *mydockercompose.override.yml olarak adlandırılmıştır.*<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose:* dosyalar bir düzey yukarı çıkar. |docker-compose|
|DockerComposeBuildArguments|dcproj|Komuta geçilen ek parametreleri `docker-compose build` belirtir. Örneğin, `--parallel --pull`. |
|DockerComposeDownArguments|dcproj|Komuta geçilen ek parametreleri `docker-compose down` belirtir. Örneğin, `--timeout 500`.|-|  
|DockerComposeProjectName| dcproj | Belirtilirse, docker-compose projesi için proje adını geçersiz kılar. | "dockercompose" + otomatik olarak oluşturulan karma |
|DockerComposeProjectPath|csproj veya vbproj|docker-compose proje (dcproj) dosyasının göreli yolu. Docker-compose.yml dosyasında depolanan ilişkili görüntü derleme ayarlarını bulmak için hizmet projesini yayımlarken bu özelliği ayarlayın.|-|
|DockerComposeProjectsToIgnore|dcproj| Hata ayıklama sırasında docker-compose araçları tarafından yoksayılacak projeleri belirtir. Bu özellik herhangi bir proje için kullanılabilir. Dosya yolları iki yoldan biri belirtilebilir: <br> 1. dcproj'a göre. Örneğin, `<DockerComposeProjectsToIgnore>path\to\AngularProject1.csproj</DockerComposeProjectsToIgnore>`. <br> 2. Mutlak yollar.<br> **Not:** Yollar sınırlayıcı karakteriyle ayrılarak `;` ayrılabilir.|-|
|DockerComposeUpArguments|dcproj|Komuta geçilen ek parametreleri `docker-compose up` belirtir. Örneğin, `--timeout 500`.|-|
|DockerDevelopmentMode| dcproj | Kullanıcı projesinin kapsayıcıda yerleşik olup olmadığını kontrol eder. Bir Dockerfile **içinde** **hangi aşamaların** [yerleşik olduğunu Hızlı veya Normal](https://aka.ms/containerfastmode) denetimin izin verilen değerleri. Hata ayıklama yapılandırması varsayılan olarak Hızlı moddur ve aksi takdirde Normal moddur. | Hızlı |
|DockerLaunchAction| dcproj | F5 veya Ctrl+F5 üzerinde gerçekleştirecek başlatma eylemlerini belirtir.  İzin verilen değerler None, LaunchBrowser ve LaunchWCFTestClient değerleridir. | Hiçbiri |
|DockerLaunchBrowser| dcproj | Tarayıcının başlatıp başlatmay olmadığını gösterir. DockerLaunchAction belirtilirse yoksayılır. | Yanlış |
|DockerServiceName| dcproj| DockerLaunchAction veya DockerLaunchBrowser belirtilirse DockerServiceName, docker-compose dosyasında başvurulan hizmeti belirtir.|-|
|DockerServiceUrl| dcproj | Tarayıcıyı başlatmada kullanmak üzere URL.  Geçerli değiştirme belirteçleri: "{ServiceIPAddress}", "{ServicePort}" ve "{Scheme}".  Örneğin: {Scheme}://{ServiceIPAddress}:{ServicePort}|-|
|DockerTargetOS| dcproj | Docker görüntüsünün inşası için kullanılan hedef işletim sistemi.|-|

## <a name="example"></a>Örnek

Docker compose dosyalarının konumunu göreli bir yola ayarerek değiştirirseniz, çözüm klasörüne başvurarak derleme bağlamının değiştiri olduğundan da `DockerComposeBaseFilePath` emin olun. Örneğin, docker compose dosyanız *DockerComposeFiles* adlı bir klasörse docker compose dosyası derleme bağlamını ".." veya "." olarak ayarlamalı. /..", çözüm klasörünün göreli olduğu yere bağlı olarak.

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

Derleme bağlamı çözüm klasörünün göreli yoluna ayarlanmış şekilde *mydockercompose.yml* dosyası aşağıdaki gibi olmalıdır (bu `..` durumda).

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
> DockerComposeBuildArguments, DockerComposeDownArguments ve DockerComposeUpArguments, Visual Studio 2019 sürüm 16.3'te yenidir.

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Uygulamanın Visual Studio yapılandırmayı Docker Compose geçersiz kılma

Docker'ın standart Docker Compose ayarlarını geçersiz kılmak için sağladığı normal yol *docker-compose.override.debug.yml* ve *docker-compose.override.release.yml* dosyalarını kullanmaktır, ancak bu dosyalarda Visual Studio'a özgü ayarları geçersiz kamazsiniz. *docker-compose.vs.debug.yml* (Hızlı mod için) veya *docker-compose.vs.release.yml* (Normal mod için) adlı  bir dosyayı *docker-compose.yml* dosyanız ile aynı dizine yerleştirerek Visual Studio ayarlarını geçersiz kılabilirsiniz.  dosya adını kullanarak dosyayı oluşturun Dosya Gezgini sonra dosyayı docker-compose projenize eklemek için Var Olan Öğeyi  >   Ekle'yi kullanın.

>[!TIP] 
>Visual Studio ayarlarından herhangi biri için varsayılan değerleri bulmak için *docker-compose.vs.debug.g.yml* veya *docker-compose.vs.release.g.yml* için doğrudan ara çıktıya *(obj/Docker)* bakın. Bu dosyalar bir Visual Studio oluşturulur ve değiştirilmemelidir.

### <a name="docker-compose-file-labels"></a>Docker Compose etiketlerini değiştirme

 *docker-compose.vs.debug.yml* veya *docker-compose.vs.release.yml* içinde, geçersiz kılmaya özgü etiketleri aşağıdaki gibi tanımlayabilirsiniz:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Önceki örnekte olduğu gibi değerlerin etrafında çift tırnak kullanın ve yollarda ters eğik çizgi için kaçış karakteri olarak ters eğik çizgi kullanın.

|Etiket adı|Description|
|----------|-----------|
|com.microsoft.visualstudio.debuggee.arguments|Hata ayıklamaya başlarken programa geçirilen bağımsız değişkenler. .NET Core uygulamaları için bu bağımsız değişkenler genellikle NuGet paketleri için ek arama yolları ve ardından projenin çıkış derlemesi yoludur.|
|com.microsoft.visualstudio.debuggee.program|Program, hata ayıklamaya başlarken başlatıldı. .NET Core uygulamaları için bu ayar genellikle **dotnet'tir.**|
|com.microsoft.visualstudio.debuggee.workingdirectory|Hata ayıklamayı başlatma sırasında başlangıç dizini olarak kullanılan dizin. Bu ayar genellikle Linux *kapsayıcıları için /app* veya kapsayıcılar için *C:\app* Windows olur.|
|com.microsoft.visualstudio.debuggee.killprogram|Bu komut, kapsayıcının içinde çalışan hata ayıklama programını durdurmak için kullanılır (gerektiğinde).|

### <a name="customize-the-docker-build-process"></a>Docker derleme işlemini özelleştirme

özelliğinde ayarını kullanarak Dockerfile içinde hangi aşamanın `target` derlemek için `build` bildirebilirsiniz. Bu geçersiz kılma yalnızca *docker-compose.vs.debug.yml* veya *docker-compose.vs.release.yml içinde kullanılabilir* 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Uygulama başlatma işlemini özelleştirme

bir komut veya özel betik çalıştırarak, ayarını kullanarak ve bu ayarına bağımlı `entrypoint` hale kullanarak, uygulama başlatmadan önce çalıştırabilirsiniz. `DockerDevelopmentMode` Örneğin, çalıştıran ancak Normal modda olmayan  hızlı modda bir sertifikayı yalnızca hızlı modda ayarlamanız gerekirse, aşağıdaki kodu yalnızca `update-ca-certificates`  *docker-compose.vs.debug.yml* koduna eklersiniz: 

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Sonraki adımlar

Özellikleri genel olarak MSBuild için bkz. [MSBuild .](../msbuild/msbuild-properties.md)

## <a name="see-also"></a>Ayrıca bkz.

[Kapsayıcı Araçları derleme özellikleri](container-msbuild-properties.md)

[Kapsayıcı Araçları başlatma ayarları](container-launch-settings.md)

[Docker Compose'da Visual Studio için başlatma profillerini yönetme](launch-profiles.md)

[MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
