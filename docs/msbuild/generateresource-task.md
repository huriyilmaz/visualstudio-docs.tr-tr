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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634064"
---
# <a name="generateresource-task"></a>GenerateResource görevi

*. Txt* ve *. resx* (XML tabanlı kaynak biçimi) dosyalarını ve ortak dil çalışma zamanı ikili *. resources* dosyalarını, bir çalışma zamanı ikili çalıştırılabilir dosyasına katıştırılabilen veya uydu derlemelerine derlenen. Bu görev genellikle *. txt* veya *. resx* dosyalarını *. resources* dosyalarına dönüştürmek için kullanılır. `GenerateResource`Görev [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)benzerdir.

## <a name="parameters"></a>Parametreler

Aşağıdaki tablo, görevin parametrelerini açıklar `GenerateResource` .

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalInputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bu görev tarafından gerçekleştirilen bağımlılık denetimi için ek girişler içerir. Örneğin, proje ve hedef dosyalar genellikle girdi olmalıdır, bu sayede güncelleniyorsa tüm kaynaklar yeniden oluşturulur.|
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametre.<br /><br /> Düzenli ortam bloğunu (veya seçmeli olarak geçersiz kılan) ek olarak, oluşturulan *resgen.exe*geçirilmesi gereken ortam değişkenlerinin ad-değer çiftleri dizisini belirtir.|
|`ExcludedInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Güncel Denetim sırasında, izlenen girişlerin yoksayıldığı yolları belirten bir öğe dizisi belirtir.|
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Gerekli sarmalayıcı derlemelerini oluşturmak için uygun hedef çerçevesinden *tlbimp.exe* ve *aximp.exe* çalışır. Bu parametre çoklu hedeflemeye izin verir `ResolveComReferences` .|
|`FilesWritten`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Diske yazılan tüm dosyaların adlarını içerir. Bu, varsa önbellek dosyasını içerir. Bu parametre, temizleme uygulamaları için yararlıdır.|
|`MinimalRebuildFromTracking`|İsteğe bağlı `Boolean` parametre.<br /><br /> İzlenen artımlı yapı 'un kullanılıp kullanılmayacağını belirten bir anahtar alır veya ayarlar. Eğer `true` Artımlı derleme açıksa; Aksi takdirde yeniden oluşturma zorunlu olur.|
|`NeverLockTypeAssemblies`|İsteğe bağlı `Boolean` parametre.<br /><br /> Kaynak (*. resx*) dosyalarını (true) değerlendirmek için yeni bir [AppDomain](/dotnet/api/system.appdomain) oluşturulup oluşturulmayacağını veya yalnızca kaynak dosyaları bir kullanıcının derlemesine başvurması durumunda yeni bir [AppDomain](/dotnet/api/system.appdomain) oluşturma (false) öğesini belirten bir Boole değeri alır veya ayarlar.|
|`OutputResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Oluşturulan dosyaların ( *. resources* dosyaları gibi) adını belirtir. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve oluşturulan *. resources* dosyası giriş dosyasını içeren dizine yerleştirilir.|
|`PublicClass`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , bir genel sınıf olarak türü kesin belirlenmiş bir kaynak sınıfı oluşturur.|
|`References`|İsteğe bağlı `String[]` parametre.<br /><br /> *. Resx* dosyalarındaki yükleme türlerine başvurular. *. resx* dosya verisi öğelerinin .NET türü olabilir. *. Resx* dosyası okun, bu, çözülmesi gerekir. Genellikle standart tür yükleme kuralları kullanılarak başarıyla çözümlenir. İçinde derlemeler sağlarsanız `References` , bunlar öncelik kazanır.<br /><br /> Bu parametre, kesin olarak belirlenmiş kaynaklar için gerekli değildir.|
|`SdkToolsPath`|İsteğe bağlı `String` parametre.<br /><br /> *resgen.exe*gibi SDK araçlarının yolunu belirtir.|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dönüştürülecek öğeleri belirtir. Bu parametreye geçirilen öğeler aşağıdaki dosya uzantılarından birine sahip olmalıdır:<br /><br /> -   *. txt*: dönüştürülecek bir metin dosyası uzantısını belirtir. Metin dosyaları yalnızca dize kaynakları içerebilir.<br />-   *. resx*: dönüştürülecek XML tabanlı bir kaynak dosyası uzantısını belirtir.<br />-   *. restext*: *. txt*ile aynı biçimi belirtir. Bu farklı uzantı, yapı sürecinizdeki diğer kaynak dosyalardan kaynakları içeren kaynak dosyaları açıkça ayırt etmek istiyorsanız yararlıdır.<br />-   *. resources*: dönüştürülecek kaynak dosyanın uzantısını belirtir.|
|`StateFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> *. Resx* giriş dosyalarındaki bağlantıların bağımlılık denetimini hızlandırmak için kullanılan isteğe bağlı bir önbellek dosyasının yolunu belirtir.|
|`StronglyTypedClassName`|İsteğe bağlı `String` parametre.<br /><br /> Türü kesin belirlenmiş kaynak sınıfı için sınıf adını belirtir. Bu parametre belirtilmemişse, kaynak dosyanın temel adı kullanılır.|
|`StronglyTypedFilename`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Kaynak dosya için dosya adını belirtir. Bu parametre belirtilmemişse, sınıfın adı, uzantısı dile bağlı olan temel dosya adı olarak kullanılır. Örneğin: *MyClass.cs*.|
|`StronglyTypedLanguage`|İsteğe bağlı `String` parametre.<br /><br /> Türü kesin belirlenmiş kaynak için sınıf kaynağı oluşturulurken kullanılacak dili belirtir. Bu parametre CodeDomProvider tarafından kullanılan dillerden tam olarak eşleşmelidir. Örneğin: `VB` veya `C#` .<br /><br /> Bu parametreye bir değer geçirerek, görevin kesin olarak belirlenmiş kaynaklar oluşturmasını söyleyebilirsiniz.|
|`StronglyTypedManifestPrefix`|İsteğe bağlı `String` parametre.<br /><br /> Türü kesin belirlenmiş kaynak için oluşturulan sınıf kaynağında kullanılacak kaynak ad alanını veya bildirim önekini belirtir.|
|`StronglyTypedNamespace`|İsteğe bağlı `String` parametre.<br /><br /> Türü kesin belirlenmiş kaynak için oluşturulan sınıf kaynağı için kullanılacak ad alanını belirtir. Bu parametre belirtilmemişse, kesin olarak belirlenmiş tüm kaynaklar genel ad alanında bulunur.|
|`TLogReadFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur parametresi.<br /><br /> Okuma izleme günlüklerini temsil eden öğelerin bir dizisini alır.|
|`TLogWriteFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunurdur parametresi.<br /><br /> Yazma izleme günlüklerini temsil eden öğelerin bir dizisini alır.|
|`ToolArchitecture`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> *ResGen.exe*üretme için kullanılıp kullanılmayacağını *Tracker.exe* için kullanılır.<br /><br /> Sabit listesinin bir üyesine ayrıştırılamayan olmalıdır <xref:Microsoft.Build.Utilities.ExecutableType> . `String.Empty`, Varsayılan bir mimariyi belirlemede buluşsal yöntem kullanır. Microsoft.Build.Utilities.ExecutableType numaralandırması üyesine ayrıştırılamayan olmalıdır.|
|`TrackerFrameworkPath`|İsteğe bağlı `String` parametre.<br /><br /> *FileTracker.dll*içeren uygun .NET Framework konumun yolunu belirtir.<br /><br /> Ayarlanırsa, Kullanıcı, geçirdikleri *FileTracker.dll* bit sayısının, kullanmayı düşündüğünüz *ResGen.exe* bit durumuyla eşleştiğinden emin olma sorumluluğunu alır. Ayarlanmamışsa, görev geçerli .NET Framework sürümüne göre uygun konuma karar verir.|
|`TrackerLogDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Bu görevi çalıştırmanın İzleme günlüklerinin yerleştirileceği ara dizini belirtir.|
|`TrackerSdkPath`|İsteğe bağlı `String` parametre.<br /><br /> *Tracker.exe*içeren uygun Windows SDK konumun yolunu belirtir.<br /><br /> Ayarlanırsa, Kullanıcı, geçirdikleri *Tracker.exe* bit sayısının, kullanmayı düşündüğünüz *ResGen.exe* bit durumuyla eşleştiğinden emin olma sorumluluğunu alır. Ayarlanmamışsa, görev geçerli Windows SDK göre uygun konuma karar verir.|
|`TrackFileAccess`|İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> True ise, göreli dosya yollarını çözümlemek için giriş dosyasının dizini kullanılır.|
|`UseSourcePath`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , göreli dosya yollarını çözümlemek için giriş dosyasının dizininin kullanılacağını belirtir.|

## <a name="remarks"></a>Açıklamalar

*. Resx* dosyaları diğer kaynak dosyalarına bağlantılar içerebileceğinden, çıkışların güncel olup olmadığını görmek için *. resx* ve *. resources* dosya zaman damgalarını karşılaştırmak yeterlidir. Bunun yerine, `GenerateResource` görev *. resx* dosyalarındaki bağlantıları izler ve bağlantılı dosyaların zaman damgalarını de denetler. Bu, genellikle `Inputs` `Outputs` görevi içeren hedef üzerinde öznitelikleri ve özniteliği `GenerateResource` gerçekten çalışması gerektiği zaman atlanmasına neden olabileceği anlamına gelir.

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından devralınan parametreleri devralır <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

.NET 3,5 projelerini hedeflemek için MSBuild 4,0 ' i kullanırken, derleme x86 kaynaklarında başarısız olabilir. Bu sorunu geçici olarak çözmek için, hedefi bir AnyCPU derlemesi olarak oluşturabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `GenerateResource` öğe koleksiyonu tarafından belirtilen dosyalardan *. resources* dosyaları oluşturmak için görevini kullanır `Resx` .

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

`GenerateResource`Görev, \<LogicalName> \<EmbeddedResource> bir derlemeye gömülü kaynağı adlandırmak için bir öğenin meta verilerini kullanır.

Derlemenin myAssembly olarak adlandırıldığını varsayarsak, aşağıdaki kod *Somequalifier. someResource. resources*adlı bir katıştırılmış kaynak oluşturur:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

\<LogicalName>Meta veriler olmadan kaynak *MyAssembly. MyResource. resources*olarak adlandırılır.  Bu örnek yalnızca Visual Basic ve Visual C# derleme işlemi için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
