---
title: Yönerge İşaretçileri (IP) Görünümü - Örnekleme Verileri | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Instruction Pointers view
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 42398e044bfc06e41249b15ac9baeebcaebd19f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774262"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Yönerge İşaretçileri (IP) Görünümü - örnekleme verileri
Örnekleme verisinin IP'leri görünümü, örnekler profil oluşturma çalışmasında toplandığında doğrudan çalıştırılan derleme yönergeleri için performans verilerini listeler.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalışmasının işlem kimliği (PID).|
|**İşlem Adı**|Sürecin adı.|
|**Modül Adı**|Talimatı içeren modülün adı.|
|**Modül Yolu**|Talimatı içeren modülün yolu.|
|**Kaynak Dosya**|Yönergeyi içeren kaynak dosya.|
|**Fonksiyon Adı**|Yönergeyi içeren işlevin adı.|
|**Fonksiyon Satır Numarası**|Kaynak dosyadaki bu işlevin başlangıcının satır numarası.|
|**Fonksiyon Adresi**|Yüklenen ikili işlevin başlangıç bellek adresi.|
|**Kaynak Satırı Başlangıç**|Bu örneğin toplandığı kaynak dosyadaki başlangıç satır numarası.|
|**Kaynak Satır Sonu**|Bu örneğin toplandığı kaynak dosyadaki bitiş satır numarası.|
|**Kaynak Karakter Başlangıç**|Bu örneğin toplandığı kaynak dosya satırındaki başlangıç karakterinin mahsup edilmesi.|
|**Kaynak Karakter Sonu**|Bu örneğin toplandığı kaynak dosya satırındaki bitiş karakterinin mahsup edilmesi.|
|**Talimat Adresi**|Yüklenen ikili deki talimatın adresi.|
|**Özel Örnekler**|Yönerge yürütüldüğünde toplanan toplam örnek sayısı.|
|**Özel Örnekler %**|Yönerge yürütüldüğünde toplanan profil oluşturma çalışmasındaki tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönerge İşaretçileri (IP) Görünümü - örnekleme](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
