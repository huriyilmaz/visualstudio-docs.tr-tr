---
title: Profil Oluşturma Araçları çağrısı Izleme raporu oluştur | Microsoft Docs
description: İşlevleriniz ve işlevleriniz tarafından çağrılan işlevler için zamanlama bilgilerini görmek üzere bir performans araçları çağrı izleme raporu oluşturun.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b9c979668cdf24fae7acddd259a82e5c62353084
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98800412"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Nasıl yapılır: Profil oluşturma araçları çağrı izleme raporu oluşturma
Profil Oluşturma Araçları için  *çağrı izleme raporu* , [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] her giriş için zamanlama bilgilerini ve uygulamanızın işlevlerine ve işleviniz tarafından yapılan her bir işleve yapılan her çağrıyı listeler. Çağrı izleme raporları yalnızca izleme yöntemiyle toplandıysa profil oluşturma verileri için kullanılabilir.

> [!NOTE]
> İçinde çağrı izleme raporları görüntüleyemezsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bir virgülle ayrılmış değer oluşturmak için **VSPerfReport** komut satırı aracını kullanmanız gerekir (.*CSV*) veya. *XML* dosyası. Bu araç hakkında daha fazla bilgi için bkz. [VSPerfReport](../profiling/vsperfreport.md).

### <a name="to-create-a-call-trace-report"></a>Bir çağrı izleme raporu oluşturmak için

1. Bir **komut istemi** penceresi açın.

2. Komut isteminde aşağıdaki komutu yazın:

     *Araçları yolu* **VSPerfReport** *vspfile*  **/calltrace [/XML]**

    |Öğe|Açıklama|
    |-|-|
    |*Araçları yolu*|Profil Oluşturma Araçları komut satırı araçlarının yolu. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|
    |*VSPFile*|Profil oluşturma verileri (.*VSP* veya. *vsps*) dosyasýný. Tam ve kısmi yollar kabul edilir.|
    |Xml|XML biçimli bir rapor oluşturur.|

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Windows için olay Izleme (ETW) verileri toplama](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)
- [Profil araçları API 'Leri](../profiling/profiling-tools-apis.md)
