---
title: Modülgörünümü - Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Modules view
- sampling profiling method,Modules view
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7ead219ddf482af5917842118d386c6fefe67973
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772720"
---
# <a name="modules-view---sampling-data"></a>Modülgörünümü - örnekleme verileri
Örnekleme verilerinin Modülgörünümü, profil oluşturma verilerinde örneklenen modüllere göre gruplanan performans verilerini görüntüler. Her modül hiyerarşik bir ağacın köküdür. Modülün örneklenmiş işlevleri modül düğümünün altında listelenir.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

 Örnekler toplandığında işlev yürütüldüyse (diğer bir şekilde işlev çağrı yığınının en üstündeydi), çalıştırılan kaynak satırları ve yönerge adresleri işlev düğümünün altında listelenir. Satır veya yönerge yürütüldüğünde bir kaynak satırı veya yönerge işaretçisi için veri toplandığından, kapsayıcı ve özel değerler hem satır verileri hem de yönerge verileri için her zaman aynıdır.

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|Modülün adı, işlevi, satır numarası veya talimat işaretçisi adresi.|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|İşlev, çizgi veya yönerge işaretçisini içeren modülün adı.|
|**Modül Yolu**|Modülü, işlevi, satırı veya talimat işaretçisini içeren modülün yolu.|
|**Kaynak Dosya**|Bu işlevin tanımını içeren kaynak dosya.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Dahil Örnekler**|- Bir işlev için, bu işlevin veya bu işlev tarafından çağrılan bir işlevin yürütüldettiği örnek sayısı; diğer bir şekilde, bu işlevi içeren çağrı yığını örneklerinin sayısıdır.<br />- Bir modül için, modülden en az bir fonksiyonun yürütüldettiği örnek sayısı.<br />- Bir satır veya yönerge için, bu satır veya yönerge yürütüldürün örnek sayısı.|
|**Kapsayıcı Örnekler %**|- Bir fonksiyon veya modül için, profil oluşturma çalışmasındaki tüm örneklerin yüzdesi bu işlevin veya modülün kapsayıcı örnekleridir.<br />- Bir satır veya yönerge için, bu satır ın veya talimatın yürütüldettiği profil oluşturma çalışmasındaki tüm örneklerin yüzdesi.|
|**Özel Örnekler**|- Bir işlev için, bu işlevin doğrudan yürütüldettiği çağrı yığını örneklerinin sayısı; diğer bir deyişle, bu işlevin çağrı yığınının en üstünde olduğu örnek sayısıdır.<br />- Bir modül için, modüldeki fonksiyonların özel örneklerinin toplamı.<br />- Bir satır veya yönerge için, bu satır veya yönerge yürütüldürün örnek sayısı.|
|**Özel Örnekler %**|- Bir fonksiyon veya modül için, profil oluşturma çalışmasındaki tüm örneklerin yüzdesi bu işlevin veya modülün özel örnekleridir.<br />- Bir satır veya yönerge için, bu satır ın veya talimatın yürütüldettiği profil oluşturma çalışmasındaki tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Modülgörünümü - örnekleme](../profiling/modules-view-dotnet-memory-sampling-data.md)
- [Modülgörünümü - enstrümantasyon](../profiling/modules-view-dotnet-memory-instrumentation-data.md)
- [Modüller Görünümü](../profiling/modules-view-instrumentation-data.md)
