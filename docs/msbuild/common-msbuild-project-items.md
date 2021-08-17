---
title: Ortak MSBuild Project Öğeleri | Microsoft Docs
description: Ortak proje öğeleri MSBuild öğrenin. Öğeler, bir veya daha fazla dosyaya yönelik adlandırılmış başvurulardır ve dosya adları, yollar ve sürüm numaraları gibi meta verilere sahip olur.
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 0b2804f86b26b8e274804c3f504b1f19cb6f83d2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055100"
---
# <a name="common-msbuild-project-items"></a>Yaygın MSBuild proje öğeleri

Bu MSBuild öğe, bir veya daha fazla dosyanın adlandırılmış başvurusu olur. Öğeler dosya adları, yollar ve sürüm numaraları gibi meta verileri içerir. Tüm proje türleri Visual Studio ortak öğeler içerir. Bu öğeler *Microsoft.Build.CommonTypes.xsd dosyasında tanımlanır.*

Bu makalede tüm ortak proje öğeleri listelanmıştır.

## <a name="reference"></a>Başvuru

Projedeki derleme (yönetilen) başvurularını temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|HintPath|İsteğe bağlı dize. Derlemenin göreli veya mutlak yolu.|
|Name|İsteğe bağlı dize. Derlemenin görünen adı, örneğin, "Sistem. Windows. Formlar."|
|FusionName|İsteğe bağlı dize. Öğe için basit veya güçlü fusion adını belirtir.<br /><br /> Bu öznitelik mevcut olduğunda, derleme dosyasının fusion adını almak için açılması gerekmaması nedeniyle zamandan tasarruf sağlar.|
|SpecificVersion|İsteğe bağlı boole. Yalnızca fusion adlarında sürüme başvurulması gerekip gerek olmadığını belirtir.|
|Diğer adlar|İsteğe bağlı dize. Başvuru için tüm diğer adlar.|
|Özel|İsteğe bağlı boole. Başvuru çıktı klasörüne kopyalanır olup olmadığını belirtir. Bu öznitelik, **IDE'de** yer alan başvuru için Copy Local Visual Studio eşler.|

## <a name="comreference"></a>COMReference

Projedeki com (unmanaged) bileşen başvurularını temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|İsteğe bağlı dize. Bileşenin görünen adı.|
|Guid|Gerekli dize. bileşeni için şeklinde bir {12345678-1234-1234-1234-1234567891234} GUID.|
|VersionMajor|Gerekli dize. Bileşenin sürüm numarasının ana bölümü. Örneğin, tam sürüm numarası "5.46" ise "5".|
|VersionMinor|Gerekli dize. Bileşenin sürüm numarasının küçük bölümü. Örneğin, tam sürüm numarası "5.46" ise "46".|
|LCID|İsteğe bağlı dize. Bileşenin LocaleID'i.|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı( örneğin, "tlbimp."|
|Yalıtılmış|İsteğe bağlı boole. Bileşenin kayıtsız bir bileşen olup olmadığını belirtir.|

## <a name="comfilereference"></a>COMFileReference

