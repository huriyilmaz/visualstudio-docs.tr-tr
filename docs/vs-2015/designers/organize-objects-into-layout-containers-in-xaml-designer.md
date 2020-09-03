---
title: Nesneleri XAML Tasarımcısı düzen kapsayıcılarına göre düzenleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 29c80c38-0fa3-48d6-b3a8-3b864f482e44
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 90c30f27ada6673608a1c5cf9500207f9aeb2d72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664191"
---
# <a name="organize-objects-into-layout-containers-in-xaml-designer"></a>XAML Tasarımcısı’nda nesneleri düzen kapsayıcılarına yerleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesnelerin sayfada görünmesini istediğiniz yeri düşünün; görüntüler, düğmeler ve videolar gibi nesneler. Belki de satırlarda ve sütunlarda, tek bir satırda, dikey veya yatay olarak veya sabit konumlarda görünmesini isteyebilirsiniz.

 Sayfanın nasıl görünebileceğini düşünmek için bir şans olduktan sonra bir Düzen paneli seçin. Nesnelerinizi eklemek için bir şey olması gerektiğinden tüm sayfalar bir ile başlar. Varsayılan olarak, bir **kılavuz** olur ancak bunu değiştirebilirsiniz.

 Düzen panelleri bir sayfadaki nesneleri düzenlemenize yardımcı olur, ancak bundan fazlasını yapın. Bunlar, farklı ekran boyutları ve çözümleri için tasarım yapmanıza yardımcı olur. Kullanıcılar uygulamanızı çalıştırdığında, düzen panelindeki her şey, cihazlarındaki ekran ile eşleşecek şekilde yeniden boyutlandırılır. Kuşkusuz, mizanpajınızı bunu yapmak istemiyorsanız, düzenin bir parçası veya tüm düzen için bu davranışı geçersiz kılabilirsiniz. Bunu denetlemek için yükseklik ve genişlik özelliklerini kullanabilirsiniz.

 Bu sayfada, düzen bölmeleri ve denetimleri açıklanmakta ve bunları kullanmaya başlamanıza yardımcı olacak kısa videolar yer alır.

> [!NOTE]
> Videolardan bazıları, Visual Studio ve Visual Studio için Blend aynı XAML tasarımcısını kullanan Blend veya Expression Blend öğesine başvurabilir.

## <a name="layout-panels"></a>Düzen bölmeleri
 Bu düzen panellerinden birini seçerek sayfanızı başlatın. Sayfanız birden fazla olabilir. Örneğin, bir **kılavuz** Düzen paneli ile başlayabilir ve ardından **kılavuzdaki** bir alana bir **StackPanel** ekleyerek, denetimleri bu öğe içinde dikey olarak düzenleyebilirsiniz.

 Aşağıdaki düzen panelleri en fazla popuya kullanılır, ancak diğerleri vardır. Bunları **varlıklar** panelinde bulabilirsiniz.

