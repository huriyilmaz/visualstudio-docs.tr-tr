---
title: Nesneleri düzen kapsayıcılarına yerleştirme
description: Bir sayfada, kılavuz, tuval, kenarlık ve Viewbox gibi nesneleri düzenlemek için kullanılan XAML Tasarımcısı düzen bölmeleri ve denetimleri hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 8233304c0fdcd0092e134e9fe690bba21b9e4a90
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037830"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>XAML Tasarımcısı’nda nesneleri düzen kapsayıcılarına yerleştirme

Bu makalede XAML Tasarımcısı yönelik düzen bölmeleri ve denetimleri açıklanmaktadır.

nesnelerin &mdash; görüntüler, düğmeler ve videolar gibi sayfa nesnelerinde görünmesini istediğiniz Imagine. Belki de satırlarda ve sütunlarda, tek bir satırda, dikey veya yatay olarak veya sabit konumlarda görünmesini isteyebilirsiniz.

Sayfanın nasıl görünebileceğini düşünmek için bir şans olduktan sonra bir Düzen paneli seçin. Nesnelerinizi eklediğiniz bir şeye ihtiyacınız olduğundan tüm sayfalar bir ile başlar. Varsayılan olarak bir **kılavuz** olur ancak bunu değiştirebilirsiniz.

Düzen panelleri bir sayfadaki nesneleri düzenlemenize yardımcı olur, ancak bundan fazlasını yapın. Bunlar, farklı ekran boyutları ve çözümleri için tasarım yapmanıza yardımcı olur. Kullanıcılar uygulamanızı çalıştırdığında, düzen panelindeki her şey, cihazlarındaki ekran ile eşleşecek şekilde yeniden boyutlandırılır. Kuşkusuz, mizanpajınızı bunu yapmak istemiyorsanız düzenin bir parçası veya tüm düzen için bu davranışı geçersiz kılabilirsiniz. Bunu denetlemek için yükseklik ve genişlik özelliklerini kullanabilirsiniz.

## <a name="layout-panels"></a>Düzen bölmeleri

Bu düzen panellerinden birini seçerek sayfanızı başlatın. Sayfanız birden fazla olabilir. Örneğin, bir **kılavuz** Düzen paneli ile başlayabilir ve ardından **kılavuzdaki** bir alana bir **StackPanel** ekleyerek, denetimleri bu öğe içinde dikey olarak düzenleyebilirsiniz.

Aşağıdaki düzen panelleri en fazla popuya kullanılır, ancak diğerleri vardır. bunların tümünü Visual Studio veya Visual Studio için Blend içindeki **varlıklar** panelinde **araç kutusu** 'nda bulabilirsiniz.

### <a name="grid"></a>Kılavuz

Nesneleri satırlar ve sütunlar halinde düzenleyin.

![Kılavuz düzen bölmesi](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png)

### <a name="uniformgrid"></a>Birlik Kılavuzu

Nesneleri eşit veya tek biçimli, ızgara bölgelerine göre düzenleyin. Bu panel, görüntülerin listesini düzenlemek için idealdir.

(Yalnızca WPF projeleri için kullanılabilir.)

![Birlik Kılavuz düzeni bölmesi](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png)

### <a name="canvas"></a>Tuval

Nesneleri istediğiniz gibi düzenleyin. Kullanıcılar uygulamanızı çalıştırdığınızda, bu öğelerin ekranda sabit konumları olur.

![Tuval düzen bölmesi](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png)

### <a name="stackpanel"></a>StackPanel

Nesneleri yatay veya dikey olarak tek bir satırda düzenleyin.

![StackPanel düzen bölmesi](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png)

### <a name="wrappanel"></a>WrapPanel

Nesneleri soldan sağa sıralı olarak düzenleyin. Panel, en sağ kenarda yer aldığında, içeriği bir sonraki satıra *kaydırır* ve bu şekilde soldan sağa, yukarıdan aşağıya doğru. Ayrıca, nesnelerin yukarıdan aşağıya, soldan sağa akmasını sağlamak için bir sarması panelinin yönünü dikey hale getirebilirsiniz.

(Yalnızca WPF projeleri için kullanılabilir.)

![WrapPanel Düzen bölmesi](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png)

### <a name="dockpanel"></a>DockPanel

Nesneleri, panelin bir kenarına kalacak veya *sabitler* olacak şekilde düzenleyin.

(Yalnızca WPF projeleri için kullanılabilir.)

![DockPanel düzen bölmesi](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png)

**Kısa bir video izleyin:** ![ Play Button ](../designers/media/bldadminconsoleinitialconfigicon.PNG) [WPF-DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Düzen denetimleri

Nesnelerinizi düzen denetimlerine de ekleyebilirsiniz. Bunlar Düzen paneli olarak zengin zengin değildir, ancak belirli senaryolar için yararlı olabilir.

Aşağıdaki düzen denetimleri en popüler, ancak diğerleri vardır. bunların tümünü Visual Studio veya Visual Studio için Blend içindeki **varlıklar** panelinde **araç kutusu** 'nda bulabilirsiniz.

### <a name="border"></a>Kenarlık

Bir nesne etrafında kenarlık, arka plan veya her ikisini birden oluşturun. Bir **kenarlığa** yalnızca bir nesne ekleyebilirsiniz. Birden fazla nesne için bir kenarlık veya arka plan uygulamak istiyorsanız, **kenarlığa** bir Düzen paneli ekleyin. Ardından, bu panele veya denetime nesne ekleyin.

![Kenarlık düzeni denetimi](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png)

### <a name="popup"></a>Açılan Pencere

Bir penceredeki kullanıcılara bilgi veya seçenek göster. Bir **açılan pencerede** yalnızca bir nesne ekleyebilirsiniz. Varsayılan olarak, bir **açılan pencere** bir **kılavuz** içerir, ancak bunu değiştirebilirsiniz.

### <a name="scrollviewer"></a>ScrollViewer

Kullanıcıların bir sayfanın sayfa veya alanını aşağı kaydırıp kaydırmaya izin vermez. Bir **ScrollViewer**'ya yalnızca bir nesne ekleyebilirsiniz, bu yüzden **Grid** veya **StackPanel** gibi bir Düzen paneli eklemek mantıklı olur.

![ScrollViewer düzen denetimi](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png)

### <a name="viewbox"></a>Viewbox

Nesneleri yakınlaştırma denetimiyle yaptığınız gibi ölçeklendirin. **Viewbox**'a yalnızca bir nesne ekleyebilirsiniz. Bu etkiyi birden fazla nesneye uygulamak istiyorsanız, **Viewbox**'a bir Düzen paneli ekleyin ve ardından denetimlerinizi bu düzen paneline ekleyin.

![ViewBox düzen denetimi](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png)

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Tasarımcısı’nda öğelerle çalışma](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [XAML Tasarımcısı’nı kullanarak bir kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
