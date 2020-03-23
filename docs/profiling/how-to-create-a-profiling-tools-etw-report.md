---
title: Nasıl? Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ce7b02be682d825205fc5fa50d07c1ca817a24d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776420"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Nasıl?
Windows için Olay İzleme (ETW) raporu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları'nın performans oturumunda kaydedilen ETW olaylarını listeler. ETW verileri bir ikili olarak toplanır (.* etl*) dosyası. Bu rapor hakkında daha fazla bilgi için [Windows için Olay İzleme (ETW) raporuna](../profiling/event-tracing-for-windows-etw-report.md)bakın.

> [!NOTE]
> ETW raporlarını için arabirimde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]görüntüleyemezsiniz.

- ETW verisinin nasıl toplandığı hakkında bilgi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]için [,](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)bkz.

- Komut isteminden ETW verilerinin nasıl toplandığı hakkında bilgi için [VSPerfCmd](../profiling/vsperfcmd.md) ve [Events'e](../profiling/events-vsperfcmd.md)bakın.

  **VSReport/summary:etw** komutunu kullanarak ETW raporunu oluşturursunuz. Şey. ETW verilerini içeren *etl,* profil oluşturma verileriyle aynı dizinde olmalıdır (.* vsp* veya . *vsps*) Dosya. Varsayılan olarak, rapor virgülle ayrılmış bir değer olarak oluşturulur (.* csv*) dosyası. Daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.

### <a name="to-generate-an-etw-report"></a>ETW raporu oluşturmak için

- Komut **İstem penceresine** aşağıdaki komut satırını yazın:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/Özet:ETW [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|Profil Oluşturma Araçları yardımcı programının yolu. Daha fazla bilgi için [bkz.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)|
    |*VSPDosyası*|Profil oluşturma verileri (.* vsp* veya . *vsps*) Dosya. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML formatında bir rapor oluşturur.|
