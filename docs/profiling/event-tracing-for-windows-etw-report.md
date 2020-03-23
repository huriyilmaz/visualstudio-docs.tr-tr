---
title: Windows (ETW) Raporu için Olay İzleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 19412d184377637c29f34b2fe3ffd033f176b97c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779304"
---
# <a name="event-tracing-for-windows-etw-report"></a>Windows (ETW) raporu için Olay İzleme
Windows için Olay İzleme (ETW) raporu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları'nın bir performans oturumunda kaydedilen ETW olaylarını listeler. ETW verileri bir ikili olarak toplanır (.* etl*) dosyası.

> [!NOTE]
> ETW raporlarını arabirimde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] görüntüleyemezsiniz.

- Arabirimden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçlarını kullanarak ETW'nin nasıl toplandığı hakkında bilgi için [bkz.](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı araçlarını kullanarak ETW verilerinin nasıl toplandığı hakkında bilgi için [Bkz.](../profiling/events-vsperfcmd.md)

- **VSReport/Summary:ETW** komutunu kullanarak ETW raporunu oluşturursunuz. Daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.

|Sütun|Açıklama|
|------------|-----------------|
|**Zaman damgası**|Olayın ne zaman oluştuğunu tanımlar.|
|**İşlem Kimliği**|Olayı oluşturan işlemi tanımlar.|
|**İş Parçacığı Kimliği**|Olayı oluşturan iş parçacığı tanımlar.|
|**Açıklama**|Olay sağlayıcısını tanımlar.|
|**Tür**|Olay türünü tanımlar.|
|**Özellikler**|Olayın özellikleri. Her olay, parantez içinde kapalı virgülle ayrılmış, ad değeri çiftidir.|
