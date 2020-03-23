---
title: VSPerfASPNetCmd | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 8c9bf465b4da7f305e97a18099a7e27db8eab6b4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778017"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
**VSPerfASPNetCmd.exe** komut satırı aracı, ortam değişkenleri ayarlamanız veya bilgisayarınızı yeniden başlatmanız gerekmeden ASP.Net web sitelerinin profilini çıkarmanızı sağlar. ASP.NET web sitelerinin profilini çıkarırken [VSPerfCmd](../profiling/vsperfcmd.md) yerine **VSPerfASPNetCmd.exe** kullanın ve **VSPerfCmd**tarafından sağlanan ek işlevselliğe ihtiyacınız yoktur. **VSPerfASPNetCmd**hakkında daha fazla bilgi için, [VSPerfASPNETCmd ile Hızlı web sitesi profilleme](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)bakın. **VSPerfASPNetCmd,** bir ASP.NET web sitesinin profilini çıkarmak için bağımsız profil oluşturucuyu kullanırken kullanılacak tercih edilen komut satırı aracıdır.

## <a name="syntax"></a>Sözdizimi
 **vsperfaspnetcmd** [/*Seçenekler*] *Web Sitesi*

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|**/Örnek** veya **/s**|Örnekleme yöntemini kullanarak profiller web sitesi. **/Örnek** varsayılan yöntemdir. /Örnek **/Trace**ile kullanılamaz.|
|**/İzleme** veya **/t**|Enstrümantasyon yöntemini kullanarak profiller web sitesi. /Trace **/Sample**ile kullanılamaz.|
|**/Bellek**[**:**`Type`]veya **/m**[**{****a**&#124;**l**}]|Profiller bellek ayırma ve isteğe bağlı profiller nesne yaşam alanları (çöp toplama). **/Bellek** örnekleme veya enstrümantasyon yöntemi ile kullanılabilir.<br /><br /> *Türü* aşağıdakilerden biri olabilir:<br /><br /> -   **ayırma** (veya **a)** yalnızca bellek ayırma verilerini toplar.<br />-   **yaşam süresi** (veya **l)** bellek ayırma ve nesne yaşam boyu verileri toplar.<br /><br /> Varsayılan `Type` **ayırmadır.**|
|**/İpucu** veya **/i**|Profil oluşturma verilerine ayrıntılı ASP.NET isteği ve çağrı bilgilerini ADO.NET ekler. **/İpucu** örnekleme veya enstrümantasyon yöntemi ile kullanılabilir ve **/Bellek** seçeneği ile kullanılabilir.|
|**/Çıkış:** `File` veya **/o:**`File`|Profil oluşturma verilerinin yol ve dosya adını belirtir (.* vsp*) dosyası.|
|**/NoWait** veya **/n**|Komut istemi penceresinde ek komutların kullanılabileceğini bilmek için komut istemini hemen döndürür. Profil oluşturmayı kapatmak için ayrı bir komut satırına **VSPerfASPNETCmd /Shutdown** yazmanız gerekir.|
|**/PackSymbols**[:{**&#124;** **kapalı**}veya **/p**[:{ kapalı **&#124;****}**|Profil oluşturma verilerine semboller (işlev ve parametre adları, vb.) yerle bir eder (.* vsp*) dosyası.|
|**/Shutdown:** `Website`veya **/d:**`Website`|Profil oluşturmayı kapatır. Profil oluşturmayı başlatmak için **/NoWait** seçeneğini kullandıktan sonra veya profil oluşturma yı başlatmak için komut satırında tek seçenek olarak kullanın. Orijinal **VSPerfASPNETCmd** komutunda kullandığınız url'yi belirtin.|
|`Website`|Profili yapılacak web sitesinin url'si.|

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfASPNETCmd ile hızlı web sitesi profiloluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
