---
title: ortak MSBuild Project öğeleri | Microsoft Docs
description: ortak MSBuild proje öğeleri hakkında bilgi edinin. Öğeler bir veya daha fazla dosyaya başvuru olarak adlandırılır ve dosya adları, yollar ve sürüm numaraları gibi meta verilere sahiptir.
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
ms.openlocfilehash: 49fd97e1d8e91cd6049bbe43f7fee9fb092e8f39
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130211967"
---
# <a name="common-msbuild-project-items"></a>Yaygın MSBuild proje öğeleri

MSBuild, öğe bir veya daha fazla dosyaya yönelik adlandırılmış bir başvurudur. Öğeler, dosya adları, yollar ve sürüm numaraları gibi meta verileri içerir. Visual Studio tüm proje türlerinde ortak olarak birkaç öğe vardır. Bu öğeler *Microsoft. Build. CommonTypes. xsd* dosyasında tanımlanmıştır.

Bu makalede tüm ortak proje öğeleri listelenir.

## <a name="reference"></a>Başvuru

Projedeki derleme (yönetilen) başvurusunu temsil eder.

|Öğe meta veri adı|Description|
|---------------|-----------------|
|HintPath|İsteğe bağlı dize. Derlemenin göreli veya mutlak yolu.|
|Name|İsteğe bağlı dize. Derlemenin görünen adı, örneğin, "System. Windows. Forms. "|
|FusionName|İsteğe bağlı dize. Öğe için basit veya güçlü Fusion adı belirtir.<br /><br /> Bu öznitelik mevcut olduğunda, derleme dosyası Fusion adını almak için açılmadığından zaman tasarrufu yapabilirsiniz.|
|Bahsedilen SpecificVersion|İsteğe bağlı Boolean. Yalnızca Fusion adındaki sürümün başvurulması gerekip gerekmediğini belirtir.|
|Diğer adlar|İsteğe bağlı dize. Başvuru için herhangi bir diğer ad.|
|Özel|İsteğe bağlı Boolean. Başvurunun çıkış klasörüne kopyalanıp kopyalanmayacağını belirtir. bu öznitelik, Visual Studio ıde 'de olan başvurunun yereli **kopyala** özelliği ile eşleşir.|

## <a name="comreference"></a>COMReference

Projedeki COM (yönetilmeyen) bileşen başvurusunu temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|İsteğe bağlı dize. Bileşenin görünen adı.|
|Guid|Gerekli dize. Formundaki bileşeni için bir GUID {12345678-1234-1234-1234-1234567891234} .|
|VersionAna|Gerekli dize. Bileşenin sürüm numarasının ana bölümü. Örneğin, tam sürüm numarası "5,46" ise "5".|
|VersionMinor|Gerekli dize. Bileşenin sürüm numarasının küçük bölümü. Örneğin, tam sürüm numarası "5,46" ise, "46".|
|EmbedInteropTypes|İsteğe bağlı Boolean. Doğru ise, birlikte çalışma DLL 'SI oluşturmak yerine bu başvurudan doğrudan birlikte çalışma türlerini derlemeye ekleyin.|
|LCID|İsteğe bağlı dize. Bileşenin LocaleID 'Si.|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı. Değerler şunlardır:<br /><br />1. birincil<br />2. Tlbimp<br />3. bu yortlbimp<br />4. Aximp|
|Yalıtılmış|İsteğe bağlı Boolean. Bileşenin bir reg-Free bileşeni olup olmadığını belirtir.|

## <a name="comfilereference"></a>COMFileReference

`TypeLibFiles` [ResolveComReference](resolvecomreference-task.md) hedefinin parametresine geçirilen tür kitaplıklarının listesini temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Description|
|---------------|-----------------|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı. Değerler şunlardır:<br /><br />1. birincil<br />2. Tlbimp<br />3. bu yortlbimp<br />4. Aximp|

## <a name="nativereference"></a>NativeReference

Yerel bir bildirim dosyasını veya bu tür bir dosyaya yapılan başvuruyu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|Gerekli dize. Bildirim dosyasının temel adı.|
|HintPath|Gerekli dize. Bildirim dosyasının göreli yolu.|

## <a name="projectreference"></a>ProjectReference

