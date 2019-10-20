---
title: 'Nasıl yapılır: sınıf diyagramlarını özelleştirme (Sınıf Tasarımcısı) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- class diagrams, customizing
- shapes, removing type from class diagrams
- type shapes, removing from class diagrams
- class diagrams, removing type shapes
ms.assetid: e9030aea-c77d-4cc1-b8f6-b6ca469b692d
caps.latest.revision: 33
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ff78bea6759359d3703f5fed6157f051c89befb0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668015"
---
# <a name="how-to-customize-class-diagrams-class-designer"></a>Nasıl Yapılır: Sınıf Diyagramlarını Özelleştirme (Sınıf Tasarımcısı)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf diyagramlarının bilgileri görüntüleme biçimini değiştirebilirsiniz. Tüm diyagramı veya tasarım yüzeyinde tek tek türleri özelleştirebilirsiniz.

 Örneğin, tüm bir sınıf diyagramının yakınlaştırma seviyesini ayarlayabilir, tek tek üyelerin gruplandırılma ve sıralanma şeklini değiştirebilir, ilişkileri gizleyebilir ya da gösterebilir ve tek tek türleri ya da tür kümelerini diyagram üzerinde istediğiniz yere taşıyabilirsiniz.

> [!NOTE]
> Şekillerin diyagram üzerinde görünme biçimi özelleştirildiğinde, diyagramda temsil edilen türlerin temelini oluşturan kod değişmez.

 Tür üyelerini içeren bölümlere (bir sınıf içindeki Özellikler bölümü gibi) bölmeler adı verilir. Tek tek bölmeleri ve tür üyelerini gizleyebilir veya gösterebilirsiniz.

 **Bu konuda**

