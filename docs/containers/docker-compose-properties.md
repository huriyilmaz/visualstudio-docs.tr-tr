---
title: Visual Studio kapsayıcı araçları Docker Compose derleme ayarları
author: ghogen
description: Kapsayıcı araçları derleme işlemine genel bakış
ms.author: ghogen
ms.date: 08/12/2019
ms.technology: vs-azure
ms.topic: conceptual
ms.openlocfilehash: 4ea1a936de215340cc13971e7a70a8d795d36cbb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73713935"
---
# <a name="docker-compose-build-properties"></a>Docker Compose derleme özellikleri

[Kapsayıcı araçları derleme özellikleri](container-msbuild-properties.md)bölümünde açıklanan, bağımsız Docker projelerini denetleyen özelliklere ek olarak, MSBuild 'in Docker Compose özelliklerini ayarlayarak Visual Studio 'nun Docker Compose projelerinizi nasıl derlemediğini de özelleştirebilirsiniz. çözümünüzü oluşturmak için kullanır. Ayrıca, Docker Compose yapılandırma dosyalarında dosya etiketlerini ayarlayarak Visual Studio hata ayıklayıcının Docker Compose uygulamalarınızı nasıl yürüttüğünde da denetleyebilirsiniz.

## <a name="how-to-set-the-msbuild-properties"></a>MSBuild özelliklerini ayarlama

Bir özelliğin değerini ayarlamak için proje dosyasını düzenleyin. Docker Compose özellikler için, bu proje dosyası bir sonraki bölümdeki tabloda aksi belirtilmedikçe. dcproj uzantılı bir uzantıdır. Örneğin, hata ayıklamaya başladığınızda tarayıcıyı başlatmak için belirtmek istediğinizi varsayalım. . Dcproj proje dosyasında `DockerLaunchAction` özelliğini aşağıdaki gibi ayarlayabilirsiniz.

```xml
<PropertyGroup>
   <DockerLaunchAction>LaunchBrowser</DockerLaunchAction>
</PropertyGroup>
```

Özellik ayarını mevcut bir `PropertyGroup` öğesine ekleyebilir veya bir tane yoksa, yeni bir `PropertyGroup` öğesi oluşturabilirsiniz.

## <a name="docker-compose-msbuild-properties"></a>MSBuild özelliklerini Docker Compose

Aşağıdaki tabloda Docker Compose projeleri için kullanılabilen MSBuild özellikleri gösterilmektedir.

| Özellik adı | Konum | Açıklama | Varsayılan değer  |
|---------------|----------|-------------|----------------|
|AdditionalComposeFiles|dcproj|Tüm komutlar için Docker-Compose. exe ' ye gönderilmek üzere noktalı virgülle ayrılmış bir listede ek oluşturma dosyaları belirtir. Docker-Compose proje dosyasından (dcproj) göreli yollara izin verilir.|-|
|DockerComposeBaseFilePath|dcproj|Docker-Compose dosyalarının dosya adlarının ilk kısmını *. yıml* uzantısı olmadan belirtir. Örneğin: <br>1. DockerComposeBaseFilePath = null/tanımsız: *Docker-Compose*taban dosya yolunu kullanın ve dosyalar *Docker-Compose. yml* ve *Docker-Compose. override. yml* olarak adlandırılır<br>2. DockerComposeBaseFilePath = *mydockercompose*: dosyalar *mydockercompose. yml* ve *mydockercompose. override. yml* olarak adlandırılacak<br> 3. DockerComposeBaseFilePath = *.. \mydockercompose*: dosyalar bir düzey yukarı kalacak. |Docker-Compose|
|DockerComposeBuildArguments|dcproj|`docker-compose build` komutuna geçirilecek ek parametreleri belirtir. Örneğin, `--parallel --pull` |
|DockerComposeDownArguments|dcproj|`docker-compose down` komutuna geçirilecek ek parametreleri belirtir. Örneğin, `--timeout 500`|-|  
|DockerComposeProjectPath|csproj veya vbproj|Docker-Compose projesi (dcproj) dosyasının göreli yolu. Docker-Compose. yıml dosyasında depolanan ilişkili görüntü derleme ayarlarını bulmak için hizmet projesini yayımlarken bu özelliği ayarlayın.|-|
|DockerComposeUpArguments|dcproj|`docker-compose up` komutuna geçirilecek ek parametreleri belirtir. Örneğin, `--timeout 500`|-|
|DockerLaunchAction| dcproj | F5 veya CTRL + F5 üzerinde gerçekleştirilecek başlatma eylemini belirtir.  İzin verilen değerler None, LaunchBrowser ve LaunchWCFTestClient 'Tur|Yok.|
|DockerLaunchBrowser| dcproj | Tarayıcının başlatılıp başlatılmayacağını belirtir. DockerLaunchAction belirtilmişse yoksayıldı. | False |
|DockerServiceName| dcproj|DockerLaunchAction veya DockerLaunchBrowser belirtilmişse DockerServiceName, başlatılacak hizmetin adıdır.  Bu özelliği kullanarak, bir Docker-Compose dosyasının başvurmasına yönelik olabilecek çok sayıda projeden hangisini başlatılacağı belirlenir.|-|
|DockerServiceUrl 'Si| dcproj | Tarayıcı başlatılırken kullanılacak URL.  Geçerli değiştirme belirteçleri şunlardır "{Serviceıpaddress}", "{ServicePort}" ve "{Scheme}".  Örneğin: {Scheme}: ı{serviceipaddress}: {ServicePort}|-|
|DockerTargetOS| dcproj | Docker görüntüsü oluşturulurken kullanılan hedef işletim sistemi.|-|

> [!NOTE]
> DockerComposeBuildArguments, DockerComposeDownArguments ve DockerComposeUpArguments, Visual Studio 2019 sürüm 16,3 ' de yenidir.

## <a name="docker-compose-file-labels"></a>Docker Compose dosya etiketleri

Ayrıca, aynı dizinde Docker-Compose. vs. Debug. yıml (hata ayıklama yapılandırması için) veya *Docker-Compose. vs. Release. yıml* (sürüm yapılandırması için) adlı bir dosya yerleştirerek belirli ayarları geçersiz kılabilirsiniz.  *Docker-Compose. yıml* dosyası.  Bu dosyada ayarları aşağıdaki gibi belirtebilirsiniz:

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

## <a name="next-steps"></a>Sonraki adımlar

MSBuild özellikleri hakkında genel bilgi için bkz. [MSBuild özellikleri](../msbuild/msbuild-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

[Kapsayıcı araçları derleme özellikleri](container-msbuild-properties.md)

[Kapsayıcı araçları başlatma ayarları](container-launch-settings.md)

[MSBuild ayrılmış ve iyi bilinen Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md)
