---
title: Yardım Içerik Yöneticisi geçersiz kılmaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70c0044a0436dcf27a3b087b3f11a5f759824735
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645559"
---
# <a name="help-content-manager-overrides"></a>Yardım İçerik Yöneticisi Geçersiz Kılmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio IDE 'deki Yardım Görüntüleyicisi ve yardım ile ilgili özelliklerin varsayılan davranışını değiştirmek için kayıt defterini değiştirebilirsiniz.

|Görev|Kayıt Defteri Anahtarı|Değer ve tanım|
|----------|------------------|--------------------------|
|Benzersiz hizmet uç noktası tanımla|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*Httpvaluefortheserviceendpoint*.|
|Çevrimiçi/çevrimdışı varsayılanı tanımla|HKEY_LOCAL_MACHINE \Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp-- `0` yerel yardım belirtmek Için yazın ve `1` çevrimiçi yardım 'ı belirtmek için girin.|
|Benzersiz F1 uç noktası tanımlama|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*Httpvaluefortheserviceendpoint*|
|BITS iş önceliğini geçersiz kıl|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (64 bitlik bir makinede) \Microsoft\help\v2,2|Bitspriallık--şu değerlerden birini kullanın: **ön plan**, **yüksek**, **normal**veya **düşük**.|
|Çevrimiçi devre dışı bırak (ve IDE çevrimiçi seçeneği)|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (64 bitlik bir makinede) \Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled--çevrimiçi Yardım içeriğinin erişimini devre dışı bırakmak için 1 olarak ayarlayın.|
|Içeriği yönetmeyi devre dışı bırak|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (64 bitlik bir makinede) \Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled--yardım görüntüleyicisinde **Içeriği Yönet** sekmesini devre dışı bırakmak için 1 olarak ayarlayın.|
|Ağ paylaşımındaki yerel içerik deposuna işaret edin|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath = "*Contentstorenetworkshare*"|
|Visual Studio 'nun ilk başlatıldığında içerik yüklemeyi devre dışı bırakın.|HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node (64 bitlik bir makinede) \Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection--Visual Studio ilk kez başlatıldığında yapılandırılmış yardım özelliklerini devre dışı bırakmak için 1 olarak ayarlayın.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Yardım Görüntüleyicisi Yönetici Kılavuzu](../ide/help-viewer-administrator-guide.md)
