---
title: 'Nasıl Yapılır: Türler Arasında İlişkilendirme Oluşturma (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61b598505ad465ec9086102b9e16e96cb7aa8275
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590390"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Nasıl yapilir: Sınıf Tasarımcısı'ndaki türler arasında ilişki oluşturma

**Sınıf Tasarımcısı'ndaki** ilişkilendirme satırları diyagramdaki sınıfların nasıl ilişkili olduğunu gösterir. İlişkilendirme çizgisi, projenizdeki başka bir sınıfın özellik veya alan türü olan bir sınıfı temsil eder. İlişkilendirme çizgileri genellikle, projenizdeki sınıflar arasında en önemli ilişkileri göstermek için kullanılır.

Tüm alanları ve özellikleri ilişkilendirmeler halinde görüntüleyebilirsiniz; bununla birlikte diyagramda vurgulamak istediğiniz unsura bağlı olarak yalnızca önemli üyeleri ilişkilendirme olarak göstermek daha anlamlı olur. (Daha az önemli üyeleri normal üye olarak gösterebilir veya bütünüyle gizleyebilirsiniz.)

> [!NOTE]
> **Sınıf Tasarımcısı** yalnızca tek yönlü çağrışımları destekler.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Sınıf Diyagramı'nda bir ilişkilendirme çizgisi tanımlamak için

1. Araç Kutusunda, **Sınıf Tasarımcısı** **altında, İlişkilendirme'yi**seçin.

2. İlişkilendirme ile bağlamak istediğiniz iki şekil arasına bir çizgi çizin.

     İlk sınıfta yeni bir özellik oluşturulur. Bu özellik varsayılan ada sahip bir ilişkilendirme çizgisi görüntüler (şekildeki bir bölme içinde özellik olarak değil). Türü ise, ilişkilendirme çizgisinin işaret ettiği şekildir.

## <a name="to-change-the-name-of-an-association"></a>İlişkilendirmenin adını değiştirmek için

Diyagram yüzeyinde ilişkilendirme çizgisinin etiketine tıklayın ve etiketi düzenleyin.

Alternatif olarak, aşağıdaki adımları izleyin:

1. İlişkilendirme olarak gösterilen özelliği içeren şekli seçin.

   Şekil odak alır ve üyeleri **Sınıf Ayrıntıları** ve **Özellikleri** pencerelerinde görüntülenir.

2. **Sınıf Ayrıntıları** veya **Özellikler** penceresinde, o özelliğin ad alanını ve **Enter**tuşuna basın.

   Ad **Sınıf Ayrıntıları** penceresinde, ilişkilendirme satırında, **Özellikler** penceresinde ve kodda güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: Üye gösterimi ile ilişkilendirme gösterimi arasında değişiklik](how-to-change-between-member-notation-and-association-notation.md)
