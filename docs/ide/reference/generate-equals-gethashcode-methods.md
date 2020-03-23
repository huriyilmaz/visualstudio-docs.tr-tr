---
title: C# Eşittir ve GetHashCode Yöntemi Overrides oluşturun
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569289"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Visual Studio'da Eşitler ve GetHashCode yöntemi geçersiz kılar

Bu kod oluşturma için geçerlidir:

- C#

**Ne:** **Eşitler** ve **GetHashCode** yöntemleri oluşturmanıza olanak tanır.

**Ne zaman:** Bellekteki nesne konumu yerine bir veya daha fazla alanla karşılaştırılması gereken bir tür olduğunda bu geçersiz kılmaları oluşturun.

**Neden:**

- Bir değer türü uyguluyorsanız, Değer Türü'nde Eşitler yönteminin varsayılan uygulaması üzerinde daha fazla performans elde etmek için **Eşitler** yöntemini geçersiz kılmayı düşünmelisiniz.

- Bir başvuru türü uyguluyorsanız, türünüz Point, String, BigNumber gibi bir taban türüne **benziyorsa Eşitler** yöntemini geçersiz kılmayı düşünmelisiniz.

- Bir türün karma tabloda doğru çalışmasına izin vermek için **GetHashCode** yöntemini geçersiz kılın. [Eşitlik operatörleri](/dotnet/standard/design-guidelines/equality-operators)hakkında daha fazla rehberlik okuyun.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi tür bildirgenizin satırında bir yere yerleştirin.

   ![Vurgulanan kod](media/overrides-highlight-cs.png)

   > [!TIP]
   > Tür adını çift tıklatmayın, yoksa menü seçeneği kullanılamaz. İmleci hatta bir yere koy.

1. Ardından, aşağıdakilerden birini yapın:

   - **Ctrl**+tuşuna**basın.** **Hızlı Eylemler ve Refactorings** menüsünü tetiklemek için.

   - Hızlı Eylemler ve **Yeniden Faktörler** menüsünü sağ tıklatın ve seçin.

   - &nbsp; ![Tornavida](../media/screwdriver-icon.png) sol kenar boşluğunda görünen simge.

   ![Önizlemeyi geçersiz kılmaoluşturma](media/overrides-preview-cs.png)

1. Açılan menüden **Eşitleri Oluştur(nesne)** veya **Eşitleri Oluştur ve GetHashCode'u** seçin.

1. Üye **Seç** iletişim kutusunda, aşağıdaki yöntemleri oluşturmak istediğiniz üyeleri seçin:

    ![Oluşturma iletişim kutusunu geçersiz kılar](media/overrides-dialog-cs.png)

    > [!TIP]
    > Ayrıca, iletişim kutusunun altındaki onay kutusunu kullanarak bu iletişim kutusundan işleçler oluşturmayı da seçebilirsiniz.

   Ve `Equals` `GetHashCode` yöntemleri varsayılan uygulamalar ile oluşturulur.

   ![Yöntem sonucu oluşturma](media/overrides-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
