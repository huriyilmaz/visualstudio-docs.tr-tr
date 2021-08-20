---
title: EtW Profil Oluşturma Araçları raporu oluşturma | Microsoft Docs
description: Windows (ETW) raporu için Olay İzleme oluşturma hakkında bilgi. Bir performans oturumunda kaydedilen ETW Visual Studio Profil Oluşturma Araçları listeler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 687e813b449f469386d1c2fce9a7b79ae7467497
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150241"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Nasıl: Profil oluşturma araçları ETW raporu oluşturma
Windows (ETW) raporu için Olay İzleme raporu, raporun bir performans oturumuna kaydedilen ETW [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] olaylarını Profil Oluşturma Araçları. ETW verileri bir ikili () içinde toplanır.*etl*) dosyasını seçin. Bu rapor hakkında daha fazla bilgi için bkz. [Windows (ETW) raporu için Olay İzleme.](../profiling/event-tracing-for-windows-etw-report.md)

> [!NOTE]
> için arabirimde ETW raporlarını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] görüntüleyesiniz.

- için arabirimini kullanarak ETW verilerini toplama hakkında bilgi için bkz. Nasıl kullanılır: Windows [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [(ETW) verileri için Olay İzleme toplama.](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

- Komut isteminden ETW verileri toplama hakkında bilgi için bkz. [VSPerfCmd ve](../profiling/vsperfcmd.md) [Olaylar.](../profiling/events-vsperfcmd.md)

  **VSReport/summary:etw** komutunu kullanarak ETW raporunu oluşturabilirsiniz. . ETW verilerini içeren *etl,* profil oluşturma verileri () ile aynı dizinde olmalıdır.*vsp* veya . *vsps*) Dosya. Varsayılan olarak, rapor virgülle ayrılmış bir değer () olarak oluşturulur.*csv*) dosyasını seçin. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>ETW raporu oluşturmak için

- Komut **İstemi** penceresinde aşağıdaki komut satırı yazın:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary:ETW [/Xml]**

    |Öğe|Açıklama|
    |-|-|
    |*ToolsPath*|Profil Oluşturma Araçları yolu. Daha fazla bilgi için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)|
    |*VSPFile*|Profil oluşturma verileri (.*vsp* veya . *vsps*) Dosya. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçiminde bir rapor üretir.|
