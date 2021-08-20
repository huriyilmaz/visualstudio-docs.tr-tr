---
title: Windows (ETW) raporu için olay izleme | Microsoft Docs
description: Visual Studio Profil Oluşturma Araçları performans oturumunda kaydedilen etw olaylarını listeleyen Windows (etw) için olay izleme raporu hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Event tracing for Windows profiling report
- ETW profiling report
ms.assetid: 81e88162-b88a-40b6-8b85-a232c8096a47
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 76749460a68c70856c735ef6ae344188d58a5efc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061135"
---
# <a name="event-tracing-for-windows-etw-report"></a>Windows için olay izleme (ETW) raporu
Windows (ETW) için olay izleme raporu, Profil Oluşturma Araçları bir performans oturumunda kaydedilen ETW olaylarını listeler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . ETW verileri bir ikili dosyada toplanır (.*ETL*) dosyası.

> [!NOTE]
> Arabiriminde ETW raporlarını görüntüleyemezsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- arabiriminden Profil Oluşturma Araçları kullanarak ETW 'nin nasıl toplanacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bkz. [nasıl yapılır: Windows için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

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
