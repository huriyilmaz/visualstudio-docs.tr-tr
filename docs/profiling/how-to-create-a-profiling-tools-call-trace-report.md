---
title: İzleme Raporu Profil Oluşturma Araçları bir çağrı oluşturma | Microsoft Docs
description: İşlevlerinize ve işlevleriniz tarafından çağrılan işlevlere ilişkin zamanlama bilgilerini görmek için bir Performans Araçları çağrı izleme raporu oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 297ca895e9cc2f24dde9ce6e271c889d6d0543c8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122141882"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Nasıl yapılır: Profil oluşturma araçları çağrı izleme raporu oluşturma
Uygulamanın çağrı izleme  *raporu Profil Oluşturma Araçları* her giriş ve çıkış noktası için uygulamanın işlevlerine zamanlama bilgilerini ve işlevinizin diğer işlevlere yapılan her [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çağrıyı listeler. Çağrı izleme raporları yalnızca izleme yöntemiyle toplanmışsa veri profili oluşturma için kullanılabilir.

> [!NOTE]
> içinde çağrı izleme raporlarını görüntüleyesiniz. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Virgülle ayrılmış değer () oluşturmak için **VSPerfReport** komut satırı aracını kullan gerekir.*csv*) veya . *xml* dosyası. Bu araç hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Bir çağrı izleme raporu oluşturmak için

1. Bir Komut **İstemi penceresi** açın.

2. Komut isteminde aşağıdaki komutu yazın:

     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**

    |Öğe|Açıklama|
    |-|-|
    |*ToolsPath*|Komut satırı Profil Oluşturma Araçları yolu. Daha fazla bilgi için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)|
    |*VSPFile*|Profil oluşturma verileri (.*vsp* veya . *vsps*) Dosya. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçimli bir rapor üretir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl kullanılır: Veri kaynağı (ETW) Windows Olay İzleme toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Profil oluşturma araçları API'leri](../profiling/profiling-tools-apis.md)
