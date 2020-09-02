---
title: Ortak MSBuild proje öğeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8e36d5e50b15a5ede425715ec756f05ab8d014de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160408"
---
# <a name="common-msbuild-project-items"></a>Yaygın MSBuild Proje Öğeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]' De, bir öğe bir veya daha fazla dosyaya adlandırılmış bir başvurudur. Öğeler, dosya adları, yollar ve sürüm numaraları gibi meta verileri içerir. İçindeki tüm proje türlerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ortak olarak birkaç öğe vardır. Bu öğeler Microsoft. Build. CommonTypes. xsd dosyasında tanımlanmıştır.  
  
## <a name="common-items"></a>Ortak öğeler  
 Tüm ortak proje öğelerinin listesi aşağıda verilmiştir.  
  
### <a name="reference"></a>Başvuru  
 Projedeki derleme (yönetilen) başvurusunu temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|HintPath|İsteğe bağlı dize. Derlemenin göreli veya mutlak yolu.|  
|Name|İsteğe bağlı dize. Derlemenin görünen adı, örneğin, "System. Windows. Forms."|  
|FusionName|İsteğe bağlı dize. Öğe için basit veya güçlü Fusion adı belirtir.<br /><br /> Bu öznitelik mevcut olduğunda, derleme dosyası Fusion adını almak için açılmadığından zaman tasarrufu yapabilirsiniz.|  
|Bahsedilen SpecificVersion|İsteğe bağlı Boolean. Yalnızca Fusion adındaki sürümün başvurulması gerekip gerekmediğini belirtir.|  
|Diğer adlar|İsteğe bağlı dize. Başvuru için herhangi bir diğer ad.|  
|Özel|İsteğe bağlı Boolean. Başvurunun çıkış klasörüne kopyalanıp kopyalanmayacağını belirtir. Bu öznitelik, Visual Studio IDE içinde olan başvurunun yereli **Kopyala** özelliğiyle eşleşir.|  
  
### <a name="comreference"></a>COMReference  
 Projedeki COM (yönetilmeyen) bileşen başvurusunu temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|Ad|İsteğe bağlı dize. Bileşenin görünen adı.|  
|Guid|İsteğe bağlı dize. Formundaki bileşeni için bir GUID {12345678-1234-1234-1234-1234567891234} .|  
|VersionAna|İsteğe bağlı dize. Bileşenin sürüm numarasının ana bölümü. Örneğin, tam sürüm numarası "5,46" ise "5".|  
|VersionMinor|İsteğe bağlı dize. Bileşenin sürüm numarasının küçük bölümü. Örneğin, tam sürüm numarası "5,46" ise, "46".|  
|LCID|İsteğe bağlı dize. Bileşenin LocaleID 'Si.|  
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı, örneğin, "Tlbimp."|  
|Yalıtılmış|İsteğe bağlı Boolean. Bileşenin bir reg-Free bileşeni olup olmadığını belirtir.|  
  
### <a name="comfilereference"></a>COMFileReference  
 ResolvedComreference hedefine akışa eklenen kitaplıkların tür bir listesini temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|WrapperTool|İsteğe bağlı dize. Bileşende kullanılan sarmalayıcı aracının adı, örneğin, "Tlbimp."|  
  
### <a name="nativereference"></a>NativeReference  
 Yerel bir bildirim dosyasını veya bu tür bir dosyaya yapılan başvuruyu temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|Ad|Gerekli dize. Bildirim dosyasının temel adı.|  
|HintPath|Gerekli dize. Bildirim dosyasının göreli yolu.|  
  
### <a name="projectreference"></a>ProjectReference  
 Başka bir projenin başvurusunu temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|Ad|İsteğe bağlı dize. Başvurunun görünen adı.|  
|Project|İsteğe bağlı dize. Formundaki, başvuru için bir GUID {12345678-1234-1234-1234-1234567891234} .|  
|Paket|İsteğe bağlı dize. Başvurulduğu proje dosyasının yolu.|  
  
### <a name="compile"></a>Se  
 Derleyicinin kaynak dosyalarını temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir.|  
