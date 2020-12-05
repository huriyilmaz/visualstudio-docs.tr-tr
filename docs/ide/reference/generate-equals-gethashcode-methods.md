---
title: C# Equals ve GetHashCode metot geçersiz kılmaları oluşturma
description: Equals ve GetHashCode yöntemlerini oluşturmak için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f6f7ec74af21ef62079a3fef18dd39544e7b42aa
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617519"
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

   - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - Sağ üst köşedeki ![Screwdriver](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

   ![Geçersiz kılmalar önizlemesi oluştur](media/overrides-preview-cs.png)

1. **Eşittir (nesne) oluştur** veya aşağı açılan menüden **Equals ve GetHashCode oluştur '** u seçin.

1. **Üyeleri Seç** iletişim kutusunda, yöntemlerini oluşturmak istediğiniz üyeleri seçin:

    ![Geçersiz kılmalar oluştur iletişim kutusu](media/overrides-dialog-cs.png)

    > [!TIP]
    > Ayrıca, iletişim kutusunun alt kısmındaki onay kutusunu kullanarak bu iletişim kutusundan işleçler oluşturmayı tercih edebilirsiniz.

   `Equals`Ve `GetHashCode` yöntemleri varsayılan uygulamalarla oluşturulur.

   ![Yöntem sonucu üret](media/overrides-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
