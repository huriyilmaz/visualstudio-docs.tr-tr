---
title: Yönerge Işaretçileri (IP) görünümü-örnekleme verileri | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74774262"
---
# <a name="instruction-pointers-ips-view---sampling-data"></a>Yönerge Işaretçileri (IP) görünümü-örnekleme verileri
Örnekleme verilerinin IP 'Leri görünümü, profil oluşturma çalıştırmasında örnek toplandığında doğrudan yürütülen derleme yönergeleri için performans verilerini listeler.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Sütun|Açıklama|
|------------|-----------------|
|**İşlem Kimliği**|Profil oluşturma çalıştırmasının işlem KIMLIĞI (PID).|
|**İşlem adı**|Sürecin adı.|
|**Modül Adı**|Yönergeyi içeren modülün adı.|
|**Modül yolu**|Yönergeyi içeren modülün yolu.|
|**Kaynak Dosya**|Yönergesini içeren kaynak dosya.|
|**İşlev adı**|Yönergeyi içeren işlevin adı.|
|**İşlev satır numarası**|Kaynak dosyada bu işlevin başlangıcına ait satır numarası.|
|**İşlev adresi**|Yüklenen ikilide işlevin başlangıç belleği adresi.|
|**Kaynak satırı başlangıç**|Bu örneğin toplandığı kaynak dosyadaki başlangıç satırı numarası.|
|**Kaynak satır sonu**|Bu örneğin toplandığı kaynak dosyadaki bitiş satırı numarası.|
|**Kaynak karakter başlangıcı**|Bu örneğin toplandığı kaynak dosya satırındaki başlangıç karakterinin boşluğu.|
|**Kaynak karakter sonu**|Bu örneğin toplandığı kaynak dosya satırındaki bitiş karakterinin boşluğu.|
|**Yönerge adresi**|Yüklenen ikilide yönergenin adresi.|
|**Dışlamalı örnekler**|Yönerge yürütüldüğü zaman toplanan örneklerin toplam sayısı.|
|**Dışlamalı örnekler%**|Yönerge yürütüldüğü sırada toplanan profil oluşturma çalıştırmasında tüm örneklerin yüzdesi.|

## <a name="see-also"></a>Ayrıca bkz.
- [Yönerge Işaretçileri (IP) görünümü-örnekleme](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)
