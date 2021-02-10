---
title: Sınıf Görünümü ve Nesne Tarayıcısı Simgeleri
description: Sınıf Görünümü ve kod varlıklarını temsil eden Nesne Tarayıcısı görüntü simgeleri (örneğin, ad alanları, sınıflar, işlevler ve değişkenler) hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 551033ce7dcd7b8755124b86734243470442b6e0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939987"
---
# <a name="class-view-and-object-browser-icons"></a>Sınıf Görünümü ve Nesne Tarayıcısı simgeleri

**Sınıf görünümü** ve **nesne tarayıcısı** ; Örneğin, ad alanları, sınıflar, işlevler ve değişkenler gibi kod varlıklarını temsil eden simgeler görüntüler. Aşağıdaki tabloda, simgeler gösterilmektedir ve açıklanmaktadır.

|Simge|Description|Simge|Description|
|----------|-----------------|----------|-----------------|
|![Ad alanı simgesi](../ide/media/vxnamespace_icon.gif)|Ad Alanı|![Bildirim simgesi](../ide/media/vxmethod_icon.gif)|Yöntem veya Işlev|
|![Sınıf simgesi](../ide/media/vxclass_icon.gif)|Sınıf|![İşleç simgesi](../ide/media/vxoperator_icon.gif)|Operatör|
|![Lolipop arabirimi simgesi](../ide/media/vxinterface_icon.gif)|Arabirim|![Özellik simgesi](../ide/media/vxproperty_icon.gif)|Özellik|
|![Yapı simgesi](../ide/media/vxstruct_icon.gif)|Yapı|![Alan simgesi](../ide/media/vxfield_icon.gif)|Alan veya değişken|
|![Birleşim simgesi](../ide/media/vxunion_icon.gif)|Birleşim|![Olay simgesi](../ide/media/vxevent_icon.gif)|Olay|
|![Sabit Listesi simgesi](../ide/media/vxenum_icon.gif)|Sabit listesi|![Sabit simgesi](../ide/media/vxconstant_icon.gif)|Sabit|
|![Tür tanımı simgesi](../ide/media/vxtypedef_icon.gif)|Genişletiyor|![Öğe sembolünü numaralandır](../ide/media/vxenumitem_icon.gif)|Enum öğesi|
|![Visual Studio modül simgesi](../ide/media/vxmodule_icon.gif)|Modül|![Harita öğesi simgesi](../ide/media/vxmapitem_icon.gif)|Eşleme öğesi|
|![Uzantı yöntemi simgesi](../ide/media/extensionmethod.gif)|Genişletme yöntemi|![Bildirim simgesi](../ide/media/vxmethod_icon.gif)|Dış bildirim|
|![Temsilci simgesi](../ide/media/vxdelegate_icon.gif)|Temsilci|![Sınıf Görünümü ve Nesne Tarayıcısı için hata simgesi](../ide/media/erroricon.gif)|Hata|
|![Özel durum simgesi](../ide/media/vxexception_icon.gif)|Özel durum|![Şablon simgesi](../ide/media/vxtemplate_icon.gif)|Şablon|
|![Harita simgesi](../ide/media/vxmap_icon.gif)|Harita|![Hata ünlem noktası simgesi](../ide/media/vxerror_icon.gif)|Bilinmiyor|
|![Tür Iletme simgesi](../ide/media/ob_type_forward.gif)|Tür Iletme|||

> [!TIP]
> Bu sayfadaki simgeleri en iyi şekilde görüntülemek için Microsoft Docs temanızın **Açık** olarak ayarlandığından emin olun. Aşağıdaki ekran görüntüsünde gösterildiği gibi, bu renk temasını sayfanın sol alt kısmında bulunan denetimden geçirebilirsiniz:
>
> ![Docs teması](../ide/media/toggle-docs-color-theme.png "Microsoft Docs sayfaları için renk temasını değiştirme")

## <a name="signal-icons"></a>Sinyal simgeleri

Aşağıdaki sinyal simgeleri önceki tüm simgelere uygulanır ve erişilebilirliğini gösterir.

|Simge|Description|
|----------|-----------------|
|\<No Signal Icon>|Geneldir. Bu bileşenin her yerinden ve ona başvuran herhangi bir bileşenden erişilebilir.|
|![Sinyal korumalı simgesi](../ide/media/vxsignal_icon_key.gif)|Korunamadı. Kapsayan sınıf veya türden ya da kapsayan sınıf veya türden türeten erişilebilir.|
|![Sinyal özel simgesi](../ide/media/vxsignal_icon_lock.gif)|Özelleştirme. Yalnızca kapsayan sınıfta veya türünde erişilebilir.|
|![Sinyal korumalı simgesi](../ide/media/vxsignal_icon_envelope.gif)|Sealed.|
|![Sinyal arkadaş&#47;Iç simge](../ide/media/vxsignal_icon_diamond.gif)|Arkadaş/Iç. Yalnızca projeden erişilebilir.|
|![Sinyal simgesi ok](../ide/media/vxsignal_icon_arrow.gif)|Kısayol. Nesnenin bir kısayolu.|

> [!NOTE]
> Projeniz bir kaynak denetim veritabanına dahil edildiğinde, iade edilen veya kullanıma alma gibi kaynak denetimi durumunu göstermek için ek sinyal simgeleri gösterilebilir.

> [!TIP]
> Visual Studio 'da görünen uygulama görüntülerinin ve simgelerinin daha fazlasını görüntülemek için [**Visual Studio Görüntü Kitaplığı**](https://www.microsoft.com/download/details.aspx?id=35825)' nı indirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod yapısını görüntüleme](../ide/viewing-the-structure-of-code.md)
