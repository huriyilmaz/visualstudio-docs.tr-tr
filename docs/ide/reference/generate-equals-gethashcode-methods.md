---
title: C# Equals ve GetHashCode metot geçersiz kılmaları oluşturma
description: Equals ve GetHashCode yöntemlerini oluşturmak için hızlı eylemler ve yeniden düzenlemeler menüsünü nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: c89c5296ced84b887c7acc5d190030cb9710305b5f066dea7bee008e6f6245b9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372627"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Visual Studio içinde Equals ve GetHashCode metot geçersiz kılmaları oluşturma

Bu kod üretimi için geçerlidir:

- C#

**Ne:** **Eşittir** ve **GetHashCode** yöntemleri oluşturmanıza olanak sağlar.

**Ne zaman:** Bellekte nesne konumu yerine bir veya daha fazla alan tarafından Karşılaştırılacak bir tür varsa bu geçersiz kılmaları oluşturun.

**Kaydol**

- Bir değer türü uygulıyoruz, **Equals** metodunu geçersiz kılmayı düşünmelisiniz. Bunu yaptığınızda ValueType üzerindeki Equals yönteminin varsayılan uygulamasında daha fazla performans elde edebilirsiniz.

- Bir başvuru türü uygulamadıysanız, türü nokta, dize, BigNumber ve benzeri bir temel tür gibi görünüyorsa **eşittir** yöntemini geçersiz kılmayı göz önünde bulundurmanız gerekir.

- Bir türün Karma tabloda düzgün çalışmasına izin vermek için **GetHashCode** metodunu geçersiz kılın. [Eşitlik işleçleri](/dotnet/standard/design-guidelines/equality-operators)hakkında daha fazla rehberlik okuyun.

## <a name="how-to"></a>Nasıl yapılır

1. İmlecinizi tür bildiricinizin satırına bir yere yerleştirin.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   Kodunuz aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

   ![Oluşturulan yöntemin uygulanacağı vurgulanan kodun ekran görüntüsü](media/overrides-highlight-cs.png)

   > [!TIP]
   > Tür adını seç ' e çift tıklamayın veya menü seçeneği kullanılamaz. İmleci satıra bir yere yerleştirmeniz yeterlidir.

1. Sonra, aşağıdaki eylemlerden birini seçin:

   - **CTRL** tuşuna basın + **.** **hızlı eylemleri ve yeniden düzenlemeler** menüsünü tetiklemek için.

   - Sağ tıklayın ve **Hızlı Eylemler ve yeniden düzenlemeler** menüsünü seçin.

   - Sağ üst köşedeki ![Visual Studio hızlı eylemler screwdriver simgesinin ekran görüntüsü](../media/screwdriver-icon.png) Sol kenar boşluğunda görünen simge.

1. Açılan menüde **eşittir (nesne) oluştur** veya **eşittir ve GetHashCode oluştur**' u seçin.

   ![Geçersiz kılmalar Oluştur açılır menüsünün ekran görüntüsü](media/overrides-preview-cs.png)

1. **Üyeleri Seç** iletişim kutusunda, yöntemlerini oluşturmak istediğiniz üyeleri seçin:

    ![Geçersiz kılmalar oluştur iletişim kutusu](media/overrides-dialog-cs.png)

    > [!TIP]
    > Ayrıca, iletişim kutusunun alt kısmındaki onay kutusunu kullanarak bu iletişim kutusundan işleçler oluşturmayı tercih edebilirsiniz.

   `Equals`Ve `GetHashCode` yöntemleri, aşağıdaki kodda gösterildiği gibi varsayılan uygulamalarla oluşturulmuştur:

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   Kodunuz aşağıdaki ekran görüntüsüne benzer şekilde görünmelidir:

   ![Oluşturulan metodun sonucunun ekran görüntüsü](media/overrides-result-cs.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kod oluşturma](../code-generation-in-visual-studio.md)
- [Değişiklikleri Önizleme](../../ide/preview-changes.md)
