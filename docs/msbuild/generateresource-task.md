---
title: GenerateResource Görev | Microsoft Docs
description: .txt veya .resx dosyaları ile ortak dil çalışma zamanı ikili .resources dosyaları arasında dönüştürme yapmak için MSBuild GenerateResource görevini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateResource
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateResource task
- GenerateResource task [MSBuild]
ms.assetid: c0aff32f-f2cc-46f6-9c3e-a5c9f8f912b1
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 834d4f3949e5d201c1dc59311c2bf9a9ed77f5cf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115830"
---
# <a name="generateresource-task"></a>GenerateResource görevi

*.txt* *ve .resx* (XML tabanlı kaynak biçimi) dosyaları ile bir çalışma zamanı ikili yürütülebilir dosyasına ekli veya uydu derlemelerine derlenmiş ortak dil çalışma zamanı *ikili .resources* dosyaları arasında dönüştürür. Bu görev genellikle.txt *veya .resx* dosyalarını *.resources dosyalarına dönüştürmek için* kullanılır. Görev, `GenerateResource` işlevsel olarak [ ](/dotnet/framework/tools/resgen-exe-resource-file-generator)resgen.exe.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `GenerateResource` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalInputs`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bu görev tarafından yapılan bağımlılık denetimine ek girişler içerir. Örneğin, proje ve hedef dosyaları genellikle girişler olmalı, böylece güncelleştirildiğinde tüm kaynaklar yeniden oluşturulur.|
|`EnvironmentVariables`|İsteğe `String[]` bağlı parametre.<br /><br /> Normal ortam bloğuna ek olarak (veya seçmeli olarak geçersiz ** kılmaya) ek olarak,resgen.exegeçirilen ortam değişkenlerinin ad-değer çiftleri dizisini belirtir.|
|`ExcludedInputPaths`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Güncel denetim sırasında takip edilmiş girişlerin yoksayılacak yolları belirten bir öğe dizisi belirtir.|
|`ExecuteAsTool`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, gereklitlbimp.exeaximp.exeoluşturmak için uygun hedef çerçeveden yordam dışından derlemeyi çalıştırır `true` ve bunu çalıştırır.   Bu parametre, çoklu hedeflemeye izin `ResolveComReferences` verir.|
|`FilesWritten`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Diske yazılan tüm dosyaların adlarını içerir. Bu, varsa önbellek dosyasını içerir. Bu parametre, Clean uygulamaları için yararlıdır.|
|`MinimalRebuildFromTracking`|İsteğe `Boolean` bağlı parametre.<br /><br /> İzli artımlı derlemenin kullanılamayacaklarını belirten bir anahtar alır veya ayarlar. , `true` artımlı derleme açıksa; aksi takdirde, yeniden derleme zorlar.|
|`NeverLockTypeAssemblies`|İsteğe `Boolean` bağlı parametre.<br /><br /> Kaynakları değerlendirmek için yeni bir [AppDomain](/dotnet/api/system.appdomain) *(.resx*) dosyası (true) veya yalnızca kaynak dosyaları bir kullanıcının derlemeye başvurduysa (false) yeni [bir AppDomain](/dotnet/api/system.appdomain) oluşturularak yeni bir AppDomain oluşturulıp oluşturul olmadığını belirten bir Boole değeri alır veya ayarlar.|
|`OutputResources`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Oluşturulan dosyaların adını belirtir, örneğin *.resources* dosyaları. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve oluşturulan *.resources* dosyası giriş dosyasını içeren dizine yerleştirilir.|
|`PublicClass`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` kesin olarak türü kesin olarak belirtilen bir kaynak sınıfını genel bir sınıf olarak oluşturur.|
|`References`|İsteğe `String[]` bağlı parametre.<br /><br /> *.resx* dosyalarında yükleme türlerine başvurular. *.resx* dosya veri öğelerinin bir .NET türü olabilir. *.resx dosyası* okundu mu, bu çözümlenmiş gerekir. Genellikle, standart tür yükleme kuralları kullanılarak başarıyla çözümlenir. içinde derlemeler `References` sağlarsanız, bunlar önceliklidir.<br /><br /> Bu parametre, kesin olarak türü kesin olarak yazıldı kaynaklar için gerekli değildir.|
|`SdkToolsPath`|İsteğe `String` bağlı parametre.<br /><br /> SDK araçlarının yolunu belirtir, örneğin *resgen.exe.*|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dönüştürülecek öğeleri belirtir. Bu parametreye geçirilen öğelerin aşağıdaki dosya uzantılarından biri olması gerekir:<br /><br /> -   *.txt:* Dönüştürülecek metin dosyasının uzantısını belirtir. Metin dosyaları yalnızca dize kaynaklarını içerebilir.<br />-   *.resx:* Dönüştürülecek XML tabanlı bir kaynak dosyasının uzantısını belirtir.<br />-   *.restext:* ile aynı biçimi *.txt.* Derleme işleminizin diğer kaynak dosyalarından kaynakları içeren kaynak dosyaları net bir şekilde ayırt etmek için bu farklı uzantı yararlı olur.<br />-   *.resources:* Dönüştürülecek kaynak dosyasının uzantısını belirtir.|
|`StateFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> *.resx* giriş dosyalarında bağlantıların bağımlılık denetlemesini hızlandırmak için kullanılan isteğe bağlı önbellek dosyasının yolunu belirtir.|
|`StronglyTypedClassName`|İsteğe `String` bağlı parametre.<br /><br /> Kesin olarak türü kesin olarak belirtilen kaynak sınıfı için sınıf adını belirtir. Bu parametre belirtilmezse kaynak dosyasının temel adı kullanılır.|
|`StronglyTypedFilename`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Kaynak dosyanın dosya adını belirtir. Bu parametre belirtilmezse, sınıfın adı temel dosya adı olarak kullanılır ve uzantı dile bağımlıdır. Örneğin: *MyClass.cs*.|
|`StronglyTypedLanguage`|İsteğe `String` bağlı parametre.<br /><br /> Türü kesin olarak belirtilen kaynak için sınıf kaynağı oluşturmada kullanmak istediğiniz dili belirtir. Bu parametre CodeDomProvider tarafından kullanılan dillerden tam olarak biri ile eşleşmeli. Örneğin: `VB` veya `C#` .<br /><br /> Bu parametreye bir değer aktararak, göreve kesin türe sahip kaynaklar oluşturma talimatı verirsiniz.|
|`StronglyTypedManifestPrefix`|İsteğe `String` bağlı parametre.<br /><br /> Kesin olarak türü kesin olarak belirtilen kaynak için oluşturulan sınıf kaynağında kullanmak üzere kaynak ad alanını veya bildirim ön eklerini belirtir.|
|`StronglyTypedNamespace`|İsteğe `String` bağlı parametre.<br /><br /> Kesin olarak türü kesin olarak belirtilen kaynak için oluşturulan sınıf kaynağı için kullanmak üzere ad alanını belirtir. Bu parametre belirtilmezse, kesin olarak belirtilmiş tüm kaynaklar genel ad alanı içindedir.|
|`TLogReadFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur parametre.<br /><br /> Okuma izleme günlüklerini temsil eden bir öğe dizisi alır.|
|`TLogWriteFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur parametre.<br /><br /> Yazma izleme günlüklerini temsil eden bir öğe dizisi alır.|
|`ToolArchitecture`|İsteğe <xref:System.String?displayProperty=fullName> bağlı parametre.<br /><br /> Bir veya daha fazlaTracker.exe *için* *ResGen.exe.*<br /><br /> Numaralamanın bir üyesiyle <xref:Microsoft.Build.Utilities.ExecutableType> ayrıştırılabilir olması gerekir. ise, `String.Empty` varsayılan bir mimariyi belirlemek için biruristic kullanır. cutableType enumeration'ın Microsoft.Build.Utilities.Exeayrıştırılabilir olması gerekir.|
|`TrackerFrameworkPath`|İsteğe `String` bağlı parametre.<br /><br /> dosya içeren uygun .NET Framework konumunun *yolunuFileTracker.dll.*<br /><br /> Ayarlanırsa, kullanıcı, geçiş yaptıkları uygulamanın bit FileTracker.dllkullanımının amacı olanResGen.exebitliğiyle *eş olduğundan* emin olmak için sorumluluğu üst alır. Ayarlanmazsa, görev geçerli sürüme göre uygun .NET Framework verir.|
|`TrackerLogDirectory`|İsteğe `String` bağlı parametre.<br /><br /> Bu görevi çalıştıran izleme günlüklerinin yerleştirilecek ara dizini belirtir.|
|`TrackerSdkPath`|İsteğe `String` bağlı parametre.<br /><br /> 'i içeren uygun Windows SDK konumunun *Tracker.exe.*<br /><br /> Ayarlanırsa, kullanıcı, geçiş yaptıkları uygulamanın bit Tracker.exekullanımının amacı olanResGen.exebitliğiyle *eş olduğundan* emin olmak için sorumluluğu üst alır. Ayarlanmazsa, görev geçerli sdk'sı temel alarak uygun Windows verir.|
|`TrackFileAccess`|İsteğe <xref:System.Boolean> bağlı parametre.<br /><br /> True ise, göreli dosya yollarını çözümlemek için giriş dosyasının dizini kullanılır.|
|`UseSourcePath`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` göreli dosya yollarını çözümlemek için giriş dosyasının dizininin kullan olacağını belirtir.|

## <a name="remarks"></a>Açıklamalar

*.resx* dosyaları diğer kaynak dosyalarına bağlantılar içereye sahip olduğundan, çıkışların güncel olup olmadığını görmek için *yalnızca .resx* ve *.resources* dosya zaman damgasını karşılaştırmak yeterli değildir. Bunun `GenerateResource` yerine, görev *.resx* dosyalarında bağlantıları izler ve bağlı dosyaların zaman damgasını da denetler. Bu, görevi içeren hedefte ve özniteliklerini genel olarak kullanmamanız gerektiği anlamına gelir, çünkü bu, gerçekten çalıştırdığında `Inputs` `Outputs` `GenerateResource` atlanabilir.

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

.NET 3.5 projelerini hedeflemek için MSBuild 4.0'ı kullanırken, derleme x86 kaynaklarında başarısız olabilir. Bu sorunu çözmek için hedefi AnyCPU derlemesi olarak derlemeniz gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğe `GenerateResource` koleksiyonu tarafından belirtilen *dosyalardan .resources* dosyaları oluşturmak için `Resx` görevini kullanır.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Görev, `GenerateResource` bir \<LogicalName> derlemeye eklenmiş olan \<EmbeddedResource> kaynağın adını oluşturmak için bir öğenin meta verilerini kullanır.

Derlemenin myAssembly olarak adlandırılmış olduğunu varsayarak, aşağıdaki kod *someQualifier.someResource.resources* adlı katıştırılmış bir kaynak üretir:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Meta veriler \<LogicalName> olmadan, kaynağın adı *myAssembly.myResource.resources olur.*  Bu örnek yalnızca Visual Basic Visual C# derleme işlemi için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
