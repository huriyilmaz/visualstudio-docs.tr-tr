---
title: Equals C# ve GetHashCode metot geçersiz kılmaları oluştur
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e70593bc04b576237a7f9f0f51ae6c3d37e40a88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660036"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Visual Studio 'da Equals ve GetHashCode metot geçersiz kılmaları oluşturma

Bu kod üretimi için geçerlidir:

- C#

**Ne:** **Eşittir** ve **GetHashCode** yöntemleri oluşturmanıza olanak sağlar.

**Ne zaman:** Bellekte nesne konumu yerine bir veya daha fazla alan tarafından Karşılaştırılacak bir tür varsa bu geçersiz kılmaları oluşturun.

**Kaydol**

- Bir değer türü uygulamadıysanız, ValueType üzerindeki Equals yönteminin varsayılan uygulamasında daha fazla performans elde etmek için **Equals** metodunu geçersiz kılmayı göz önünde bulundurmanız gerekir.

- Bir başvuru türü uygulamadıysanız, türü nokta, dize, BigNumber, vb. gibi bir temel tür gibi görünüyorsa **eşittir** yöntemini geçersiz kılmayı göz önünde bulundurmanız gerekir.

- Bir türün Karma tabloda düzgün çalışmasına izin vermek için **GetHashCode** metodunu geçersiz kılın. [Eşitlik işleçleri](/dotnet/standard/design-guidelines/equality-operators)hakkında daha fazla rehberlik okuyun.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi tür bildiricinizin satırına bir yere yerleştirin.

   ![Vurgulanan kod](media/overrides-highlight-cs.png)

   > [!TIP]
   > Tür adını seç ' e çift tıklamayın veya menü seçeneği kullanılamaz. İmleci satıra bir yere yerleştirmeniz yeterlidir.

1. Sonra, aşağıdakilerden birini yapın:

   - **Ctrl** + tuşuna basın **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - &nbsp; ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Geçersiz kılmalar önizlemesi oluştur](media/overrides-preview-cs.png)

1. **Eşittir (nesne) oluştur** veya aşağı açılan menüden **Equals ve GetHashCode oluştur '** u seçin.

1. **Üyeleri Seç** iletişim kutusunda, yöntemlerini oluşturmak istediğiniz üyeleri seçin:

    ![Geçersiz kılmalar oluştur iletişim kutusu](media/overrides-dialog-cs.png)

    > [!TIP]
    > Ayrıca, iletişim kutusunun alt kısmındaki onay kutusunu kullanarak bu iletişim kutusundan işleçler oluşturmayı tercih edebilirsiniz.

   @No__t_0 ve `GetHashCode` yöntemleri varsayılan uygulamalarla oluşturulur.

   ![Yöntem sonucu üret](media/overrides-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)