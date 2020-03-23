---
title: Sınıf Tasarımcısı'ndaki sınıfları ve türleri yeniden adlandırın ve taşıyın
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e060f044af666f5a4357e527819286d3bd87267
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590754"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Sınıf Tasarımcısı'nda refactor sınıfları ve türleri

Kodu yeniden düzenlediğinizzaman, iç yapısını ve nesnelerinin dış davranışıdeğil, nasıl tasarlandığını değiştirerek daha kolay anlaşılmasını, bakımını ve daha verimli olmasını sağlarsınız. Visual Studio projenizde C#, Visual Basic veya C++ kodunu yeniden eklediğinizde yapmanız gereken işi ve hataları tanıtma olasılığını azaltmak için Sınıf Tasarımcısı ve Sınıf Ayrıntıları penceresini kullanın.

> [!NOTE]
> Proje kaynak kodu denetimi altında olduğundan ve kullanıma alınmadığından, başvurulan bir proje olduğundan veya dosyaları diskte salt okunur olarak işaretlendirilmediği için, projenin dosyaları yalnızca okunabilir. Bu durumlardan birinde bir projede çalıştığınızda, proje durumuna bağlı olarak çalışmanızı kaydetmek için çeşitli yollar sunulur. Bu, kodu yeniden düzenleme ve doğrudan düzenleme gibi başka bir şekilde değiştirdiğiniz kod için de geçerlidir.

## <a name="common-tasks"></a>Genel görevler

|Görev|Destekleyici İçerik|
|----------| - |
|**Yeniden düzenleme sınıfları:** Bir sınıfı kısmi sınıflara bölmek veya soyut bir taban sınıf uygulamak için yeniden düzenleme işlemlerini kullanabilirsiniz.|-   [Nasıl Yapilir: Bir Sınıfı Kısmi Sınıflara Bölme](how-to-split-a-class-into-partial-classes.md)|
|**Arayüzlerle çalışma:** Sınıf Tasarımcısı'nda, arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim uygulayabilirsiniz.|-   [Nasıl Yapılsın: Arayüz Uygulama](how-to-implement-an-interface.md)|
|**Yeniden düzenleme türleri, tür üyeleri ve parametreler:** Sınıf Tasarımcısı'nı kullanarak türleri yeniden adlandırabilir, tür üyelerini geçersiz kılabilir veya bunları bir türden diğerine taşıyabilirsiniz. Ayrıca geçersiz türleri oluşturabilirsiniz.|-   [Türleri ve tür üyelerini yeniden adlandırma](#rename-types-and-type-members)<br />-   [Tür üyelerini bir türden diğerine taşıma](#move-type-members-from-one-type-to-another)<br />-   [Nasıl yapılsın: Nullable Türü Oluşturma](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Türleri ve tür üyelerini yeniden adlandırma

Sınıf Tasarımcısı'nda, sınıf diyagramında veya **Özellikler** penceresinde bir türü veya bir türün üyesini yeniden adlandırabilirsiniz. Sınıf **Ayrıntıları** penceresinde, bir üyenin adını değiştirebilirsiniz, ancak bir tür değiştiremezsiniz. Bir tür veya tür üyesinin yeniden adlandırılması, eski adın göründüğü tüm pencerelere ve kod konumlarına yayılır.

### <a name="rename-in-the-class-designer"></a>Sınıf Tasarımcısı'nda Yeniden Adlandırma

1. Sınıf diyagramında, türü veya üyeyi seçin ve adı seçin.

     Üyenin adı değiştirilebilir hale gelir.

2. Tür veya tür üyesi için yeni adı yazın

### <a name="rename-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde yeniden adlandırma

1. **Sınıf Ayrıntıları** penceresini görüntülemek için, tür veya tür üyesisağ tıklayın ve **Sınıf Ayrıntıları**seçin.

     **Sınıf Ayrıntıları** penceresi görüntülenir.

2. **Ad** sütununda, tür üyesinin adını değiştirin

3. Odağı hücreden uzaklaştırmak için **Enter** tuşuna basın veya hücreden uzaklaşın.

    > [!NOTE]
    > Sınıf **Ayrıntıları** penceresinde, bir üyenin adını değiştirebilirsiniz, ancak bir tür değiştiremezsiniz.

### <a name="rename-in-the-properties-window"></a>Özellikler penceresinde yeniden adlandırma

1. Sınıf diyagramında veya **Sınıf Ayrıntıları** penceresinde, türü veya üyeyi sağ tıklatın ve ardından **Özellikler'i**seçin.

     **Özellikler** penceresi görüntülenir ve tür veya tür üyesi için özellikleri görüntüler.

2. **Ad** özelliğinde, tür veya tür üyesinin adını değiştirin.

     Yeni ad, eski adın göründüğü geçerli projedeki tüm pencerelere ve kod konumlarına yayılır.

## <a name="move-type-members-from-one-type-to-another"></a>Tür üyelerini bir türden diğerine taşıma

**Sınıf Tasarımcısı'nı**kullanarak, bir tür üyesini bir türden başka bir türe taşıyabilirsiniz. Her iki tür de geçerli sınıf diyagramında görünür olmalıdır.

1. Tasarım yüzeyinde görünen bir türde, başka bir türe geçmek istediğiniz üyeyi sağ tıklatın ve ardından **Kes'i**seçin.

2. Hedef türüne sağ tıklayın ve **Yapıştır'ı**seçin.

     Özellik kaynak türünden kaldırılır ve hedef türünde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıfları ve Türleri Tasarlama](designing-and-viewing-classes-and-types.md)