- [Sınıf diyagramını yakınlaştırma ve uzaklaştırma](../ide/how-to-customize-class-diagrams-class-designer.md#ZoomInOut)

- [Tür üyelerinin gruplandırmasını ve sıralamasını özelleştirme](../ide/how-to-customize-class-diagrams-class-designer.md#CustomizeGroupingSorting)

- [Bir tür üzerinde bölmeleri gizle](../ide/how-to-customize-class-diagrams-class-designer.md#HideCompartments)

- [Bir türdeki üyeleri tek tek gizle](../ide/how-to-customize-class-diagrams-class-designer.md#HideMembers)

- [Bir tür üzerinde gizli bölmeleri ve üyeleri göster](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayHiddenCompartmentsAndMemberrs)

- [İlişkileri gizle](../ide/how-to-customize-class-diagrams-class-designer.md#HideAssociationAndInheritance)

- [Gizli ilişkileri göster](../ide/how-to-customize-class-diagrams-class-designer.md#DisplayAssociationAndInheritance)

- [Sınıf diyagramından bir şekli kaldırma](../ide/how-to-customize-class-diagrams-class-designer.md#RemoveCodeAndShape)

- [Bir tür şeklini ve onun temelindeki kodu silme](../ide/how-to-customize-class-diagrams-class-designer.md#DeleteTypeShapeAndCode)

## <a name="ZoomInOut"></a>Sınıf diyagramını yakınlaştırma ve uzaklaştırma

1. Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.

2. Tasarımcı yüzeyinin yakınlaştırma düzeyini değiştirmek için Sınıf Tasarımcısı araç çubuğunda **Yakınlaştır** veya **uzaklaştır** düğmesine tıklayın.

     veya

     Belirli bir yakınlaştırma değeri belirtin. **Yakınlaştırma** açılan listesini kullanabilir veya geçerli bir yakınlaştırma düzeyi yazabilirsiniz (geçerli Aralık %10 ile %400 arasında).

    > [!NOTE]
    > Yakınlaştırma seviyesinin değiştirilmesi sınıf diyagramı çıktınızın ölçeğini etkilemez.

## <a name="CustomizeGroupingSorting"></a>Tür üyelerinin gruplandırmasını ve sıralamasını özelleştirme

1. Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.

2. Tasarım yüzeyinde boş bir alana sağ tıklayın ve **Grup üyeleri**' nin üzerine gelin.

3. Kullanılabilir seçeneklerden birini belirtin:

    1. **Gruplandırma ölçütü** , tek tür üyelerini bir gruplanmış özellikler, Yöntemler, olaylar ve alanlar listesine ayırır. Tek tek gruplar varlıklar tanımına göre değişir: Örneğin, bir sınıf için henüz hiç tanımlı olay yoksa, bu sınıf olaylar grubunu görüntülemez.

    2. **Gruplandırma ölçütü** , bireysel tür üyelerini üyenin erişim değiştiricilerine göre gruplanmış bir liste halinde ayırır. Örneğin, Genel ve Özel.

    3. **Alfabetik olarak Sırala** , bir varlığı oluşturan öğeleri tek bir alfabetik liste olarak görüntüler. Liste artan düzende sıralanır.

## <a name="HideCompartments"></a>Bir tür üzerinde bölmeleri gizle

1. Sınıf tasarımcısında bir sınıf diyagramı dosyasını açın ve seçin.

2. Özelleştirmek istediğiniz türdeki üye kategorisine sağ tıklayın (örneğin, bir sınıfta **Yöntemler** düğümünü seçin).

3. Bölmeyi **Gizle**' ye tıklayın.

     Seçili bölme tür kapsayıcısından kaybolur.

## <a name="HideMembers"></a>Bir türdeki üyeleri tek tek gizle

1. Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.

2. Gizlemek istediğiniz türde üyeye sağ tıklayın.

3. **Gizle**'yi tıklatın.

     Seçili üye tür kapsayıcısından kaybolur.

## <a name="DisplayHiddenCompartmentsAndMemberrs"></a>Bir tür üzerinde gizli bölmeleri ve üyeleri göster

1. Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.

2. Gizli bölmeyi içeren türün adına sağ tıklayın.

3. **Tüm üyeleri göster**' e tıklayın.

     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.

## <a name="HideAssociationAndInheritance"></a>İlişkileri gizle

1. Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.

2. Gizlemek istediğiniz ilişkilendirme veya devralma çizgisine sağ tıklayın.

3. İlişkilendirme çizgileri için **Gizle** ' ye tıklayın ve devralma çizgileri Için **Devralma satırını Gizle** ' ye tıklayın.

4. **Tüm üyeleri göster**' e tıklayın.

     Tüm gizli bölmeler ve üyeler tür kapsayıcısında görünür.

## <a name="DisplayAssociationAndInheritance"></a>Gizli ilişkileri göster

1. Sınıf Tasarımcısı'nda bir sınıf diyagramı dosyasını açın ve seçin.

2. Gizli ilişkilendirmeyi veya devralmayı içeren türün adına sağ tıklayın.

   İlişki çizgileri için **tüm üyeleri göster** ' e tıklayın ve **temel sınıfı göster** ' e tıklayın veya devralma çizgileri için **türetilmiş sınıfları göster** ' e tıklayın

## <a name="RemoveCodeAndShape"></a>Sınıf diyagramından bir şekli kaldırma
 Türün temelini oluşturan koda etkisi olmaksızın, bir tür şeklini sınıf diyagramından kaldırabilirsiniz. Tür şekillerinin bir sınıf diyagramından kaldırılması yalnızca o diyagramı etkiler: Türü tanımlayan temel kod ve türü görüntüleyen diğer diyagramlar bundan etkilenmez.

1. Sınıf diyagramında, diyagramdan kaldırmak istediğiniz tür şeklini seçin.

2. **Düzenle** menüsünde **diyagramdan kaldır**' ı seçin.

     Tür şekli ve varsa bu şekle bağlı ilişkilendirme ya da devralma çizgileri bundan böyle diyagramda görünmez.

## <a name="DeleteTypeShapeAndCode"></a>Bir tür şeklini ve onun temelindeki kodu silme

1. Tasarım yüzeyinde şekle sağ tıklayın.

2. Bağlam menüsünden **kodu Sil** ' i seçin.

     Şekil diyagramdan kaldırılır ve temelini oluşturan kod projeden silinir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Sınıf diyagramları Ile çalışma (sınıf Tasarımcısı)](../ide/working-with-class-diagrams-class-designer.md) [nasıl yapılır: üye gösterimi Ile Ilişkilendirme gösterimi arasında geçiş (sınıf Tasarımcısı)](../ide/how-to-change-between-member-notation-and-association-notation-class-designer.md) [nasıl yapılır: varolan türleri görüntüleme (sınıf Tasarımcısı)](../ide/how-to-view-existing-types-class-designer.md) [türleri ve ilişkileri görüntüleme (sınıf Tasarımcısı) ](../ide/viewing-types-and-relationships-class-designer.md)
