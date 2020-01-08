---
title: Sınıf Tasarımcısı sınıfları ve türleri yeniden adlandırma ve taşıma
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590754"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Sınıf Tasarımcısı sınıfları ve türleri yeniden düzenleme

Kodu yeniden oluştururken, iç yapısını değiştirerek ve onun dış davranışını değil, nesnelerin nasıl tasarlandığına ilişkin daha kolay bir şekilde anlaşılmasını, bakımını ve daha verimli hale getirebilirsiniz. Sınıf Tasarımcısı ve sınıf ayrıntıları penceresini, sizin yapmanız gereken işi ve Visual Studio projenizde yeniden düzenleme C#, Visual Basic ya C++ da kod oluştururken hata tanıtma olasılığını azaltmak için kullanın.

> [!NOTE]
> Proje kaynak kodu denetimi altında olduğu ve kullanıma alınmamış, başvurulan bir proje veya dosyaları diskte salt okuma olarak işaretlendiğinden bir projenin dosyaları salt okunurdur. Bu durumlardan birindeki bir projede çalışırken, işinizi projenin durumuna bağlı olarak kaydetmek için çeşitli yollarla karşılaşırsınız. Bu, yeniden düzenleme kodu ve ayrıca, başka bir şekilde değiştirdiğiniz kod için geçerlidir (örneğin, doğrudan düzenleme).

## <a name="common-tasks"></a>Ortak görevler

|Görev|Destekleyici İçerik|
|----------| - |
|**Sınıfları yeniden düzenleme:** Yeniden düzenleme işlemlerini, bir sınıfı kısmi sınıflara bölmek veya bir soyut temel sınıf uygulamak için kullanabilirsiniz.|-   [nasıl yapılır: sınıfı kısmi sınıflara bölme](how-to-split-a-class-into-partial-classes.md)|
|**Arabirimler Ile çalışma:** Sınıf Tasarımcısı ' de, arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim uygulayabilirsiniz.|-   [nasıl yapılır: arabirim uygulama](how-to-implement-an-interface.md)|
|Yeniden **düzenleme türleri, tür üyeleri ve Parametreler:** Sınıf Tasarımcısı kullanarak, türleri yeniden adlandırabilir, tür üyelerini geçersiz kılabilir veya bir türden diğerine taşıyabilirsiniz. Null yapılabilir türler de oluşturabilirsiniz.|-   [türlerini ve tür üyelerini yeniden adlandırma](#rename-types-and-type-members)<br />[tür üyelerini bir türden diğerine taşımak](#move-type-members-from-one-type-to-another) -   <br />-   [nasıl yapılır: null yapılabilir bir tür oluşturma](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Türleri ve tür üyelerini yeniden adlandırma

Sınıf Tasarımcısı, sınıf diyagramında veya **Özellikler** penceresinde bir tür veya bir türün bir üyesini yeniden adlandırabilirsiniz. **Sınıf Ayrıntıları** penceresinde bir üyenin adını değiştirebilirsiniz ancak bir tür değil. Bir tür veya tür üyesini yeniden adlandırmak, eski adın göründüğü tüm Windows ve kod konumlarına yayar.

### <a name="rename-in-the-class-designer"></a>Sınıf Tasarımcısı yeniden adlandır

1. Sınıf diyagramında türü veya üyeyi seçin ve adı seçin.

     Üyenin adı düzenlenebilir hale gelir.

2. Tür veya tür üyesi için yeni bir ad yazın

### <a name="rename-in-the-class-details-window"></a>Sınıf Ayrıntıları penceresinde yeniden adlandır

1. **Sınıf Ayrıntıları** penceresini göstermek için, türe veya tür üyesine sağ tıklayın ve **Sınıf Ayrıntıları**' nı seçin.

     **Sınıf Ayrıntıları** penceresi görüntülenir.

2. **Ad** sütununda, tür üyesinin adını değiştirin

3. Odağı hücreden uzağa taşımak için **ENTER** tuşuna basın veya hücreden uzakta ' ye tıklayın.

    > [!NOTE]
    > **Sınıf Ayrıntıları** penceresinde bir üyenin adını değiştirebilirsiniz ancak bir tür değil.

### <a name="rename-in-the-properties-window"></a>Özellikler penceresi yeniden adlandır

1. Sınıf diyagramında veya **Sınıf Ayrıntıları** penceresinde, türü veya üyeyi sağ tıklatın ve ardından **Özellikler**' i seçin.

     **Özellikler** penceresi görünür ve tür ya da tür üyesinin özelliklerini görüntüler.

2. **Ad** özelliğinde, türün veya tür üyesinin adını değiştirin.

     Yeni ad, geçerli projedeki tüm Windows ve kod konumlarına, eski adın göründüğü yere yayar.

## <a name="move-type-members-from-one-type-to-another"></a>Tür üyelerini bir türden diğerine taşıma

**Sınıf Tasarımcısı**kullanarak, bir tür üyesini bir türden başka bir türe taşıyabilirsiniz. Her iki tür de geçerli sınıf diyagramında görünür olmalıdır.

1. Tasarım yüzeyinde görünür olan bir türde, başka bir türe taşımak istediğiniz üyeye sağ tıklayın ve ardından **Kes**' i seçin.

2. Hedef türüne sağ tıklayıp **Yapıştır**' ı seçin.

     Özelliği, kaynak türünden kaldırılır ve hedef türünde görünür.

## <a name="see-also"></a>Ayrıca bkz.

- [Sınıfları ve türleri tasarlama](designing-and-viewing-classes-and-types.md)
