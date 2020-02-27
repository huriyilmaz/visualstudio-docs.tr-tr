---
title: GenerateResource Görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd5946612889e98b3b90f2ee3cb8665c43827a5e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634064"
---
# <a name="generateresource-task"></a>GenerateResource görevi

*. Txt* ve *. resx* (XML tabanlı kaynak biçimi) dosyalarını ve ortak dil çalışma zamanı ikili *. resources* dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemelerine derlenen. Bu görev genellikle *. txt* veya *. resx* dosyalarını *. resources* dosyalarına dönüştürmek için kullanılır. `GenerateResource` görevi [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)' ye benzer.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda `GenerateResource` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalInputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Bu görev tarafından gerçekleştirilen bağımlılık denetimi için ek girişler içerir. Örneğin, proje ve hedef dosyalar genellikle girdi olmalıdır, bu sayede güncelleniyorsa tüm kaynaklar yeniden oluşturulur.|
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametresi.<br /><br /> Normal ortam bloğunun yanı sıra (veya seçmeli olarak geçersiz kılan) üretilmiş *Resgen. exe*' ye geçirilmesi gereken ortam değişkenlerinin ad-değer çiftleri dizisini belirtir.|
|`ExcludedInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Güncel Denetim sırasında, izlenen girişlerin yoksayıldığı yolları belirten bir öğe dizisi belirtir.|
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, gerekli sarmalayıcı derlemelerini oluşturmak için uygun hedef Framework 'ten *Tlbimp. exe* ve *Aximp. exe* ' yi çalıştırır. Bu parametre `ResolveComReferences`çoklu hedeflemesini sağlar.|
|`FilesWritten`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Diske yazılan tüm dosyaların adlarını içerir. Bu, varsa önbellek dosyasını içerir. Bu parametre, temizleme uygulamaları için yararlıdır.|
|`MinimalRebuildFromTracking`|İsteğe bağlı `Boolean` parametresi.<br /><br /> İzlenen artımlı yapı 'un kullanılıp kullanılmayacağını belirten bir anahtar alır veya ayarlar. `true`, Artımlı derleme açıktır; Aksi takdirde, yeniden oluşturma zorunlu olacaktır.|
|`NeverLockTypeAssemblies`|İsteğe bağlı `Boolean` parametresi.<br /><br /> Kaynak ( *. resx*) dosyalarını (true) değerlendirmek için yeni bir [AppDomain](/dotnet/api/system.appdomain) oluşturulup oluşturulmayacağını veya yalnızca kaynak dosyaları bir kullanıcının derlemesine başvurması durumunda yeni bir [AppDomain](/dotnet/api/system.appdomain) oluşturma (false) öğesini belirten bir Boole değeri alır veya ayarlar.|
|`OutputResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Oluşturulan dosyaların ( *. resources* dosyaları gibi) adını belirtir. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve oluşturulan *. resources* dosyası giriş dosyasını içeren dizine yerleştirilir.|
|`PublicClass`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, bir genel sınıf olarak türü kesin belirlenmiş bir kaynak sınıfı oluşturur.|
|`References`|İsteğe bağlı `String[]` parametresi.<br /><br /> *. Resx* dosyalarındaki yükleme türlerine başvurular. *. resx* dosya verisi öğelerinin .NET türü olabilir. *. Resx* dosyası okun, bu, çözülmesi gerekir. Genellikle standart tür yükleme kuralları kullanılarak başarıyla çözümlenir. `References`derlemeleri sağlarsanız, bunlar önceliklidir.<br /><br /> Bu parametre, kesin olarak belirlenmiş kaynaklar için gerekli değildir.|
|`SdkToolsPath`|İsteğe bağlı `String` parametresi.<br /><br /> *Resgen. exe*gibi SDK araçlarının yolunu belirtir.|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dönüştürülecek öğeleri belirtir. Bu parametreye geçirilen öğeler aşağıdaki dosya uzantılarından birine sahip olmalıdır:<br /><br /> -    *. txt*: dönüştürülecek bir metin dosyası uzantısını belirtir. Metin dosyaları yalnızca dize kaynakları içerebilir.<br />-    *. resx*: dönüştürülecek XML tabanlı bir kaynak dosyası uzantısını belirtir.<br />-    *. restext*: *. txt*ile aynı biçimi belirtir. Bu farklı uzantı, yapı sürecinizdeki diğer kaynak dosyalardan kaynakları içeren kaynak dosyaları açıkça ayırt etmek istiyorsanız yararlıdır.<br />-    *. resources*: dönüştürülecek kaynak dosyanın uzantısını belirtir.|
|`StateFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> *. Resx* giriş dosyalarındaki bağlantıların bağımlılık denetimini hızlandırmak için kullanılan isteğe bağlı bir önbellek dosyasının yolunu belirtir.|
|`StronglyTypedClassName`|İsteğe bağlı `String` parametresi.<br /><br /> Türü kesin belirlenmiş kaynak sınıfı için sınıf adını belirtir. Bu parametre belirtilmemişse, kaynak dosyanın temel adı kullanılır.|
|`StronglyTypedFilename`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Kaynak dosya için dosya adını belirtir. Bu parametre belirtilmemişse, sınıfın adı, uzantısı dile bağlı olan temel dosya adı olarak kullanılır. Örneğin: *MyClass.cs*.|
|`StronglyTypedLanguage`|İsteğe bağlı `String` parametresi.<br /><br /> Türü kesin belirlenmiş kaynak için sınıf kaynağı oluşturulurken kullanılacak dili belirtir. Bu parametre CodeDomProvider tarafından kullanılan dillerden tam olarak eşleşmelidir. Örneğin: `VB` veya `C#`.<br /><br /> Bu parametreye bir değer geçirerek, görevin kesin olarak belirlenmiş kaynaklar oluşturmasını söyleyebilirsiniz.|
|`StronglyTypedManifestPrefix`|İsteğe bağlı `String` parametresi.<br /><br /> Türü kesin belirlenmiş kaynak için oluşturulan sınıf kaynağında kullanılacak kaynak ad alanını veya bildirim önekini belirtir.|
|`StronglyTypedNamespace`|İsteğe bağlı `String` parametresi.<br /><br /> Türü kesin belirlenmiş kaynak için oluşturulan sınıf kaynağı için kullanılacak ad alanını belirtir. Bu parametre belirtilmemişse, kesin olarak belirlenmiş tüm kaynaklar genel ad alanında bulunur.|
|`TLogReadFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>salt `[]` parametresi.<br /><br /> Okuma izleme günlüklerini temsil eden öğelerin bir dizisini alır.|
|`TLogWriteFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>salt `[]` parametresi.<br /><br /> Yazma izleme günlüklerini temsil eden öğelerin bir dizisini alır.|
|`ToolArchitecture`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> *Tracker. exe* ' nin *Resgen. exe*' yi oluşturma için kullanılması gerekip gerekmediğini belirlemekte kullanılır.<br /><br /> <xref:Microsoft.Build.Utilities.ExecutableType> sabit listesinin bir üyesine ayrıştırılamayan olmalıdır. `String.Empty`, varsayılan mimariyi belirlemede buluşsal bir değer kullanır. , Microsoft. Build. Utilities. ExecutableType numaralandırması üyesine ayrıştırılamayan olmalıdır.|
|`TrackerFrameworkPath`|İsteğe bağlı `String` parametresi.<br /><br /> *FileTracker. dll dosyasını*içeren uygun .NET Framework konumun yolunu belirtir.<br /><br /> Ayarlanırsa, Kullanıcı, işledikleri *FileTracker. dll* ' nin, kullanmayı düşündüğünüz *Resgen. exe* ' nin bit durumuyla eşleştiğinden emin olma sorumluluğunu üstlenir. Ayarlanmamışsa, görev geçerli .NET Framework sürümüne göre uygun konuma karar verir.|
|`TrackerLogDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Bu görevi çalıştırmanın İzleme günlüklerinin yerleştirileceği ara dizini belirtir.|
|`TrackerSdkPath`|İsteğe bağlı `String` parametresi.<br /><br /> *Tracker. exe*' yi içeren uygun Windows SDK konumun yolunu belirtir.<br /><br /> Ayarlanırsa, Kullanıcı, geçirdikleri *izleyici. exe* ' nin, kullanmayı düşündüğünüz *Resgen. exe* ' nin bit durumuyla eşleştiğinden emin olma sorumluluğunu alır. Ayarlanmamışsa, görev geçerli Windows SDK göre uygun konuma karar verir.|
|`TrackFileAccess`|İsteğe bağlı <xref:System.Boolean> parametresi.<br /><br /> True ise, göreli dosya yollarını çözümlemek için giriş dosyasının dizini kullanılır.|
|`UseSourcePath`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, girdi dosyasının dizininin göreli dosya yollarını çözümlemek için kullanılacağını belirtir.|

## <a name="remarks"></a>Açıklamalar

*. Resx* dosyaları diğer kaynak dosyalarına bağlantılar içerebileceğinden, çıkışların güncel olup olmadığını görmek için *. resx* ve *. resources* dosya zaman damgalarını karşılaştırmak yeterlidir. Bunun yerine, `GenerateResource` görevi *. resx* dosyalarındaki bağlantıları izler ve bağlantılı dosyaların zaman damgasını de denetler. Bu, genellikle `GenerateResource` görevi içeren hedef üzerinde `Inputs` ve `Outputs` özniteliklerini kullanmamalıdır, çünkü aslında çalışması gerektiği zaman atlanmasına neden olabilir.

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

.NET 3,5 projelerini hedeflemek için MSBuild 4,0 ' i kullanırken, derleme x86 kaynaklarında başarısız olabilir. Bu sorunu geçici olarak çözmek için, hedefi bir AnyCPU derlemesi olarak oluşturabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Resx` öğesi koleksiyonu tarafından belirtilen dosyalardan *. resources* dosyaları oluşturmak için `GenerateResource` görevini kullanır.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

`GenerateResource` görevi, bir derlemeye gömülü kaynağı adlandırmak için \<EmbeddedResource > öğesinin \<LogicalName > meta verilerini kullanır.

Derlemenin myAssembly olarak adlandırıldığını varsayarsak, aşağıdaki kod *Somequalifier. someResource. resources*adlı bir katıştırılmış kaynak oluşturur:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

\<LogicalName > meta verileri olmadan, kaynak *MyAssembly. myResource. resources*olarak adlandırılır.  Bu örnek yalnızca Visual Basic ve Visual C# derleme işlemi için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
