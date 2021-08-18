---
title: Sınıf Tasarımcısı'de sınıfları ve türleri yeniden adlandırma ve taşıma
description: Sınıf Tasarımcısı ve Sınıf Ayrıntıları penceresini kullanarak sınıfları ve türleri yeniden adlandırmayı ve taşımayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d217f85d57e4e44e824f708343764a89f3ba2efe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101953"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Sınıf Tasarımcısı'da sınıfları ve türleri yeniden Sınıf Tasarımcısı

Kodu yeniden düzenlemeyi, iç yapısını ve nesnelerinin dış davranışını değil, nasıl tasarlanmalarını değiştirerek daha kolay anlaşılır, bakımlı ve daha verimli hale getirirsiniz. Sınıf Tasarımcısı projenize C#, Visual Basic veya C++ kodunu yeniden düzenlemeniz gereken işi ve hataları ortaya Visual Basic için Sınıf Ayrıntıları penceresini Visual Studio kullanın.

> [!NOTE]
> Proje kaynak kodu denetimi altında olduğundan ve kullanıma alınmış olduğundan, başvurulan bir proje olduğundan veya dosyaları diskte salt okunur olarak işaretlendiğinden projenin dosyaları salt okunur olabilir. Bu durumlardan birinin projesinde çalışıyorken, projenin durumuna bağlı olarak çalışmanızı kaydetmenin çeşitli yolları size sunulacaktır. Bu, kodu yeniden düzenleme ve doğrudan düzenleme gibi başka bir şekilde değiştirerek kod için geçerlidir.

## <a name="common-tasks"></a>Genel görevler

|Görev|Destekleyici İçerik|
|----------| - |
|**Sınıfları yeniden düzenleme:** Bir sınıfı kısmi sınıflara bölmek veya soyut bir temel sınıf uygulamak için yeniden düzenleme işlemlerini kullanabilirsiniz.|-   [Nasıl: Sınıfı Kısmi Sınıflara Bölme](how-to-split-a-class-into-partial-classes.md)|
|**Arabirimlerle çalışma:** Bu Sınıf Tasarımcısı, arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim gerçekleştirebilirsiniz.|-   [Nasıl kullanılır: Arabirim Uygulama](how-to-implement-an-interface.md)|
|**Türleri, tür üyelerini ve parametreleri yeniden düzenleme:** Bu Sınıf Tasarımcısı kullanarak türleri yeniden adlandırarak, tür üyelerini geçersiz kılamaz veya bir türden diğerine taşımayı tercih edersiniz. Boş değere değiştirilebilir türler de oluşturabilirsiniz.|-   [Türleri ve tür üyelerini yeniden adlandırma](#rename-types-and-type-members)<br />-   [Tür üyelerini bir türden diğerine taşıma](#move-type-members-from-one-type-to-another)<br />-   [Nasıl olur: Boş Değer Değere Sahip Tür Oluşturma](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Türleri ve tür üyelerini yeniden adlandırma

Bu Sınıf Tasarımcısı sınıf diyagramında veya Özellikler penceresinde bir türü veya türün üyesini yeniden **adlandırabilirsiniz.** Sınıf **Ayrıntıları penceresinde** bir üyenin adını değiştirebilirsiniz ancak türü değiştiremezsiniz. Bir tür veya tür üyesini yeniden adlandırarak, eski adın bulunduğu tüm pencerelere ve kod konumlara yayma.

### <a name="rename-in-the-class-designer"></a>Dosyada yeniden Sınıf Tasarımcısı

1. Sınıf diyagramında türü veya üyeyi seçin ve adı seçin.

     Üyenin adı düzenlenebilir hale gelir.

2. Tür veya tür üyesi için yeni adı yazın

### <a name="rename-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde yeniden adlandırma

1. Sınıf Ayrıntıları **penceresini görüntülemek için** tür veya tür üyesine sağ tıklayın ve Sınıf Ayrıntıları'ı **seçin.**

     Sınıf **Ayrıntıları penceresi** görüntülenir.

2. Ad **sütununda** tür üyesinin adını değiştirme

3. Odağı hücreden taşımak için Enter tuşuna **basın** veya hücreden uzağa tıklayın.

    > [!NOTE]
    > Sınıf **Ayrıntıları penceresinde** bir üyenin adını değiştirebilirsiniz ancak türü değiştiremezsiniz.

### <a name="rename-in-the-properties-window"></a>Dosyada yeniden Özellikler penceresi

1. Sınıf diyagramında veya Sınıf **Ayrıntıları penceresinde** türe veya üyeye sağ tıklayın ve ardından Özellikler'i **seçin.**

     Özellikler **penceresi** görünür ve tür veya tür üyesinin özelliklerini görüntüler.

2. Name **özelliğinde** tür veya tür üyesinin adını değiştirebilirsiniz.

     Yeni ad, geçerli projede eski adın bulunduğu tüm pencerelere ve kod konumlara yayma.

## <a name="move-type-members-from-one-type-to-another"></a>Tür üyelerini bir türden diğerine taşıma

bir **Sınıf Tasarımcısı** kullanarak bir tür üyesini bir türden başka bir türe taşıma. Her iki tür de geçerli sınıf diyagramında görünür olmalıdır.

1. Tasarım yüzeyinde görünen bir türde, başka bir türe taşımak istediğiniz üyeye sağ tıklayın ve ardından Kes'i **seçin.**

2. Hedef türüne sağ tıklayın ve Yapıştır'ı **seçin.**

     özelliği kaynak türünden kaldırılır ve hedef türünde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıfları ve Türleri Tasarlama](designing-and-viewing-classes-and-types.md)
