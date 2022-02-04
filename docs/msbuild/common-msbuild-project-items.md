---
title: Ortak MSBuild Project Öğeleri | Microsoft Docs
description: 'Ortak proje öğeleri MSBuild öğrenin. Öğeler, bir veya daha fazla dosyaya yönelik adlandırılmış başvurulardır ve dosya adları, yollar ve sürüm numaraları gibi meta verilere sahip olur.'
ms.custom: SEO-VS-2020
ms.date: 10/29/2020
ms.topic: reference
dev_langs:
  - VB
  - CSharp
  - C++
  - jsharp
helpviewer_keywords:
  - 'MSBuild, common project items'
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
  - multiple
---
# <a name="common-msbuild-project-items"></a>Yaygın MSBuild proje öğeleri

Bu MSBuild öğe, bir veya daha fazla dosyanın adlandırılmış başvurusu olur. Öğeler dosya adları, yollar ve sürüm numaraları gibi meta verileri içerir. Tüm proje türlerinin Visual Studio ortak öğeleri vardır. Bu öğeler *Microsoft.Build.CommonTypes.xsd dosyasında tanımlanır*.

Bu makalede tüm ortak proje öğeleri listelanmıştır.

## <a name="reference"></a>Başvuru

Projedeki derleme (yönetilen) başvurularını temsil eder.

|Öğe meta veri adı|Description|
|---------------|-----------------|
|HintPath|İsteğe bağlı dize. Derlemenin göreli veya mutlak yolu.|
|Adı|İsteğe bağlı dize. Derlemenin görünen adı, örneğin, "Sistem. Windows. Formlar."|
|FusionName|İsteğe bağlı dize. Öğe için basit veya güçlü fusion adını belirtir.<br /><br /> Bu öznitelik mevcut olduğunda, derleme dosyasının fusion adını almak için açılması gerekmay olduğundan zaman kaydedebilir.|
|SpecificVersion|İsteğe bağlı boole. Yalnızca fusion adlarında sürüme başvurulması gerekip gerek olmadığını belirtir.|
|Diğer adlar|İsteğe bağlı dize. Başvuru için tüm diğer adlar.|
|Özel|İsteğe bağlı boole. Başvuru çıktı klasörüne kopyalanır olup olmadığını belirtir. Bu öznitelik, **IDE'de** yer alan başvuru için Copy Local Visual Studio eşler.|

## <a name="comreference"></a>COMReference

Projedeki com (unmanaged) bileşen başvurularını temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|İsteğe bağlı dize. Bileşenin görünen adı.|
|Guid|Gerekli dize. bileşeni için şeklinde {12345678-1234-1234-1234-123456781234}bir GUID.|
|VersionMajor|Gerekli dize. Bileşenin sürüm numarasının ana bölümü. Örneğin, tam sürüm numarası "5.46" ise "5".|
|VersionMinor|Gerekli dize. Bileşenin sürüm numarasının küçük bölümü. Örneğin, tam sürüm numarası "5.46" ise "46".|
|EmbedInteropTypes|İsteğe bağlı boole. True ise, birlikte çalışma DLL'si oluşturmak yerine bu başvurudan birlikte çalışma türlerini doğrudan derlemenize ekleyin.|
|LCID|İsteğe bağlı dize. Bileşenin LocaleID'i.|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı. Değerler:<br /><br />1. birincil<br />2. tlbimp<br />3. primaryortlbimp<br />4. aximp|
|Yalıtılmış|İsteğe bağlı boole. Bileşenin kayıtsız bir bileşen olup olmadığını belirtir.|

## <a name="comfilereference"></a>COMFileReference

[ResolveComReference](resolvecomreference-task.md) hedefinin parametresine geçirilen `TypeLibFiles` tür kitaplıklarının listesini temsil eder. Bu öğe yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Description|
|---------------|-----------------|
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı. Değerler:<br /><br />1. birincil<br />2. tlbimp<br />3. primaryortlbimp<br />4. aximp|

## <a name="nativereference"></a>NativeReference

Yerel bildirim dosyasını veya bu tür bir dosyaya başvuruyu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|Gerekli dize. Bildirim dosyasının temel adı.|
|HintPath|Gerekli dize. Bildirim dosyasının göreli yolu.|

## <a name="projectreference"></a>ProjectReference

Başka bir projeye başvuru temsil eder. `ProjectReference` öğeleri hedef tarafından [Başvuru](#reference) `ResolveProjectReferences` öğelerine dönüşür, bu nedenle dönüştürme işlemi üzerine yazmazsa bir Başvurudaki `ProjectReference`geçerli meta veriler üzerinde geçerli olabilir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Ad|İsteğe bağlı dize. Başvuru görünen adı.|
|GlobalPropertiesToRemove|İsteğe bağlı `string[]` . Başvurulan proje oluşturulurken kaldırılacak özelliklerin adları (örneğin `RuntimeIdentifier;PackOnBuild` ,). Varsayılan olarak boştur.|
|Project|İsteğe bağlı dize. Formundaki {12345678-1234-1234-1234-123456781234} , başvuru için BIR GUID.|
|Outputıtemtype|İsteğe bağlı dize. Hedef çıkışları içine yayan öğe türü. Varsayılan değer boştur. Başvuru meta verileri "true" (varsayılan) olarak ayarlandıysa, hedef çıkışlar derleyici için başvurular olur.|
|ReferenceOutputAssembly|İsteğe bağlı Boolean. , Olarak `false` ayarlanırsa, başvurulan projenin çıktısını bu projenin bir [başvurusu](#reference) olarak içermez, ancak yine de diğer projenin bundan önce derleme yapmalarını sağlar. Varsayılan olarak `true` olur.|
|SetConfiguration|İsteğe bağlı dize. Başvurulan proje için genel özelliği `Configuration` Ayarlar, örneğin `Configuration=Release` .|
|SetPlatform|İsteğe bağlı dize. Başvurulan proje için genel özelliği `Platform` Ayarlar, örneğin `Platform=AnyCPU` .|
|SetTargetFramework|İsteğe bağlı dize. Başvurulan proje için genel özelliği `TargetFramework` Ayarlar, örneğin `TargetFramework=netstandard2.0` .|
|SkipGetTargetFrameworkProperties|İsteğe bağlı Boolean. İse `true` , başvurulan projeyi en uyumlu `TargetFramework` değere anlaşmadan oluşturur. Varsayılan olarak `false` olur.|
|Targets|İsteğe bağlı `string[]` . Başvurulan projelerde oluşturulması gereken hedeflerin noktalı virgülle ayrılmış listesi. Varsayılan, varsayılan hedefleri gösteren varsayılan değeri boş olan değeridir `$(ProjectReferenceBuildTargets)` .|

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

Olarak `[AssemblyMetadata(key, value)]` oluşturulacak derleme özniteliklerini temsil eder.

| Öğe meta veri adı | Description |
|-----------------------| - |
| Şunları Dahil Et: | Öznitelik oluşturucusunda ilk parametre (anahtar) `AssemblyMetadataAttribute` olur. |
| Değer | Gerekli dize. Öznitelik oluşturucusunda ikinci parametre (değer) `AssemblyMetadataAttribute` olur. |

> [!NOTE]
> Bu öğe, .NET 5 (ve .NET Core) ve sonraki sürümler için SDK 'Yı kullanan projeler için geçerlidir.

## <a name="internalsvisibleto"></a>InternalsVisibleTo

Derleme öznitelikleri olarak `[InternalsVisibleTo(..)]` yayınlanedilecek derlemeleri belirtir.

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
