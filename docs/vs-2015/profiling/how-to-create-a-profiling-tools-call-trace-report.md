---
title: 'Nasıl yapılır: Profil Oluşturma Araçları çağrısı Izleme raporu oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fbf92b38f9408455e10048fbd4a5e84fdf822ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547998"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Nasıl yapılır: Profil Oluşturma Araçları Çağrı İzleme Raporu Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Profil Oluşturma Araçları için  *çağrı izleme raporu* , [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] her giriş için zamanlama bilgilerini ve uygulamanızın işlevlerine ve işleviniz tarafından yapılan her bir işleve yapılan her çağrıyı listeler. Çağrı izleme raporları yalnızca izleme yöntemiyle toplandıysa profil oluşturma verileri için kullanılabilir.  
  
> [!NOTE]
> İçinde çağrı izleme raporları görüntüleyemezsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Bir virgülle ayrılmış değer (. csv) veya XML dosyası oluşturmak için **VSPerfReport** komut satırı aracını kullanmanız gerekir. Bu araç hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Bir çağrı izleme raporu oluşturmak için  
  
1. Bir **komut istemi**penceresi açın.  
  
2. Komut isteminde aşağıdaki komutu yazın:  
  
     *Araçları yolu* **VSPerfReport** *vspfile*  **/calltrace [/XML]**  
  
    |Komut öğesi|Description|
    |-|-|  
    |*Araçları yolu*|Profil Oluşturma Araçları komut satırı araçlarının yolu. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Profil oluşturma verileri (. vsp veya. vsps) dosyası. Tam ve kısmi yollar kabul edilir.|  
    |Xml|XML biçimli bir rapor oluşturur.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Profil Araçları API'leri](../profiling/profiling-tools-apis.md)
