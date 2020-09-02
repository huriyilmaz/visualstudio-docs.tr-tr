---
title: ResolveComReference görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc9ca34d8b8afc01787db594ffba5a1a36ec190e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815499"
---
# <a name="resolvecomreference-task"></a>ResolveComReference Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir veya daha fazla tür kitaplığı adının veya. tlb dosyasının bir listesini alır ve bu tür kitaplıklarını disk üzerindeki konumlara çözümler.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tablo, görevin parametrelerini açıklar `ResolveCOMReference` .  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , ortak anahtarı derlemeye koyar. İse `false` , derlemeyi tamamen imzalar.|  
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametre.<br /><br /> Ortam değişkenlerinin çiftler dizisi, eşittir işaretleriyle ayrılmıştır. Bu değişkenler oluşturulan tlbimp.exe geçirilir ve normal ortam bloğunu seçerek veya seçmeli olarak geçersiz kılan aximp.exe...|  
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametre.<br /><br /> `true`, Gerekli sarmalayıcı derlemelerini oluşturmak için uygun hedef çerçevesinden tlbimp.exe ve aximp.exe çalışır. Bu parametre Çoklu hedefleme etkinleştirilir.|  
|`IncludeVersionInInteropName`|İsteğe bağlı `Boolean` parametre.<br /><br /> İse `true` , TypeLib sürümü sarmalayıcı adına dahil edilir. Varsayılan değer: `false`.|  
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Ortak/özel tutan bir kapsayıcı belirtir<br /><br /> anahtar çifti.|  
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Ortak/özel içeren bir öğe belirtir<br /><br /> anahtar çifti.|  
|`NoClassMembers`|İsteğe bağlı `Boolean` parametre.|  
|`ResolvedAssemblyReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Çözümlenen derleme başvurularını belirtir.|  
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıkış parametresi.<br /><br /> Bu göreve giriş olarak sunulan tür kitaplıklarının fiziksel konumlarına karşılık gelen diskte tam nitelikli dosyaları belirtir.|  
|`ResolvedModules`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.|  
|`SdkToolsPath`|İsteğe bağlı [dize] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->parametresinin.<br /><br /> `ExecuteAsTool`İse `true` , bu parametre hedeflenen Framework sürümü için SDK araçları yoluna ayarlanmalıdır.|  
|`StateFile`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> COM bileşeni zaman damgaları için önbellek dosyasını belirtir. Mevcut değilse, her çalıştırma sarmalayıcılarını yeniden üretmez.|  
|`TargetFrameworkVersion`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> Proje hedef Framework sürümünü belirtir.<br /><br /> Varsayılan değer: `String.Empty`. Bu, hedef çerçeveye dayalı bir başvuru için filtreleme olmadığı anlamına gelir.|  
|`TargetProcessorArchitecture`|İsteğe Bağlı <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> parametresinin.<br /><br /> Tercih edilen hedef işlemci mimarisini belirtir. Çeviri sonrasında tlbimp.exe/MACHINE bayrağına geçildi.<br /><br /> Parametre değeri öğesinin bir üyesi olmalıdır <xref:Microsoft.Build.Utilities.ProcessorArchitecture> .|  
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> COM başvurularının tür kitaplığı dosya yolunu belirtir. Bu parametreye dahil edilen öğeler, öğe meta verileri içerebilir. Daha fazla bilgi için aşağıdaki "TypeLibFiles öğe meta verileri" bölümüne bakın.|  
|`TypeLibNames`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çözülecek tür kitaplığı adlarını belirtir. Bu parametreye dahil edilen öğeler bazı öğe meta verileri içermelidir. Daha fazla bilgi için aşağıdaki "TypeLibNames Item Metadata" bölümüne bakın.|  
|`WrapperOutputDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan birlikte çalışma derlemesinin yerleştirildiği diskteki konumu. Bu öğe meta verileri belirtilmemişse, görev, proje dosyasının bulunduğu dizinin mutlak yolunu kullanır.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="typelibnames-item-metadata"></a>TypeLibNames öğe meta verileri  
 Aşağıdaki tabloda, parametresine geçirilen öğeler için kullanılabilen öğe meta verileri açıklanmaktadır `TypeLibNames` .  
  
|Meta Veriler|Description|  
|--------------|-----------------|  
|`GUID`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığı için GUID. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|  
|`VersionMajor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ana sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|  
|`VersionMinor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ikincil sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|  
|`LocaleIdentifier`|İsteğe bağlı öğe meta verileri.<br /><br /> Tür kitaplığının yerel ayar tanımlayıcısı (veya LCıD). Bu, bir Kullanıcı, bölge veya uygulama tarafından tercih edilen insan dilini belirleyen 32 bitlik bir değer olarak belirtilir. Bu öğe meta verileri belirtilmemişse, görev "0" varsayılan yerel ayar tanıtıcısını kullanır.|  
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "Tlbimp" öğesinin varsayılan sarmalayıcı aracını kullanır. Mevcut, büyük/küçük harf duyarsız seçenekleri şunlardır:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesini kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullandığınızda, bir sarmalayıcı çıkış dizini belirtmeyin çünkü bu, görevin başarısız olmasına neden olur.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.<br />-   `AXImp`: Bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.|  
  
## <a name="typelibfiles-item-metadata"></a>TypeLibFiles öğe meta verileri  
 Aşağıdaki tabloda, parametresine geçirilen öğeler için kullanılabilen öğe meta verileri açıklanmaktadır `TypeLibFiles` .  
  
|Meta Veriler|Description|  
|--------------|-----------------|  
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcısı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "Tlbimp" öğesinin varsayılan sarmalayıcı aracını kullanır. Mevcut, büyük/küçük harf duyarsız seçenekleri şunlardır:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesini kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullandığınızda, bir sarmalayıcı çıkış dizini belirtmeyin çünkü bu, görevin başarısız olmasına neden olur.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.<br />-   `AXImp`: Bir ActiveX denetimi için birlikte çalışma derlemesi oluşturmak istediğinizde bu sarmalayıcı aracını kullanın.|  
  
> [!NOTE]
> Bir tür kitaplığını benzersiz şekilde tanımlamak için sağladığınız daha fazla bilgi, görevin diskteki doğru dosyaya çözümlenme olasılığı artar.  
  
## <a name="remarks"></a>Açıklamalar  
 Yukarıda listelenen parametrelere ek olarak, bu görev sınıfından parametreleri devralır <xref:Microsoft.Build.Utilities.Task> . Bu ek parametrelerin ve açıklamalarının listesi için bkz. [görev temel sınıfı](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görevlerinize](../msbuild/msbuild-tasks.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
