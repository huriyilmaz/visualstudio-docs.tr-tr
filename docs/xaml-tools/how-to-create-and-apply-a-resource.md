---
title: Kaynak oluşturma ve uygulama
description: Öğeler için stilleri ve şablonları depolaya XAML Tasarımcısı için kaynak oluşturma ve uygulama hakkında bilgi edinebilirsiniz.
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
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: ff5ed15a39df75d01ea2ac1be9abf03df04393c4a573ef47f28deef7251e4af0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121365398"
---
# <a name="how-to-create-and-apply-a-resource"></a>Kaynak oluşturma ve uygulama

XAML Tasarımcısı öğeleri için stiller ve şablonlar, kaynaklar olarak adlandırılan yeniden kullanılabilir varlıklarda depolanır. Stiller, öğe özelliklerini ayarlamaya ve birden çok öğede tutarlı bir görünüm elde etmek için bu ayarları yeniden kullanmanıza olanak sağlar. [ControlTemplate,](xref:Windows.UI.Xaml.Controls.ControlTemplate) bir denetimin görünümünü tanımlar ve kaynak olarak da uygulanabilir. Daha fazla bilgi için [bkz. XAML stilleri](/windows/uwp/design/controls-and-patterns/xaml-styles) [ve Denetim şablonları.](/windows/uwp/design/controls-and-patterns/control-templates)

Mevcut bir özellik olan [Style](xref:Windows.UI.Xaml.Style)veya [ControlTemplate'dan](xref:Windows.UI.Xaml.Controls.ControlTemplate)yeni  bir kaynak ekleyebilirsiniz. Kaynak Oluştur iletişim kutusu, kaynağı uygulama düzeyinde, belge düzeyinde veya öğe düzeyinde tanımlamanızı sağlar. Bu düzeyler kaynağı nerede kullanabileceğiniz belirler. Örneğin, kaynağı öğe düzeyinde tanımlarsanız, kaynak yalnızca kaynağı oluşturduğunuz öğeye uygulanabilir. Ayrıca, kaynağı başka bir projede yeniden [kullanabileceğiniz](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references)ayrı bir dosya olan kaynak sözlüğünde depolamayı da seçebilirsiniz.

## <a name="create-a-new-resource"></a>Yeni kaynak oluşturma

1. Bir XAML dosyası XAML Tasarımcısı, bir öğe oluşturun veya Belge Ana Hat penceresinde bir öğe seçin.

2. Özellikler **penceresinde,** bir özellik değerinin sağ yanında kutu simgesi olarak görünen özellik işaretçisini seçin ve ardından Yeni Kaynağa **Dönüştür'e tıklayın.** Beyaz kutu simgesi varsayılan bir değeri, siyah kutu simgesi ise genellikle yerel bir kaynağın uygulandığını gösterir.

     Bir kaynak oluşturmak için uygun bir iletişim kutusu görüntülenir. Bu iletişim kutusu, fırçadan kaynak 700000000000000000000000000000000

     ![Kaynak Oluştur İletişim Kutusu](../designers/media/xaml_create_resource.png)

3. Ad **(Anahtar)** kutusuna bir anahtar adı girin. Bu, diğer öğelerin kaynağa başvurulmalarını istediğiniz zaman kullanabileceğiniz addır.

4. Içinde **tanımla** altında kaynağın nerede tanımlanmalıdır? seçeneğini belirtin:

    - Kaynağı uygulamanıza herhangi bir belge için kullanılabilir hale yapmak için Uygulama'ya **tıklayın.**

    - Kaynağı yalnızca geçerli belge için kullanılabilir yapmak için Bu **belge'yi seçin.**

    - Kaynağı yalnızca kaynağı oluşturduğunuz öğenin veya alt öğelerinin kullanımına bırakmak için Bu belge'yi seçin ve açılan listede öğesi: **name öğesini** **seçin.**

    - Kaynağı diğer projelerde [yeniden ekleyebilirsiniz bir](/windows/uwp/design/controls-and-patterns/resourcedictionary-and-xaml-resource-references) kaynak sözlüğü dosyasında tanımlamak için Kaynak sözlüğü **'ne tıklayın.** Ardından, açılan listeden **StandardStyles.xaml** gibi mevcut bir kaynak sözlüğü dosyasını seçin.

5. Kaynağı **oluşturmak** ve kaynağı oluşturduğunuz öğeye uygulamak için Tamam düğmesini seçin.

## <a name="apply-a-resource-to-an-element-or-property"></a>Bir öğeye veya özel kaynağa kaynak uygulama

1. Belge Ana Hat penceresinde, kaynak uygulamak istediğiniz öğeyi seçin.

2. Aşağıdakilerden birini yapın:

   - Özelliğine kaynak uygulama. Özellikler **penceresinde,** özellik değerinin yanındaki özellik işaretçisini  seçin, Yerel Kaynak veya Sistem Kaynağı'ı seçin ve sonra görüntülenen listeden kullanılabilir bir kaynak seçin.

      Görmeyi beklediğiniz bir kaynağı görmüyorsanız, bunun nedeni kaynağın türünün özelliğin türüyle eşleşmesi olabilir.

   - Bir denetime stil veya denetim şablonu kaynağı uygulama. Belge Ana Hat penceresinde bir denetim için sağ tıklama menüsünü  (bağlam menüsü) açın, Şablonu Düzenle veya Ek Şablonları Düzenle'yi **seçin,** Kaynağı Uygula'yı seçin ve sonra görüntülenen listeden denetim şablonunun adını seçin.

     > [!NOTE]
     > **Şablonu Düzenle** denetim şablonları uygular. **Ek Şablonları Düzenle diğer** şablon türlerini uygular.

     Uyumlu olduğu her yerde kaynakları uygulayabilirsiniz. Örneğin, [textBox](xref:Windows.UI.Xaml.Controls.TextBox) denetimi için **Foreground** özelliğine fırça kaynağı uygulayabilirsiniz.

## <a name="edit-a-resource"></a>Kaynağı düzenleme

1. Çalışma panosunda veya Belge Ana Hat penceresinde bir öğe seçin.

2. Özellikler penceresinde özelliğin sağ tarafından Varsayılan veya  Yerel özellik işaretçisini  seçin ve ardından Kaynağı Düzenle iletişim kutusunu açmak için **Kaynağı Düzenle'yi** seçin.

3. Kaynağın seçeneklerini değiştirme.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
