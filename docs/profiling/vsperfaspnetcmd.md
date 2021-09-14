---
title: VSPerfASPNetCmd | Microsoft Docs
description: VSPerfASPNetCmd.exe komut satırı aracının, ortam değişkenlerini ayarlamanıza veya bilgisayarınızı yeniden başlatmanıza gerek kalmadan web sitelerinin profilini oluşturmanızı nasıl ASP.Net olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0a496c0ab434ed115e28d88874e4fdbc64931f89
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725646"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
Komut **VSPerfASPNetCmd.exe** aracı, ortam değişkenlerini ayarlamanıza veya bilgisayarınızı ASP.Net gerek kalmadan web sitelerinin profilini oluşturmanızı sağlar. Web **VSPerfASPNetCmd.exe** profillerini oluşturma ve [VSPerfCmd](../profiling/vsperfcmd.md) tarafından sağlanan ek işlevlere ASP.NET **vsPerfCmd yerine vsPerfCmd kullanın.** **VSPerfASPNetCmd** hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)ile hızlı web sitesi profili oluşturma. **VSPerfASPNetCmd,** tek başına profilleyiciyi kullanarak bir web sitesi için profil oluşturmak üzere tercih edilen komut ASP.NET aracıdır.

## <a name="syntax"></a>Syntax
 **vsperfaspnetcmd** [/*Seçenekler*] *Web sitesi*

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|**/Sample** veya   **/s**|Örnekleme yöntemini kullanarak profiller web sitesi. **/Sample** varsayılan yöntemdir. /Sample , **/Trace ile kullanılamaz.**|
|**/Trace** veya   **/t**|Ölçümleme yöntemini kullanarak web sitesinin profilini oluşturun. /Trace , **/Sample ile kullanılamaz.**|
|**/Memory**[**:** `Type` ]or **/m**[**:**{**a&#124;** **l**}]|Bellek ayırma profilini oluşturur ve isteğe bağlı olarak nesne yaşam sürelerini (çöp toplama) profilini oluşturur. **/Memory** örnekleme veya ölçümleme yöntemiyle birlikte kullanılabilir.<br /><br /> *Tür,* aşağıdakilerden biri olabilir:<br /><br /> -   **ayırma** (veya **)** yalnızca bellek ayırma verilerini toplar.<br />-   **lifetime** (veya **l**) bellek ayırma ve nesne yaşam süresi verilerini toplar.<br /><br /> Varsayılan değer `Type` **ayırmadır.**|
|**/Tip** veya   **/i**|Profil oluşturma ASP.NET ayrıntılı ADO.NET ve çağrı bilgilerini ekler. **/Tip** örnekleme veya ölçüm yöntemiyle ve **/Memory** seçeneğiyle kullanılabilir.|
|**/Output:** `File` veya   **/o:**`File`|Profil oluşturma verisi yolunu ve dosya adını () belirtir.*vsp*) dosyasını seçin.|
|**/NoWait** veya   **/n**|Komut istemi penceresinde ek komutların kullanılası için komut istemini hemen döndürür. Profil oluşturmayı kapatmak **için ayrı bir komut satırına VSPerfASPNETCmd /Shutdown** yazmalısiniz.|
|**/PackSymbols****[:{**&#124;**}veya** **/p**[:{**&#124;** **kapalı**}|Profil oluşturma verilerine *(. vsp*) dosyasını seçin.|
|**/Shutdown:** `Website` veya   **/d:**`Website`|Profil oluşturmayı kapatıyor. Profil oluşturmayı başlatmak için **/NoWait** seçeneğini kullandıktan sonra veya profil oluşturma beklenmedik bir şekilde sona erdiğinde komut satırı üzerinde tek seçenek olarak kullanın. Özgün **VSPerfASPNETCmd komutunda kullanılan url'yi** belirtin.|
|`Website`|Profili oluşturmak için web sitesinin URL'si.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
