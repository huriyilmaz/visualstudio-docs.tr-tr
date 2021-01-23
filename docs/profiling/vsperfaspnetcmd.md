---
title: VSPerfASPNetCmd | Microsoft Docs
description: VSPerfASPNetCmd.exe komut satırı aracının, ortam değişkenlerini ayarlamanıza veya bilgisayarınızı yeniden başlatmanıza gerek kalmadan ASP.Net Web sitelerini nasıl profilinize izin verdiğini öğrenin.
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b594141d6209c8ede9171df880e7523b81a34775
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719233"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** komut satırı aracı, ortam değişkenlerini ayarlamanıza veya bilgisayarınızı yeniden başlatmanıza gerek kalmadan ASP.NET Web sitelerini profiletmenize olanak tanır. ASP.NET Web siteleri profilini oluştururken [VSPerfCmd](../profiling/vsperfcmd.md) yerine **VSPerfASPNetCmd.exe** kullanın ve **VSPerfCmd** tarafından sunulan ek işlevlere ihtiyacınız yoktur. **VSPerfASPNETCmd** hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNETCmd** , bir ASP.NET Web sitesini profil için tek başına profil oluşturucu kullandığınızda kullanılacak tercih edilen komut satırı aracıdır.

## <a name="syntax"></a>Syntax
 **VSPerfASPNETCmd** [/*Options*] *Web sitesi*

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|**/Sample** veya   **/s**|Örnekleme yöntemini kullanarak Profiles Web sitesi. **/Sample** varsayılan yöntemdir. /Sample, **/Trace** ile birlikte kullanılamaz.|
|**/Trace** veya   **/t**|İzleme yöntemini kullanarak profiller Web sitesi. /Trace, **/Sample** ile kullanılamaz.|
|**/Memory**[**:** `Type` ] veya **/m**[**:**{**a**&#124;**l**}]|Profiller bellek ayırma ve isteğe bağlı olarak profiller nesne yaşam süreleri (çöp toplama). **/Memory** , örnekleme veya izleme yöntemiyle birlikte kullanılabilir.<br /><br /> *Tür* aşağıdakilerden biri olabilir:<br /><br /> -   **ayırma** (veya **a**) yalnızca bellek ayırma verilerini toplar.<br />-   **yaşam süresi** (veya **l**), bellek ayırma ve nesne yaşam süresi verilerini toplar.<br /><br /> Varsayılan değer `Type` **ayırma**' dır.|
|**/Ipucu** veya   **/i**|Profil oluşturma verilerine ayrıntılı ASP.NET isteği ve ADO.NET çağrı bilgisi ekler. **/Tıp** , örnekleme veya izleme yöntemiyle birlikte kullanılabilir ve **/Memory** seçeneğiyle birlikte kullanılabilir.|
|**/Output:** `File` veya   **/o:**`File`|Profil oluşturma verilerinin yolunu ve dosya adını belirtir (.*VSP*) dosyası.|
|**/Nowait** veya   **/n**|Komut istemi penceresinde ek komutların kullanılabilmesi için, komut istemi ' ni hemen döndürür. Profil oluşturmayı devre dışı bırakmak için ayrı bir komut satırına **VSPerfASPNETCmd/Shutdown** yazmanız gerekir.|
|**/Packsymbols**[: {**on**&#124;**off**} veya   **/p**[: {**on**&#124;**off**}|Profil oluşturma verilerinde sembolleri (işlev ve parametre adları, vb.) katıştırır (.*VSP*) dosyası.|
|**/Shutdown:** `Website` or   **/d:**`Website`|Profil oluşturmayı devre dışı bırakır. Profil oluşturmayı başlatmak için **ya da profil** Oluşturucu beklenmedik bir şekilde sona erdiğinde, bir komut satırında tek seçenek olarak kullanın. Özgün **VSPerfASPNETCmd** komutunda kullandığınız URL 'yi belirtin.|
|`Website`|Profili oluşturulacak Web sitesinin URL 'si.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
