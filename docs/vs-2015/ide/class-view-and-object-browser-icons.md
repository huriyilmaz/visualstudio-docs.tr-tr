---
title: Sınıf Görünümü ve Nesne Tarayıcısı simgeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons, in Object Browser
- signal icons
- Class View tool, symbols
- graphic symbols
- IntelliSense, icons
- icons, IntelliSense
- symbols, Object Browser icons
- Object Browser, icons in Class View
ms.assetid: 58cc3f44-c296-4a88-a008-09d28598d9c0
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e67763234ff7b3778cccabaed45fbbc0bc04d30
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72620477"
---
# <a name="class-view-and-object-browser-icons"></a>Sınıf Görünümü ve Nesne Tarayıcısı Simgeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sınıf Görünümü * * ve **nesne tarayıcısı** ; Örneğin, ad alanları, sınıflar, işlevler ve değişkenler gibi kod varlıklarını temsil eden simgeler görüntüler. Aşağıdaki tabloda, simgeler gösterilmektedir ve açıklanmaktadır.

|Simge|Açıklama|Simge|Açıklama|
|----------|-----------------|----------|-----------------|
|![Ad alanı simgesi](../ide/media/vxnamespace-icon.gif "vxNamespace_Icon")|Ad Alanı|![Bildirim simgesi](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Yöntem veya Işlev|
|![Sınıf simgesi](../ide/media/vxclass-icon.gif "vxClass_Icon")|örneği|![İşleç simgesi](../ide/media/vxoperator-icon.gif "vxOperator_Icon")|İşleç|
|![Lolipop arabirimi simgesi](../ide/media/vxinterface-icon.gif "vxInterface_Icon")|Arabirim|![Özellik simgesi](../ide/media/vxproperty-icon.gif "vxProperty_Icon")|Özellik|
|![Yapı simgesi](../ide/media/vxstruct-icon.gif "vxStruct_Icon")|Yapı|![Alan simgesi](../ide/media/vxfield-icon.gif "vxField_Icon")|Alan veya değişken|
|![Birleşim simgesi](../ide/media/vxunion-icon.gif "vxUnion_Icon")|UNION|![Olay simgesi](../ide/media/vxevent-icon.gif "vxEvent_Icon")|Olay|
|![Sabit Listesi simgesi](../ide/media/vxenum-icon.gif "vxEnum_Icon")|Enum|![Sabit simgesi](../ide/media/vxconstant-icon.gif "vxConstant_Icon")|Sabit|
|![Tür tanımı simgesi](../ide/media/vxtypedef-icon.gif "vxTypeDef_Icon")|Genişletiyor|![Öğe sembolünü numaralandır](../ide/media/vxenumitem-icon.gif "vxEnumItem_Icon")|Enum öğesi|
|![Visual Studio modül simgesi](../ide/media/vxmodule-icon.gif "vxModule_Icon")|Modül|![Harita öğesi simgesi](../ide/media/vxmapitem-icon.gif "vxMapItem_Icon")|Eşleme öğesi|
|![Uzantı yöntemi simgesi](../ide/media/extensionmethod.gif "ExtensionMethod")|Genişletme yöntemi|![Bildirim simgesi](../ide/media/vxmethod-icon.gif "vxMethod_Icon")|Dış bildirim|
|![Temsilci simgesi](../ide/media/vxdelegate-icon.gif "vxDelegate_Icon")|Temsilci|![Sınıf Görünümü ve Nesne Tarayıcısı için hata simgesi](../ide/media/erroricon.gif "ErrorIcon")|Hata|
|![Özel durum simgesi](../ide/media/vxexception-icon.gif "vxException_Icon")|Özel Durum|![Şablon simgesi](../ide/media/vxtemplate-icon.gif "vxTemplate_Icon")|Şablon|
|![Harita simgesi](../ide/media/vxmap-icon.gif "vxMap_Icon")|Harita|![Hata ünlem noktası simgesi](../ide/media/vxerror-icon.gif "vxError_Icon")|Bilinmiyor|
|![Tür Iletme simgesi](../ide/media/ob-type-forward.gif "ob_type_forward")|Tür Iletme|||

## <a name="signal-icons"></a>Sinyal simgeleri
 Aşağıdaki sinyal simgeleri önceki tüm simgelere uygulanır ve erişilebilirliğini gösterir.

> [!NOTE]
> Projeniz bir kaynak denetim veritabanına dahil edildiğinde, iade edilen veya kullanıma alma gibi kaynak denetimi durumunu göstermek için ek sinyal simgeleri gösterilebilir.

|Simge|Açıklama|
|----------|-----------------|
|\<No sinyal simgesi >|Geneldir. Bu bileşenin her yerinden ve ona başvuran herhangi bir bileşenden erişilebilir.|
|![Sinyal korumalı simgesi](../ide/media/vxsignal-icon-key.gif "vxSignal_Icon_Key")|Korunamadı. Kapsayan sınıf veya türden ya da kapsayan sınıf veya türden türeten erişilebilir.|
|![Sinyal özel simgesi](../ide/media/vxsignal-icon-lock.gif "vxSignal_Icon_Lock")|Özelleştirme. Yalnızca kapsayan sınıfta veya türünde erişilebilir.|
|![Sinyal korumalı simgesi](../ide/media/vxsignal-icon-envelope.gif "vxSignal_Icon_Envelope")|Sealed.|
|![Sinyal arkadaş&#47;iç simgesi](../ide/media/vxsignal-icon-diamond.gif "vxSignal_Icon_Diamond")|Arkadaş/Iç. Yalnızca projeden erişilebilir.|
|![Sinyal simgesi ok](../ide/media/vxsignal-icon-arrow.gif "vxSignal_Icon_Arrow")|Kısayol. Nesnenin bir kısayolu.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Kod Yapısını Görüntüleme](../ide/viewing-the-structure-of-code.md)
