---
title: Kaynak oluşturma ve uygulama
description: Öğeleri için stilleri ve şablonları depolayabilmeniz ve yeniden kullanabilmeniz için XAML Tasarımcısı bir kaynağı oluşturma ve uygulama hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b6c6c243896370cc97b8a85d5de520c4c033d49b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971615"
---
# <a name="how-to-create-and-apply-a-resource"></a>Kaynak oluşturma ve uygulama

XAML Tasarımcısı öğeler için stiller ve şablonlar, kaynaklar adlı yeniden kullanılabilir varlıklarda depolanır. Stiller, öğe özelliklerini ayarlamanıza ve bu ayarları birden çok öğe arasında tutarlı bir görünüm için yeniden kullanmanıza olanak sağlar. Bir [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate) , bir denetimin görünümünü tanımlar ve kaynak olarak da uygulanabilir. Daha fazla bilgi için bkz. [xaml stilleri](/windows/uwp/design/controls-and-patterns/xaml-styles) ve [Denetim şablonları](/windows/uwp/design/controls-and-patterns/control-templates).

Varolan bir özellikten, [stille](xref:Windows.UI.Xaml.Style)veya [ControlTemplate](xref:Windows.UI.Xaml.Controls.ControlTemplate)'ten yeni bir kaynak oluşturduğunuzda **kaynak oluştur** iletişim kutusu, kaynağı uygulama düzeyinde, belge düzeyinde veya öğe düzeyinde tanımlamanızı sağlar. Bu düzeyler, kaynağı nerede kullanacağınızı tespit edebilir. Örneğin, kaynağı öğe düzeyinde tanımlarsanız, kaynak yalnızca sizin oluşturduğunuz öğe için uygulanabilir. Kaynağı, başka bir projede tekrar kullanabileceğiniz ayrı bir dosya olan bir [kaynak sözlüğünde](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references)depolamayı da tercih edebilirsiniz.

## <a name="create-a-new-resource"></a>Yeni kaynak oluşturma

1. XAML dosyası XAML Tasarımcısı açın, bir öğesi oluşturun veya belge anahattı penceresinde bir öğe seçin.

2. **Özellikler** penceresinde, özellik değerinin sağında bir kutu simgesi olarak görünen Özellik işaretçisini seçin ve ardından **yeni kaynağa Dönüştür**' ü seçin. Beyaz kutu simgesi bir varsayılan değeri gösterir ve bir siyah kutu sembolü genellikle yerel bir kaynağın uygulandığını belirtir.

     Bir kaynak oluşturmak için uygun bir iletişim kutusu görüntülenir. Fırçayla kaynak oluşturduğunuzda bu iletişim kutusu görüntülenir:

     ![Kaynak oluştur Iletişim kutusu](../designers/media/xaml_create_resource.png)

3. **Ad (anahtar)** kutusuna bir anahtar adı girin. Bu, diğer öğelerin kaynağa başvuruda bulunmasını istediğinizde kullanabileceğiniz addır.

4. **Içinde tanımla** altında kaynağın tanımlanmasını istediğiniz yeri belirten seçeneği belirleyin:

    - Kaynağı uygulamanızdaki herhangi bir belge için kullanılabilir hale getirmek için **uygulama**' yı seçin.

    - Kaynağı yalnızca geçerli belge için kullanılabilir hale getirmek için **Bu belgeyi** seçin.

    - Kaynağı yalnızca kaynağı veya onun alt öğelerini oluşturduğunuz öğe için kullanılabilir hale getirmek için, **Bu belgeyi** seçin ve açılan listeden **öğe**: **ad**' ı seçin.

    - Kaynağı diğer projelerde yeniden kullanılabilen bir [kaynak sözlüğü](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references) dosyasında tanımlamak için **kaynak sözlüğü**' ne tıklayın. Ardından, açılan listede **StandardStyles. xaml** gibi var olan bir kaynak sözlüğü dosyası seçin.

5. Kaynağı oluşturmak için **Tamam** düğmesini seçin ve bunu oluşturduğunuz öğeye uygulayın.

## <a name="apply-a-resource-to-an-element-or-property"></a>Bir öğeye veya özelliğe kaynak uygulama

1. Belge Anahattı penceresinde, kaynak uygulamak istediğiniz öğeyi seçin.

2. Aşağıdakilerden birini yapın:

   - Bir özelliğe kaynak uygulayın. **Özellikler** penceresinde, özellik değerinin yanındaki Özellik işaretçisini seçin, **yerel kaynak** veya **sistem kaynağı**' nı seçin ve açılan listeden kullanılabilir bir kaynak seçin.

      Görmeyi düşündüğünüz bir kaynağı görmüyorsanız, bunun nedeni kaynağın türünün özelliğin türüyle eşleşmemesi olabilir.

   - Bir denetime stil veya denetim şablonu kaynağı uygulayın. Belge Anahattı penceresinde bir denetim için sağ tıklama menüsünü (bağlam menüsü) açın, **Şablonu Düzenle** veya **Ek Şablonları Düzenle**' yi seçin, **kaynağı Uygula**' yı seçin ve açılan listeden denetim şablonunun adını seçin.

     > [!NOTE]
     > **Şablonu Düzenle** denetim şablonlarını uygular. **Ek Şablonları Düzenle** diğer şablon türlerini uygular.

     Kaynakları, uyumlu oldukları yerde uygulayabilirsiniz. Örneğin, bir [TextBox](xref:Windows.UI.Xaml.Controls.TextBox) denetiminin **ön plan** özelliğine bir fırça kaynağı uygulayabilirsiniz.

## <a name="edit-a-resource"></a>Bir kaynağı düzenleme

1. Çalışma yüzeyinde veya belge anahattı penceresinde bir öğe seçin.

2. **Özellikler** penceresinde özelliğin sağında varsayılan veya yerel özellik işaretçisini seçin ve **ardından Kaynağı Düzenle iletişim kutusunu** açmak için **Kaynağı Düzenle** ' yi seçin.

3. Kaynağın seçeneklerini değiştirin.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
