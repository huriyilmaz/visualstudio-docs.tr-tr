---
title: Windows için olay Izleme (ETW) raporu | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779304"
---
# <a name="event-tracing-for-windows-etw-report"></a>Windows için olay Izleme (ETW) raporu
Windows için olay Izleme (ETW) raporu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları bir performans oturumunda kaydedilmiş ETW olaylarını listeler. ETW verileri bir ikili dosyada toplanır (. *ETL*) dosyası.

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] arabiriminde ETW raporlarını görüntüleyemezsiniz.

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] arabiriminden Profil Oluşturma Araçları kullanarak ETW 'nin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı araçlarını kullanarak ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [Olaylar](../profiling/events-vsperfcmd.md).

- **VSReport/Summary: ETW** komutunu kullanarak ETW raporunu oluşturabilirsiniz. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

|Sütun|Açıklama|
|------------|-----------------|
|**İlişkin**|Olayın ne zaman oluştuğunu tanımlar.|
|**İşlem KIMLIĞI**|Olayı oluşturan işlemi tanımlar.|
|**İş parçacığı KIMLIĞI**|Olayı oluşturan iş parçacığını tanımlar.|
|**Açıklama**|Olay sağlayıcısını tanımlar.|
|**Türüyle**|Olay türünü tanımlar.|
|**Veri Erişimi**|Etkinliğin özellikleri. Her olay, köşeli ayraçlar içine alınmış, virgülle ayrılmış bir ad-değer çiftidir.|