- [Kılavuz](#Grid)

- [Birlik Kılavuzu](#Uniform)

- [Tuval](#Canvas)

- [StackPanel](#Stack)

- [WrapPanel](#Wrap)

- [DockPanel](#Dock)

### <a name="grid"></a><a name="Grid"></a> Çizgisi
 Nesneleri satırlar ve sütunlar halinde düzenleyin.

 ![](../designers/media/98b234b2-ac3b-441f-9136-98375fee87b7.png "98b234b2-ac3b-441f-9136-98375fee87b7")

 **Kısa bir video izleyin:** [Kılavuzlar kullanarak](http://www.popscreen.com/v/6A4hj/Microsoft-Expression-Blend-Using-Grids) ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon")

### <a name="uniformgrid"></a><a name="Uniform"></a> Birlik Kılavuzu
 Nesneleri eşit veya tek biçimli, ızgara bölgelerine göre düzenleyin. Bu panel, görüntülerin listesini düzenlemek için idealdir.

 ![](../designers/media/928b9284-a7e8-4678-875a-656b80b78076.png "928b9284-a7e8-4678-875a-656b80b78076")

 (Yalnızca WPF projeleri için kullanılabilir)

 **Kısa bir video izleyin:** [bir birlik kılavuzuyla çalışan](http://www.popscreen.com/v/6A4iq/Microsoft-Expression-Blend-Working-with-a-UniformGrid) ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon")

### <a name="canvas"></a><a name="Canvas"></a> Tuvalinin
 Nesneleri istediğiniz gibi düzenleyin. Kullanıcılar uygulamanızı çalıştırdığınızda, bu öğelerin ekranda sabit konumları olur.

 ![](../designers/media/e1ae27f0-3a57-454e-b580-877dcea8836d.png "e1ae27f0-3a57-454e-b580-877dcea8836d")

 **Kısa bir video izleyin:** [tuvalle çalışan](http://www.popscreen.com/v/6A4hT/Microsoft-Expression-Blend-Working-with-the-Canvas) ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon")

### <a name="stackpanel"></a><a name="Stack"></a> StackPanel
 Nesneleri yatay veya dikey olarak tek bir satırda düzenleyin.

 ![](../designers/media/a85a7b57-b0a8-495e-b985-f0291e41d093.png "a85a7b57-b0a8-495e-b985-f0291e41d093")

 **Kısa bir video izleyin:** [StackPanel ve WrapPanel Ile çalışan](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel) ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon")

### <a name="wrappanel"></a><a name="Wrap"></a> WrapPanel
 Nesneleri soldan sağa sıralı olarak düzenleyin. Panel, en sağ kenarda yer aldığında, içeriği bir sonraki satıra *kaydırır* ve bu şekilde soldan sağa, yukarıdan aşağıya doğru. Ayrıca, nesnelerin yukarıdan aşağıya, soldan sağa akmasını sağlamak için bir sarması panelinin yönünü dikey hale getirebilirsiniz.

 (Yalnızca WPF projeleri için kullanılabilir)

 ![](../designers/media/b1c415fb-9a32-4a18-aa0b-308fca994ac9.png "b1c415fb-9a32-4a18-aa0b-308fca994ac9")

 **Kısa bir video izleyin:** [StackPanel ve WrapPanel Ile çalışan](http://www.popscreen.com/v/6A4i5/Microsoft-Expression-Blend-Using-the-StackPanel-and-WrapPanel) ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon")

### <a name="dockpanel"></a><a name="Dock"></a> DockPanel
 Nesneleri, panelin bir kenarına kalacak veya *sabitler*olacak şekilde düzenleyin.

 (Yalnızca WPF projeleri için kullanılabilir)

 ![](../designers/media/72d46b58-9a49-4dd5-8af7-6843c0440226.png "72d46b58-9a49-4dd5-8af7-6843c0440226")

 **Kısa bir video izleyin:** ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [WPF-DockPanel](https://www.youtube.com/watch?v=EBH_OIM-zPo)

## <a name="layout-controls"></a>Düzen denetimleri
 Nesnelerinizi düzen denetimlerine de ekleyebilirsiniz. Bunlar Düzen paneli olarak zengin zengin değildir, ancak belirli senaryolar için yararlı olabilir.

 Aşağıdaki düzen denetimleri en fazla popuya kullanılan, ancak diğerleri vardır. Bunları **varlıklar** panelinde bulabilirsiniz.

- [Kenarlık](#Border)

- [Açılan Pencere](#Popup)

- [ScrollViewer](#Scroll)

- [Birlik Kılavuzu](#Uniform)

- [Viewbox](#View)

### <a name="border"></a><a name="Border"></a> Sınırının
 Bir nesne etrafında kenarlık, arka plan veya her ikisini birden oluşturun. Bir **kenarlığa**yalnızca bir nesne ekleyebilirsiniz. Birden fazla nesne için bir kenarlık veya arka plan uygulamak istiyorsanız, **kenarlığa**Düzen paneli ekleyin. Ardından, bu panele veya denetime nesne ekleyin.

 ![](../designers/media/e761238b-99fd-43c5-bbc4-57538b8289ff.png "e761238b-99fd-43c5-bbc4-57538b8289ff")

 **Kısa bir video izleyin:** [Kenarlıklar Ile çalışan](http://www.popscreen.com/v/6A4hB/Microsoft-Expression-Blend-Working-with-Borders) ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon")

### <a name="popup"></a><a name="Popup"></a> Kutu
 Bir penceredeki kullanıcılara bilgi veya seçenek göster. Bir **açılan pencerede**yalnızca bir nesne ekleyebilirsiniz. Varsayılan olarak, bir **açılan pencere** bir **kılavuz** içerir, ancak bunu değiştirebilirsiniz.

### <a name="scrollviewer"></a><a name="Scroll"></a> ScrollViewer
 Sayfanın bir sayfasını veya alanını kaydırmak için kullanımları etkinleştirin. Bir **ScrollViewer** için yalnızca bir nesne ekleyebilirsiniz. böylece, **kılavuz** veya **StackPanel**gibi bir Düzen paneli eklemek çok anlamlı olur.

 ![](../designers/media/06b326d4-f23d-41a6-b26b-e1aff37572a7.png "06b326d4-f23d-41a6-b26b-e1aff37572a7")

### <a name="viewbox"></a><a name="View"></a> Viewbox
 Nesneleri yakınlaştırma denetimiyle yaptığınız gibi ölçeklendirin. **Viewbox**'a yalnızca bir nesne ekleyebilirsiniz. Bu etkiyi birden fazla nesneye uygulamak istiyorsanız, **Viewbox**'a bir Düzen paneli ekleyin ve ardından denetimlerinizi bu düzen paneline ekleyin.

 (Yalnızca WPF projeleri için kullanılabilir)

 ![](../designers/media/f5b13c66-d918-4141-8a16-bd8f8628687a.png "f5b13c66-d918-4141-8a16-bd8f8628687a")

## <a name="see-also"></a>Ayrıca Bkz.
 [XAML Tasarımcısı kullanarak bir kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md) [XAML Tasarımcısı öğeleriyle çalışma](../designers/working-with-elements-in-xaml-designer.md)
