---
title: MSBuild Özellikler | Microsoft Docs
description: Ad-MSBuild çiftlerinin görevlere değer geçişi, koşulları değerlendirme ve değerleri depolama hakkında bilgi alın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 2d1dec974c9271c12ab0780233a31361c4e7d359
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077185"
---
# <a name="msbuild-properties"></a>MSBuild özellikleri

Özellikler, yapıları yapılandırmak için kullanılabilen ad-değer çiftleridir. Özellikler, değerlerin görevlere geçirilmesinde, koşulların değerlendirilmesinde ve proje dosyası boyunca başvurulacak olan değerlerin depolanmasında yararlıdır.

## <a name="define-and-reference-properties-in-a-project-file"></a>Proje dosyasında özellikleri tanımlama ve başvuru

 Özellikler, bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesinin alt öğesi olarak özelliğin adına sahip bir öğe oluşturarak bildirildi. Örneğin aşağıdaki XML, bir `BuildDir` değerine sahip olan `Build` adında bir özellik oluşturur.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Proje dosyası boyunca özelliklere $(\<PropertyName>) söz dizimi kullanılarak başvurulur. Örneğin, önceki örnekteki özellik $(BuildDir) kullanılarak başvurulur.

 Özelliği yeniden tanımlayarak özellik değerlerini değiştirebilirsiniz. Aşağıdaki XML kullanılarak `BuildDir` özelliğine yeni bir değer verilebilir:

```xml
<PropertyGroup>
    <BuildDir>Alternate</BuildDir>
</PropertyGroup>
```

 Özellikler, proje dosyasında göründükleri sırayla değerlendirilir. `BuildDir` öğesine ait yeni değerin, eski değer atandıktan sonra bildirilmesi gerekir.

## <a name="reserved-properties"></a>Ayrılmış özellikler

 MSBuild, proje dosyası ve MSBuild ikili dosyaları hakkındaki bilgileri depolamak için bazı özellik adlarını saklar. Bu özellikler, diğer özelliklere benzer şekilde $ simgesi kullanılarak başvurulur. Örneğin $(MSBuildProjectFile), dosya adı uzantısı dahil olmak üzere proje dosyasının tüm dosya adını döndürür.

 Daha fazla bilgi için [bkz. Nasıl kullanılır: Proje](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) dosyasının adına veya konumuna başvurun ve MSBuild iyi [bilinen özelliklere bakın.](../msbuild/msbuild-reserved-and-well-known-properties.md)

## <a name="environment-properties"></a>Ortam özellikleri

 Proje dosyalarındaki ortam değişkenlerine, ayrılmış özelliklere başvurduğunuz şekilde başvurabilirsiniz. Örneğin, proje dosyanızda `PATH` ortam değişkenini kullanmak için, $(Yol) işaretini kullanın. Proje, ortam özelliği ile aynı ada sahip bir özellik tanımı içeriyorsa projedeki özellik, ortam değişkeninin değerini geçersiz kılar.

 Her MSBuild projesi bir yalıtılmış ortam bloğuna sahiptir; yalnızca kendi bloğundaki okumaları ve yazmaları görür.  Proje dosyası değerlendirilmeden veya oluşturulmadan önce MSBuild, özellik koleksiyonunu başlattığında yalnızca ortam değişkenlerini okur. Bunun ardından bu ortam özellikleri statiktir, yani her bir araç aynı adlar ve değerler ile başlar.

 Ortam değişkenlerinin geçerli değerini bir araçtan almak için [](../msbuild/property-functions.md) System.Environment.GetEnvironmentVariable Özellik işlevlerini kullanın. Ancak tercih edilen yöntem, <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> görev parametresinin kullanılmasıdır. Bu dize dizisinde ayarlanan ortam özellikleri, sistem ortamı değişkenlerini etkilemeden oluşturulan araca gönderilebilir.

