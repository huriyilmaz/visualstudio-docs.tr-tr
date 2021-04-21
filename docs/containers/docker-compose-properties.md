---
title: Docker Compose derleme ayarları
author: ghogen
description: Visual Studio 'Nun bir Docker Compose uygulamasını nasıl oluşturup yürüttüleceğini özelleştirmek için Docker Compose derleme özelliklerini nasıl düzenleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.author: ghogen
ms.date: 04/06/2021
ms.technology: vs-azure
ms.topic: reference
ms.openlocfilehash: 7f1ebb11133c640c2e0bdcfd84660592792d4205
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825010"
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

| Özellik adı | Konum | Description | Varsayılan değer  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFilePaths|dcproj|Tüm komutlar için docker-compose.exe gönderilmek üzere, noktalı virgülle ayrılmış bir listede ek oluşturma dosyaları belirtir. Docker-Compose proje dosyasından (dcproj) göreli yollara izin verilir.|-|
|DockerComposeBaseFilePath|dcproj|Docker-Compose dosyalarının dosya adlarının ilk kısmını *. yıml* uzantısı olmadan belirtir. Örnek: <br>1. DockerComposeBaseFilePath = null/tanımsız: *Docker-Compose* taban dosya yolunu kullanın ve dosyalar *Docker-Compose. yml* ve *Docker-Compose. override. yml* olarak adlandırılır<br>2. DockerComposeBaseFilePath = *mydockercompose*: dosyalar *mydockercompose. yml* ve *mydockercompose. override. yml* olarak adlandırılacak<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: dosyalar bir düzey yukarı kalacak. |Docker-Compose|
|DockerComposeBuildArguments|dcproj|Komuta geçirilecek ek parametreleri belirtir `docker-compose build` . Örneğin, `--parallel --pull` |
|DockerComposeDownArguments|dcproj|Komuta geçirilecek ek parametreleri belirtir `docker-compose down` . Örneğin, `--timeout 500`|-|
|DockerComposeProjectName| dcproj | Belirtilmişse, Docker-Compose projesi için proje adını geçersiz kılar. | "dockercompose" + otomatik üretilen karma |
|DockerComposeProjectPath|csproj veya vbproj|Docker-Compose projesi (dcproj) dosyasının göreli yolu. Docker-Compose. yıml dosyasında depolanan ilişkili görüntü derleme ayarlarını bulmak için hizmet projesini yayımlarken bu özelliği ayarlayın.|-|
|DockerComposeUpArguments|dcproj|Komuta geçirilecek ek parametreleri belirtir `docker-compose up` . Örneğin, `--timeout 500`|-|
|DockerDevelopmentMode|dcproj| "Konak oluşturma" iyileştirmesi ("hızlı mod" hata ayıklama) etkin olup olmadığını denetler.  İzin verilen değerler `Fast` ve ' dir `Regular` . | `Fast` Hata ayıklama yapılandırmasında veya `Regular` diğer tüm yapılandırmalarda |
|DockerLaunchAction| dcproj | F5 veya CTRL + F5 üzerinde gerçekleştirilecek başlatma eylemini belirtir.  İzin verilen değerler None, LaunchBrowser ve LaunchWCFTestClient 'Tur.|Yok|
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

## <a name="overriding-visual-studios-docker-compose-configuration"></a>Visual Studio 'nun Docker Compose yapılandırmasını geçersiz kılma

*Docker-Compose. yıml* dosyanızdaki aynı dizinde *Docker-Compose. vs. Debug. Yıml* ( **hızlı** mod için) veya *Docker-Compose. vs. Release. yıml* ( **normal** mod için) adlı bir dosya yerleştirerek belirli ayarları geçersiz kılabilirsiniz. 

>[!TIP] 
>Bu ayarlardan herhangi birinin varsayılan değerlerini bulmak için *Docker-Compose. vs. Debug. g. yıml* veya *Docker-Compose. vs. Release. g. yıml* bölümüne bakın.

### <a name="docker-compose-file-labels"></a>Docker Compose dosya etiketleri

 *Docker-Compose. vs. Debug. yml* veya *Docker-Compose. vs. Release. yml* içinde, geçersiz kılmaya özgü etiketleri aşağıdaki gibi tanımlayabilirsiniz:

```yml
services:
  webapplication1:
    labels:
      com.microsoft.visualstudio.debuggee.workingdirectory: "C:\\my_app_folder"
```

Yukarıdaki örnekte olduğu gibi, değerlerin etrafında çift tırnak işareti kullanın ve ters eğik çizgiyi yollarda ters eğik çizgi için kaçış karakteri olarak kullanın.

|Etiket adı|Description|
|----------|-----------|
|com. Microsoft. VisualStudio. debugayıklanan. Arguments|Hata ayıklama başlatılırken programa geçirilen bağımsız değişkenler. .NET Core uygulamaları için, bu bağımsız değişkenler genellikle NuGet paketleri için ek arama yollarıdır ve ardından projenin çıkış derlemesinin yoludur.|
|com. Microsoft. VisualStudio. debugayıklanan. program|Hata ayıklama başlatılırken program başlatıldı. .NET Core uygulamaları için bu ayar genellikle **DotNet**' dir.|
|com. Microsoft. VisualStudio. debugayıklanan. WorkingDirectory|Hata ayıklama başlatılırken başlangıç dizini olarak kullanılan dizin. Bu ayar genellikle Linux kapsayıcıları için */App* veya Windows kapsayıcıları için *c:\app* ' dir.|
|com. Microsoft. VisualStudio. debugayıklanan. killprogram|Bu komut, kapsayıcının içinde çalışan hata ayıklanan programı durdurmak için kullanılır (gerektiğinde).|

### <a name="customize-the-docker-build-process"></a>Docker Build işlemini özelleştirme

Özelliğindeki ayarı kullanarak Dockerfile içinde hangi aşamayı derlemek istediğinizi bildirebilirsiniz `target` `build` . Bu geçersiz kılma yalnızca *Docker-Compose. vs. Debug. yıml* veya *Docker-Compose. vs. Release. yıml* içinde kullanılabilir 

```yml
services:
  webapplication1:
    build:
      target: customStage
    labels:
      ...
```

### <a name="customize-the-app-startup-process"></a>Uygulama başlatma işlemini özelleştirme

Ayarını kullanarak uygulamanızı başlatmadan önce bir komut veya özel betik çalıştırabilir `entrypoint` ve bunu öğesine bağımlı hale getirebilirsiniz `DockerDevelopmentMode` . Örneğin, normal modda değil, yalnızca **hızlı** modda bir sertifika ayarlamanız gerekirse `update-ca-certificates` , aşağıdaki kodu **yalnızca** *Docker-Compose. vs. Debug. yml* içine ekleyebilirsiniz: 

```yml
services:
  webapplication1:
    entrypoint: "sh -c 'update-ca-certificates && tail -f /dev/null'"
    labels:
      ...
```

## <a name="next-steps"></a>Sonraki adımlar

MSBuild özellikleri hakkında genel bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[Kapsayıcı araçları derleme özellikleri](container-msbuild-properties.md)

[Kapsayıcı araçları başlatma ayarları](container-launch-settings.md)

[MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
