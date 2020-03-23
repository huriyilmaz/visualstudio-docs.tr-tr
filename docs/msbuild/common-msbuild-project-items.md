---
title: Ortak MSBuild Proje Öğeleri | Microsoft Dokümanlar
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
ms.openlocfilehash: c7725108fd71f4292a8d3fa4dfe68ca29d3dcd90
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634454"
---
# <a name="common-msbuild-project-items"></a>Ortak MSBuild proje öğeleri

MSBuild'te bir öğe, bir veya daha fazla dosyaiçin adlandırılmış bir başvurudur. Öğeler dosya adları, yollar ve sürüm numaraları gibi meta veriler içerir. Visual Studio'daki tüm proje türlerinin ortak birkaç öğesi vardır. Bu öğeler *Microsoft.Build.CommonTypes.xsd*dosyasında tanımlanır.
## <a name="common-items"></a>Ortak öğeler

 Aşağıda, tüm ortak proje öğelerinin bir listesi vetir.
Aşağıda, tüm ortak proje öğelerinin bir listesi vetir.

### <a name="reference"></a>Başvuru

 Projedeki bir derleme (yönetilen) başvuruyu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|HintPath|İsteğe bağlı dize. Derlemenin göreli veya mutlak yolu.|
|Adı|İsteğe bağlı dize. Derlemenin görüntü adı, örneğin, "System.Windows.Forms."|
|FusionName|İsteğe bağlı dize. Öğe için basit veya güçlü bir kaynaşma adını belirtir.<br /><br /> Bu öznitelik mevcut olduğunda, derleme dosyası nın birliş adını almak için açılması gerekmedığından zaman kazandırabilir.|
|SpecificVersion|İsteğe bağlı boolean. Yalnızca kaynaştırma adındaki sürüme başvurup başvurulmaması gerektiğini belirtir.|
|Diğer adlar|İsteğe bağlı dize. Başvuru için herhangi bir takma ad.|
|Özel|İsteğe bağlı boolean. Başvurunun çıktı klasörüne kopyalanıp kopyalanmayacağını belirtir. Bu öznitelik, Visual Studio IDE'deki başvurunun **Yerel Kopya** özelliğiyle eşleşir.|

### <a name="comreference"></a>COMReference

 Projedeki bir COM (yönetilmeyen) bileşen başvuruyu temsil eder. Bu madde yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Adı|İsteğe bağlı dize. Bileşenin görüntü adı.|
|Guid|Gerekli dize. Bileşen için bir GUID, {12345678-1234-1234-1234-1234567891234}şeklinde .|
|SürümMajor|Gerekli dize. Bileşenin sürüm numarasının ana bölümü. Örneğin, tam sürüm numarası "5,46" ise "5" olur.|
|SürümMinor|Gerekli dize. Bileşenin sürüm numarasının küçük bölümü. Örneğin, tam sürüm numarası "5,46" ise "46".|
|LCID|İsteğe bağlı dize. Bileşen için LocaleID.|
|Sarma Aracı|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı, örneğin, "tlbimp."|
|Yalıtılmış|İsteğe bağlı boolean. Bileşenin reg-free bileşeni olup olmadığını belirtir.|

### <a name="comfilereference"></a>COMFileReference

 `TypeLibFiles` [ÇözümcomReference](resolvecomreference-task.md) hedefinin parametresine geçirilen tür kitaplıklarının listesini temsil eder. Bu madde yalnızca .NET projeleri için geçerlidir.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Sarma Aracı|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı, örneğin, "tlbimp."|

### <a name="nativereference"></a>NativeReference

 Yerel bir bildirim dosyasını veya böyle bir dosyaya başvurumu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Adı|Gerekli dize. Bildirim dosyasının temel adı.|
|HintPath|Gerekli dize. Bildirim dosyasının göreli yolu.|

### <a name="projectreference"></a>ProjeReferans

 Başka bir projeye yapılan başvuruyu temsil eder.

