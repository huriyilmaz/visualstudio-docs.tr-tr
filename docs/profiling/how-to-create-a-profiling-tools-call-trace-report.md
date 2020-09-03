---
title: Nasıl yapılır-Profil Oluşturma Araçları çağrısı Izleme raporu oluşturma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2fe1ae2870e2e48d092f303f3e7458e7498c0ba5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548167"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Nasıl yapılır: Profil oluşturma araçları çağrı izleme raporu oluşturma
Profil Oluşturma Araçları için  *çağrı izleme raporu* , [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] her giriş için zamanlama bilgilerini ve uygulamanızın işlevlerine ve işleviniz tarafından yapılan her bir işleve yapılan her çağrıyı listeler. Çağrı izleme raporları yalnızca izleme yöntemiyle toplandıysa profil oluşturma verileri için kullanılabilir.

> [!NOTE]
> İçinde çağrı izleme raporları görüntüleyemezsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bir virgülle ayrılmış değer oluşturmak için **VSPerfReport** komut satırı aracını kullanmanız gerekir (.* CSV*) veya. *XML* dosyası. Bu araç hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Bir çağrı izleme raporu oluşturmak için

1. Bir **komut istemi** penceresi açın.

2. Komut isteminde aşağıdaki komutu yazın:

     *Araçları yolu* **VSPerfReport** *vspfile*  **/calltrace [/XML]**

    |Öğe|Açıklama|
    |-|-|
    |*Araçları yolu*|Profil Oluşturma Araçları komut satırı araçlarının yolu. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Profil oluşturma verileri (.* VSP* veya. *vsps*) dosyasýný. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçimli bir rapor oluşturur.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Profil araçları API 'Leri](../profiling/profiling-tools-apis.md)
