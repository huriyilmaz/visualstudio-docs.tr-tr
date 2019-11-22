---
title: Kaynak oluşturma ve uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.CreateResource
- VS.XamlDesigner.EditResource
ms.assetid: 3ff4006d-659d-4073-9a41-06ff85e6cfdf
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ab048fe69ca89086e9811e5277dccb86aeee6194
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300866"
---
# <a name="how-to-create-and-apply-a-resource"></a>Kaynak oluşturma ve uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML Tasarımcısı öğeler için stiller ve şablonlar, kaynaklar adlı yeniden kullanılabilir varlıklarda depolanır. Stiller, öğe özelliklerini ayarlamanıza ve bu ayarları birden çok öğe arasında tutarlı bir görünüm için yeniden kullanmanıza olanak sağlar. Bir [ControlTemplate](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.controltemplate.aspx) , bir denetimin görünümünü tanımlar ve kaynak olarak da uygulanabilir. Daha fazla bilgi için bkz. [hızlı başlangıç: stil denetimleri](https://go.microsoft.com/fwlink/?LinkID=248239) ve [hızlı başlangıç: denetim şablonları](https://go.microsoft.com/fwlink/?LinkID=247982).

 Mevcut bir özellikten, [stille](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.style.aspx)veya `ControlTemplate`yeni bir kaynak oluşturduğunuzda **kaynak oluştur** iletişim kutusu, kaynağı uygulama düzeyinde, belge düzeyinde veya öğe düzeyinde tanımlamanızı sağlar. Bu düzeyler, kaynağı nerede kullanacağınızı tespit edebilir. Örneğin, kaynağı öğe düzeyinde tanımlarsanız, kaynak yalnızca sizin oluşturduğunuz öğe için uygulanabilir. Ayrıca, yeniden başka bir projede kullanabileceğiniz ayrı bir dosya olan bir kaynak sözlüğünde kaynağı saklamayı da seçebilirsiniz.

### <a name="to-create-a-new-resource"></a>Yeni bir kaynak oluşturmak için

1. XAML dosyası XAML Tasarımcısı açın, bir öğesi oluşturun veya belge anahattı penceresinde bir öğe seçin.

2. Özellikler penceresi, özellik değerinin sağında bir kutu simgesi olarak görünen Özellik işaretçisini seçin ve ardından **yeni kaynağa Dönüştür**' ü seçin. Beyaz kutu simgesi bir varsayılan değeri gösterir ve bir siyah kutu sembolü genellikle yerel bir kaynağın uygulandığını gösterir

     Bir kaynak oluşturmak için uygun bir iletişim kutusu görüntülenir. Fırçayla kaynak oluşturduğunuzda bu iletişim kutusu görüntülenir:

     ![Kaynak oluştur Iletişim kutusu](../designers/media/xaml-create-resource.png "xaml_create_resource")

3. **Ad (anahtar)** kutusuna bir anahtar adı girin. Bu, diğer öğelerin kaynağa başvuruda bulunmasını istediğinizde kullanabileceğiniz addır.

4. **Içinde tanımla**altında kaynağın tanımlanmasını istediğiniz yeri belirten seçeneği belirleyin:

    - Kaynağı uygulamanızdaki herhangi bir belge için kullanılabilir hale getirmek için **uygulama**' yı seçin.

    - Kaynağı yalnızca geçerli belge için kullanılabilir hale getirmek için **Bu belgeyi**seçin.

    - Kaynağı yalnızca kaynağı veya onun alt öğelerini oluşturduğunuz öğe için kullanılabilir hale getirmek için, **Bu belgeyi**seçin ve açılan listeden *öğe*: *ad*' ı seçin.

    - Kaynağı diğer projelerde yeniden kullanılabilen bir kaynak sözlüğü dosyasında tanımlamak için **kaynak sözlüğü**' ne tıklayın ve ardından aşağı açılan listede **StandardStyles. xaml**gibi var olan bir kaynak sözlüğü dosyası seçin.

5. Kaynağı oluşturmak için **Tamam** düğmesini seçin ve bunu oluşturduğunuz öğeye uygulayın.

### <a name="to-apply-a-resource-to-an-element-or-property"></a>Bir öğeyi veya özelliği bir kaynağı uygulamak için

1. Belge Anahattı penceresinde, kaynak uygulamak istediğiniz öğeyi seçin.

2. Aşağıdakilerden birini yapın:

   - Bir özelliğe kaynak uygulayın. Özellikler penceresi, özellik değerinin yanındaki Özellik işaretçisini seçin, **yerel kaynak** veya **sistem kaynağı**' nı seçin ve açılan listeden kullanılabilir bir kaynak seçin.

      Görmeyi düşündüğünüz bir kaynağı görmüyorsanız, bunun nedeni kaynağın türünün özelliğin türüyle eşleşmemesi olabilir.

   - Bir denetime stil veya denetim şablonu kaynağı uygulayın. Belge Anahattı penceresinde bir denetimin bağlam menüsünü açın, **Şablonu Düzenle** veya **Ek Şablonları Düzenle**' yi seçin, **kaynağı Uygula**' yı seçin ve ardından görüntülenen listeden denetim şablonunun adını seçin.

     > [!NOTE]
     > **Şablonu Düzenle** denetim şablonlarını uygulamak için kullanılır. Diğer şablon türlerini uygulamak için **Ek Şablonları Düzenle** kullanılır.

     Kaynaklar, uyumlu oldukları her yerde uygulanabilir. Örneğin, bir fırça kaynağı bir <xref:Windows.UI.Xaml.Controls.TextBox> denetiminin **ön plan** özelliğine uygulanabilir.

### <a name="to-edit-a-resource"></a>Bir kaynağı düzenlemek için

1. Çalışma yüzeyinde veya belge anahattı penceresinde bir öğe seçin.

2. Özellikler penceresi özelliğin sağında varsayılan veya yerel özellik işaretçisini seçin ve **ardından Kaynağı Düzenle iletişim kutusunu** açmak Için **Kaynağı Düzenle** ' yi seçin.

3. Kaynağın seçeneklerini değiştirin.

## <a name="see-also"></a>Ayrıca Bkz.
 [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