|Öğe meta veri adı|Açıklama|
|---------------|-----------------|
|Adı|İsteğe bağlı dize. Başvurunun görüntü adı.|
|Project|İsteğe bağlı dize. Formda, başvuru için bir {12345678-1234-1234-1234-1234567891234}GUID .|
|Paket|İsteğe bağlı dize. Başvurulan proje dosyasının yolu.|
|ReferansÇıktı Montajı|İsteğe bağlı boolean. `false`Ayarlanırsa, bu projenin [Başvurusu](#reference) olarak başvurulan projenin çıktısını içermez, ancak yine de diğer projenin bundan önce oluşturulmasını sağlar. Varsayılan `true`değer.|

### <a name="compile"></a>Derlemek

 Derleyicinin kaynak dosyalarını temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Bağımlı | İsteğe bağlı dize. Bu dosyanın doğru derlemek için bağlı olduğu dosyayı belirtir. |
| Otojen | İsteğe bağlı boolean. Dosyanın Visual Studio tümleşik geliştirme ortamı (IDE) tarafından proje için oluşturulup oluşturulmadığını gösterir. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak proje dosyasının etkisi dışında bulunduğunda görüntülenecek gösterim yolu. |
| Görünür | İsteğe bağlı boolean. Dosyanın Visual Studio'da **Solution Explorer'da** görüntülenip görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıktı dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. Asla<br />2. Her zaman<br />3. Koruma Yeni |

### <a name="embeddedresource"></a>EmbeddedResource

 Oluşturulan derlemeye katışacak kaynakları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Bağımlı | İsteğe bağlı dize. Bu dosyanın doğru derlemek için bağlı olduğu dosyayı belirtir |
| Oluşturucu | Gerekli dize. Bu öğeüzerinde çalıştırılabilen herhangi bir dosya üretecisinin adı. |
| LastGenOutput | Gerekli dize. Bu öğeüzerinde çalıştırılabilen herhangi bir dosya oluşturucusu tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğeüzerinde çalışan herhangi bir dosya oluşturucukodu oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında bulunuyorsa, gösterim yolu görüntülenir. |
| Görünür | İsteğe bağlı boolean. Dosyanın Visual Studio'da **Solution Explorer'da** görüntülenip görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıktı dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. Asla<br />2. Her zaman<br />3. Koruma Yeni |
| Mantıksal Ad | Gerekli dize. Katıştırılmış kaynağın mantıksal adı. |

### <a name="content"></a>İçerik

 Projeye derlenmemiş, ancak katıştırılmış veya birlikte yayımlanabilen dosyaları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Bağımlı | İsteğe bağlı dize. Bu dosyanın doğru derlemek için bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğeüzerinde çalışan herhangi bir dosya üreteciadı. |
| LastGenOutput | Gerekli dize. Bu öğeüzerinde çalıştırılabilen herhangi bir dosya oluşturucusu tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğeüzerinde çalışan herhangi bir dosya oluşturucukodu oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında bulunuyorsa görüntülenecek gösterim yolu. |
| Yayın Durumu | Gerekli dize. İçeriğin yayımlama durumu aşağıdakileri de içerir:<br /><br /> - Varsayılan<br />- Dahil<br />- Hariç<br />- Veri Dosyası<br />- Ön koşul |
| ısassembly | İsteğe bağlı boolean. Dosyanın derleme olup olmadığını belirtir. |
| Görünür | İsteğe bağlı boolean. Dosyanın Visual Studio'da **Solution Explorer'da** görüntülenip görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıktı dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. Asla<br />2. Her zaman<br />3. Koruma Yeni |

### <a name="none"></a>None

 Yapı işleminde rolü olmaması gereken dosyaları temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Bağımlı | İsteğe bağlı dize. Bu dosyanın doğru derlemek için bağlı olduğu dosyayı belirtir. |
| Oluşturucu | Gerekli dize. Bu öğeüzerinde çalıştırılabilen herhangi bir dosya üretecisinin adı. |
| LastGenOutput | Gerekli dize. Bu öğeüzerinde çalıştırılabilen herhangi bir dosya oluşturucusu tarafından oluşturulan dosyanın adı. |
| CustomToolNamespace | Gerekli dize. Bu öğeüzerinde çalışan herhangi bir dosya oluşturucukodu oluşturması gereken ad alanı. |
| Bağlantı | İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında bulunuyorsa görüntülenecek gösterim yolu. |
| Görünür | İsteğe bağlı boolean. Dosyanın Visual Studio'da **Solution Explorer'da** görüntülenip görüntülenip görüntülenmeyeceğini gösterir. |
| CopyToOutputDirectory | İsteğe bağlı dize. Dosyanın çıktı dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. Asla<br />2. Her zaman<br />3. Koruma Yeni |

### <a name="assemblymetadata"></a>Assemblymetadata

 ', '' olarak `[AssemblyMetadata(key, value)]`oluşturulacak derleme özniteliklerini temsil eder.

| Öğe meta veri adı | Açıklama |
|-----------------------| - |
| Şunları Dahil Et: | Öznitelik oluşturucudaki `AssemblyMetadataAttribute` ilk parametre (anahtar) olur. |
| Değer | Gerekli dize. Öznitelik oluşturucudaki `AssemblyMetadataAttribute` ikinci parametre (değer) olur. |

> [!NOTE]
> Bu, yalnızca .NET Core SDK kullanan projeler için geçerlidir.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

 Yapının temel uygulama bildirimini temsil eder ve ClickOnce dağıtım güvenlik bilgilerini içerir.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

 İthalat için FxCop projesini temsil eder.

### <a name="import"></a>İçeri Aktarma

 Ad alanları Visual Basic derleyicisi tarafından içe aktarılması gereken derlemeleri temsil eder.

## <a name="see-also"></a>Ayrıca bkz.

- [Ortak MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
