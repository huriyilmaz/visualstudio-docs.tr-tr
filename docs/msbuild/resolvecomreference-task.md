---
title: ResolveComReference Task | Microsoft Docs
description: Bir MSBuild veya daha fazla tür kitaplığı adı veya .tlb dosyası listesini almak ve bunları diskte konumlara çözümlemek için ResolveComReference görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d621646ff5408cfa03d070f11fab697f0d983ed5
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130211941"
---
# <a name="resolvecomreference-task"></a>ResolveComReference görevi

Bir veya daha fazla tür kitaplığı adı veya *.tlb* dosyası listesini alır ve bu tür kitaplıklarını diskte konumlara çözümler.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `ResolveCOMReference` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`DelaySign`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` ortak anahtarı derlemeye yer. ise, `false` derlemeyi tam olarak imzalar.|
|`EnvironmentVariables`|İsteğe `String[]` bağlı parametre.<br /><br /> Ortam değişkenlerinin eşit işaretlerle ayrılmış çiftleri dizisi. Bu değişkenler, normal ortam *bloğunatlbimp.exe* *aximp.exe* veya seçmeli olarak geçersiz kılmanın yanı sıra, bu değişkenler de ortaya çıktıya geçiri.|
|`ExecuteAsTool`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, gereklitlbimp.exederlemeleriaximp.exeuygun hedef çerçeveden yordam dışından çalıştırarak `true` derlemeyi çalıştırır.   Bu parametre çoklu hedeflemeyi sağlar.|
|`IncludeVersionInInteropName`|İsteğe `Boolean` bağlı parametre.<br /><br /> ise, `true` typelib sürümü sarmalayıcı adına dahil edilir. Varsayılan değer: `false`.|
|`KeyContainer`|İsteğe `String` bağlı parametre.<br /><br /> Ortak/özel anahtar çiftini tutan bir kapsayıcı belirtir.|
|`KeyFile`|İsteğe `String` bağlı parametre.<br /><br /> Ortak/özel anahtar çifti içeren bir öğeyi belirtir.|
|`NoClassMembers`|İsteğe `Boolean` bağlı parametre.|
|`ResolvedAssemblyReferences`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Çözümlenen derleme başvurularını belirtir.|
|`ResolvedFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Diskte, bu göreve giriş olarak sağlanan tür kitaplıklarının fiziksel konumlarına karşılık gelen tam dosyaları belirtir.|
|`ResolvedModules`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.|
|`SdkToolsPath`|İsteğe <xref:System.String?displayProperty=fullName> bağlı parametre.<br /><br /> ise, `ExecuteAsTool` `true` bu parametrenin hedeflenen çerçeve sürümü için SDK araçları yoluna ayarlanmış olması gerekir.|
|`StateFile`|İsteğe `String` bağlı parametre.<br /><br /> COM bileşen zaman damgası için önbellek dosyasını belirtir. Yoksa, her çalıştırma tüm sarmalayıcıları yeniden üretecek.|
|`TargetFrameworkVersion`|İsteğe `String` bağlı parametre.<br /><br /> Proje hedef çerçevesi sürümünü belirtir.<br /><br /> Varsayılan değer: `String.Empty`. başka bir ifadeyle, hedef çerçeveye göre bir başvuru için filtreleme yoktur.|
|`TargetProcessorArchitecture`|İsteğe `String` bağlı parametre.<br /><br /> Tercih edilen hedef işlemci mimarisini belirtir. Çeviriden sonra *tlbimp.exe*/machine bayrağına geçirildi.<br /><br /> Parametre değeri üyesi <xref:Microsoft.Build.Utilities.ProcessorArchitecture> olmalıdır.|
|`TypeLibFiles`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> COM başvurularını içeren tür kitaplığı dosya yolunu belirtir. Bu parametreye dahil edilen öğeler öğe meta verilerini içerebilir. Daha fazla bilgi için aşağıdaki [TypeLibFiles öğe meta verileri bölümüne](#typelibfiles-item-metadata) bakın.|
|`TypeLibNames`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı parametre.<br /><br /> Çözümlen tür kitaplığı adlarını belirtir. Bu parametreye dahil edilen öğelerin bazı öğe meta verileri içermesi gerekir. Daha fazla bilgi için aşağıdaki [TypeLibNames öğe meta verileri bölümüne](#typelibnames-item-metadata) bakın.|
|`WrapperOutputDirectory`|İsteğe `String` bağlı parametre.<br /><br /> Diskte, oluşturulan birlikte çalışma derlemenin yerleştiril olduğu konum. Bu öğe meta verileri belirtilmezse, görev proje dosyasının bulunduğu dizinin mutlak yolunu kullanır.|

## <a name="typelibnames-item-metadata"></a>TypeLibNames öğe meta verileri

 Aşağıdaki tabloda, parametresine geçirilen öğeler için kullanılabilen öğe meta verileri `TypeLibNames` açık almaktadır.

|Meta veri|Description|
|--------------|-----------------|
|`GUID`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığı için GUID. Bu öğe meta verileri belirtilmezse görev başarısız olur.|
|`VersionMajor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ana sürümü. Bu öğe meta verileri belirtilmezse görev başarısız olur.|
|`VersionMinor`|Gerekli öğe meta verileri.<br /><br /> Tür kitaplığının ikincil sürümü. Bu öğe meta verileri belirtilmezse görev başarısız olur.|
|`EmbedInteropTypes`|İsteğe `Boolean` bağlı meta veriler.<br /><br />  ise, `true` birlikte çalışma DLL'si oluşturmak yerine bu başvurudan birlikte çalışma türlerini doğrudan derlemenize ekleyin.|
|`LocaleIdentifier`|İsteğe bağlı öğe meta verileri.<br /><br /> Tür kitaplığı için Yerel Kimlik Tanımlayıcısı (veya LCID). Bu, bir kullanıcı, bölge veya uygulama tarafından tercih edilen insan dilini tanımlayan 32 bitlik bir değer olarak belirtilir. Bu öğe meta verileri belirtilmezse, görev varsayılan "0" yerel ayar tanımlayıcısını kullanır.|
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmezse, görev "tlbimp" varsayılan sarmalayıcı aracını kullanır. Tür seçimlerinin kullanılabilir, büyük/büyük harfe duyarsız seçenekleri:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesi kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullanıyorsanız, görevin başarısız olmasına neden olacak bir sarmalayıcı çıkış dizini belirtme.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğiniz zaman bu sarmalayıcı aracını kullanın.<br /> -   `PrimaryOrTLBImp`: Uygun olup olmadığınız konusunda emin değilseniz bu `Primary` sarmalayıcı `TLBImp` aracını kullanın. Mantık `Primary` önce ve ardından `TLBImp` uygulanır.<br />-   `AXImp`:Bir ActiveX Denetimi için birlikte çalışma derlemesi oluşturmak istediğiniz zaman bu sarmalayıcı aracını kullanın.|

## <a name="typelibfiles-item-metadata"></a>TypeLibFiles öğe meta verileri

 Aşağıdaki tabloda, parametresine geçirilen öğeler için kullanılabilen öğe meta verileri `TypeLibFiles` açık almaktadır.

|Meta veri|Description|
|--------------|-----------------|
|`EmbedInteropTypes`|İsteğe `Boolean` bağlı parametre.<br /><br />  ise, `true` birlikte çalışma DLL'si oluşturmak yerine bu başvurudan birlikte çalışma türlerini doğrudan derlemenize ekleyin.|
|`WrapperTool`|İsteğe bağlı öğe meta verileri.<br /><br /> Bu tür kitaplığı için derleme sarmalayıcı oluşturmak için kullanılan sarmalayıcı aracını belirtir. Bu öğe meta verileri belirtilmezse, görev "tlbimp" varsayılan sarmalayıcı aracını kullanır. Tür seçimlerinin kullanılabilir, büyük/büyük harfe duyarsız seçenekleri:<br /><br /> -   `Primary`: COM bileşeni için önceden oluşturulmuş bir birincil birlikte çalışma derlemesi kullanmak istediğinizde bu sarmalayıcı aracını kullanın. Bu sarmalayıcı aracını kullanıyorsanız, görevin başarısız olmasına neden olacak bir sarmalayıcı çıkış dizini belirtme.<br />-   `TLBImp`: COM bileşeni için birlikte çalışma derlemesi oluşturmak istediğiniz zaman bu sarmalayıcı aracını kullanın.<br />-   `AXImp`: Bir ActiveX Denetimi için birlikte çalışma derlemesi oluşturmak istediğiniz zaman bu sarmalayıcı aracını kullanın.|

> [!NOTE]
> Bir tür kitaplığını benzersiz olarak tanımlamak için ne kadar fazla bilgi sağlarsanız, görevin diskte doğru dosyaya çözümleme olasılığı o kadar yüksek olur.

## <a name="remarks"></a>Açıklamalar

Bu görev, yukarıda listelenen parametrelere ek olarak sınıfından parametreleri <xref:Microsoft.Build.Utilities.Task> devralıyor. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [Görev temel sınıfı.](../msbuild/task-base-class.md)

Bu görevin çalışması için COM DLL'nin makineye kayıtlı olması gerekir.

## <a name="msb4803-error"></a>MSB4803 Hatası

CLI komutlarından görevi kullanan bir projeyi `ResolveCOMReference` çalıştırmayı `dotnet` denersanız şu hatayı alırsınız:

```output
MSB4803: The task "ResolveComReference" is not supported on the .NET Core version of MSBuild. Please use the .NET Framework version of MSBuild.
```

Bu görev, MSBuild'nin .NET Core sürümünde desteklenmiyor. Bu, komutu komut satırdan çalıştırarak `dotnet build` kullanılan görevdir. Bu, uygulamanınMSBuild.exesürümünü [kullandığından](msbuild-command-line-reference.md) Visual Studio Geliştirici Komut İstemi'i .NET Framework projeyi MSBuild.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
