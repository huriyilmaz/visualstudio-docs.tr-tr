---
title: VSPerfMon | Microsoft Docs
description: Bir uygulama için performans verilerini toplamak üzere VSPerfMon aracını nasıl kullanabileceğinizi öğrenin. Bu araç genellikle VSPerfCmd.exe tarafından başlatılır.
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d7874686dc9a3ccb1774520d7521cfd557cf9b2d48b2c324f18bac78f420de7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367856"
---
# <a name="vsperfmon"></a>VSPerfMon
Bir uygulamanın performans verilerini toplamak için VSPerfMon aracını kullanabilirsiniz; genellikle bu araç *VSPerfCmd.exe* tarafından başlatılır. VSPerfMon, VSPerfCmd aracı kullanılarak kullanılamayan işlem iliştirme veya ayırma hakkında ek bilgiler görüntüler. Bu bilgileri görüntülemek için, VSPerfMon 'yi ayrı bir pencerede başlatın. VSPerfMon 'yi çağırmak için aşağıdaki sözdizimini kullanın:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 Aşağıdaki tabloda, VSPerfMon araç seçenekleri açıklanmaktadır:

|Seçenekler|Açıklama|
|-------------|-----------------|
|**Larınız**|Yeniden yönlendirilen konsol çıkışı Unicode olarak yazılmıştır.  Bu, belirtilen ilk seçenek olmalıdır.|
|**Çıkış:** `<` *dosya adı*`>`|Çıktıyı belirtilen dosya adına yönlendirir.|
|**IZLEMESININ**|Araçlı profil oluşturma için performans izleyicisini başlatır.|
|**SAMPLE**|Örnekleme profili oluşturma için performans izleyicisini başlatır.|
|**KAPLAMA**|Kod kapsamı koleksiyonu için performans izleyicisini başlatır.|
|**ZAMANLı**|Kaynak çakışması profili oluşturma için performans izleyicisini başlatır.|
|**Kullanıcı:** `[` *etki alanı* `\]` *Kullanıcı adı*|Belirtilen hesaptan performans izleyicisine istemci erişimine izin verir.|
|**CROSSSESSION**|Çapraz oturum profilini oluşturmayı mümkün.|
|**Sayaç**`:cfg`|İzleme (TRACE) profil oluşturma yöntemi kullanıldığında, her bir araç noktasında toplanacak bir CPU sayacı belirtir. Birden çok sayaç seçeneği belirterek birden çok sayaç verisi toplayabilirsiniz.<br /><br /> Sayaç (*cfg*) verilerini belirtmek için aşağıdaki sözdizimini kullanın:<br /><br /> **CounterName** [**, yeniden yükle**[,**FriendlyName**]]<br /><br /> -   **CounterName** , VSPerfCmd/QueryCounters komutu tarafından döndürülen bir sayacın adıdır.<br />-   **Yeniden yükleme** , sayaç olay örnekleme aralığıdır. İzleme yöntemiyle *yeniden yükleme* kullanmayın.<br />-Belirtildiğinde, **FriendlyName** profil oluşturma araçları rapor sütunu adlarında **CounterName** yerini alır.|
|**WinCounter**`:path`|işaretleme verileriyle birlikte içerilecek bir Windows performans sayacı belirtir. `path`, PDH sayaç yolu biçiminde bir Windows performans sayacı dizesidir. Örnek:<br /><br /> \ İşlemci (0) \\ % Işlemci zamanı<br /><br /> \System\Context geçişleri/sn|
|**Otomatik işaret**`:n`|/Wincounterkullandığınızda otomatik işaretler arasındaki zaman aralığını (milisaniye olarak) belirtir. En yakın 500 MS 'ye yuvarlanır.<br /><br /> Otomatik işaretleri devre dışı bırakmak için 0 kullanın. (belirtilmemişse varsayılan = 500ms)|

## <a name="see-also"></a>Ayrıca bkz.
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Performans raporu görünümleri](../profiling/performance-report-views.md)
