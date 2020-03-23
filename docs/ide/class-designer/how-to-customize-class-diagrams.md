---
title: 'Nasıl Yapılır: Sınıf Diyagramlarını Özelleştirme (Sınıf Tasarımcısı)'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: f4c55204983f9e7a546867621ec21070c8d69645
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590169"
---
# <a name="how-to-customize-class-diagrams"></a>Nasıl? sınıf diyagramlarını özelleştirin

Sınıf diyagramlarının bilgileri görüntüleme biçimini değiştirebilirsiniz. Tüm diyagramı veya tasarım yüzeyinde tek tek türleri özelleştirebilirsiniz.

Örneğin, tüm bir sınıf diyagramının yakınlaştırma seviyesini ayarlayabilir, tek tek üyelerin gruplandırılma ve sıralanma şeklini değiştirebilir, ilişkileri gizleyebilir ya da gösterebilir ve tek tek türleri ya da tür kümelerini diyagram üzerinde istediğiniz yere taşıyabilirsiniz.

> [!NOTE]
> Şekillerin diyagram üzerinde görünme biçimi özelleştirildiğinde, diyagramda temsil edilen türlerin temelini oluşturan kod değişmez.

Bir sınıftaki **Özellikler** bölümü gibi tür üyeleri içeren bölümlere bölme denir. Tek tek bölmeleri ve tür üyelerini gizleyebilir veya gösterebilirsiniz.

## <a name="zoom-in-and-out-of-the-class-diagram"></a>Sınıf diyagramını yakınlaştırma ve uzaklaştırma

1. **Sınıf Tasarımcısı'nda**sınıf diyagramı dosyasini açın ve seçin.

2. Sınıf **Tasarımcısı** araç çubuğunda, tasarımcı yüzeyinin yakınlaştırma düzeyini değiştirmek için **Yakınlaştır** veya **Uzaklaştır** düğmesini tıklatın.

     or

     Belirli bir yakınlaştırma değeri belirtin. **Yakınlaştırma** açılır listesini kullanabilir veya geçerli bir yakınlaştırma düzeyi yazabilirsiniz (geçerli aralık %10 ile %400 arasındadır).

    > [!NOTE]
    > Yakınlaştırma seviyesinin değiştirilmesi sınıf diyagramı çıktınızın ölçeğini etkilemez.

## <a name="customize-grouping-and-sorting-of-type-members"></a>Tür üyelerinin gruplandırmasını ve sıralamasını özelleştirme

1. **Sınıf Tasarımcısı'nda**sınıf diyagramı dosyasini açın ve seçin.

2. Tasarım yüzeyindeboş bir alana sağ tıklayın ve **Grup Üyeleri'ni**işaret edin.

3. Kullanılabilir seçeneklerden birini belirtin:

    - **Türe göre grup,** tek tek tür üyelerini Özellikler, Yöntemler, Olaylar ve Alanlar gruplanmış bir listeye ayırır. Tek tek gruplar varlıklar tanımına göre değişir: Örneğin, bir sınıf için henüz hiç tanımlı olay yoksa, bu sınıf olaylar grubunu görüntülemez.

    - **Group by Access,** tek tek tür üyelerini üyenin erişim değiştiricilere göre gruplanmış bir listeye ayırır. Örneğin, Genel ve Özel.

    - **Sıralama Alfabetik olarak** tek bir alfabetik liste olarak bir varlık oluşturan öğeleri görüntüler. Liste artan düzende sıralanır.

## <a name="hide-compartments-on-a-type"></a>Türe göre bölmeleri gizleme

1. **Sınıf Tasarımcısı'nda**sınıf diyagramı dosyasını açın ve seçin.

2. Özelleştirmek istediğiniz türdeki üye kategorisini sağ tıklatın (örneğin, bir sınıftaki **Yöntem** düğümünü seçin.

3. **Bölmeyi Gizle'yi**tıklatın.

     Seçili bölme tür kapsayıcısından kaybolur.

## <a name="hide-individual-members-on-a-type"></a>Türe göre tek tek üyeleri gizleme

1. **Sınıf Tasarımcısı'nda**sınıf diyagramı dosyasini açın ve seçin.

2. Gizlemek istediğiniz türde üyeye sağ tıklayın.

3. **Gizle'yi**tıklatın.

     Seçili üye tür kapsayıcısından kaybolur.

## <a name="show-hidden-compartments-and-members-on-a-type"></a>Türe göre gizli bölmeleri ve üyeleri gösterme

1. **Sınıf Tasarımcısı'nda**sınıf diyagramı dosyasini açın ve seçin.

2. Gizli bölmeyi içeren türün adına sağ tıklayın.

3. **Tüm Üyeleri Göster'i**tıklatın.

     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.

## <a name="hide-relationships"></a>İlişkileri gizleme

1. **Sınıf Tasarımcısı'nda**sınıf diyagramı dosyasini açın ve seçin.

2. Gizlemek istediğiniz ilişkilendirme veya devralma çizgisine sağ tıklayın.

3. İlişkilendirme satırları için **Gizle'yi** tıklatın ve devralma satırları için **Devralma SatırLarını Gizle'yi** tıklatın.

4. **Tüm Üyeleri Göster'i**tıklatın.

     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.

## <a name="show-hidden-relationships"></a>Gizli ilişkileri gösterme

1. **Sınıf Tasarımcısı'nda**sınıf diyagramı dosyasini açın ve seçin.

2. Gizli ilişkilendirmeyi veya devralmayı içeren türün adına sağ tıklayın.

   Ilişkilendirme satırları için **Tüm Üyeleri Göster'i** tıklatın ve devralma satırları için **Taban Sınıf'ı göster** veya **Türetilmiş Sınıfları Göster'i** tıklatın.

## <a name="remove-a-shape-from-a-class-diagram"></a>Sınıf diyagramından şekil kaldırma
Türün temelini oluşturan koda etkisi olmaksızın, bir tür şeklini sınıf diyagramından kaldırabilirsiniz. Tür şekillerinin bir sınıf diyagramından kaldırılması yalnızca o diyagramı etkiler: Türü tanımlayan temel kod ve türü görüntüleyen diğer diyagramlar bundan etkilenmez.

1. Sınıf diyagramında, diyagramdan kaldırmak istediğiniz tür şeklini seçin.

2. **Edit** menüsünde **Diyagramdan Kaldır'ı**seçin.

     Tür şekli ve varsa bu şekle bağlı ilişkilendirme ya da devralma çizgileri bundan böyle diyagramda görünmez.

## <a name="delete-a-type-shape-and-its-underlying-code"></a>Bir tür şeklini ve temelini oluşturan kodu silme

1. Tasarım yüzeyinde şekle sağ tıklayın.

2. Bağlam menüsünden **Kodu Sil'i** seçin.

     Şekil diyagramdan kaldırılır ve temelini oluşturan kod projeden silinir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: Üye Notasyonu ile Dernek Gösterimi Arasında Değişiklik](how-to-change-between-member-notation-and-association-notation.md)
- [Nasıl yapılı: Varolan Türleri Görüntüleme](how-to-view-existing-types.md)
- [Türleri ve İlişkileri Görüntüleme](designing-and-viewing-classes-and-types.md)
