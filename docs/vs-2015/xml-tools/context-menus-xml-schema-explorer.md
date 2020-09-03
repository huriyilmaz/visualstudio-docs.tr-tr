---
title: Bağlam menüleri (XML şema Gezgini) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5065ecb1dc0905d1aa593ee4aa62dddd2f62c3a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609632"
---
# <a name="context-menus-xml-schema-explorer"></a>Bağlam Menüleri (XML Şeması Gezgini)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Şemaya özgü aramalar ve diğer işlemleri gerçekleştirmek için aşağıdaki bağlam menüsü öğeleri kullanılır.

## <a name="node-type-schema-set"></a>Düğüm türü: şema kümesi
 Aşağıdaki tabloda, bir şema kümesi düğümü için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|------------|-----------------|
|**En olası kök öğeleri göster**|Kendi dışındaki genel öğelerden başvurulmayan tüm genel öğeleri bulur ve vurgular.|
|**Genel türleri göster**|Şema kümesindeki tüm genel türleri bulur ve vurgular.|
|**Genel öğeleri göster**|Şema kümesindeki tüm genel öğeleri bulur ve vurgular.|
|**Özellikler penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

## <a name="node-type-namespace"></a>Düğüm türü: ad alanı
 Aşağıdaki tabloda, bir ad alanı düğümü için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|------------|-----------------|
|**Tüm gelen başvuruları göster**|Seçilen ad alanını içeri aktarma dosyalarını bulur ve vurgular.|
|**Tüm giden başvuruları göster**|Seçili ad alanındaki her dosya için aşağıdakileri bulur ve vurgular:<br /><br /> -İçeri aktarma deyimlerine bir özniteliği olmadan başvuruda bulunulan tüm ad alanları `schemaLocation` .<br />- `schemaLocation` İçeri aktarma ve ekleme deyimlerine ait özniteliğinde belirtilen bir ad alanındaki tüm dosyalar.|
|**Genel türleri göster**|Seçilen ad alanındaki tüm genel türleri bulur ve vurgular.|
|**Genel öğeleri göster**|Seçilen ad alanındaki tüm genel öğeleri bulur ve vurgular.|
|**Özellikler penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

## <a name="node-type-file"></a>Düğüm türü: dosya
 Aşağıdaki tabloda bir dosya düğümü için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|------------|-----------------|
|**Tüm gelen başvuruları göster**|`schemaLocation`Dahil edilen ve içeri aktarma deyimlerinin özniteliklerinde seçili dosyayı belirten tüm dosyaları bulur ve vurgular.|
|**Tüm giden başvuruları göster**|Aşağıdakileri bulur ve vurgular:<br /><br /> -Özniteliği olmayan tüm Import deyimlerinin ad alanı özniteliklerinde belirtilen tüm ad alanları `schemaLocation` .<br />- `schemaLocation` Tüm Import ve Include deyimlerinin özniteliklerinde belirtilen tüm dosyalar.|
|**Genel türleri göster**|Bu dosyadaki tüm genel türleri bulur ve vurgular.|
|**Genel öğeleri göster**|Bu dosyadaki tüm genel öğeleri bulur ve vurgular.|
|**Kodu Görüntüle**|XML düzenleyicisinde Seçili düğümü içeren dosyayı açar. XML şeması Gezgininde seçilen öğe, XML düzenleyicisinde de seçilir.|
|**Özellikler penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

## <a name="all-global-node-types"></a>Tüm genel düğüm türleri
 Aşağıdaki tabloda tüm genel düğümler için kullanılabilen seçenekler açıklanmaktadır.

|Seçenek|Açıklama|
|------------|-----------------|
|**Grafik görünümünde göster**|Grafik görünümünü açar. Seçili düğüm çalışma alanında değilse, çalışma alanına ekler ve düğümü seçer.|
|**Içerik modeli görünümünde göster**|Içerik modeli görünümünü açar. Seçili düğüm çalışma alanında değilse, çalışma alanına ekler ve düğümü seçer.|
|**Kodu Görüntüle**|XML düzenleyicisinde Seçili düğümü içeren dosyayı açar. XML şeması Gezgininde seçilen öğe, XML düzenleyicisinde de seçilir.|
|**Özellikler penceresi**|**Özellikler** penceresini açar (zaten açık değilse). Bu pencere, düğüm hakkındaki bilgileri görüntüler.|

