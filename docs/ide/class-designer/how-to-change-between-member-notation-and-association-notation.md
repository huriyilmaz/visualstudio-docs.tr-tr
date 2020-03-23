---
title: Üye & ilişkilendirme gösterimi (Sınıf Tasarımcısı) arasındaki değişim
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f706acfbaee7c6170f74bc655f9172ff6bdd3b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592275"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Nasıl yapilir: Sınıf Tasarımcısı'nda üye gösterimi ile ilişkilendirme gösterimi arasında değişiklik

**Sınıf**Tasarımcısı'nda, sınıf diyagramı üye gösteriminden ilişkilendirme notasına ve tam tersi iki tür arasındaki ilişkiyi temsil etme biçimini değiştirebilirsiniz. İlişkilendirme satırları olarak görüntülenen üyeler genellikle türlerin nasıl ilişkili olduğuna ilişkin yararlı bir görselleştirme sağlar.

> [!NOTE]
> İlişki ilişkileri bir üye özellik veya alan olarak temsil edilebilir. Üye notasyonunu ilişkilendirme notasyonuna değiştirmek için, bir türbaşka bir türe üye olmalıdır. İlişkilendirme notunu üye gösterimine değiştirmek için, iki tür bir ilişkilendirme satırıyla bağlanması gerekir. Daha fazla bilgi için [bkz: Nasıl: Türleri arasında ilişki oluşturma](how-to-create-associations-between-types.md). Projeniz birden çok sınıf diyagramı içeriyorsa, diyagramın ilişkilendirme ilişkilerini görüntüleme şeklinde yaptığınız değişiklikler yalnızca bu diyagramı etkiler. Başka bir diyagramın ilişkilendirme ilişkilerini görüntüleme şeklini değiştirmek için, bu diyagramı açın veya görüntüleyin ve bu adımları gerçekleştirin.

## <a name="to-change-member-notation-to-association-notation"></a>Üye notunu ilişkilendirme notasyonuna değiştirmek için

1. Çözüm Gezgini'ndeki proje düğümünden sınıf diyagramı (.cd) dosyasını açın.

2. Sınıf diyagramındaki tür şeklinde, ilişkilendirmeyi temsil eden üye özelliği veya alanı sağ tıklatın ve **İlişki olarak göster'i**seçin.

    > [!TIP]
    > Tür şeklinde hiçbir özellik veya alan görünmüyorsa, şekildeki bölmeler daraltılmış olabilir. Türü genişletmek için, bölme adını çift tıklatın veya tür şeklini sağ tıklatın ve **Genişlet'i**seçin.

    Üye tür şeklinde bölmeden kaybolur ve bir ilişkilendirme satırı iki tür bağlamak için görünür. İlişkilendirme satırı, özelliğin veya alanın adıyla etiketlenir.

## <a name="to-change-association-notation-to-member-notation"></a>Dernek notunu üye notasyonuna değiştirmek için

Sınıf diyagramında, ilişkilendirme satırına sağ tıklayın ve uygun **olarak Özellik olarak Göster** veya Alanı **Göster'i** seçin. İlişkilendirme satırı kaybolur ve özellik diyagramdaki tür şekli içinde uygun bölmede görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılacağını: Türler Arasında Devralma Oluşturma](how-to-create-inheritance-between-types.md)
- [Nasıl yapılı: Türler Arasında Devralma Yı Görüntüle](how-to-view-inheritance-between-types.md)
- [Türleri ve İlişkileri Görüntüleme](designing-and-viewing-classes-and-types.md)
- [Nasıl yapilir: Koleksiyon İlişkisini Görselleştir](how-to-visualize-a-collection-association.md)
