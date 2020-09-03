---
title: 'Nasıl yapılır: Profil Oluşturma Araçları ETW raporu oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7dc74f0486ac7196cf406994ee603bc6c0cf4c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548011"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Nasıl yapılır: Profil Oluşturma Araçları ETW Raporu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows için olay Izleme (ETW) raporu, Profil Oluşturma Araçları bir performans oturumunda kaydedilen ETW olaylarını listeler [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . ETW verileri bir ikili (. etl) dosyasında toplanır. Bu rapor hakkında daha fazla bilgi için bkz. [Windows Için olay izleme (ETW) raporu](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
> İçin arabirimindeki ETW raporlarını görüntüleyemezsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Arabirimini kullanarak ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bkz. [nasıl yapılır: Windows Için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Bir komut isteminden ETW verilerinin nasıl toplanacağı hakkında daha fazla bilgi için bkz. [VSPerfCmd](../profiling/vsperfcmd.md) ve [Events](../profiling/events-vsperfcmd.md).  
  
  **VSReport/Summary: ETW** komutunu kullanarak ETW raporunu oluşturabilirsiniz. ETW verilerini içeren. etl, profil oluşturma verileri (. vsp veya. vsps) dosyası ile aynı dizinde olmalıdır. Varsayılan olarak, rapor bir virgülle ayrılmış değer (. csv) dosyası olarak oluşturulur. Daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>ETW raporu oluşturmak için  
  
- **Komut istemi** penceresinde, aşağıdaki komut satırını yazın:  
  
     *Araçları yolu* **VSPerfReport** *vspfile*  **/summary: ETW [/XML]**  
  
    |Komut öğesi|Description|  
    |-|-|  
    |*Araçları yolu*|Profil Oluşturma Araçları yardımcı programının yolu. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Profil oluşturma verileri (. vsp veya. vsps) dosyası. Tam ve kısmi yollar kabul edilir.|  
    |Xml|XML biçiminde biçimlendirilen bir rapor oluşturur.|