## <a name="node-type-element"></a>Düğüm türü: öğe
 Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, öğe düğümleri için bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|------------|-----------------|
|**Tür tanımına git**|Seçili öğenin tür tanımına gider. Bu, öğesi için kullanılan tür genel bir tür olduğunda geçerlidir.|
|**Özgün öğeye git**|Öğe başvuruları için, öğenin gerçek tanımına gider.|
|**Tüm başvuruları göster**|Genel öğeler için, seçili öğe için tüm başvuruları bulur ve vurgular (olan öğeler `ref="selectedElement"` ).|
|**Değiştirme grubunun üyelerini göster**|Değiştirme grubunun kafaları için, seçili öğenin üyesi olduğu değiştirme grubunun üyesi olan tüm öğeleri bulur ve vurgular. Bu, doğrudan ve dolaylı katılımcıları gösterir.|
|**Değiştirme grubu kafalarını göster**|Bir değiştirme grubunun üyesi olan genel öğeler için, aşağıdaki gibi, seçili öğe için tüm doğrudan ve dolaylı kafaları bulur ve vurgular:<br /><br /> -Seçili öğede bir değiştirme grubu kafası belirtildi.<br />-Baş öğesinde bir değiştirme grubu kafası belirtildi.|
|**Örnek XML oluştur**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası oluşturur.|

## <a name="node-type-global-types"></a>Düğüm türü: genel türler
 Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, genel tür düğümlerinin bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|------------|-----------------|
|**Taban türünü göster**|Seçilen tür genel bir türden türetildiyse, seçilen türün temel türüne gider.|
|**Tüm başvuruları göster**|Seçilen türe yapılan tüm başvuruları bulur ve vurgular. Bu, seçilen tür ve seçilen türden türetilen türlerin öğelerini ve özniteliklerini içerir.|
|**Tüm türetilmiş türleri göster**|Seçilen türden doğrudan ve dolaylı olarak türetilen tüm türleri bulur ve vurgular.|
|**Tüm üst öğeleri göster**|Tüm üst (taban) türlerini göster.|

## <a name="node-type-attribute"></a>Düğüm türü: öznitelik
 Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, öznitelik düğümleri için bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|------------|-----------------|
|**Tür tanımına git**|Özniteliği için kullanılan tür genel bir tür olduğunda, Seçili özniteliğin tür tanımına gider.|
|**Özgün özniteliğe git**|Öznitelik başvuruları için, özniteliğin gerçek tanımına gider.|
|**Tüm başvuruları göster**|Genel öznitelikler için, seçilen özniteliğe ilişkin tüm başvuruları bulur ve vurgular (diğer öznitelikler `ref="selectedAttribute"` ).|

## <a name="node-type-attribute-group"></a>Düğüm türü: öznitelik grubu
 Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, öznitelik grubu düğümleri için bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|------------|-----------------|
|**Tanıma Git**|Başvurular için, özniteliğin gerçek tanımına gider.|
|**Tüm üyeleri göster**|Öznitelik grubunun tüm üyelerini bulur ve vurgular.|
|**Tüm başvuruları göster**|Seçilen öznitelik grubuna yönelik tüm başvuruları bulur ve vurgular (öznitelik grupları `ref="selectedAttributeGroup"` ).|

## <a name="node-type-named-group"></a>Düğüm türü: adlandırılmış Grup
 Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, adlandırılmış Grup düğümleri için bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|------------|-----------------|
|**Tanıma Git**|Başvurular için, özniteliğin gerçek tanımına gider.|
|**Tüm üyeleri göster**|Adlandırılmış grubun tüm üyelerini bulur ve vurgular.|
|**Tüm başvuruları göster**|Seçili grup için tüm başvuruları (sahip olan gruplar) bulur ve vurgular `ref="selectedGroup"` .|

## <a name="see-also"></a>Ayrıca Bkz.
 [Şema kümesini arayan](../xml-tools/searching-the-schema-set.md) [XML şema Gezgini](../xml-tools/xml-schema-explorer.md)
