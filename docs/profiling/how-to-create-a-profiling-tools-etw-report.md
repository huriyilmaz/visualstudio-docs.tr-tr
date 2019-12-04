---
title: 'Nasıl yapılır: Profil Oluşturma Araçları ETW raporu oluşturma | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74776420"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Nasıl yapılır: profil oluşturma araçları ETW raporu oluşturma
Windows için olay Izleme (ETW) raporu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları bir performans oturumunda kaydedilen ETW olaylarını listeler. ETW verileri bir ikili dosyada toplanır (. *ETL*) dosyası. Bu rapor hakkında daha fazla bilgi için bkz. [Windows Için olay izleme (ETW) raporu](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]için arabirimdeki ETW raporlarını görüntüleyemezsiniz.

- [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]arabirimini kullanarak ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [nasıl yapılır: Windows Için olay izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Bir komut isteminden ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md) ve [Events](../profiling/events-vsperfcmd.md).

  **VSReport/Summary: ETW** komutunu kullanarak ETW raporunu oluşturabilirsiniz. İçin. ETW verilerini içeren *ETL* , profil oluşturma verileriyle aynı dizinde olmalıdır (. *VSP* veya. *vsps*) dosyasýný. Varsayılan olarak, rapor bir virgülle ayrılmış değer (. *CSV*) dosyası. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>ETW raporu oluşturmak için

- **Komut istemi** penceresinde, aşağıdaki komut satırını yazın:

     *Araçları yolu* **VSPerfReport** *vspfile*  **/summary: ETW [/XML]**

    |||
    |-|-|
    |*Araçları yolu*|Profil Oluşturma Araçları yardımcı programının yolu. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Profil oluşturma verileri (. *VSP* veya. *vsps*) dosyasýný. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçiminde biçimlendirilen bir rapor oluşturur.|
