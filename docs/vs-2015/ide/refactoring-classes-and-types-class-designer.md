---
title: Sınıfları ve türleri yeniden düzenleme (Sınıf Tasarımcısı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5803b720ae1271d8319310820d1f0dc159db8bf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670266"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Sınıfları ve Türleri Yeniden Düzenleme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kodu yeniden oluştururken, iç yapısını değiştirerek ve onun dış davranışını değil, nesnelerin nasıl tasarlandığına ilişkin daha kolay bir şekilde anlaşılmasını, bakımını ve daha verimli hale getirebilirsiniz. Visual Studio projenizde Visual C# .NET, Visual Basic .NET veya C++ kodu yeniden oluştururken yapmanız gereken işi ve hata tanıtma olasılığını azaltmak için Sınıf Tasarımcısı ve sınıf ayrıntıları penceresini kullanın.

> [!NOTE]
> Proje kaynak kodu denetimi altında olduğundan ve kullanıma verilmediği için bir projenin dosyaları salt okunabilir olabilir; başvurulan bir projem; veya dosyaları diskte salt okuma olarak işaretlenir. Bu durumlardan birindeki bir projede çalışırken, işinizi projenin durumuna bağlı olarak kaydetmek için çeşitli yollarla karşılaşırsınız. Bu, yeniden düzenleme kodu ve ayrıca, başka bir şekilde değiştirdiğiniz kod için geçerlidir (örneğin, doğrudan düzenleme). Daha fazla bilgi için bkz. [salt okuma bilgilerini görüntüleme (sınıf Tasarımcısı)](https://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).

## <a name="common-tasks"></a>Ortak Görevler

|Görev|Destekleyici İçerik|
|----------|------------------------|
|**Sınıfları yeniden düzenleme:** Yeniden düzenleme işlemlerini, bir sınıfı kısmi sınıflara bölmek veya bir soyut temel sınıf uygulamak için kullanabilirsiniz.|-   [Nasıl yapılır: sınıfı kısmi sınıflara bölme (Sınıf Tasarımcısı)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|
|**Arabirimler Ile çalışma:** Sınıf Tasarımcısı ' de, arabirim yöntemleri için kod sağlayan bir sınıfa bağlayarak sınıf diyagramında bir arabirim uygulayabilirsiniz.|-   [Nasıl yapılır: arabirim uygulama (Sınıf Tasarımcısı)](../ide/how-to-implement-an-interface-class-designer.md)|
|Yeniden **düzenleme türleri, tür üyeleri ve Parametreler:** Sınıf Tasarımcısı kullanarak, türleri yeniden adlandırabilir, tür üyelerini geçersiz kılabilir veya bir türden diğerine taşıyabilirsiniz. Null yapılabilir türler de oluşturabilirsiniz.|-   [Türler ve tür üyelerini yeniden adlandırma](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Tür üyelerini bir türden diğerine taşıma](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Nasıl yapılır: null yapılabilir bir tür oluşturma (Sınıf Tasarımcısı)](../ide/how-to-create-a-nullable-type-class-designer.md)|

### <a name="renaming-types-and-type-members"></a><a name="RenamingTypesAndMembers"></a> Türler ve tür üyelerini yeniden adlandırma
 Sınıf Tasarımcısı, sınıf diyagramında veya Özellikler penceresi bir türün bir türünü ya da bir üyesini yeniden adlandırabilirsiniz. Sınıf Ayrıntıları penceresinde bir üyenin adını değiştirebilirsiniz ancak bir tür değil. Bir tür veya tür üyesini yeniden adlandırmak, eski adın göründüğü tüm Windows ve kod konumlarına yayar.

##### <a name="to-rename-a-name-in-the-class-designer"></a>Sınıf Tasarımcısı bir adı yeniden adlandırmak için

1. Sınıf diyagramında türü veya üyeyi seçin ve ada tıklayın.

     Üyenin adı düzenlenebilir hale gelir.

2. Tür veya tür üyesi için yeni bir ad yazın

##### <a name="to-rename-a-name-in-the-class-details-window"></a>Sınıf Detayları Penceresi bir adı yeniden adlandırmak için

1. Sınıf ayrıntıları penceresini göstermek için, türe veya tür üyesine sağ tıklayın ve ardından **Sınıf Ayrıntıları**' na tıklayın.

     Sınıf Ayrıntıları penceresi görüntülenir.

2. **Ad** sütununda, tür üyesinin adını değiştirin

3. Odağı hücreden uzağa taşımak için **ENTER** tuşuna basın veya hücreden uzakta ' ye tıklayın.

    > [!NOTE]
    > Sınıf Ayrıntıları penceresinde bir üyenin adını değiştirebilirsiniz ancak bir tür değil.

##### <a name="to-rename-a-name-in-the-properties-window"></a>Özellikler penceresi bir adı yeniden adlandırmak için

1. Sınıf diyagramında veya sınıf Ayrıntıları penceresinde, türe veya üyeye sağ tıklayın ve ardından **Özellikler**' e tıklayın.

     Özellikler penceresi görünür ve tür ya da tür üyesinin özelliklerini görüntüler.

2. **Ad** özelliğinde, türün veya tür üyesinin adını değiştirin.

     Yeni ad, geçerli projedeki tüm Windows ve kod konumlarına, eski adın göründüğü yere yayar.

### <a name="moving-type-members-from-one-type-to-another"></a><a name="MovingTypeMembers"></a> Tür üyelerini bir türden diğerine taşıma
 **Sınıf Tasarımcısı**kullanarak, her ikisi de geçerli sınıf diyagramında görünür durumdaysa, bir tür üyesini bir türden başka bir türe taşıyabilirsiniz.

##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Bir tür üyesini bir türden diğerine taşımak için

1. Tasarım yüzeyinde görünür olan bir türde, başka bir türe taşımak istediğiniz üyeye sağ tıklayın ve ardından **Kes**' e tıklayın.

2. Hedef türüne sağ tıklayıp **Yapıştır**' a tıklayın.

     Özelliği, kaynak türünden kaldırılır ve hedef türünde görünür.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[Türleri ve İlişkilendirmeleri Görüntüleme (Sınıf Tasarımcısı)](../ide/viewing-types-and-relationships-class-designer.md)||
|[Sınıfları ve Türleri Tasarlama (Sınıf Tasarımcısı)](../ide/designing-classes-and-types-class-designer.md)||
