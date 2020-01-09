---
title: Alan, özellik, yerel değişken oluştur
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b554aa5586150942c0fc7d7aeada9356a67029ca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595611"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Visual Studio'da bir alan, özelliği veya yerel değişken oluştur

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** hemen önce bildirilmemiş alan, özelliği veya yerel kodu oluşturmanıza olanak tanır.

**Ne zaman:** yazarken, yeni bir alan, özelliği veya yerel tanıtır ve düzgün bir şekilde, otomatik olarak bildirmek istiyor.

**Neden:** ancak bu özellik bildirimi oluşturmak ve otomatik olarak yazın, kullanmadan önce alan, özelliği veya yerel bildirebilirsiniz.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. İmlecinizi satıra Yerleştir kırmızı dalgalı olduğu. Kırmızı dalgalı çizgi, alan, yerel veya henüz mevcut olmayan özellik gösterir.

   - C#:

       ![Vurgulanmış kodu C#](media/field-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu VB](media/field-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - Kırmızı dalgalı çizgi gelin ve tıklayın ![ampul hatası](media/error-bulb.png) Bu simge görünür.
      - &nbsp; ![ampul hatası](media/error-bulb.png) kırmızı dalgalı çizgi içeren satırda metin imleci ise sol kenar boşluğunda görünür simge.

      ![Alan/özellik/yerel Önizleme oluşturma](media/field-preview-cs.png)

3. Bir oluşturma seçenekleri, aşağı açılan menüden seçin.

   > [!TIP]
   > Kullanım **değişiklik önizlemesi** Önizleme pencerenin alt kısmındaki bağlantı [tüm değişiklikleri görmek için](../../ide/preview-changes.md) , oluşturulacak, seçim yapmadan önce.

   Alan, özelliği veya yerel, kullanımdan çıkarılan türü ile oluşturulur.

   - C#:

       ![Yöntem sonuç C# oluştur](media/field-result-cs.png)

   - Visual Basic:

       ![Yöntem sonuç VB oluştur](media/field-result-vb.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
