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
ms.openlocfilehash: 3fdc6c6ccd58bcc83cc37ff3a9f7888af837ed6e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595208"
---
# <a name="resolvecomreference-task"></a>ResolveComReference görevi

Bir veya daha fazla tür kitaplığı adının veya *. tlb* dosyasının bir listesini alır ve bu tür kitaplıklarını disk üzerindeki konumlara çözümler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `ResolveCOMReference` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DelaySign`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, ortak anahtarı derlemeye koyar. `false`, derlemeyi tamamen imzalar.|
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametresi.<br /><br /> Ortam değişkenlerinin çiftler dizisi, eşittir işaretleriyle ayrılmıştır. Bu değişkenler, normal ortam bloğunu seçerek veya seçmeli olarak geçersiz kılan, oluşturulan *Tlbimp. exe* ve *Aximp. exe* ' ye geçirilir.|
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, gerekli sarmalayıcı derlemelerini oluşturmak için uygun hedef Framework 'ten *Tlbimp. exe* ve *Aximp. exe* ' yi çalıştırır. Bu parametre Çoklu hedefleme etkinleştirilir.|
|`IncludeVersionInInteropName`|İsteğe bağlı `Boolean` parametresi.<br /><br /> `true`, TypeLib sürümü sarmalayıcı adına dahil edilir. Varsayılan, `false` değeridir.|
|`KeyContainer`|İsteğe bağlı `String` parametresi.<br /><br /> Ortak/özel anahtar çiftini tutan bir kapsayıcı belirtir.|
|`KeyFile`|İsteğe bağlı `String` parametresi.<br /><br /> Ortak/özel anahtar çifti içeren bir öğeyi belirtir.|
|`NoClassMembers`|İsteğe bağlı `Boolean`parametresi.|
|`ResolvedAssemblyReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Çözümlenen derleme başvurularını belirtir.|
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` çıkış parametresi.<br /><br /> Bu göreve giriş olarak sunulan tür kitaplıklarının fiziksel konumlarına karşılık gelen diskte tam nitelikli dosyaları belirtir.|
|`ResolvedModules`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]`parametresi.|
|`SdkToolsPath`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametresi.<br /><br /> `ExecuteAsTool` `true`ise, bu parametre hedeflenen Framework sürümü için SDK araçları yoluna ayarlanmalıdır.|
|`StateFile`|İsteğe bağlı `String` parametresi.<br /><br /> COM bileşeni zaman damgaları için önbellek dosyasını belirtir. Mevcut değilse, her çalıştırma sarmalayıcılarını yeniden üretmez.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametresi.<br /><br /> Proje hedef Framework sürümünü belirtir.<br /><br /> Varsayılan, `String.Empty` değeridir. Bu, hedef çerçeveye dayalı bir başvuru için filtreleme olmadığı anlamına gelir.|
|`TargetProcessorArchitecture`|İsteğe bağlı `String` parametresi.<br /><br /> Tercih edilen hedef işlemci mimarisini belirtir. Çeviri sonrasında *Tlbimp. exe*/MACHINE bayrağına geçildi.<br /><br /> Parametre değeri <xref:Microsoft.Build.Utilities.ProcessorArchitecture>bir üyesi olmalıdır.|
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> COM başvurularının tür kitaplığı dosya yolunu belirtir. Bu parametreye dahil edilen öğeler, öğe meta verileri içerebilir. Daha fazla bilgi için aşağıdaki [TypeLibFiles öğe meta verileri](#typelibfiles-item-metadata) bölümüne bakın.|
|`TypeLibNames`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametresi.<br /><br /> Çözülecek tür kitaplığı adlarını belirtir. Bu parametreye dahil edilen öğeler bazı öğe meta verileri içermelidir. Daha fazla bilgi için aşağıdaki [TypeLibNames öğesi metasection](#typelibnames-item-metadata) bölümüne bakın.|
|`WrapperOutputDirectory`|İsteğe bağlı `String` parametresi.<br /><br /> Oluşturulan birlikte çalışma derlemesinin yerleştirildiği diskteki konumu. Bu öğe meta verileri belirtilmemişse, görev, proje dosyasının bulunduğu dizinin mutlak yolunu kullanır.|

## <a name="typelibnames-item-metadata"></a>TypeLibNames öğe meta verileri

 Aşağıdaki tabloda `TypeLibNames` parametresine geçirilen öğeler için kullanılabilen öğe meta verileri açıklanmaktadır.

|Meta Veriler|Açıklama|
|--------------|-----------------|
|`GUID`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığı için GUID. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`VersionMajor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ana sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`VersionMinor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ikincil sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`EmbedInteropTypes`|İsteğe bağlı `Boolean` meta verileri.<br /><br />  `true`, birlikte çalışma bir DLL oluşturmak yerine bu başvurudaki birlikte çalışma türlerini doğrudan derlemenizin içine ekleyin.|
|`LocaleIdentifier`|İsteğe bağlı öğe meta verileri.<br /><br /> Tür kitaplığının yerel ayar tanımlayıcısı (veya LCıD). Bu, bir Kullanıcı, bölge veya uygulama tarafından tercih edilen insan dilini belirleyen 32 bitlik bir değer olarak belirtilir. Bu öğe meta verileri belirtilmemişse, görev "0" varsayılan yerel ayar tanıtıcısını kullanır.|
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "Tlbimp" öğesinin varsayılan sarmalayıcı aracını kullanır. Mevcut, büyük/küçük harf duyarsız seçenekleri şunlardır:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesini kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullandığınızda, bir sarmalayıcı çıkış dizini belirtmeyin çünkü bu, görevin başarısız olmasına neden olur.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.<br />-   `AXImp`: bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.|

## <a name="typelibfiles-item-metadata"></a>TypeLibFiles öğe meta verileri

 Aşağıdaki tabloda `TypeLibFiles` parametresine geçirilen öğeler için kullanılabilen öğe meta verileri açıklanmaktadır.

|Meta Veriler|Açıklama|
|--------------|-----------------|
|`EmbedInteropTypes`|İsteğe bağlı `Boolean`parametresi.<br /><br />  `true`, birlikte çalışma bir DLL oluşturmak yerine bu başvurudaki birlikte çalışma türlerini doğrudan derlemenizin içine ekleyin.|
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "Tlbimp" öğesinin varsayılan sarmalayıcı aracını kullanır. Mevcut, büyük/küçük harf duyarsız seçenekleri şunlardır:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesini kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullandığınızda, bir sarmalayıcı çıkış dizini belirtmeyin çünkü bu, görevin başarısız olmasına neden olur.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.<br />-   `AXImp`: bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.|

> [!NOTE]
> Bir tür kitaplığını benzersiz şekilde tanımlamak için sağladığınız daha fazla bilgi, görevin diskteki doğru dosyaya çözümlenme olasılığı artar.

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev <xref:Microsoft.Build.Utilities.Task> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).

Bu görevin çalışması için COM DLL 'nin makinede kayıtlı olması gerekmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
