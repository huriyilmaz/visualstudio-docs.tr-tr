---
title: XAML Tasarımcısı denetimleri ekleme ve davranışlarını değiştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 02d51c5799391863262d285e1cda209a3b7938d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300846"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>XAML Tasarımcısı'de denetimler ekleme ve bunların davranışlarını değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Denetimler, kullanıcıların uygulamanızla etkileşime geçmesini sağlar. Bunları, bilgi toplamak ve bir nesneye animasyon ekleme ya da bir veri kaynağını sorgulama gibi eylemler gerçekleştirmek için kullanabilirsiniz.

 **Bu konuda:**

- [Çalışma yüzeyine denetim ekleme](#Insert)

- [Denetimleri yapın](#Modify)

## <a name="Insert"></a>Çalışma yüzeyine denetim ekleme
 Denetimleri **varlıklar** panelinden **çalışma yüzeyine**sürükleyebilir ve sonra bunları **Özellikler** penceresinde değiştirebilirsiniz.

 ![Blend &#45; varlıkları &#45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")

 Bu videolar, daha yaygın denetimlerin bazılarını nasıl kullanacağınızı gösterir.

|Denetim|Kısa bir video izleyin|
|-------------|-------------------------|
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [denetimleri ekleme](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436B-b834-a91b7995a3ec")|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [düğme tasarımı](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [bir TextBlock 'a görüntü ekleme](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [araç ipucuyla kaydırıcı oluşturma](https://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|[Bir GridSplitter ile çalışan](https://www.youtube.com/watch?v=bf4t6c8ms2w) ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon")|

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Bir görüntü, şekil veya yoldan bir denetim yapın
 Herhangi bir nesneyi denetimde yapabilirsiniz.

 ![Blend denetimine oluştur iletişim kutusu](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")

 Örneğin, bir sayfanın merkezinde bir televizyon resmi düşünün. Televizyon düğmeleri gibi görünen küçük görüntülerden denetimleri yapabilirsiniz. Ardından kullanıcılar bu düğmeleri tıklatarak kanalı değiştirebilir.

 Düğmeler artık denetimler olduğundan bu mümkündür. Denetimlerle, kullanıcı etkileşimlerine yanıt verebilirsiniz; Bu durumda, Kullanıcı bir düğmeye tıkladığında.

 Bir denetim yapmak için bir nesne seçin. Ardından, **Araçlar** menüsünde **Denetim oluştur**' a tıklayın.

## <a name="Modify"></a>Denetimleri yapın
 Denetimler, kullanıcılar onlarla etkileşim kurarken eylemler gerçekleştirebilir. Örneğin, bir animasyon başlatabilir, bir veri kaynağını güncelleştirebilir veya video oynatabilir.

 Denetimleri yapmak için *Tetikleyiciler*, *davranışlar*ve *olayları* kullanın.

### <a name="triggers"></a>Tetikleyiciler
 *Tetikleyici* bir özelliği değiştirir veya bir olaya ya da başka bir özellikte değişikliğe yanıt olarak bir görev gerçekleştirir. Örneğin, kullanıcılar üzerine gelindiğinde bir düğmenin rengini değiştirebilirsiniz.

 !["Tetikleyiciler" paneli](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")

 **Kısa bir video izleyin:** ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [bir özellik tetikleyicisi ekleyin](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).

### <a name="behaviors"></a>Davranışlar
 *Davranış* , bir kod paketi yeniden kullanılabilir. Değişiklik özelliklerinden biraz daha fazlasını yapabilir. Veri hizmetini sorgulama gibi eylemleri gerçekleştirebilir. Blend, küçük bir koleksiyon ile birlikte gelir, ancak daha fazla ekleyebilirsiniz. Çalışma yüzeyinizdeki herhangi bir nesneye bir davranış sürükleyin ve sonra özellikleri ayarlayarak davranışı özelleştirin.

 ![Özellikler panelinde Floıdmovebehavior](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")

 **Kısa bir video izleyin:** ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [Blend ipuçları: davranış Bölüm 1 ' i kullanma tanıtımı](https://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).

### <a name="events"></a>Olaylar
 Ultimate esnekliği için bir *olayı*işleyin. Kod yazmanız gerekir.

 **Kısa bir video izleyin:** ![yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [fare olayı ekleme](https://www.youtube.com/watch?v=2PMxAlb-x_E).
