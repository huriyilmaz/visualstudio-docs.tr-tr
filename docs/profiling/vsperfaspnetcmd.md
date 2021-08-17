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
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 72cdbacef70ec64567333cc11e88eb761d44beebc64d05b61f32a90edfd53b11
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121230904"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** komut satırı aracı, ortam değişkenlerini ayarlamanıza veya bilgisayarınızı yeniden başlatmanıza gerek kalmadan ASP.NET Web sitelerini profiletmenize olanak tanır. ASP.NET web siteleri profilini oluştururken [vsperfcmd](../profiling/vsperfcmd.md) yerine **VSPerfASPNetCmd.exe** kullanın ve **vsperfcmd** tarafından sunulan ek işlevlere ihtiyacınız yoktur. **VSPerfASPNETCmd** hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **vsperfaspnetcmd** , bir ASP.NET web sitesini profil için tek başına profil oluşturucu kullandığınızda kullanılacak tercih edilen komut satırı aracıdır.

## <a name="syntax"></a>Syntax
 **VSPerfASPNETCmd** [/*Options*] *Web sitesi*

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|**/Sample** veya   **/s**|Örnekleme yöntemini kullanarak Profiles Web sitesi. **/Sample** varsayılan yöntemdir. /Sample, **/Trace** ile birlikte kullanılamaz.|
|**/Trace** veya   **/t**|İzleme yöntemini kullanarak profiller Web sitesi. /Trace, **/Sample** ile kullanılamaz.|
|**/Memory**[**:** `Type` ] veya **/m**[**:**{**a**&#124;**l**}]|Profiller bellek ayırma ve isteğe bağlı olarak profiller nesne yaşam süreleri (çöp toplama). **/Memory** , örnekleme veya izleme yöntemiyle birlikte kullanılabilir.<br /><br /> *Tür* aşağıdakilerden biri olabilir:<br /><br /> -   **ayırma** (veya **a**) yalnızca bellek ayırma verilerini toplar.<br />-   **yaşam süresi** (veya **l**), bellek ayırma ve nesne yaşam süresi verilerini toplar.<br /><br /> Varsayılan değer `Type` **ayırma**' dır.|
|**/Ipucu** veya   **/i**|profil oluşturma verilerine ayrıntılı ASP.NET isteği ve ADO.NET çağrı bilgilerini ekler. **/Tıp** , örnekleme veya izleme yöntemiyle birlikte kullanılabilir ve **/Memory** seçeneğiyle birlikte kullanılabilir.|
|**/Output:** `File` veya   **/o:**`File`|Profil oluşturma verilerinin yolunu ve dosya adını belirtir (.*VSP*) dosyası.|
|**/Nowait** veya   **/n**|Komut istemi penceresinde ek komutların kullanılabilmesi için, komut istemi ' ni hemen döndürür. Profil oluşturmayı devre dışı bırakmak için ayrı bir komut satırına **VSPerfASPNETCmd/Shutdown** yazmanız gerekir.|
|**/Packsymbols**[: {**on**&#124;**off**} veya   **/p**[: {**on**&#124;**off**}|Profil oluşturma verilerinde sembolleri (işlev ve parametre adları, vb.) katıştırır (.*VSP*) dosyası.|
|**/Shutdown:** `Website` or   **/d:**`Website`|Profil oluşturmayı devre dışı bırakır. Profil oluşturmayı başlatmak için **ya da profil** Oluşturucu beklenmedik bir şekilde sona erdiğinde, bir komut satırında tek seçenek olarak kullanın. Özgün **VSPerfASPNETCmd** komutunda kullandığınız URL 'yi belirtin.|
|`Website`|Profili oluşturulacak Web sitesinin URL 'si.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
