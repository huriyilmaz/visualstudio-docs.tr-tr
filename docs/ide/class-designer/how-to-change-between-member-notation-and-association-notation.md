---
title: Üye & ilişkilendirme gösterimi arasında geçiş (Sınıf Tasarımcısı)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd1bb86e13fb5f5b654ad4f4e1ee7fe7a243f1f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647739"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Nasıl yapılır: Sınıf Tasarımcısı içindeki üye gösterimi ile ilişkilendirme gösterimi arasında geçiş yapma

**Sınıf Tasarımcısı**, sınıf diyagramının üye gösterimden ilişki gösterimine ve tam tersi şekilde iki tür arasındaki ilişki ilişkisini temsil ettiğini değiştirebilirsiniz. İlişki hatları olarak görüntülenen Üyeler genellikle türlerin nasıl ilişkili olduğu konusunda yararlı bir görselleştirme sağlar.

> [!NOTE]
> İlişki ilişkileri, üye özelliği veya alanı olarak gösterilebilir. Üye gösterimini ilişkilendirme gösterimi olarak değiştirmek için, bir türün başka bir türün üyesi olması gerekir. İlişki gösterimini üye gösterimine göre değiştirmek için, iki tür bir ilişkilendirme satırıyla bağlanmalıdır. Daha fazla bilgi için bkz. [nasıl yapılır: tür Ilişkilendirmelerini bler oluşturma](how-to-create-associations-between-types.md). Projeniz birden çok sınıf diyagramı içeriyorsa, bir diyagramın ilişki ilişkilerini gösterdiği şekilde yaptığınız değişiklikler yalnızca bu diyagramı etkiler. Başka bir diyagramın ilişki ilişkilerini görüntüleme şeklini değiştirmek için bu diyagramı açın veya görüntüleyin ve bu adımları uygulayın.

## <a name="to-change-member-notation-to-association-notation"></a>Üye gösterimini ilişkilendirme gösterimi olarak değiştirmek için

1. Çözüm Gezgini içindeki proje düğümünden sınıf diyagramı (. CD) dosyasını açın.

2. Sınıf diyagramındaki tür şeklinin içinde, ilişkiyi temsil eden üye özelliğine veya alana sağ tıklayın ve **ilişkilendirme olarak göster**' i seçin.

    > [!TIP]
    > Tür şeklinin içinde hiçbir özellik veya alan görünmüyorsa, şekildeki bölmeleri daraltılmış olabilir. Tür şeklini genişletmek için bölme adına çift tıklayın veya tür şekline sağ tıklayın ve **Genişlet**' i seçin.

    Üye tür şeklindeki bölmeden kaybolur ve iki türü bağlamak için bir ilişkilendirme satırı görünür. İlişkilendirme çizgisi, özelliğin veya alanın adıyla etiketlenir.

## <a name="to-change-association-notation-to-member-notation"></a>İlişki gösterimini üye gösterimine göre değiştirmek için

Sınıf diyagramında, ilişkilendirme satırına sağ tıklayın ve **özellik olarak göster** ' i seçin veya uygun şekilde **alanı göster** ' i seçin. İlişkilendirme satırı kaybolur ve özelliği, diyagramda tür şeklinin içindeki uygun bölme içinde görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: türler arasında devralma oluşturma](how-to-create-inheritance-between-types.md)
- [Nasıl yapılır: türler arasında devralmayı görüntüleme](how-to-view-inheritance-between-types.md)
- [Türleri ve İlişkileri Görüntüleme](designing-and-viewing-classes-and-types.md)
- [Nasıl yapılır: koleksiyon Ilişkilendirmesini görselleştirme](how-to-visualize-a-collection-association.md)