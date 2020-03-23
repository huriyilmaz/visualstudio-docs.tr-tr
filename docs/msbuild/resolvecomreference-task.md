---
title: ÇözümcomReference Görevi | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595208"
---
# <a name="resolvecomreference-task"></a>ResolveComReference görevi

Bir veya daha fazla tür kitaplık adlarının veya *.tlb* dosyalarının listesini alır ve bu tür kitaplıklarını diskteki konumlara giderir.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `ResolveCOMReference` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DelaySign`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`ortak anahtarı derlemeye yerleştirir. Eğer, `false`tam olarak montaj imzalar.|
|`EnvironmentVariables`|İsteğe bağlı `String[]` parametre.<br /><br /> Eşit işaretlerle ayrılmış ortam değişkenleri dizilimi. Bu değişkenler yumurtlanan *tlbimp.exe* ve *aximp.exe'ye* normal ortam bloğuna ek olarak veya seçici olarak geçersiz kılınan değişkenlere iletilir...|
|`ExecuteAsTool`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer, `true`gerekli sarıcı montajları oluşturmak için uygun hedef çerçeve out-of-proc *tlbimp.exe* ve *aximp.exe* çalışır. Bu parametre çoklu hedefleme sağlar.|
|`IncludeVersionInInteropName`|İsteğe bağlı `Boolean` parametre.<br /><br /> Eğer `true`, typelib sürümü sarıcı adına eklenecektir. Varsayılan değer: `false`.|
|`KeyContainer`|İsteğe bağlı `String` parametre.<br /><br /> Ortak/özel anahtar çifti tutan bir kapsayıcı belirtir.|
|`KeyFile`|İsteğe bağlı `String` parametre.<br /><br /> Ortak/özel anahtar çifti içeren bir öğe belirtir.|
|`NoClassMembers`|İsteğe bağlı `Boolean`parametre.|
|`ResolvedAssemblyReferences`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Çözümlenmiş derleme başvurularını belirtir.|
|`ResolvedFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Bu göreve girdi olarak sağlanan tür kitaplıklarının fiziksel konumlarına karşılık gelen diskteki tam nitelikli dosyaları belirtir.|
|`ResolvedModules`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]`parametre.|
|`SdkToolsPath`|İsteğe bağlı <xref:System.String?displayProperty=fullName> parametre.<br /><br /> `ExecuteAsTool` Varsa, `true`bu parametre hedeflenen çerçeve sürümü için SDK araçları yoluna ayarlanmalıdır.|
|`StateFile`|İsteğe bağlı `String` parametre.<br /><br /> COM bileşen zaman damgaları için önbellek dosyasını belirtir. Eğer mevcut değilse, her çalışma tüm sarmalayıcıları yeniler.|
|`TargetFrameworkVersion`|İsteğe bağlı `String` parametre.<br /><br /> Proje hedef çerçeve sürümünü belirtir.<br /><br /> Varsayılan değer: `String.Empty`. bu da hedef çerçeveye dayalı bir başvuru için filtreleme olmadığı anlamına gelir.|
|`TargetProcessorArchitecture`|İsteğe bağlı `String` parametre.<br /><br /> Tercih edilen hedef işlemci mimarisini belirtir. Çeviriden sonra *tlbimp.exe*/machine bayrağına geçti.<br /><br /> Parametre <xref:Microsoft.Build.Utilities.ProcessorArchitecture>değeri.|
|`TypeLibFiles`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Com başvuruları için tür kitaplığı dosya yolunu belirtir. Bu parametrede yer alan öğeler madde meta verileri içerebilir. Daha fazla bilgi için aşağıdaki [TypeLibFiles öğe meta verilerine](#typelibfiles-item-metadata) bakın.|
|`TypeLibNames`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametre.<br /><br /> Çözümlemek için tür kitaplık adlarını belirtir. Bu parametrede yer alan öğelerin bazı madde meta verileri içermesi gerekir. Daha fazla bilgi için aşağıdaki [TypeLibNames öğesi meta verilerine](#typelibnames-item-metadata) bakın.|
|`WrapperOutputDirectory`|İsteğe bağlı `String` parametre.<br /><br /> Oluşturulan interop derlemesinin yerleştirildiği diskteki konum. Bu öğe meta verileri belirtilmemişse, görev proje dosyasının bulunduğu dizinin mutlak yolunu kullanır.|

## <a name="typelibnames-item-metadata"></a>TypeLibNames öğe meta verileri

 Aşağıdaki tabloda `TypeLibNames` parametreye geçirilen maddeler için kullanılabilir madde meta verileri açıklanmaktadır.

|Meta Veriler|Açıklama|
|--------------|-----------------|
|`GUID`|Gerekli madde meta verileri.<br /><br /> Tür kitaplığı için GUID. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`VersionMajor`|Gerekli madde meta verileri.<br /><br /> Tür kitaplığın ana sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`VersionMinor`|Gerekli madde meta verileri.<br /><br /> Tür kitaplığın küçük sürümü. Bu öğe meta verileri belirtilmemişse, görev başarısız olur.|
|`EmbedInteropTypes`|İsteğe bağlı `Boolean` meta veriler.<br /><br />  Eğer, `true`bu başvurudan interop türlerini doğrudan bir interop DLL oluşturmak yerine derlemenize gömün.|
|`LocaleIdentifier`|İsteğe bağlı madde meta verileri.<br /><br /> Tür kitaplığı için Yerel Tanımlayıcı (veya LCID). Bu, bir kullanıcı, bölge veya uygulama tarafından tercih edilen insan dilini tanımlayan 32 bitlik bir değer olarak belirtilir. Bu öğe meta verileri belirtilmemişse, görev "0" varsayılan yerel tanımlayıcı kullanır.|
|`WrapperTool`|İsteğe bağlı madde meta verileri.<br /><br /> Bu tür kitaplığı için montaj sarıcı oluşturmak için kullanılan sarıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "tlbimp" varsayılan sarıcı aracını kullanır. Typelibs mevcut, büyük/küçük harf duyarsız seçimler şunlardır:<br /><br /> -   `Primary`: COM bileşeni için zaten oluşturulmuş bir birincil interop montajını kullanmak istediğinizde bu sarıcı aracını kullanın. Bu sarıcı aracını kullandığınızda, görevin başarısız lığa neden olacağından sarmalayıcı çıktı dizini belirtmeyin.<br />-   `TLBImp`: COM bileşeni için bir interop montaj oluşturmak istediğinizde bu sarıcı aracını kullanın.<br />-   `AXImp`:ActiveX Denetimi için bir interop montajı oluşturmak istediğinizde bu sarıcı aracını kullanın.|

## <a name="typelibfiles-item-metadata"></a>TypeLibFiles öğe meta verileri

 Aşağıdaki tabloda `TypeLibFiles` parametreye geçirilen maddeler için kullanılabilir madde meta verileri açıklanmaktadır.

|Meta Veriler|Açıklama|
|--------------|-----------------|
|`EmbedInteropTypes`|İsteğe bağlı `Boolean`parametre.<br /><br />  Eğer, `true`bu başvurudan interop türlerini doğrudan bir interop DLL oluşturmak yerine derlemenize gömün.|
|`WrapperTool`|İsteğe bağlı madde meta verileri.<br /><br /> Bu tür kitaplığı için montaj sarıcı oluşturmak için kullanılan sarıcı aracını belirtir. Bu öğe meta verileri belirtilmemişse, görev "tlbimp" varsayılan sarıcı aracını kullanır. Typelibs mevcut, büyük/küçük harf duyarsız seçimler şunlardır:<br /><br /> -   `Primary`: COM bileşeni için zaten oluşturulmuş bir birincil interop montajını kullanmak istediğinizde bu sarıcı aracını kullanın. Bu sarıcı aracını kullandığınızda, görevin başarısız lığa neden olacağından sarmalayıcı çıktı dizini belirtmeyin.<br />-   `TLBImp`: COM bileşeni için bir interop montaj oluşturmak istediğinizde bu sarıcı aracını kullanın.<br />-   `AXImp`: ActiveX Denetimi için bir interop montajı oluşturmak istediğinizde bu sarıcı aracını kullanın.|

> [!NOTE]
> Bir tür kitaplığını benzersiz olarak tanımlamak için ne kadar çok bilgi sağlarsanız, görevin diskteki doğru dosyaya çözüme kavuşturulması olasılığı da o kadar artar.

## <a name="remarks"></a>Açıklamalar

Yukarıda listelenen parametrelere ek olarak, bu görev <xref:Microsoft.Build.Utilities.Task> sınıftan parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için [Görev taban sınıfına](../msbuild/task-base-class.md)bakın.

Bu görevin çalışması için COM DLL'nin makineye kaydedilmesi gerekmez.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
