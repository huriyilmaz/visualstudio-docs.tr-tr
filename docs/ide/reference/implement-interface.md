---
title: Arabirim uygulama
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d420bd0d42e89476696966f7eda94a19893fc23
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595559"
---
# <a name="implement-an-interface-in-visual-studio"></a>Visual Studio'da arabirimi uygulama

Bu kod oluşturma için geçerlidir:

- C#

- Visual Basic

**Ne:** hemen bir arabirim uygulamak için gereken kodu oluşturmanıza olanak tanır.

**Ne zaman:** bir arabirimden devralma istiyorsunuz.

**Neden:** bu özellik otomatik olarak tüm yöntem imzaları oluşturur ancak tüm arabirimi birer birer el ile uygulayabilirsiniz.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. İmlecinizi satırdaki bir arabirim başvurulan, ancak gerekli tüm üyeleri uygulanmadı belirten bir kırmızı dalgalı olduğu.

   - C#:

       ![Vurgulanmış kodu C#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Vurgulanmış kodu VB](media/interface-highlight-vb.png)

2. Ardından, aşağıdakilerden birini yapın:

   - **Klavye**
      - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
   - **Fare**
      - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.
      - Kırmızı dalgalı çizgi gelin ve tıklayın ![ampul hatası](media/error-bulb.png) Bu simge görünür.
      - &nbsp; ![ampul hatası](media/error-bulb.png) kırmızı dalgalı çizgi içeren satırda metin imleci ise sol kenar boşluğunda görünür simge.

3. Seçin **arabirim uygulama** aşağı açılan menüden.

   ![Uygulama arabirimi Önizleme](media/interface-preview-cs.png)

   > [!TIP]
   > - Kullanım **değişiklik önizlemesi** Önizleme pencerenin alt kısmındaki bağlantı [tüm değişiklikleri görmek için](../../ide/preview-changes.md) , oluşturulacak, seçim yapmadan önce.
   > - Kullanım **belge**, **proje**, ve **çözüm** uygulayan birden fazla sınıflar arasında uygun bir yöntem imzaları oluşturmak için Önizleme pencerenin alt kısmındaki bağlantıları arabirim.

   Arabirimin yöntem imzaları oluşturulur ve uygulanması hazırdır.

   - C#:

       ![C# arabirimi sonucu uygulayın](media/interface-result-cs.png)

   - Visual Basic:

       ![Uygulama arabirimi sonucu VB](media/interface-result-vb.png)

   > [!TIP]
   > (C# yalnızca) Kullanım **arayüzleri açıkça gerçekleştir** seçeneği her yazdığınızdan oluşturulan yöntemi ile ad çakışmalarını önlemek için arabirim adı.
   >
   > ![Arabirim uygulama açıkça neden](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
