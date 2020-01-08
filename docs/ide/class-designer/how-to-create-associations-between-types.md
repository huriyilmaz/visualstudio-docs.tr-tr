---
title: 'Nasıl yapılır: türler arasında Ilişkilendirme oluşturma (Sınıf Tasarımcısı)'
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590390"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı türler arasında ilişkilendirme oluşturma

**Sınıf Tasarımcısı** içindeki ilişkilendirme çizgileri, diyagramdaki sınıfların nasıl ilişkili olduğunu gösterir. İlişkilendirme çizgisi, projenizdeki başka bir sınıfın özellik veya alan türü olan bir sınıfı temsil eder. İlişkilendirme çizgileri genellikle, projenizdeki sınıflar arasında en önemli ilişkileri göstermek için kullanılır.

Tüm alanları ve özellikleri ilişkilendirmeler halinde görüntüleyebilirsiniz; bununla birlikte diyagramda vurgulamak istediğiniz unsura bağlı olarak yalnızca önemli üyeleri ilişkilendirme olarak göstermek daha anlamlı olur. (Daha az önemli üyeleri normal üye olarak gösterebilir veya bütünüyle gizleyebilirsiniz.)

> [!NOTE]
> **Sınıf Tasarımcısı** yalnızca tek yönlü ilişkilendirmeleri destekler.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Sınıf Diyagramı'nda bir ilişkilendirme çizgisi tanımlamak için

1. Araç kutusunda, **Sınıf Tasarımcısı**altında **ilişkilendirme**' yi seçin.

2. İlişkilendirme ile bağlamak istediğiniz iki şekil arasına bir çizgi çizin.

     İlk sınıfta yeni bir özellik oluşturulur. Bu özellik varsayılan ada sahip bir ilişkilendirme çizgisi görüntüler (şekildeki bir bölme içinde özellik olarak değil). Türü ise, ilişkilendirme çizgisinin işaret ettiği şekildir.

## <a name="to-change-the-name-of-an-association"></a>İlişkilendirmenin adını değiştirmek için

Diyagram yüzeyinde ilişkilendirme çizgisinin etiketine tıklayın ve etiketi düzenleyin.

Alternatif olarak, aşağıdaki adımları izleyin:

1. İlişki olarak gösterilen özelliği içeren şekli seçin.

   Şekil odağı ve üyelerini edinir **Sınıf Ayrıntıları** ve **Özellikler** penceresinde görüntüler.

2. **Sınıf Ayrıntıları** veya **Özellikler** penceresinde, bu özellik için ad alanını düzenleyin ve **ENTER**tuşuna basın.

   Ad, **Sınıf Ayrıntıları** penceresinde, ilişkilendirme satırında, **Özellikler** penceresinde ve kod ' de güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: üye gösterimi ile ilişkilendirme gösterimi arasında geçiş yapma](how-to-change-between-member-notation-and-association-notation.md)
