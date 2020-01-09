---
title: Equals C# ve GetHashCode metot geçersiz kılmaları oluştur
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569289"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Visual Studio 'da Equals ve GetHashCode metot geçersiz kılmaları oluşturma

Bu kod oluşturma için geçerlidir:

- C#

**Ne:** **Eşittir** ve **GetHashCode** yöntemleri oluşturmanıza olanak sağlar.

**Ne zaman:** Bellekte nesne konumu yerine bir veya daha fazla alan tarafından Karşılaştırılacak bir tür varsa bu geçersiz kılmaları oluşturun.

**Kaydol**

- Bir değer türü uygulamadıysanız, ValueType üzerindeki Equals yönteminin varsayılan uygulamasında daha fazla performans elde etmek için **Equals** metodunu geçersiz kılmayı göz önünde bulundurmanız gerekir.

- Bir başvuru türü uygulamadıysanız, türü nokta, dize, BigNumber, vb. gibi bir temel tür gibi görünüyorsa **eşittir** yöntemini geçersiz kılmayı göz önünde bulundurmanız gerekir.

- Bir türün Karma tabloda düzgün çalışmasına izin vermek için **GetHashCode** metodunu geçersiz kılın. [Eşitlik işleçleri](/dotnet/standard/design-guidelines/equality-operators)hakkında daha fazla rehberlik okuyun.

## <a name="how-to"></a>Nasıl Yapılır Konuları

1. İmlecinizi tür bildiricinizin satırına bir yere yerleştirin.

   ![Vurgulanan kod](media/overrides-highlight-cs.png)

   > [!TIP]
   > Tür adını seç ' e çift tıklamayın veya menü seçeneği kullanılamaz. İmleci satıra bir yere yerleştirmeniz yeterlidir.

1. Ardından, aşağıdakilerden birini yapın:

   - Tuşuna **Ctrl**+ **.** Tetikleyici için **hızlı Eylemler ve yeniden düzenlemeler** menüsü.

   - Sağ tıklayıp **hızlı Eylemler ve yeniden düzenlemeler** menüsü.

   - &nbsp; ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Geçersiz kılmalar önizlemesi oluştur](media/overrides-preview-cs.png)

1. **Eşittir (nesne) oluştur** veya aşağı açılan menüden **Equals ve GetHashCode oluştur '** u seçin.

1. **Üyeleri Seç** iletişim kutusunda, yöntemlerini oluşturmak istediğiniz üyeleri seçin:

    ![Geçersiz kılmalar oluştur iletişim kutusu](media/overrides-dialog-cs.png)

    > [!TIP]
    > Ayrıca, iletişim kutusunun alt kısmındaki onay kutusunu kullanarak bu iletişim kutusundan işleçler oluşturmayı tercih edebilirsiniz.

   `Equals` ve `GetHashCode` yöntemleri varsayılan uygulamalarla oluşturulur.

   ![Yöntem sonucu üret](media/overrides-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