`TypeLibFiles` [ResolveComReference](resolvecomreference-task.md) hedefinin parametresine geçirilen tür kitaplıklarının listesini temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı( örneğin, "tlbimp."|

## <a name="nativereference"></a>NativeReference

Yerel bildirim dosyasını veya bu tür bir dosyaya başvuruyu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|Gerekli dize. Bildirim dosyasının temel adı.|
|HintPath|Gerekli dize. Bildirim dosyasının göreli yolu.|

## <a name="projectreference"></a>ProjectReference

Başka bir projeye başvuru temsil eder. `ProjectReference` öğeleri hedef tarafından [Başvuru](#reference) öğelerine dönüşür, bu nedenle dönüştürme işlemi üzerine yazmazsa bir Başvurudaki geçerli meta veriler `ResolveProjectReferences` üzerinde geçerli `ProjectReference` olabilir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|İsteğe bağlı dize. Başvuru görünen adı.|
|GlobalPropertiesToRemove|İsteğe bağlı `string[]` . Başvurulan projeyi inşa etmek için kaldırılan özelliklerin adları, örneğin `RuntimeIdentifier;PackOnBuild` . Varsayılan olarak boştur.|
|Project|İsteğe bağlı dize. Başvuru için, formunda bir {12345678-1234-1234-1234-1234567891234} GUID.|
|OutputItemType|İsteğe bağlı dize. Hedef çıkışların yayma öğesi türü. Varsayılan değer boştur. Başvuru meta verileri "true" (varsayılan) olarak ayarlanırsa, hedef çıkışlar derleyici için başvuru haline gelir.|
|ReferenceOutputAssembly|İsteğe bağlı Boolean. , Olarak ayarlanırsa `false` , başvurulan projenin çıktısını bu projenin bir [başvurusu](#reference) olarak içermez, ancak yine de diğer projenin bundan önce derleme yapmalarını sağlar. Varsayılan olarak olur `true` .|
|SetConfiguration|İsteğe bağlı dize. `Configuration`Başvurulan proje için genel özelliği ayarlar, örneğin `Configuration=Release` .|
|SetPlatform|İsteğe bağlı dize. `Platform`Başvurulan proje için genel özelliği ayarlar, örneğin `Platform=AnyCPU` .|
|SetTargetFramework|İsteğe bağlı dize. `TargetFramework`Başvurulan proje için genel özelliği ayarlar, örneğin `TargetFramework=netstandard2.0` .|
|SkipGetTargetFrameworkProperties|İsteğe bağlı Boolean. İse `true` , başvurulan projeyi en uyumlu değere anlaşmadan oluşturur `TargetFramework` . Varsayılan olarak olur `false` .|
|Targets|İsteğe bağlı `string[]` . Başvurulan projelerde oluşturulması gereken hedeflerin noktalı virgülle ayrılmış listesi. Varsayılan, varsayılan `$(ProjectReferenceBuildTargets)` hedefleri gösteren varsayılan değeri boş olan değeridir.|

## <a name="compile"></a>Se

Derleyicinin kaynak dosyalarını temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oto gen | İsteğe bağlı Boolean. Visual Studio tümleşik geliştirme ortamı (ıde) tarafından proje için dosyanın oluşturulup oluşturulmayacağını gösterir. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak proje dosyasının etki dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| Görünür | İsteğe bağlı Boolean. Dosyanın Visual Studio **Çözüm Gezgini** ' de görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |

## <a name="embeddedresource"></a>EmbeddedResource

Oluşturulan derlemeye gömülebilen kaynakları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir |
| Oluşturucu | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya oluşturucusunun adı. |
| LastGenOutput | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etki alanının dışında konumlandırıldığında, notational yolu görüntülenir. |
| Görünür | İsteğe bağlı Boolean. Dosyanın Visual Studio **Çözüm Gezgini** ' de görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |
| LogicalName | Gerekli dize. Gömülü kaynağın mantıksal adı. |

## <a name="content"></a>Content

Projeye derlenmemiş ancak birlikte gömülebilir veya onunla birlikte yayımlanabilir olan dosyaları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun adı. |
| LastGenOutput | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya Oluşturucu tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| PublishState | Gerekli dize. İçeriğin Yayımlanma Durumu, aşağıdakilerden biri:<br /><br /> -Varsayılan<br />-Dahil edilen<br />-Dışlanan<br />- DataFile<br />- Önkoşul |
| ısassembly | İsteğe bağlı boole. Dosyanın bir derleme olup olmadığını belirtir. |
| Görünür | İsteğe bağlı boole. Dosyanın dosyanın dosya içinde **Çözüm Gezgini** olup Visual Studio. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalayıp kopyalan olmadığını belirler. Değerler:<br /><br /> 1. Hiçbir zaman<br />2. Her zaman<br />3. KoruYeni |

## <a name="none"></a>Hiçbiri

Derleme sürecinde rolü olması gereken dosyaları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Bu dosyanın doğru derlenmiş şekilde bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğe üzerinde çalıştıracak herhangi bir dosya oluşturucu adı. |
| LastGenOutput | Gerekli dize. Bu öğe üzerinde çalıştırılan herhangi bir dosya oluşturucu tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan tüm dosya oluşturucuların kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya, projenin etkisinin dışında fiziksel olarak bulunuyorsa görüntülenecek olan notational yol. |
| Görünür | İsteğe bağlı boole. Dosyanın dosyanın dosya içinde **Çözüm Gezgini** olup Visual Studio. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalayıp kopyalan olmadığını belirler. Değerler:<br /><br /> 1. Hiçbir zaman<br />2. Her zaman<br />3. KoruYeni |

## <a name="assemblymetadata"></a>Assemblymetadata

olarak oluşturulecek derleme özniteliklerini temsil `[AssemblyMetadata(key, value)]` eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Şunları Dahil Et: | Öznitelik oluşturucusuzda ilk parametre (anahtar) `AssemblyMetadataAttribute` olur. |
| Değer | Gerekli dize. Öznitelik oluşturucusuzda ikinci parametre (değer) `AssemblyMetadataAttribute` olur. |

> [!NOTE]
> Bu öğe, .NET 5 (ve .NET Core) ve sonraki sürümleri için SDK kullanan projeler için geçerlidir.

## <a name="internalsvisibleto"></a>InternalsVisibleTo

Derleme öznitelikleri olarak yayılacak `[InternalsVisibleTo(..)]` derlemeleri belirtir.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Şunları Dahil Et: | Derleme adı. |
| Anahtar | İsteğe bağlı dize. Derlemenin ortak anahtarı. |

> [!NOTE]
> Bu öğe, .NET 5 (ve .NET Core) ve sonraki sürümleri için SDK kullanan projeler için geçerlidir.

## <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Derleme için temel uygulama bildirimini temsil eder ve dağıtım ClickOnce bilgilerini içerir.

## <a name="codeanalysisimport"></a>CodeAnalysisImport

İçeri aktarıla fxcop projesini temsil eder.

## <a name="import"></a>İçeri Aktar

Veri derleyicisi tarafından ad alanları içe aktarılacak derlemeleri Visual Basic temsil eder.

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
