---
title: VSPerfMon | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 50519554f7ec71e277dc776b05bc2967c1071f52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779902"
---
# <a name="vsperfmon"></a>VSPerfMon
Bir uygulama için performans verileri toplamak için VSPerfMon aracını kullanabilirsiniz; genellikle bu araç *VSPerfCmd.exe*tarafından başlatılır. VSPerfMon, VSPerfCmd aracını kullanarak kullanılamayan proses ekleme veya ayırma hakkında ek bilgiler görüntüler. Bu bilgileri görüntülemek için, vsPerfMon'u ayrı bir pencerede başlatın. VSPerfMon çağırmak için aşağıdaki sözdizimini kullanın:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Aşağıdaki tabloda VSPerfMon takım seçenekleri açıklanmaktadır:

|Seçenekler|Açıklama|
|-------------|-----------------|
|**U**|Yönlendirilen konsol çıktısı Unicode olarak yazılır.  Bu belirtilen ilk seçenek olmalıdır.|
|**OUTPUT:** `<` *dosya adı*`>`|Çıktıyı belirtilen dosya adına yönlendirir.|
|**Izleme**|Enstrümanting profilleme için performans monitörü başlatır.|
|**Örnek**|Profil örneklemesi için performans monitörünü başlatır.|
|**Kapsama**|Kod kapsamı koleksiyonu için performans monitörünü başlatır.|
|**Eşzamanlılık**|Kaynak çekişmesi profiloluşturma için performans izleme başlatın.|
|**KULLANICI:** `[` *alan adı* `\]` *kullanıcı adı*|İstemci belirtilen hesaptan performans monitörüne erişim sağlar.|
|**Crosssession**|Oturumlar arası profil oluşturmayı sağlar.|
|**SAYAÇ**`:cfg`|Enstrümantasyon (TRACE) profil oluşturma yöntemi kullanıldığında, her enstrümantasyon noktasında toplanacak bir CPU sayacı belirtir. Birden çok Sayaç seçeneği belirterek birden çok sayaç verisi toplayabilirsiniz.<br /><br /> Sayaç *(cfg*) verilerini belirtmek için aşağıdaki sözdizimini kullanın:<br /><br /> **CounterName** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **CounterName,** VSPerfCmd /QueryCounters komutu tarafından döndürülen bir sayacın adıdır.<br />-   **Yeniden yükleme,** karşı olay örnekleme aralığıdır. Enstrümantasyon yöntemiyle *Yeniden Yükle'yi* kullanmayın.<br />- Belirtildiğinde, **FriendlyName** Profil Oluşturma Araçları rapor sütun adlarında **CounterName'nin** yerini alır.|
|**WINCOUNTER**`:path`|İşaret verileriyle birlikte dahil olacak bir Windows performans sayacı belirtir. `path`PDH sayaç yolu biçiminde bir Windows Performance sayıcı dizesidir. Örnek:<br /><br /> \İşlemci(0)\\% İşlemci Süresi<br /><br /> \Sistem\Bağlam Anahtarları/sn|
|**AUTOMARK**`:n`|/WINCOUNTER kullanırken otomatik işaretler arasındaki zaman aralığını (milisaniye cinsinden) belirtir. En yakın 500ms kadar yuvarlatılmış.<br /><br /> Otomatik işaretleri devre dışı kalmak için 0 kullanın. (belirtilmemişse varsayılan=500m)|

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
