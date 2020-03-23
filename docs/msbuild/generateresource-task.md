---
title: Kaynak Görevi Oluşturma | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634064"
---
# <a name="generateresource-task"></a>GenerateResource görevi

*.txt* ve *.resx* (XML tabanlı kaynak biçimi) dosyaları ile çalışma zamanı ikili çalıştırılabilir veya uydu derlemelerine derlenebilir ortak dil çalışma zamanı ikili *.kaynaklar* dosyaları arasında dönüştürür. Bu görev genellikle *.txt* veya *.resx* dosyalarını *.resources* dosyalarına dönüştürmek için kullanılır. Görev `GenerateResource` işlevsel olarak [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)benzer.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevparametreleri `GenerateResource` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalInputs`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Bu görev tarafından yapılan bağımlılık denetimine ek girişler içerir. Örneğin, proje ve hedefleri dosyaları genellikle girişleri olmalıdır, böylece bunlar güncelleştirilirse, tüm kaynaklar yeniden oluşturulur.|
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametre.<br /><br /> Normal ortam bloğuna ek olarak, yumurtlanan *resgen.exe'ye*geçirilmesi gereken bir dizi ad değeri çifti gösterir.|
|`ExcludedInputPaths`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Güncel denetim sırasında izlenen girişlerin yoksayılmasıgereken yolları belirten bir dizi öğe belirtir.|
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`gerekli sarıcı montajları oluşturmak için uygun hedef çerçeve out-of-proc *tlbimp.exe* ve *aximp.exe* çalışır. Bu parametre, 'nin `ResolveComReferences`çoklu hedeflemesine izin verir.|
|`FilesWritten`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Diske yazılmış tüm dosyaların adlarını içerir. Varsa önbellek dosyasını içerir. Bu parametre, Clean uygulamaları için yararlıdır.|
|`MinimalRebuildFromTracking`|İsteğe bağlı `Boolean` parametre.<br /><br /> İzlenen artımlı yapının kullanılıp kullanılmayacağını belirten bir anahtar alır veya ayarlar. `true`, artımlı yapı açıksa; aksi takdirde, yeniden inşa etmek zorlanacaktır.|
|`NeverLockTypeAssemblies`|İsteğe bağlı `Boolean` parametre.<br /><br /> Kaynakları değerlendirmek için yeni bir [AppDomain](/dotnet/api/system.appdomain) oluşturup oluşturmayacağımı belirten bir Boolean değeri alır veya ayarlar *(.resx)* dosyaları (true) veya yalnızca kaynaklar dosyaları bir kullanıcının derlemesine (yanlış) başvuruyaptığında yeni bir [AppDomain](/dotnet/api/system.appdomain) oluşturmak için.|
|`OutputResources`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> *.resources* dosyaları gibi oluşturulan dosyaların adını belirtir. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve oluşturulan *.resources* dosyası giriş dosyasını içeren dizine yerleştirilir.|
|`PublicClass`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`ortak sınıf olarak güçlü bir şekilde yazılan bir kaynak sınıfı oluşturur.|
|`References`|İsteğe bağlı `String[]` parametre.<br /><br /> *.resx* dosyalarındaki yük türlerine başvurular. *.resx* dosya veri elemanları .NET türüne sahip olabilir. *.resx* dosyası okunduğunda, bu çözülmelidir. Genellikle, standart tür yükleme kuralları kullanılarak başarıyla çözülür. Eğer derlemeler sağlarsanız `References`, bunlar önceliklidir.<br /><br /> Bu parametre güçlü bir şekilde yazılan kaynaklar için gerekli değildir.|
|`SdkToolsPath`|İsteğe bağlı `String` parametre.<br /><br /> *Resgen.exe*gibi SDK araçlarına giden yolu belirtir.|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dönüştürmek için öğeleri belirtir. Bu parametreye geçirilen öğeler aşağıdaki dosya uzantılarından birine sahip olmalıdır:<br /><br /> -   *.txt*: Bir metin dosyasının dönüştürülmesi için uzantıyı belirtir. Metin dosyaları yalnızca dize kaynaklarını içerebilir.<br />-   *.resx*: XML tabanlı kaynak dosyasının dönüştürülmesi için uzantıyı belirtir.<br />-   *.restext*: *.txt*ile aynı biçimi belirtir. Bu farklı uzantı, yapı işleminizdeki diğer kaynak dosyalarıiçeren kaynak dosyaları açıkça ayırt etmek istiyorsanız yararlıdır.<br />-   *.resources*: Kaynak dosyasının dönüştürülmesi için uzantıyı belirtir.|
|`StateFile`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> *.resx* giriş dosyalarındaki bağlantıların bağımlılık denetimini hızlandırmak için kullanılan isteğe bağlı önbellek dosyasına giden yolu belirtir.|
|`StronglyTypedClassName`|İsteğe bağlı `String` parametre.<br /><br /> Güçlü bir şekilde yazılan kaynak sınıfının sınıf adını belirtir. Bu parametre belirtilmemişse, kaynak dosyasının temel adı kullanılır.|
|`StronglyTypedFilename`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Kaynak dosyanın dosya adını belirtir. Bu parametre belirtilmemişse, sınıfın adı temel dosya adı olarak kullanılır ve uzantı dile bağlıdır. Örneğin: *MyClass.cs*.|
|`StronglyTypedLanguage`|İsteğe bağlı `String` parametre.<br /><br /> Güçlü bir şekilde yazılan kaynak için sınıf kaynağını oluştururken kullanılacak dili belirtir. Bu parametre, CodeDomProvider tarafından kullanılan dillerden tam olarak biriyle eşleşmelidir. Örneğin: `VB` veya `C#`.<br /><br /> Bu parametreye bir değer geçirerek, görevi güçlü bir şekilde yazılmış kaynaklar oluşturması için talimat verirsiniz.|
|`StronglyTypedManifestPrefix`|İsteğe bağlı `String` parametre.<br /><br /> Güçlü bir şekilde yazılan kaynak için oluşturulan sınıf kaynağında kullanılacak kaynak ad alanını veya bildirim önekini belirtir.|
|`StronglyTypedNamespace`|İsteğe bağlı `String` parametre.<br /><br /> Güçlü bir şekilde yazılan kaynak için oluşturulan sınıf kaynağı için kullanılacak ad alanını belirtir. Bu parametre belirtilmemişse, genel ad alanında güçlü bir şekilde yazılan kaynaklar vardır.|
|`TLogReadFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur parametresi.<br /><br /> Okuma izleme günlüklerini temsil eden bir dizi öğe alır.|
|`TLogWriteFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` salt okunur parametresi.<br /><br /> Yazma izleme günlüklerini temsil eden bir dizi öğe alır.|
|`ToolArchitecture`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> *Tracker.exe'nin* *ResGen.exe'yi yumurtlamak*için kullanılması gerekip gerekmediğini belirlemek için kullanılır.<br /><br /> Numaralandırmanın <xref:Microsoft.Build.Utilities.ExecutableType> bir üyesi yle ayrışabilir olmalıdır. Eğer, `String.Empty`varsayılan bir mimari belirlemek için buluşsal kullanır. Microsoft.Build.Utilities.ExecutableType numaralandırmasının bir üyesi yle ayrışabilir olmalıdır.|
|`TrackerFrameworkPath`|İsteğe bağlı `String` parametre.<br /><br /> *FileTracker.dll*içeren uygun .NET Framework konumuna giden yolu belirtir.<br /><br /> Ayarlanırsa, kullanıcı, geçtikleri *FileTracker.dll'nin* bitliğinin kullanmak istedikleri *ResGen.exe'nin* bitliğiyle eşleştiğinden emin olmak için sorumluluk alır. Ayarlanmazsa, görev geçerli .NET Framework sürümüne göre uygun konumu belirler.|
|`TrackerLogDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Bu görevi çalıştıran izleme günlüklerinin yerleştirileceği ara dizini belirtir.|
|`TrackerSdkPath`|İsteğe bağlı `String` parametre.<br /><br /> *Tracker.exe*içeren uygun Windows SDK konumuna giden yolu belirtir.<br /><br /> Eğer ayarlanırsa, kullanıcı, geçtikleri *Tracker.exe'nin* bitliğinin kullanmak istedikleri *ResGen.exe'nin* bitliğiyle eşleştiğinden emin olmak için sorumluluk alır. Ayarlanmazsa, görev geçerli Windows SDK'ya göre uygun konumu belirler.|
|`TrackFileAccess`|İsteğe bağlı <xref:System.Boolean> parametre.<br /><br /> Doğruysa, giriş dosyasının dizini göreli dosya yollarını çözmek için kullanılır.|
|`UseSourcePath`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`giriş dosyasının dizininin göreli dosya yollarını çözmek için kullanılacağını belirtirse.|

## <a name="remarks"></a>Açıklamalar

*.resx* dosyaları diğer kaynak dosyalarına bağlantılar içerebileceğinden, çıktıların güncel olup olmadığını görmek için *.resx* ve *.resources* dosya zaman damgalarını karşılaştırmak yeterli değildir. Bunun yerine, `GenerateResource` görev *.resx* dosyalarındaki bağlantıları izler ve bağlı dosyaların zaman damgalarını da denetler. Bu, `GenerateResource` görevi içeren hedefte `Inputs` `Outputs` genel olarak kullanmamanız ve öznitelikleri kullanmanız gerektiği anlamına gelir, çünkü bu, gerçekten çalışması gerektiğinde atlanmasına neden olabilir.

Yukarıda listelenen parametrelere ek olarak, bu görev, kendisinden sınıftan <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınan sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.

.NET 3.5 projelerini hedeflemek için MSBuild 4.0 kullanırken, yapı x86 kaynaklarında başarısız olabilir. Bu sorunu aşmak için, hedef bir AnyCPU derlemesi olarak oluşturabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki `Resx` örnekte, `GenerateResource` madde koleksiyonu tarafından belirtilen dosyalardan *.resources* dosyaları oluşturmak için görev kullanır.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Görev, `GenerateResource` derlemeye \< \<katıştırılmış kaynağı adlandırmak için Bir EmbeddedResource> öğesinin Mantıksal Adı> meta verilerini kullanır.

Derlemenin myAssembly olarak adlandırıldığını varsayarsak, aşağıdaki kod *someQualifier.someResource.resources*adlı katıştırılmış bir kaynak oluşturur:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

\<MantıksalAd> meta veri olmadan, kaynak *myAssembly.myResource.resources*olarak adlandırılır.  Bu örnek yalnızca Visual Basic ve Visual C# yapı işlemi için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
