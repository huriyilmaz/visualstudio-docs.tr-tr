---
title: Profil Oluşturma Araçları ETW raporu oluşturma | Microsoft Docs
description: Windows için olay Izleme (ETW) raporu oluşturmayı öğrenin. Bir Visual Studio Profil Oluşturma Araçları Performans oturumunda kaydedilen ETW olaylarını listeler.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3cc48c3409ad4e683032da402c2ecedbccea3da7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873677"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Nasıl yapılır: profil oluşturma araçları ETW raporu oluşturma
Windows için olay Izleme (ETW) raporu, Profil Oluşturma Araçları bir performans oturumunda kaydedilen ETW olaylarını listeler [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . ETW verileri bir ikili dosyada toplanır (.*ETL*) dosyası. Bu rapor hakkında daha fazla bilgi için bkz. [Windows Için olay izleme (ETW) raporu](../profiling/event-tracing-for-windows-etw-report.md).

> [!NOTE]
> İçin arabirimindeki ETW raporlarını görüntüleyemezsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

- Arabirimini kullanarak ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bkz. [nasıl yapılır: Windows Için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).

- Bir komut isteminden ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md) ve [Events](../profiling/events-vsperfcmd.md).

  **VSReport/Summary: ETW** komutunu kullanarak ETW raporunu oluşturabilirsiniz. İçin. ETW verilerini içeren *ETL* , profil oluşturma verileriyle aynı dizinde olmalıdır (.*VSP* veya. *vsps*) dosyasýný. Varsayılan olarak, rapor bir virgülle ayrılmış değer (.*CSV*) dosyası. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-generate-an-etw-report"></a>ETW raporu oluşturmak için

- **Komut istemi** penceresinde, aşağıdaki komut satırını yazın:

     *Araçları yolu* **VSPerfReport** *vspfile*  **/summary: ETW [/XML]**

    |Öğe|Açıklama|
    |-|-|
    |*Araçları yolu*|Profil Oluşturma Araçları yardımcı programının yolu. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Profil oluşturma verileri (.*VSP* veya. *vsps*) dosyasýný. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçiminde biçimlendirilen bir rapor oluşturur.|
