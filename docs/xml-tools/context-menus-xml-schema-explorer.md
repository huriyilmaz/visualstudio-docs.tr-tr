---
title: XML Şema Gezgini'nde Bağlam Menüleri
description: Şemaya özgü aramalar ve diğer işlemler gerçekleştirmeye yönelik öğeler içeren XML Şema Gezgini'nde Bağlam Menüleri hakkında bilgi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 4c630d4acf88bd1a3eb776e3ca63cf65fb833449
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633646"
---
# <a name="context-menus-xml-schema-explorer"></a>Bağlam menüleri (XML Şema Gezgini)

Bağlam menüsü, bir şeye sağ tıklarken görüntülenen menü olur. Şemaya özgü aramalar ve diğer işlemleri gerçekleştirmek için aşağıdaki bağlam menüsü öğeleri kullanılır.

## <a name="node-type-schema-set"></a>Düğüm türü: Şema kümesi

Aşağıdaki tabloda şema kümesi düğümü için kullanılabilen seçenekler açık almaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**Büyük Olasılıkla Kök Öğeleri Göster**|Kendileri dışında genel öğelerden başvurulmay tüm genel öğeleri bulur ve vurgular.|
|**Genel Türleri Göster**|Şema kümesinde tüm genel türleri bulur ve vurgular.|
|**Genel Öğeleri Göster**|Şema kümesinde tüm genel öğeleri bulur ve vurgular.|
|**Özellikler Penceresi**|Özellikler **penceresini** açar (henüz açık değilse). Bu pencerede düğümle ilgili bilgiler görüntülenir.|

## <a name="node-type-namespace"></a>Düğüm türü: Ad alanı
Aşağıdaki tabloda, bir ad alanı düğümü için kullanılabilen seçenekler açık almaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm Gelen Başvuruları Göster**|Seçilen ad alanını içeri aktaran dosyaları bulur ve vurgular.|
|**Tüm Giden Başvuruları Göster**|Seçilen ad alanı içinde yer alan her dosya için aşağıdakini bulur ve vurgular:<br /><br /> - Öznitelik olmadan içeri aktarma deyimleri içinde başvurulan tüm ad `schemaLocation` alanları.<br />- import ve include deyimleri özniteliğinde belirtilen seçili dosya dışında `schemaLocation` ad alanlarındaki tüm dosyalar.|
|**Genel Türleri Göster**|Seçilen ad alanı içinde tüm genel türleri bulur ve vurgular.|
|**Genel Öğeleri Göster**|Seçilen ad alanı içinde tüm genel öğeleri bulur ve vurgular.|
|**Özellikler Penceresi**|Özellikler **penceresini** açar (henüz açık değilse). Bu pencerede düğümle ilgili bilgiler görüntülenir.|

## <a name="node-type-file"></a>Düğüm türü: Dosya
Aşağıdaki tabloda, bir dosya düğümü için kullanılabilen seçenekler açık almaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**Tüm Gelen Başvuruları Göster**|Include ve import deyimlerinin özniteliklerinde seçili dosyayı `schemaLocation` belirten tüm dosyaları bulur ve vurgular.|
|**Tüm Giden Başvuruları Göster**|Aşağıdakini bulur ve vurgular:<br /><br /> - Özniteliği olmayan tüm içeri aktarma deyimlerinin ad alanı özniteliklerinde belirtilen tüm ad `schemaLocation` alanları.<br />- Tüm içeri aktarma ve `schemaLocation` dahil deyimlerinin özniteliklerinde belirtilen tüm dosyalar.|
|**Genel Türleri Göster**|Bu dosyada tüm genel türleri bulur ve vurgular.|
|**Genel Öğeleri Göster**|Bu dosyada tüm genel öğeleri bulur ve vurgular.|
|**Kodu Görüntüle**|Seçilen düğümü içeren dosyayı XML düzenleyicisinde açar. XML Şema Gezgini'nde seçilen öğe de XML düzenleyicisinde seçilir.|
|**Özellikler Penceresi**|Özellikler **penceresini** açar (henüz açık değilse). Bu pencerede düğümle ilgili bilgiler görüntülenir.|

## <a name="all-global-node-types"></a>Tüm genel düğüm türleri
Aşağıdaki tabloda tüm genel düğümler için kullanılabilen seçenekler açık almaktadır.

|Seçenek|Açıklama|
|-|-----------------|
|**Görünümde Graph Göster**|Graph açar. Seçilen düğüm çalışma alanında yoksa çalışma alanına ekler ve düğümü seçer.|
|**İçerik Modeli Görünümünde Göster**|İçerik Modeli Görünümünü açar. Seçilen düğüm çalışma alanında yoksa çalışma alanına ekler ve düğümü seçer.|
|**Kodu Görüntüle**|Seçilen düğümü içeren dosyayı XML düzenleyicisinde açar. XML Şema Gezgini'nde seçilen öğe de XML düzenleyicisinde seçilir.|
|**Özellikler Penceresi**|Özellikler **penceresini** açar (henüz açık değilse). Bu pencerede düğümle ilgili bilgiler görüntülenir.|

