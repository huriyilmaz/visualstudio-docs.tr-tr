---
title: Windows için olay Izleme (ETW) raporu | Microsoft Docs
description: Visual Studio Profil Oluşturma Araçları Performans oturumunda kaydedilmiş ETW olaylarını listeleyen Windows için olay Izleme (ETW) raporu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e7167f2fb5c78a6fa8c3d83fb56c2c2eba217516
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801421"
---
# <a name="event-tracing-for-windows-etw-report"></a>Windows için olay Izleme (ETW) raporu
Windows için olay Izleme (ETW) raporu, Profil Oluşturma Araçları Performans oturumunda kaydedilmiş olan ETW olaylarını listeler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . ETW verileri bir ikili dosyada toplanır (.*ETL*) dosyası.

> [!NOTE]
> Arabiriminde ETW raporlarını görüntüleyemezsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Arabiriminden Profil Oluşturma Araçları kullanarak ETW 'nin nasıl toplanacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bkz. [nasıl yapılır: Windows Için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı araçlarını kullanarak ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [Olaylar](../profiling/events-vsperfcmd.md).

- **VSReport/Summary: ETW** komutunu kullanarak ETW raporunu oluşturabilirsiniz. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

|Sütun|Açıklama|
|------------|-----------------|
|**İlişkin**|Olayın ne zaman oluştuğunu tanımlar.|
|**İşlem Kimliği**|Olayı oluşturan işlemi tanımlar.|
|**İş parçacığı KIMLIĞI**|Olayı oluşturan iş parçacığını tanımlar.|
|**Açıklama**|Olay sağlayıcısını tanımlar.|
|**Tür**|Olay türünü tanımlar.|
|**Özellikler**|Etkinliğin özellikleri. Her olay, köşeli ayraçlar içine alınmış, virgülle ayrılmış bir ad-değer çiftidir.|
