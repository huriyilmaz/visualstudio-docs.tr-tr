---
title: Türler arasında ilişkilendirme oluşturma
description: Sınıf Tasarımcısı farklı türler arasında ilişkilendirme oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: cfd60aba37931d6200cd241a7f0863b3c2e52eb8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109532"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı türler arasında ilişkilendirme oluşturma

**Sınıf Tasarımcısı** içindeki ilişkilendirme çizgileri, diyagramdaki sınıfların nasıl ilişkili olduğunu gösterir. İlişkilendirme çizgisi, projenizdeki başka bir sınıfın özellik veya alan türü olan bir sınıfı temsil eder. İlişkilendirme çizgileri genellikle, projenizdeki sınıflar arasında en önemli ilişkileri göstermek için kullanılır.

Tüm alanları ve özellikleri ilişkilendirmeler halinde görüntüleyebilirsiniz; bununla birlikte diyagramda vurgulamak istediğiniz unsura bağlı olarak yalnızca önemli üyeleri ilişkilendirme olarak göstermek daha anlamlı olur. (Daha az önemli üyeleri normal üye olarak gösterebilir veya bütünüyle gizleyebilirsiniz.)

> [!NOTE]
> **Sınıf Tasarımcısı** yalnızca tek yönlü ilişkilendirmeleri destekler.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Sınıf Diyagramı'nda bir ilişkilendirme çizgisi tanımlamak için

1. Araç kutusunda, **Sınıf Tasarımcısı** altında **ilişkilendirme**' yi seçin.

2. İlişkilendirme ile bağlamak istediğiniz iki şekil arasına bir çizgi çizin.

     İlk sınıfta yeni bir özellik oluşturulur. Bu özellik varsayılan ada sahip bir ilişkilendirme çizgisi görüntüler (şekildeki bir bölme içinde özellik olarak değil). Türü ise, ilişkilendirme çizgisinin işaret ettiği şekildir.

## <a name="to-change-the-name-of-an-association"></a>İlişkilendirmenin adını değiştirmek için

Diyagram yüzeyinde ilişkilendirme çizgisinin etiketine tıklayın ve etiketi düzenleyin.

Alternatif olarak, aşağıdaki adımları izleyin:

1. İlişki olarak gösterilen özelliği içeren şekli seçin.

   Şekil odağı ve üyelerini edinir **Sınıf Ayrıntıları** ve **Özellikler** penceresinde görüntüler.

2. **Sınıf Ayrıntıları** veya **Özellikler** penceresinde, bu özellik için ad alanını düzenleyin ve **ENTER** tuşuna basın.

   Ad, **Sınıf Ayrıntıları** penceresinde, ilişkilendirme satırında, **Özellikler** penceresinde ve kod ' de güncelleştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: üye gösterimi ile ilişkilendirme gösterimi arasında geçiş yapma](how-to-change-between-member-notation-and-association-notation.md)
