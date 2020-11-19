---
title: 'Nasıl Yapılır: Sınıf Diyagramlarını Özelleştirme (Sınıf Tasarımcısı)'
description: Sınıf diyagramlarının bilgileri nasıl görüntüleyeceği ve tasarım yüzeyindeki tüm diyagram ya da tek türlerin nasıl özelleştirileceği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05f0b20307ac0802c4c4350588f5dc0c47cb3b6b
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901433"
---
# <a name="how-to-customize-class-diagrams"></a>Nasıl yapılır: sınıf diyagramlarını özelleştirme

Sınıf diyagramlarının bilgileri görüntüleme biçimini değiştirebilirsiniz. Tüm diyagramı veya tasarım yüzeyinde tek tek türleri özelleştirebilirsiniz.

Örneğin, tüm bir sınıf diyagramının yakınlaştırma seviyesini ayarlayabilir, tek tek üyelerin gruplandırılma ve sıralanma şeklini değiştirebilir, ilişkileri gizleyebilir ya da gösterebilir ve tek tek türleri ya da tür kümelerini diyagram üzerinde istediğiniz yere taşıyabilirsiniz.

> [!NOTE]
> Şekillerin diyagram üzerinde görünme biçimi özelleştirildiğinde, diyagramda temsil edilen türlerin temelini oluşturan kod değişmez.

Bir sınıftaki **Özellikler** bölümü gibi tür üyelerini içeren bölümler, bölmeleri olarak adlandırılır. Tek tek bölmeleri ve tür üyelerini gizleyebilir veya gösterebilirsiniz.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Sınıf diyagramını yakınlaştırma ve uzaklaştırma

1. **Sınıf Tasarımcısı**' de bir sınıf diyagramı dosyası açın ve seçin.

2. Tasarımcı yüzeyinin yakınlaştırma düzeyini değiştirmek için **Sınıf Tasarımcısı** araç çubuğunda **Yakınlaştır** veya **uzaklaştır** düğmesine tıklayın.

     veya

     Belirli bir yakınlaştırma değeri belirtin. **Yakınlaştırma** açılan listesini kullanabilir veya geçerli bir yakınlaştırma düzeyi yazabilirsiniz (geçerli Aralık %10 ile %400 arasında).

    > [!NOTE]
    > Yakınlaştırma seviyesinin değiştirilmesi sınıf diyagramı çıktınızın ölçeğini etkilemez.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Tür üyelerinin gruplandırmasını ve sıralamasını özelleştirme

1. **Sınıf Tasarımcısı**' de bir sınıf diyagramı dosyası açın ve seçin.

2. Tasarım yüzeyinde boş bir alana sağ tıklayın ve **Grup üyeleri**' nin üzerine gelin.

3. Kullanılabilir seçeneklerden birini belirtin:

    - **Gruplandırma ölçütü** , tek tür üyelerini bir gruplanmış özellikler, Yöntemler, olaylar ve alanlar listesine ayırır. Tek tek gruplar varlıklar tanımına göre değişir: Örneğin, bir sınıf için henüz hiç tanımlı olay yoksa, bu sınıf olaylar grubunu görüntülemez.

    - **Gruplandırma ölçütü** , bireysel tür üyelerini üyenin erişim değiştiricilerine göre gruplanmış bir liste halinde ayırır. Örneğin, Genel ve Özel.

    - **Alfabetik olarak Sırala** , bir varlığı oluşturan öğeleri tek bir alfabetik liste olarak görüntüler. Liste artan düzende sıralanır.

## <a name="hide-compartments-on-a-type"></a>Türe göre bölmeleri gizleme

1. **Sınıf Tasarımcısı** bir sınıf diyagramı dosyası açın ve seçin.

2. Özelleştirmek istediğiniz türdeki üye kategorisine sağ tıklayın (örneğin, bir sınıfta **Yöntemler** düğümünü seçin).

3. Bölmeyi **Gizle**' ye tıklayın.

     Seçili bölme tür kapsayıcısından kaybolur.

## <a name="hide-individual-members-on-a-type"></a>Türe göre tek tek üyeleri gizleme

1. **Sınıf Tasarımcısı**' de bir sınıf diyagramı dosyası açın ve seçin.

2. Gizlemek istediğiniz türde üyeye sağ tıklayın.

3. **Gizle**'yi tıklatın.

     Seçili üye tür kapsayıcısından kaybolur.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Türe göre gizli bölmeleri ve üyeleri gösterme

1. **Sınıf Tasarımcısı**' de bir sınıf diyagramı dosyası açın ve seçin.

2. Gizli bölmeyi içeren türün adına sağ tıklayın.

3. **Tüm üyeleri göster**' e tıklayın.

     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.

## <a name="hide-relationships"></a>İlişkileri gizleme

1. **Sınıf Tasarımcısı**' de bir sınıf diyagramı dosyası açın ve seçin.

2. Gizlemek istediğiniz ilişkilendirme veya devralma çizgisine sağ tıklayın.

3. İlişkilendirme çizgileri için **Gizle** ' ye tıklayın ve devralma çizgileri Için **Devralma satırını Gizle** ' ye tıklayın.

4. **Tüm üyeleri göster**' e tıklayın.

     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.

## <a name="show-hidden-relationships"></a>Gizli ilişkileri gösterme

1. **Sınıf Tasarımcısı**' de bir sınıf diyagramı dosyası açın ve seçin.

2. Gizli ilişkilendirmeyi veya devralmayı içeren türün adına sağ tıklayın.

   İlişki çizgileri için **tüm üyeleri göster** ' e tıklayın ve **temel sınıfı göster** ' e tıklayın veya devralma çizgileri için **türetilmiş sınıfları göster** ' e tıklayın

## <a name="remove-a-shape-from-a-class-diagram"></a>Sınıf diyagramından şekil kaldırma
Türün temelini oluşturan koda etkisi olmaksızın, bir tür şeklini sınıf diyagramından kaldırabilirsiniz. Tür şekillerinin bir sınıf diyagramından kaldırılması yalnızca o diyagramı etkiler: Türü tanımlayan temel kod ve türü görüntüleyen diğer diyagramlar bundan etkilenmez.

1. Sınıf diyagramında, diyagramdan kaldırmak istediğiniz tür şeklini seçin.

2. **Düzenle** menüsünde **diyagramdan kaldır**' ı seçin.

     Tür şekli ve varsa bu şekle bağlı ilişkilendirme ya da devralma çizgileri bundan böyle diyagramda görünmez.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Bir tür şeklini ve temelini oluşturan kodu silme

1. Tasarım yüzeyinde şekle sağ tıklayın.

2. Bağlam menüsünden **kodu Sil** ' i seçin.

     Şekil diyagramdan kaldırılır ve temelini oluşturan kod projeden silinir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: üye gösterimi ile Ilişkilendirme gösterimi arasında geçiş yapma](how-to-change-between-member-notation-and-association-notation.md)
- [Nasıl yapılır: varolan türleri görüntüleme](how-to-view-existing-types.md)
- [Türleri ve İlişkileri Görüntüleme](designing-and-viewing-classes-and-types.md)
