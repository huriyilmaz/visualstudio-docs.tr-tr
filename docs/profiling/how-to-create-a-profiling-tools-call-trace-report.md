---
title: 'Nasıl yapılır: Profil Oluşturma Araçları çağrısı Izleme raporu oluşturma | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4b184310d837193679a1a5eacf2fbae4ecf29caa
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778992"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Nasıl yapılır: profil oluşturma araçları çağrı izleme raporu oluşturma
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profil Oluşturma Araçları için *çağrı izleme raporu* , her giriş için zamanlama bilgilerini, uygulamanızın işlevlerine ve her bir çıkış noktasına, işleviniz tarafından yapılan her çağrıya yönelik olarak listeler. Çağrı izleme raporları yalnızca izleme yöntemiyle toplandıysa profil oluşturma verileri için kullanılabilir.

> [!NOTE]
> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]içinde çağrı izleme raporları görüntüleyemezsiniz. Bir virgülle ayrılmış değer oluşturmak için **VSPerfReport** komut satırı aracını kullanmanız gerekir (. *CSV*) veya. *XML* dosyası. Bu araç hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Bir çağrı izleme raporu oluşturmak için

1. Bir **komut istemi** penceresi açın.

2. Komut satırında, aşağıdaki komutu yazın:

     *Araçları yolu* **VSPerfReport** *vspfile*  **/calltrace [/XML]**

    |||
    |-|-|
    |*Araçları yolu*|Profil Oluşturma Araçları komut satırı araçlarının yolu. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Profil oluşturma verileri (. *VSP* veya. *vsps*) dosyasýný. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçimli bir rapor oluşturur.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Profil araçları API 'Leri](../profiling/profiling-tools-apis.md)