|Oto gen|İsteğe bağlı Boolean. Dosyanın proje için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tümleşik geliştirme ortamı (IDE) tarafından oluşturulup oluşturulmayacağını gösterir.|  
|Bağlantı|İsteğe bağlı dize. Dosya fiziksel olarak proje dosyasının etki dışında konumlandırıldığında görüntülenecek olan notational yolu.|  
|Görünür|İsteğe bağlı Boolean. Dosyasında **Çözüm Gezgini** içinde görüntülenip görüntülenmeyeceğini gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı|  
  
### <a name="embeddedresource"></a>EmbeddedResource  
 Oluşturulan derlemeye gömülebilen kaynakları temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir|  
|Oluşturucu|Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya oluşturucusunun adı.|  
|LastGenOutput|Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı.|  
|CustomToolNamespace|Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı.|  
|Bağlantı|İsteğe bağlı dize. Dosya fiziksel olarak projenin etki alanının dışında konumlandırıldığında, notational yolu görüntülenir.|  
|Görünür|İsteğe bağlı Boolean. Dosyasında **Çözüm Gezgini** içinde görüntülenip görüntülenmeyeceğini gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı|  
|LogicalName|Gerekli dize. Gömülü kaynağın mantıksal adı.|  
  
### <a name="content"></a>Content  
 Projeye derlenmemiş ancak birlikte gömülebilir veya onunla birlikte yayımlanabilir olan dosyaları temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir.|  
|Oluşturucu|Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun adı.|  
|LastGenOutput|Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya Oluşturucu tarafından oluşturulan dosyanın adı.|  
|CustomToolNamespace|Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı.|  
|Bağlantı|İsteğe bağlı Boolean. Dosyasında **Çözüm Gezgini** içinde görüntülenip görüntülenmeyeceğini gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|PublishState|Gerekli dize. İçeriğin Yayımlanma Durumu, aşağıdakilerden biri:<br /><br /> -Varsayılan<br />-Dahil edilen<br />-Dışlanan<br />-Veri dosyası<br />-Önkoşul|  
|IsAssembly|İsteğe bağlı Boolean. Dosyanın bir derleme olup olmadığını belirtir.|  
|Görünür|İsteğe bağlı Boolean. Dosyasında **Çözüm Gezgini** içinde görüntülenip görüntülenmeyeceğini gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı|  
  
### <a name="none"></a>Hiçbiri  
 Yapı işleminde rolü olmaması gereken dosyaları temsil eder.  
  
|Öğe Adı|Açıklama|  
|---------------|-----------------|  
|DependentUpon|İsteğe bağlı dize. Doğru derlemek için bu dosyanın bağlı olduğu dosyayı belirtir.|  
|Oluşturucu|Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya oluşturucusunun adı.|  
|LastGenOutput|Gerekli dize. Bu öğede çalıştırılan herhangi bir dosya üreticisi tarafından oluşturulan dosyanın adı.|  
|CustomToolNamespace|Gerekli dize. Bu öğe üzerinde çalışan herhangi bir dosya oluşturucusunun kod oluşturması gereken ad alanı.|  
|Bağlantı|İsteğe bağlı dize. Dosya fiziksel olarak projenin etkisi dışında konumlandırıldığında görüntülenecek olan notational yolu.|  
|Görünür|İsteğe bağlı Boolean. Dosyasında **Çözüm Gezgini** içinde görüntülenip görüntülenmeyeceğini gösterir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|CopyToOutputDirectory|İsteğe bağlı dize. Dosyanın çıkış dizinine kopyalanıp kopyalanmayacağını belirler. Değerler şunlardır:<br /><br /> 1. hiçbir şekilde<br />2. her zaman<br />3. Preservenebatı|  
  
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest  
 Yapı için temel uygulama bildirimini temsil eder ve [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] dağıtım güvenliği bilgilerini içerir.  
  
### <a name="codeanalysisimport"></a>Codeanalysisımport  
 İçeri aktarılacak FxCop projesini temsil eder.  
  
### <a name="import"></a>İçeri Aktar  
 Ad alanları derleyici tarafından içeri aktarılmalıdır derlemeleri temsil eder [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ortak MSBuild proje özellikleri](../msbuild/common-msbuild-project-properties.md)
