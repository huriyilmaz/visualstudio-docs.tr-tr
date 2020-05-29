---
title: Ortak MSBuild proje öğeleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e728f6c4c04e0a3c9ce567c4aaae83ce15cb0cc
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84182917"
---
# <a name="common-msbuild-project-items"></a>Ortak MSBuild proje öğeleri

MSBuild 'de, bir öğe bir veya daha fazla dosyaya adlandırılmış bir başvurudur. Öğeler, dosya adları, yollar ve sürüm numaraları gibi meta verileri içerir. Visual Studio 'daki tüm proje türlerinde ortak olarak birkaç öğe vardır. Bu öğeler *Microsoft. Build. CommonTypes. xsd*dosyasında tanımlanmıştır.

## <a name="common-items"></a>Ortak öğeler

Tüm ortak proje öğelerinin listesi aşağıda verilmiştir.

### <a name="reference"></a>Başvuru

Projedeki derleme (yönetilen) başvurusunu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|HintPath|İsteğe bağlı dize. Derlemenin göreli veya mutlak yolu.|
|Adı|İsteğe bağlı dize. Derlemenin görünen adı, örneğin, "System. Windows. Forms."|
|FusionName|İsteğe bağlı dize. Öğe için basit veya güçlü Fusion adı belirtir.<br /><br /> Bu öznitelik mevcut olduğunda, derleme dosyası Fusion adını almak için açılmadığından zaman tasarrufu yapabilirsiniz.|
|Bahsedilen SpecificVersion|İsteğe bağlı Boolean. Yalnızca Fusion adındaki sürümün başvurulması gerekip gerekmediğini belirtir.|
|Diğer adlar|İsteğe bağlı dize. Başvuru için herhangi bir diğer ad.|
|Özel|İsteğe bağlı Boolean. Başvurunun çıkış klasörüne kopyalanıp kopyalanmayacağını belirtir. Bu öznitelik, Visual Studio IDE içinde olan başvurunun yereli **Kopyala** özelliğiyle eşleşir.|

### <a name="comreference"></a>COMReference

Projedeki COM (yönetilmeyen) bileşen başvurusunu temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Adı|İsteğe bağlı dize. Bileşenin görünen adı.|
|Guid|Gerekli dize. Formundaki bileşeni için bir GUID {12345678-1234-1234-1234-1234567891234} .|
|VersionAna|Gerekli dize. Bileşenin sürüm numarasının ana bölümü. Örneğin, tam sürüm numarası "5,46" ise "5".|
|VersionMinor|Gerekli dize. Bileşenin sürüm numarasının küçük bölümü. Örneğin, tam sürüm numarası "5,46" ise, "46".|
|LCID|İsteğe bağlı dize. Bileşenin LocaleID 'Si.|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı, örneğin, "Tlbimp."|
|Yalıtılmış|İsteğe bağlı Boolean. Bileşenin bir reg-Free bileşeni olup olmadığını belirtir.|

### <a name="comfilereference"></a>COMFileReference

`TypeLibFiles` [ResolveComReference](resolvecomreference-task.md) hedefinin parametresine geçirilen tür kitaplıklarının listesini temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı, örneğin, "Tlbimp."|

### <a name="nativereference"></a>NativeReference

Yerel bir bildirim dosyasını veya bu tür bir dosyaya yapılan başvuruyu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Adı|Gerekli dize. Bildirim dosyasının temel adı.|
|HintPath|Gerekli dize. Bildirim dosyasının göreli yolu.|

### <a name="projectreference"></a>ProjectReference

Başka bir projenin başvurusunu temsil eder. `ProjectReference`öğeler, hedef tarafından [başvuru](#reference) öğelerine dönüştürülür `ResolveProjectReferences` `ProjectReference` . bu nedenle, dönüştürme işlemi onun üzerine yazmazsa, başvurudaki geçerli meta veriler üzerinde geçerli olabilir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Adı|İsteğe bağlı dize. Başvurunun görünen adı.|
|Project|İsteğe bağlı dize. Formundaki, başvuru için bir GUID {12345678-1234-1234-1234-1234567891234} .|
|Paket|İsteğe bağlı dize. Başvurulduğu proje dosyasının yolu.|
|ReferenceOutputAssembly|İsteğe bağlı Boolean. , Olarak ayarlanırsa `false` , başvurulan projenin çıktısını bu projenin bir [başvurusu](#reference) olarak içermez, ancak yine de diğer projenin bundan önce derleme yapmalarını sağlar. Varsayılan olarak olur `true` .|

### <a name="compile"></a>Se

Derleyicinin kaynak dosyalarını temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oto gen | İsteğe bağlı Boolean. Visual Studio tümleşik geliştirme ortamı (IDE) tarafından proje için dosyanın oluşturulup oluşturulmayacağını gösterir. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak proje dosyasının etki dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| Görünür | İsteğe bağlı Boolean. Visual Studio 'da **Çözüm Gezgini** dosyanın görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |

### <a name="embeddedresource"></a>EmbeddedResource

Oluşturulan derlemeye gömülebilen kaynakları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir |
| Oluşturucu | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya oluşturucusunun adı. |
| LastGenOutput | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etki alanının dışında konumlandırıldığında, notational yolu görüntülenir. |
| Görünür | İsteğe bağlı Boolean. Visual Studio 'da **Çözüm Gezgini** dosyanın görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |
| LogicalName | Gerekli dize. Gömülü kaynağın mantıksal adı. |

### <a name="content"></a>İçerik

Projeye derlenmemiş ancak birlikte gömülebilir veya onunla birlikte yayımlanabilir olan dosyaları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun adı. |
| LastGenOutput | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya Oluşturucu tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| PublishState | Gerekli dize. İçeriğin Yayımlanma Durumu, aşağıdakilerden biri:<br /><br /> -Varsayılan<br />-Dahil edilen<br />-Dışlanan<br />-Veri dosyası<br />-Önkoşul |
| IsAssembly | İsteğe bağlı Boolean. Dosyanın bir derleme olup olmadığını belirtir. |
| Görünür | İsteğe bağlı Boolean. Visual Studio 'da **Çözüm Gezgini** dosyanın görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |

### <a name="none"></a>Hiçbiri

Yapı işleminde rolü olmaması gereken dosyaları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya oluşturucusunun adı. |
| LastGenOutput | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| Görünür | İsteğe bağlı Boolean. Visual Studio 'da **Çözüm Gezgini** dosyanın görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |

### <a name="assemblymetadata"></a>AssemblyMetadata

Olarak oluşturulacak derleme özniteliklerini temsil eder `[AssemblyMetadata(key, value)]` .

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Şunları Dahil Et: | Öznitelik oluşturucusunda ilk parametre (anahtar) olur `AssemblyMetadataAttribute` . |
| Değer | Gerekli dize. Öznitelik oluşturucusunda ikinci parametre (değer) olur `AssemblyMetadataAttribute` . |

> [!NOTE]
> Bu, yalnızca .NET Core SDK kullanan projeler için geçerlidir.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Yapı için temel uygulama bildirimini temsil eder ve ClickOnce dağıtımı güvenlik bilgilerini içerir.

### <a name="codeanalysisimport"></a>Codeanalysisımport

İçeri aktarılacak FxCop projesini temsil eder.

### <a name="import"></a>İçeri Aktar

Ad alanları Visual Basic Derleyicisi tarafından içeri aktarılması gereken derlemeleri temsil eder.

## <a name="see-also"></a>Ayrıca bkz.

- [Ortak MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
- [.NET Core SDK projeleri için MSBuild özellikleri](/dotnet/core/project-sdk/msbuild-props)
