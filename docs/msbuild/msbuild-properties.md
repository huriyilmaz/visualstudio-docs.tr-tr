---
title: MSBuild özellikleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, properties
ms.assetid: 962912ac-8931-49bf-a88c-0200b6e37362
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39f1f612244fedcc707475d067e67500dc76e1d9
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633297"
---
# <a name="msbuild-properties"></a>MSBuild özellikleri

Özellikler, yapıları yapılandırmak için kullanılabilen ad-değer çiftleridir. Özellikler, değerlerin görevlere geçirilmesinde, koşulların değerlendirilmesinde ve proje dosyası boyunca başvurulacak olan değerlerin depolanmasında yararlıdır.

## <a name="define-and-reference-properties-in-a-project-file"></a>Proje dosyasında özellikleri tanımlama ve başvuru

 Özellikler, bir [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) öğesinin alt öğesi olarak özelliğin adına sahip bir öğe oluşturularak belirtilir. Örneğin aşağıdaki XML, bir `BuildDir` değerine sahip olan `Build` adında bir özellik oluşturur.

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Proje dosyasının tamamında, Özellikler $ (\<PropertyName >) sözdizimi kullanılarak başvurulur. Örneğin, önceki örnekteki özellik $(BuildDir) kullanılarak başvurulur.

 Özelliği yeniden tanımlayarak özellik değerlerini değiştirebilirsiniz. Aşağıdaki XML kullanılarak `BuildDir` özelliğine yeni bir değer verilebilir:

```xml
<PropertyGroup>
    <BuildDir>Alternate</BuildDir>
</PropertyGroup>
```

 Özellikler, proje dosyasında göründükleri sırayla değerlendirilir. `BuildDir` öğesine ait yeni değerin, eski değer atandıktan sonra bildirilmesi gerekir.

