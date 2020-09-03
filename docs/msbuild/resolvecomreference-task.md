---
title: ResolveComReference görevi | Microsoft Docs
ms.date: 07/25/2019
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b99e743cf5bc9e3e634a8738e30d17c8e5517191
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286186"
---
# <a name="resolvecomreference-task"></a>ResolveComReference görevi

Bir veya daha fazla tür kitaplığı adının veya *. tlb* dosyasının bir listesini alır ve bu tür kitaplıklarını disk üzerindeki konumlara çözümler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tablo, görevin parametrelerini açıklar `ResolveCOMReference` .

|Parametre|Açıklama|
|---------------|-----------------|
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , ortak anahtarı derlemeye koyar. İse `false` , derlemeyi tamamen imzalar.|
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametre.<br /><br /> Ortam değişkenlerinin çiftler dizisi, eşittir işaretleriyle ayrılmıştır. Bu değişkenler oluşturulan *tlbimp.exe* geçirilir ve normal ortam bloğunu seçerek veya seçmeli olarak geçersiz kılan *aximp.exe* ...|
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Gerekli sarmalayıcı derlemelerini oluşturmak için uygun hedef çerçevesinden *tlbimp.exe* ve *aximp.exe* çalışır. Bu parametre Çoklu hedefleme etkinleştirilir.|
|`IncludeVersionInInteropName`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , TypeLib sürümü sarmalayıcı adına dahil edilir. Varsayılan değer: `false`.|
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Ortak/özel anahtar çiftini tutan bir kapsayıcı belirtir.|
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Ortak/özel anahtar çifti içeren bir öğeyi belirtir.|
|`NoClassMembers`|İsteğe bağlı `Boolean` parametre.|
|`ResolvedAssemblyReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çözümlenen derleme başvurularını belirtir.|
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu göreve giriş olarak sunulan tür kitaplıklarının fiziksel konumlarına karşılık gelen diskte tam nitelikli dosyaları belirtir.|
|`ResolvedModules`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.|
|`SdkToolsPath`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> `ExecuteAsTool`İse `true` , bu parametre hedeflenen Framework sürümü için SDK araçları yoluna ayarlanmalıdır.|
|`StateFile`|İsteğe bağlı `String` parametre.<br /><br /> COM bileşeni zaman damgaları için önbellek dosyasını belirtir. Mevcut değilse, her çalıştırma sarmalayıcılarını yeniden üretmez.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> Proje hedef Framework sürümünü belirtir.<br /><br /> Varsayılan değer: `String.Empty`. Bu, hedef çerçeveye dayalı bir başvuru için filtreleme olmadığı anlamına gelir.|
|`TargetProcessorArchitecture`|İsteğe bağlı `String` parametre.<br /><br /> Tercih edilen hedef işlemci mimarisini belirtir. Çeviri sonrasında *tlbimp.exe*/MACHINE bayrağına geçildi.<br /><br /> Parametre değeri öğesinin bir üyesi olmalıdır <xref:Microsoft.Build.Utilities.ProcessorArchitecture> .|
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> COM başvurularının tür kitaplığı dosya yolunu belirtir. Bu parametreye dahil edilen öğeler, öğe meta verileri içerebilir. Daha fazla bilgi için aşağıdaki [TypeLibFiles öğe meta verileri](#typelibfiles-item-metadata) bölümüne bakın.|
|`TypeLibNames`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çözülecek tür kitaplığı adlarını belirtir. Bu parametreye dahil edilen öğeler bazı öğe meta verileri içermelidir. Daha fazla bilgi için aşağıdaki [TypeLibNames öğesi metasection](#typelibnames-item-metadata) bölümüne bakın.|
|`WrapperOutputDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan birlikte çalışma derlemesinin yerleştirildiği diskteki konumu. Bu öğe meta verileri belirtilmemişse, görev, proje dosyasının bulunduğu dizinin mutlak yolunu kullanır.|

## <a name="typelibnames-item-metadata"></a>TypeLibNames öğe meta verileri

 Aşağıdaki tabloda, parametresine geçirilen öğeler için kullanılabilen öğe meta verileri açıklanmaktadır `TypeLibNames` .

|Meta Veriler|Açıklama|
|--------------|-----------------|
|`GUID`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığı için GUID. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`VersionMajor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ana sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`VersionMinor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ikincil sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`EmbedInteropTypes`|İsteğe bağlı `Boolean` meta veriler.<br /><br />  İse `true` , birlikte çalışma BIR DLL oluşturmak yerine bu başvurudan doğrudan birlikte çalışma türlerini derlemeye ekleyin.|
|`LocaleIdentifier`|İsteğe bağlı öğe meta verileri.<br /><br /> Tür kitaplığının yerel ayar tanımlayıcısı (veya LCıD). Bu, bir Kullanıcı, bölge veya uygulama tarafından tercih edilen insan dilini belirleyen 32 bitlik bir değer olarak belirtilir. Bu öğe meta verileri belirtilmemişse, görev "0" varsayılan yerel ayar tanıtıcısını kullanır.|
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "Tlbimp" öğesinin varsayılan sarmalayıcı aracını kullanır. Mevcut, büyük/küçük harf duyarsız seçenekleri şunlardır:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesini kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullandığınızda, bir sarmalayıcı çıkış dizini belirtmeyin çünkü bu, görevin başarısız olmasına neden olur.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.<br />-   `AXImp`: Bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.|

## <a name="typelibfiles-item-metadata"></a>TypeLibFiles öğe meta verileri

 Aşağıdaki tabloda, parametresine geçirilen öğeler için kullanılabilen öğe meta verileri açıklanmaktadır `TypeLibFiles` .

|Meta Veriler|Açıklama|
|--------------|-----------------|
|`EmbedInteropTypes`|İsteğe bağlı `Boolean` parametre.<br /><br />  İse `true` , birlikte çalışma BIR DLL oluşturmak yerine bu başvurudan doğrudan birlikte çalışma türlerini derlemeye ekleyin.|
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "Tlbimp" öğesinin varsayılan sarmalayıcı aracını kullanır. Mevcut, büyük/küçük harf duyarsız seçenekleri şunlardır:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesini kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullandığınızda, bir sarmalayıcı çıkış dizini belirtmeyin çünkü bu, görevin başarısız olmasına neden olur.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.<br />-   `AXImp`: Bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.|

> [!NOTE]
> Bir tür kitaplığını benzersiz şekilde tanımlamak için sağladığınız daha fazla bilgi, görevin diskteki doğru dosyaya çözümlenme olasılığı artar.

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından parametreleri devralır <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

Bu görevin çalışması için COM DLL 'nin makinede kayıtlı olması gerekmez.

## <a name="msb4803-error"></a>MSB4803 hatası

CLI komutlarından görevi kullanan bir projeyi çalıştırmaya çalışırsanız, şu `ResolveCOMReference` `dotnet` hatayı alırsınız:

```output
MSB4803: The task "ResolveComReference" is not supported on the .NET Core version of MSBuild. Please use the .NET Framework version of MSBuild.
```

Bu görev, komut satırından komutunu çalıştırdığınızda kullanılan MSBuild 'in .NET Core sürümünde desteklenmez `dotnet build` . MSBuild 'in .NET Framework sürümünü kullandığından, Visual Studio Geliştirici Komut İstemi [MSBuild.exe](msbuild-command-line-reference.md) çağırarak projeyi oluşturmayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
