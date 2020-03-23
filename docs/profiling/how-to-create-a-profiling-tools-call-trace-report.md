---
title: 'Nasıl Yapilir: Profil Oluşturma Araçları Arama İzleme Raporu | Microsoft Dokümanlar'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778992"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Nasıl yapılır: Profil oluşturma araçları çağrı izleme raporu oluşturma
Profil Oluşturma Araçları için *arama izleme raporu,* uygulamanızın işlevlerine her giriş ve çıkış noktası için zamanlama bilgilerini ve işleviniz tarafından diğer işlevlere yapılan her aramayı listeler. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Arama izleme raporları, yalnızca enstrümantasyon yöntemiyle toplanmışsa, verilerin profilini çıkarmak için kullanılabilir.

> [!NOTE]
> Arama izleme raporlarını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]' da görüntüleyemezsiniz. Virgülden ayrılmış bir değer oluşturmak için **VSPerfReport** komut satırı aracını kullanmanız gerekir (.* csv*) veya . *xml* dosyası. Bu araç hakkında daha fazla bilgi için [VSPerfReport'a](../profiling/vsperfreport.md)bakın.

### <a name="to-create-a-call-trace-report"></a>Çağrı izleme raporu oluşturmak için

1. Komut **İstemi penceresi** açın.

2. Komut isteminde aşağıdaki komutu yazın:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |||
    |-|-|
    |*ToolsPath*|Profil Oluşturma Araçları komut satırı araçlarının yolu. Daha fazla bilgi için [bkz.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)|
    |*VSPDosyası*|Profil oluşturma verileri (.* vsp* veya . *vsps*) Dosya. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçimlendirilmiş bir rapor oluşturur.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows (ETW) verileri için Olay İzlemesini Toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Profil oluşturma araçları API'leri](../profiling/profiling-tools-apis.md)