Başka bir projenin başvurusunu temsil eder. `ProjectReference` öğeler, hedef tarafından [başvuru](#reference) öğelerine dönüştürülür `ResolveProjectReferences` `ProjectReference` . bu nedenle, dönüştürme işlemi onun üzerine yazmazsa, başvurudaki geçerli meta veriler üzerinde geçerli olabilir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|İsteğe bağlı dize. Başvurunun görünen adı.|
|GlobalPropertiesToRemove|İsteğe bağlı `string[]` . Başvurulan proje oluşturulurken kaldırılacak özelliklerin adları (örneğin,) `RuntimeIdentifier;PackOnBuild` . Varsayılan olarak boştur.|
|Project|İsteğe bağlı dize. Formundaki, başvuru için bir GUID {12345678-1234-1234-1234-1234567891234} .|
|Outputıtemtype|İsteğe bağlı dize. Hedef çıkışları içine yayan öğe türü. Varsayılan değer boştur. Başvuru meta verileri "true" (varsayılan) olarak ayarlandıysa, hedef çıkışlar derleyici için başvurular olur.|
|ReferenceOutputAssembly|İsteğe bağlı Boolean. , Olarak ayarlanırsa `false` , başvurulan projenin çıktısını bu projenin bir [başvurusu](#reference) olarak içermez, ancak yine de diğer projenin bundan önce derleme yapmalarını sağlar. Varsayılan olarak olur `true` .|
|SetConfiguration|İsteğe bağlı dize. `Configuration`Başvurulan proje için genel özelliği ayarlar, örneğin `Configuration=Release` .|
|SetPlatform|İsteğe bağlı dize. `Platform`Başvurulan proje için genel özelliği ayarlar, örneğin `Platform=AnyCPU` .|
|SetTargetFramework|İsteğe bağlı dize. `TargetFramework`Başvurulan proje için genel özelliği ayarlar, örneğin `TargetFramework=netstandard2.0` .|
|SkipGetTargetFrameworkProperties|İsteğe bağlı Boolean. İse `true` , başvurulan projeyi en uyumlu değere anlaşmadan oluşturur `TargetFramework` . Varsayılan olarak olur `false` .|
|Targets|İsteğe bağlı `string[]` . Başvurulan projelerde oluşturulması gereken hedeflerin noktalı virgülle ayrılmış listesi. Varsayılan, varsayılan `$(ProjectReferenceBuildTargets)` hedefleri gösteren varsayılan değeri boş olan değeridir.|

## <a name="compile"></a>Se

Derleyicinin kaynak dosyalarını temsil eder.

| Öğe meta veri adı | Description |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oto gen | İsteğe bağlı Boolean. Visual Studio tümleşik geliştirme ortamı (ıde) tarafından proje için dosyanın oluşturulup oluşturulmayacağını gösterir. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak proje dosyasının etki dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| Görünür | İsteğe bağlı Boolean. Dosyanın Visual Studio **Çözüm Gezgini** ' de görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |

## <a name="embeddedresource"></a>EmbeddedResource

Oluşturulan derlemeye gömülebilen kaynakları temsil eder.

| Öğe meta veri adı | Description |
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

| Öğe meta veri adı | Description |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun adı. |
| LastGenOutput | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya Oluşturucu tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| PublishState | Gerekli dize. İçeriğin Yayımlanma Durumu, aşağıdakilerden biri:<br /><br /> -Varsayılan<br />-Dahil edilen<br />-Dışlanan<br />-Veri dosyası<br />-Önkoşul |
| IsAssembly | İsteğe bağlı Boolean. Dosyanın bir derleme olup olmadığını belirtir. |
| Görünür | İsteğe bağlı Boolean. Dosyanın Visual Studio **Çözüm Gezgini** ' de görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |

## <a name="none"></a>Hiçbiri

Yapı işleminde rolü olmaması gereken dosyaları temsil eder.

| Öğe meta veri adı | Description |
|-----------------------| - |
| DependentUpon | İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya oluşturucusunun adı. |
| LastGenOutput | Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında konumlandırıldığında görüntülenecek olan notational yolu. |
| Görünür | İsteğe bağlı Boolean. Dosyanın Visual Studio **Çözüm Gezgini** ' de görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı |

## <a name="assemblymetadata"></a>AssemblyMetadata

Olarak oluşturulacak derleme özniteliklerini temsil eder `[AssemblyMetadata(key, value)]` .

| Öğe meta veri adı | Description |
|-----------------------| - |
| Şunları Dahil Et: | Öznitelik oluşturucusunda ilk parametre (anahtar) olur `AssemblyMetadataAttribute` . |
| Değer | Gerekli dize. Öznitelik oluşturucusunda ikinci parametre (değer) olur `AssemblyMetadataAttribute` . |

> [!NOTE]
> Bu öğe, .NET 5 (ve .NET Core) ve sonraki sürümler için SDK 'Yı kullanan projeler için geçerlidir.

## <a name="internalsvisibleto"></a>InternalsVisibleTo

Derleme öznitelikleri olarak yayınlanedilecek derlemeleri belirtir `[InternalsVisibleTo(..)]` .

| Öğe meta veri adı | Description |
|-----------------------| - |
| Şunları Dahil Et: | Bütünleştirilmiş kod adı. |
| Anahtar | İsteğe bağlı dize. Derlemenin ortak anahtarı. |

> [!NOTE]
> Bu öğe, .NET 5 (ve .NET Core) ve sonraki sürümler için SDK 'Yı kullanan projeler için geçerlidir.

## <a name="baseapplicationmanifest"></a>BaseApplicationManifest

yapı için temel uygulama bildirimini temsil eder ve ClickOnce dağıtım güvenliği bilgilerini içerir.

## <a name="codeanalysisimport"></a>Codeanalysisımport

İçeri aktarılacak FxCop projesini temsil eder.

## <a name="import"></a>İçeri Aktar

ad alanları Visual Basic derleyicisi tarafından içeri aktarılması gereken derlemeleri temsil eder.

## <a name="see-also"></a>Ayrıca bkz.

- [Yaygın MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
- [Yaygın MSBuild öğesi meta verileri](common-msbuild-item-metadata.md)