> [!TIP]
> Tüm ortam değişkenleri, başlangıç özellikleri olması için okunmaz. Adı "386" gibi MSBuild bir özellik adı olmayan ortam değişkeni yoksayılır.

 Daha fazla bilgi için, [bkz. How to: Use environment variables in a build](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="registry-properties"></a>Kayıt defteri özellikleri

 Sistem kayıt defteri değerlerini aşağıdaki sözdizimini kullanarak okuyabilirsiniz; burada kayıt defteri kovanı `Hive` (örneğin, **HKEY_LOCAL_MACHINE),** anahtar adıdır, alt anahtar adıdır ve alt anahtarın `MyKey` `MySubKey` `Value` değeridir.

```xml
$(registry:Hive\MyKey\MySubKey@Value)
```

 Varsayılan alt anahtar değerini almak için `Value` öğesini atın.

```xml
$(registry:Hive\MyKey\MySubKey)
```

 Bu kayıt defteri değeri, bir yapı özelliğini başlatmak için kullanılabilir. Örneğin, Visual Studio web tarayıcısı giriş sayfasını temsil eden bir yapı özelliği oluşturmak için şu kodu kullanın:

```xml
<PropertyGroup>
  <VisualStudioWebBrowserHomePage>
    $(registry:HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\WebBrowser@HomePage)
  </VisualStudioWebBrowserHomePage>
<PropertyGroup>
```

## <a name="global-properties"></a>Genel özellikler

 MSBuild , -property (veya **-p** ) anahtarını kullanarak komut satırı özelliklerini **ayarlamaya** olanak sağlar. Bu genel özellik değerleri proje dosyasında ayarlanan özellik değerlerini geçersiz kılar. Bu ortam özellikleri içerir, ancak değiştirilemeyen ayrılmış özellikleri içermez.

 Aşağıdaki örnek genel `Configuration` özelliğini `DEBUG` olarak ayarlar.

```cmd
msbuild.exe MyProj.proj -p:Configuration=DEBUG
```

 Genel özellikler, MSBuild görevinin `Properties` özniteliğini kullanarak aynı zamanda çoklu bir proje yapısındaki alt projeler için ayarlanabilir veya değiştirilebilir. Genel özellikler ayrıca, MSBuild değil özellik listesini belirtmek için MSBuild alt `RemoveProperties` projelere iletebilirsiniz. Daha fazla bilgi için [bkz. MSBuild görev.](../msbuild/msbuild-task.md)

 Bir proje etiketinde `TreatAsLocalProperty` özniteliğini kullanarak bir özellik belirtirseniz bu genel özellik değeri, proje dosyasında ayarlanan özellik değerini geçersiz kılmaz. Daha fazla bilgi için [bkz. Project öğesi (MSBuild)](../msbuild/project-element-msbuild.md) ve [Nasıl kullanılır: Farklı seçeneklerle aynı kaynak dosyaları derleme.](../msbuild/how-to-build-the-same-source-files-with-different-options.md)

## <a name="property-functions"></a>Özellik işlevleri

 .NET Framework sürüm 4'ten başlayarak, MSBuild komut dosyalarınızı değerlendirmek için özellik işlevlerini kullanabilirsiniz. MSBuild görevlerini kullanmadan, yapı komut dosyanızdaki sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadeleri eşleştirebilir ve başka birçok eylemi gerçekleştirebilirsiniz.

 Herhangi bir özelliğin üzerinde gerçekleştirmek için dize (örnek) yöntemlerini kullanabilirsiniz ve birçok sistem sınıfının statik yöntemlerini çağırabilirsiniz. Örneğin, bir yapı özelliğini bugünün tarihine aşağıdaki gibi ayarlayabilirsiniz.

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

 Daha fazla bilgi ve özellik işlevlerinin listesi için bkz. [Özellik işlevleri.](../msbuild/property-functions.md)

## <a name="create-properties-during-execution"></a>Yürütme sırasında özellik oluşturma

 `Target` öğeleri dışında konumlanan özelliklere, bir yapının değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında özellikler aşağıdaki şekilde oluşturulabilir veya değiştirilebilir:

- Bir özellik herhangi bir görev tarafından yayılabilir. Bir özellik yayma için, [Görev öğesinin](../msbuild/task-element-msbuild.md) özniteliği [olan](../msbuild/output-element-msbuild.md) bir alt Çıkış öğesi olması `PropertyName` gerekir.

- Bir özellik [CreateProperty görevi tarafından yayma.](../msbuild/createproperty-task.md) Bu kullanım önerilmiyor.

- .NET Framework 3.5'de başlayarak `Target` öğeleri, özellik bildirimlerini içerebilen `PropertyGroup` öğelerini içerebilir.

## <a name="store-xml-in-properties"></a>XML'i özelliklerde depolama

 Özellikler, değerlerin görevlere geçirilmesini veya günlük bilgilerin görüntülenmesini sağlayabilecek rastgele bir XML içerebilir. Aşağıdaki örnek, XML ve diğer özellik başvurularını içeren bir değere sahip olan `ConfigTemplate` özelliğini gösterir. MSBuild, ilgili özellik değerlerini kullanarak özellik başvurularını değiştirir. Özellik değerleri göründükleri sırayla atanır. Bu nedenle bu örnekte, `$(MySupportedVersion)`, `$(MyRequiredVersion)` ve `$(MySafeMode)` öğelerinin önceden tanımlanmış olması gerekir.

```xml
<PropertyGroup>
    <ConfigTemplate>
        <Configuration>
            <Startup>
                <SupportedRuntime
                    ImageVersion="$(MySupportedVersion)"
                    Version="$(MySupportedVersion)"/>
                <RequiredRuntime
                    ImageVersion="$(MyRequiredVersion)"
                    Version="$(MyRequiredVersion)"
                    SafeMode="$(MySafeMode)"/>
            </Startup>
        </Configuration>
    </ConfigTemplate>
</PropertyGroup>
```

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Nasıl kullanılır: Derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md)
- [Nasıl olur: Proje dosyasının adına veya konumuna başvuru](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)
- [Nasıl kullanılır: Farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
- [MSBuild ayrılmış ve tanınmış özellikleri](../msbuild/msbuild-reserved-and-well-known-properties.md)
- [Özellik öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