## <a name="reserved-properties"></a>Ayrılmış Özellikler

 MSBuild, proje dosyası ve MSBuild ikili dosyaları hakkındaki bilgileri depolamak için bazı özellik adlarını saklar. Bu özellikler, diğer özelliklere benzer şekilde $ simgesi kullanılarak başvurulur. Örneğin $(MSBuildProjectFile), dosya adı uzantısı dahil olmak üzere proje dosyasının tüm dosya adını döndürür.

 Daha fazla bilgi için bkz. [nasıl yapılır: proje dosyasının adına veya konumuna başvurma](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md) ve özel olarak [bilinen MSBuild ve tanınmış Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="environment-properties"></a>Ortam özellikleri

 Proje dosyalarındaki ortam değişkenlerine, ayrılmış özelliklere başvurduğunuz şekilde başvurabilirsiniz. Örneğin, proje dosyanızda `PATH` ortam değişkenini kullanmak için, $(Yol) işaretini kullanın. Proje, ortam özelliği ile aynı ada sahip bir özellik tanımı içeriyorsa projedeki özellik, ortam değişkeninin değerini geçersiz kılar.

 Her MSBuild projesi bir yalıtılmış ortam bloğuna sahiptir; yalnızca kendi bloğundaki okumaları ve yazmaları görür.  Proje dosyası değerlendirilmeden veya oluşturulmadan önce MSBuild, özellik koleksiyonunu başlattığında yalnızca ortam değişkenlerini okur. Bunun ardından bu ortam özellikleri statiktir, yani her bir araç aynı adlar ve değerler ile başlar.

 Oluşturulan bir araç içinden ortam değişkenlerinin geçerli değerini almak için System. Environment. GetEnvironmentVariable [özelliğini](../msbuild/property-functions.md) kullanın. Ancak tercih edilen yöntem, <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> görev parametresinin kullanılmasıdır. Bu dize dizisinde ayarlanan ortam özellikleri, sistem ortamı değişkenlerini etkilemeden oluşturulan araca gönderilebilir.

> [!TIP]
> Tüm ortam değişkenleri, başlangıç özellikleri olması için okunmaz. Adı geçerli bir MSBuild özellik adı olmayan ("386" gibi) herhangi bir ortam değişkeni yok sayılır.

 Daha fazla bilgi için bkz. [nasıl yapılır: bir derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md).

## <a name="registry-properties"></a>Kayıt defteri özellikleri

 Aşağıdaki sözdizimini kullanarak sistem kayıt defteri değerlerini okuyabilirsiniz, burada `Hive` kayıt defteri Hive (örneğin, **HKEY_LOCAL_MACHINE**), `MyKey` anahtar adı, `MySubKey` alt anahtar adı ve `Value` alt anahtarın değeridir.

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

## <a name="global-properties"></a>Genel Özellikler

 MSBuild, **-Property** (veya **-p**) anahtarını kullanarak komut satırında özellikleri ayarlamanıza olanak sağlar. Bu genel özellik değerleri proje dosyasında ayarlanan özellik değerlerini geçersiz kılar. Bu ortam özellikleri içerir, ancak değiştirilemeyen ayrılmış özellikleri içermez.

 Aşağıdaki örnek genel `Configuration` özelliğini `DEBUG` olarak ayarlar.

```cmd
msbuild.exe MyProj.proj -p:Configuration=DEBUG
```

 Genel özellikler, MSBuild görevinin `Properties` özniteliğini kullanarak aynı zamanda çoklu bir proje yapısındaki alt projeler için ayarlanabilir veya değiştirilebilir. Genel Özellikler Ayrıca, MSBuild görevinin `RemoveProperties` özniteliği, iletilmeyecek özelliklerin listesini belirtmek için kullanılmamışsa alt projelere de iletilir. Daha fazla bilgi için bkz. [MSBuild görevi](../msbuild/msbuild-task.md).

 Bir proje etiketinde `TreatAsLocalProperty` özniteliğini kullanarak bir özellik belirtirseniz bu genel özellik değeri, proje dosyasında ayarlanan özellik değerini geçersiz kılmaz. Daha fazla bilgi için bkz. [Proje öğesi (MSBuild)](../msbuild/project-element-msbuild.md) ve [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md).

## <a name="property-functions"></a>Özellik işlevleri

 .NET Framework sürüm 4'ten başlayarak, MSBuild komut dosyalarınızı değerlendirmek için özellik işlevlerini kullanabilirsiniz. MSBuild görevlerini kullanmadan, yapı komut dosyanızdaki sistem saatini okuyabilir, dizeleri karşılaştırabilir, normal ifadeleri eşleştirebilir ve başka birçok eylemi gerçekleştirebilirsiniz.

 Herhangi bir özelliğin üzerinde gerçekleştirmek için dize (örnek) yöntemlerini kullanabilirsiniz ve birçok sistem sınıfının statik yöntemlerini çağırabilirsiniz. Örneğin, bir yapı özelliğini bugünün tarihine aşağıdaki gibi ayarlayabilirsiniz.

```xml
<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>
```

 Daha fazla bilgi ve özellik işlevlerinin bir listesi için bkz. [özellik işlevleri](../msbuild/property-functions.md).

## <a name="create-properties-during-execution"></a>Yürütme sırasında özellikler oluşturma

 `Target` öğeleri dışında konumlanan özelliklere, bir yapının değerlendirme aşamasında değerler atanır. Sonraki yürütme aşamasında özellikler aşağıdaki şekilde oluşturulabilir veya değiştirilebilir:

- Bir özellik herhangi bir görev tarafından yayılabilir. Bir özelliği göstermek için, [görev](../msbuild/task-element-msbuild.md) öğesinin bir `PropertyName` özniteliğine sahip bir alt [Çıkış](../msbuild/output-element-msbuild.md) öğesi olması gerekir.

- Bir özellik [CreateProperty](../msbuild/createproperty-task.md) görevi tarafından dağıtılabilir. Bu kullanım önerilmiyor.

- .NET Framework 3.5'de başlayarak `Target` öğeleri, özellik bildirimlerini içerebilen `PropertyGroup` öğelerini içerebilir.

## <a name="store-xml-in-properties"></a>Özelliklerde XML 'yi depola

 Özellikler, değerlerin görevlere geçirilmesini veya günlük bilgilerin görüntülenmesini sağlayabilecek rastgele bir XML içerebilir. Aşağıdaki örnek, XML ve diğer özellik başvurularını içeren bir değere sahip olan `ConfigTemplate` özelliğini gösterir. MSBuild, özellik başvurularını kendi ilgili özellik değerlerini kullanarak değiştirir. Özellik değerleri göründükleri sırayla atanır. Bu nedenle bu örnekte, `$(MySupportedVersion)`, `$(MyRequiredVersion)` ve `$(MySafeMode)` öğelerinin önceden tanımlanmış olması gerekir.

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
- [Nasıl yapılır: bir derlemede ortam değişkenlerini kullanma](../msbuild/how-to-use-environment-variables-in-a-build.md)
- [Nasıl yapılır: proje dosyasının adına veya konumuna başvurma](../msbuild/how-to-reference-the-name-or-location-of-the-project-file.md)
- [Nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları derleme](../msbuild/how-to-build-the-same-source-files-with-different-options.md)
- [MSBuild ayrılmış ve iyi bilinen Özellikler](../msbuild/msbuild-reserved-and-well-known-properties.md)
- [Property öğesi (MSBuild)](../msbuild/property-element-msbuild.md)
