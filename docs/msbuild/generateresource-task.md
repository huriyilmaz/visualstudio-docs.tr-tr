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
ms.openlocfilehash: 1d0054ab1520bc021cc37ddd51220593e7ce627b
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133514486"
---
# <a name="generateresource-task"></a>GenerateResource görevi

ve (XML tabanlı kaynak biçimi) dosyaları ile bir çalışma zamanı ikili yürütülebilir dosyasına katıştırılacak veya uydu derlemelerine derlenmiş ortak dil çalışma zamanı ikili dosyaları `.txt` `.resx` arasında `.resources` dönüştürür. Bu görev genellikle veya dosyalarını dosyalara `.txt` `.resx` dönüştürmek için `.resources` kullanılır. Görev, `GenerateResource` işlevsel olarak [ ](/dotnet/framework/tools/resgen-exe-resource-file-generator)resgen.exe.

## <a name="parameters"></a>Parametreler

Aşağıdaki tabloda görevin parametreleri açık `GenerateResource` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`AdditionalInputs`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Bu görev tarafından yapılan bağımlılık denetimine ek girişler içerir. Örneğin, proje ve hedef dosyaları genellikle girişler olmalı, böylece güncelleştirildiğinde tüm kaynaklar yeniden oluşturulur.|
|`EnvironmentVariables`|İsteğe `String[]` bağlı parametre.<br /><br /> Normal ortam bloğuna ek olarak (veya seçmeli olarak geçersiz ** kılmaya) ek olarak,resgen.exegeçirilen ortam değişkenlerinin ad-değer çiftleri dizisini belirtir.|
|`ExcludedInputPaths`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Güncel denetim sırasında takip edilmiş girişlerin yoksayılacak yolları belirten bir öğe dizisi belirtir.|
|`ExecuteAsTool`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, gereklitlbimp.exeaximp.exederlemeleri oluşturmak için uygun hedef çerçeveden yordam dışından derlemeyi çalıştırır `true` ve bunu çalıştırır.   Bu parametre, çoklu hedeflemeye izin `ResolveComReferences` verir.|
|`FilesWritten`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Diske yazılan tüm dosyaların adlarını içerir. Bu, varsa önbellek dosyasını içerir. Bu parametre, Clean uygulamaları için yararlıdır.|
|`MinimalRebuildFromTracking`|İsteğe `Boolean` bağlı parametre.<br /><br /> İzli artımlı derlemenin kullanılamayacaklarını belirten bir anahtar alır veya ayarlar. , `true` artımlı derleme açıksa; aksi takdirde, yeniden derleme zorlar.|
|`NeverLockTypeAssemblies`|İsteğe `Boolean` bağlı parametre.<br /><br /> Kaynakları değerlendirmek için yeni bir AppDomain *(.resx*) dosyası (true) veya yalnızca kaynak dosyaları bir kullanıcının derlemeye başvurduysa (false) yeni [bir AppDomain](/dotnet/api/system.appdomain) oluşturularak yeni bir [AppDomain](/dotnet/api/system.appdomain) oluşturulıp oluşturul olmadığını belirten bir Boole değeri alır veya ayarlar.|
|`OutputResources`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Dosyalar gibi oluşturulan dosyaların adını `.resources` belirtir. Bir ad belirtmezseniz, eşleşen giriş dosyasının adı kullanılır ve oluşturulan dosya, giriş `.resources` dosyasını içeren dizine yerleştirilir.|
|`PublicClass`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` kesin olarak türü kesin olarak belirtilen bir kaynak sınıfı genel sınıf olarak oluşturur.|
|`References`|İsteğe `String[]` bağlı parametre.<br /><br /> Dosyalarda yükleme türlerine `.resx` başvurular. `.resx` dosya veri öğelerinin bir .NET türü olabilir. *.resx dosyası* okundu mu, bu tür çözümlenmiş olması gerekir. Genellikle, standart tür yükleme kuralları kullanılarak başarıyla çözümlenir. içinde derlemeler `References` sağlarsanız, bunlar önceliklidir.<br /><br /> Bu parametre, kesin olarak türü kesin olarak belirtnan kaynaklar için gerekli değildir.|
|`SdkToolsPath`|İsteğe `String` bağlı parametre.<br /><br /> SDK araçlarının yolunu belirtir, örneğin *resgen.exe.*|
|`Sources`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Dönüştürülecek öğeleri belirtir. Bu parametreye geçirilen öğelerin aşağıdaki dosya uzantılarından biri olması gerekir:<br /><br /> -   `.txt`: Dönüştürülecek metin dosyasının uzantısını belirtir. Metin dosyaları yalnızca dize kaynaklarını içerebilir.<br />-   *.resx:* Dönüştürülecek XML tabanlı bir kaynak dosyasının uzantısını belirtir.<br />-   *.restext:* ile aynı biçimi *.txt.* Derleme işleminizin diğer kaynak dosyalarından kaynakları içeren kaynak dosyaları net bir şekilde ayırt etmek için bu farklı uzantı yararlı olur.<br />-   *.resources:* Dönüştürülecek kaynak dosyasının uzantısını belirtir.|
|`StateFile`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> *.resx* giriş dosyalarında bağlantıların bağımlılık denetlemesini hızlandırmak için kullanılan isteğe bağlı önbellek dosyasının yolunu belirtir.|
|`StronglyTypedClassName`|İsteğe `String` bağlı parametre.<br /><br /> Kesin olarak türü kesin olarak belirtilen kaynak sınıfının sınıf adını belirtir. Bu parametre belirtilmezse kaynak dosyasının temel adı kullanılır.|
|`StronglyTypedFilename`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> Kaynak dosyanın dosya adını belirtir. Bu parametre belirtilmezse, sınıfın adı temel dosya adı olarak kullanılır ve uzantı dile bağımlıdır. Örneğin: *MyClass.cs*.|
|`StronglyTypedLanguage`|İsteğe `String` bağlı parametre.<br /><br /> Kesin türü kesin olarak belirtilen kaynak için sınıf kaynağı oluşturmada kullanmak istediğiniz dili belirtir. Bu parametre CodeDomProvider tarafından kullanılan dillerden tam olarak biri ile eşleşmeli. Örneğin: `VB` veya `C#` .<br /><br /> Bu parametreye bir değer aktararak, göreve kesin türe sahip kaynaklar oluşturma talimatı verirsiniz.|
|`StronglyTypedManifestPrefix`|İsteğe `String` bağlı parametre.<br /><br /> Kesin türe sahip kaynak için oluşturulan sınıf kaynağında kullanmak üzere kaynak ad alanını veya bildirim ön eklerini belirtir.|
|`StronglyTypedNamespace`|İsteğe `String` bağlı parametre.<br /><br /> Kesin türü kesin olarak belirtilen kaynak için oluşturulan sınıf kaynağı için kullanmak üzere ad alanını belirtir. Bu parametre belirtilmezse, kesin olarak belirtilmiş tüm kaynaklar genel ad alanı içindedir.|
|`TLogReadFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur parametre.<br /><br /> Okuma izleme günlüklerini temsil eden bir öğe dizisi alır.|
|`TLogWriteFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı salt okunur parametre.<br /><br /> Yazma izleme günlüklerini temsil eden bir öğe dizisi alır.|
|`ToolArchitecture`|İsteğe <xref:System.String?displayProperty=fullName> bağlı parametre.<br /><br /> Bir veya daha fazlaTracker.exe *için* *ResGen.exe.*<br /><br /> Numaralamanın bir üyesiyle <xref:Microsoft.Build.Utilities.ExecutableType> ayrıştırılabilir olması gerekir. ise, `String.Empty` varsayılan bir mimariyi belirlemek için biruristic kullanır. Microsoft.Build.Utilities.ExecutableType numaralarının bir üyesiyle ayrıştırılabilir olması gerekir.|
|`TrackerFrameworkPath`|İsteğe `String` bağlı parametre.<br /><br /> dosyanın bulunduğu uygun .NET Framework konumunun *FileTracker.dll.*<br /><br /> Ayarlanırsa, kullanıcı, geçenFileTracker.dll'nin kullanmayı *ResGen.exe* bitliğiyle *eş olduğundan emin* olmak için sorumluluğu üst alır. Ayarlanmazsa, görev geçerli sürüme göre uygun .NET Framework verir.|
|`TrackerLogDirectory`|İsteğe `String` bağlı parametre.<br /><br /> Bu görevi çalıştıran izleme günlüklerinin yerleştirilecek ara dizini belirtir.|
|`TrackerSdkPath`|İsteğe `String` bağlı parametre.<br /><br /> 'i içeren uygun Windows SDK konumunun *Tracker.exe.*<br /><br /> Ayarlanırsa, kullanıcı, geçenTracker.exe'nin kullanmayı *ResGen.exe* bitliğiyle *eş olduğundan emin* olmak için sorumluluğu üst alır. Ayarlanmazsa, görev geçerli sdk'sı temel alarak uygun Windows verir.|
|`TrackFileAccess`|İsteğe <xref:System.Boolean> bağlı parametre.<br /><br /> True ise, göreli dosya yollarını çözümlemek için giriş dosyasının dizini kullanılır.|
|`UsePreserializedResources`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, Dize olmayan kaynakların yerine kullanılarak seri hale getirileceklerini belirtir. Bu, .NET Core veya `true` .NET 5 veya sonraki bir üzerinde <xref:System.Resources.Extensions.PreserializedResourceWriter> <xref:System.Resources.ResourceWriter> desteklenmiyor. 
|`UseSourcePath`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` göreli dosya yollarını çözümlemek için giriş dosyasının dizininin kullan olacağını belirtir.|

## <a name="remarks"></a>Açıklamalar

Dosyalar diğer kaynak dosyalarına bağlantılar içerene kadar, çıkışların güncel olup olmadığını görmek için yalnızca ve dosya zaman damgası `.resx` `.resx` `.resources` karşılaştırması yapmak yeterli değildir. Bunun `GenerateResource` yerine, görev dosyalarda bağlantıları izler ve bağlı `.resx` dosyaların zaman damgasını da denetler. Bu, görevi içeren hedefte ve özniteliklerini genel olarak kullanmamanız gerektiği anlamına gelir, çünkü bu, gerçekten çalıştırdığında `Inputs` `Outputs` `GenerateResource` atlanabilir.

Bu görev, yukarıda listelenen parametrelere ek olarak, sınıfından devralınan parametreleri de <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

.NET 3.5 projelerini hedeflemek için MSBuild 4.0'ı kullanırken, derleme x86 kaynaklarında başarısız olabilir. Bu sorunu çözmek için hedefi AnyCPU derlemesi olarak derlemeniz gerekir.

parametresi, `UsePreserializedResources` normal .NET derleme işlemi içinde `$(GenerateResourceUsePreserializedResources)` özelliğinden değerini alır. Bu özellik , .NET Core projelerinde ve .NET 5 veya sonraki bir kullanan `true` projelerde varsayılan olarak olarak ayarlanır. .NET SDK'sına dize dışı kaynaklar kullanan `$(GenerateResourceUsePreserializedResources)` .NET Framework 4.6.1 veya sonraki bir sürümü hedef alan projeler oluşturmasına izin vermek `true` için olarak ayarlayın. Derleme çalışma `System.Resources.Extensions` zamanında kullanılabilir olmalıdır. .NET Core 3.0 ve sonraki ve .NET 5 ve üzerinde kullanılabilir ve PackageReference..NET Framework aracılığıyla .NET Framework 4.6.1 veya sonraki bir |

## <a name="example"></a>Örnek

Aşağıdaki örnek, öğe `GenerateResource` koleksiyonu tarafından `.resources` belirtilen dosyalardan dosya oluşturmak için görevini `Resx` kullanır.

```xml
<GenerateResource
    Sources="@(Resx)"
    OutputResources="@(Resx->'$(IntermediateOutputPath)%(Identity).resources')">
    <Output
        TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

Görev, `GenerateResource` bir `<LogicalName>` derlemeye eklenmiş olan `<EmbeddedResource>` kaynağın adını oluşturmak için bir öğenin meta verilerini kullanır.

Derlemenin myAssembly olarak adlandırılmış olduğu varsayıldı, aşağıdaki kod adlı ekli bir kaynak `someQualifier.someResource.resources` üretir:

```xml
<ItemGroup>
    <EmbeddedResource Include="myResource.resx">
        <LogicalName>someQualifier.someResource.resources</LogicalName>
    </EmbeddedResource>
</ItemGroup>
```

Meta `<LogicalName>` veriler olmadan kaynağın adı `myAssembly.myResource.resources` olur.  Bu örnek yalnızca Visual Basic Visual C# derleme işlemi için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