## <a name="node-type-element"></a>Düğüm türü: Öğe
Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, öğe düğümlerinin bağlam menüsünde aşağıdaki seçenekler vardır:

|Seçenek|Açıklama|
|-|-----------------|
|**Tür tanımına git**|Seçilen öğenin tür tanımına gidin. Öğe için kullanılan tür genel bir tür olduğunda bu geçerlidir.|
|**Özgün öğeye gidin**|Öğe başvuruları için, öğesinin gerçek tanımına gidin.|
|**Tüm Başvuruları Göster**|Genel öğeler için, seçili öğeye yapılan tüm başvuruları (sahip olan öğeler) bulur `ref="selectedElement"` ve vurgular.|
|**Değiştirme Grubunun Üyelerini Gösterme**|Bir değiştirme grubunun turaları için, seçili öğenin üye olduğu değiştirme grubunun üyesi olan tüm öğeleri bulur ve vurgular. Bu, doğrudan ve dolaylı katılımcıları gösterir.|
|**Değiştirme Grubu TuraLarını Göster**|Bir değiştirme grubunun üyesi olan genel öğeler için, aşağıdaki gibi seçili öğe için tüm doğrudan ve dolaylı turaları bulur ve vurgular:<br /><br /> - Seçilen öğede belirtilen bir değiştirme grubu başı.<br />- Baş öğesinde belirtilen bir değiştirme grubu başı.|
|**Örnek XML Oluşturma**|Yalnızca genel öğeler için kullanılabilir. Genel öğe için örnek bir XML dosyası üretir.|

## <a name="node-type-global-types"></a>Düğüm türü: Genel türler
Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, genel tür düğümlerinin bağlam menüsünde aşağıdaki seçenekler vardır:

|Seçenek|Açıklama|
|-|-----------------|
|**Temel Türü Göster**|Seçilen tür genel bir türden türetildiyse, seçilen türün temel türüne gidin.|
|**Tüm Başvuruları Göster**|Seçilen türe yapılan tüm başvuruları bulur ve vurgular. Bu, seçilen tür ve seçilen türden türetilen türlerin öğelerini ve özniteliklerini içerir.|
|**Tüm türetilmiş türleri göster**|Seçilen türden doğrudan ve dolaylı olarak türetilen tüm türleri bulur ve vurgular.|
|**Tüm üst öğeleri göster**|Tüm üst (taban) türlerini göster.|

## <a name="node-type-attribute"></a>Düğüm türü: öznitelik
Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, öznitelik düğümleri için bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tür tanımına git**|Özniteliği için kullanılan tür genel bir tür olduğunda, Seçili özniteliğin tür tanımına gider.|
|**Özgün özniteliğe git**|Öznitelik başvuruları için, özniteliğin gerçek tanımına gider.|
|**Tüm başvuruları göster**|Genel öznitelikler için, seçilen özniteliğe ilişkin tüm başvuruları bulur ve vurgular (diğer öznitelikler `ref="selectedAttribute"` ).|

## <a name="node-type-attribute-group"></a>Düğüm türü: öznitelik grubu
Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, öznitelik grubu düğümleri için bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tanıma Git**|Başvurular için, özniteliğin gerçek tanımına gider.|
|**Tüm üyeleri göster**|Öznitelik grubunun tüm üyelerini bulur ve vurgular.|
|**Tüm başvuruları göster**|Seçilen öznitelik grubuna yönelik tüm başvuruları bulur ve vurgular (öznitelik grupları `ref="selectedAttributeGroup"` ).|

## <a name="node-type-named-group"></a>Düğüm türü: adlandırılmış Grup
Yukarıda açıklanan genel düğüm seçeneklerine ek olarak, adlandırılmış Grup düğümleri için bağlam menüsü aşağıdaki seçeneklere sahiptir:

|Seçenek|Açıklama|
|-|-----------------|
|**Tanıma Git**|Başvurular için, özniteliğin gerçek tanımına gider.|
|**Tüm üyeleri göster**|Adlandırılmış grubun tüm üyelerini bulur ve vurgular.|
|**Tüm başvuruları göster**|Seçili grup için tüm başvuruları (sahip olan gruplar) bulur ve vurgular `ref="selectedGroup"` .|

## <a name="see-also"></a>Ayrıca bkz.

- [XML Şema Gezgini](../xml-tools/xml-schema-explorer.md)
- [Şema kümesi aranıyor](../xml-tools/searching-the-schema-set.md)
