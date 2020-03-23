---
title: Fonksiyonlar Görünümü - Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Functions View
- Functions view
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 70fda712a29ff07ee34a4ac76a06198cb5ead8a5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780032"
---
# <a name="functions-view---sampling-data"></a>İşlevler Görünümü - örnekleme verileri
Örnekleme profili yönteminin İşlevler rapor görünümü, profil oluşturma çalışması sırasında örneklenmiş işlevleri listeler.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşleviçeren modülün adı.|
|**Modül Yolu**|İşleviçeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Fonksiyon Adı**|İşlevin tam nitelikli adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|Fonksiyonun adresi.|
|**Dahil Örnekler**|Bu işlev yürütüldüğünde toplanan toplam örnek sayısı; diğer bir şey, bu işlev çağrı yığınında yken toplanan örnek sayısıdır. Sayı, bu işlev tarafından çağrılan işlevler yürütüldüğünde toplanan örnekleri içerir.|
|**Kapsayıcı Örnekler %**|Profil oluşturma çalışmasındaki tüm örneklerin yüzdesi, bu işlevin kapsayıcı örnekleriydi.|
|**Özel Örnekler**|Bu işlevin gövdesinde kod yürütüldüğünde toplanan toplam örnek sayısı; diğer bir de, bu işlev çağrı yığınının en üstündeyken. Bu işlev tarafından çağrılan işlevlerde toplanan örnekler dahil edilmez.|
|**Özel Örnekler %**|Profil oluşturma çalışmasındaki tüm örneklerin yüzdesi, bu işlevin özel örnekleriydi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Rapor Görünümü sütunlarını özelleştir](../profiling/how-to-customize-report-view-columns.md)
- [Fonksiyonlar Görünümü - enstrümantasyon](../profiling/functions-view-dotnet-memory-instrumentation-data.md)
- [Fonksiyonlar Görünümü - örnekleme](../profiling/functions-view-dotnet-memory-sampling-data.md)
- [Fonksiyonlar Görünümü](../profiling/functions-view-instrumentation-data.md)
