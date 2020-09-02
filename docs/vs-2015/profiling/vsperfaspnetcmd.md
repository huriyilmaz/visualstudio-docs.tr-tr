---
title: VSPerfASPNetCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools,VSPerfASPNETCmd
- VSPerfASPNETCmd
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9cb81f17abd1e7891dc3f78a85d6d1276991f070
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145282"
---
# <a name="vsperfaspnetcmd"></a>VSPerfASPNetCmd
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Komut satırı aracı **VSPerfASPNetCmd.exe** , ortam değişkenlerini ayarlamanıza veya bilgisayarınızı yeniden başlatmanıza gerek kalmadan ASP.NET Web sitelerini profillerinizi düzenlemenize olanak tanır. ASP.NET Web siteleri profilini oluştururken [VSPerfCmd](../profiling/vsperfcmd.md) yerine **VSPerfASPNetCmd.exe** kullanın ve **VSPerCmd**tarafından sunulan ek işlevlere ihtiyacınız yoktur. **VSPerfASPNETCmd**hakkında daha fazla bilgi için bkz. [VSPerfASPNETCmd Ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md). **VSPerfASPNETCmd** , bir ASP.NET Web sitesini profil için tek başına profil oluşturucu kullandığınızda kullanılacak tercih edilen komut satırı aracıdır.  
  
## <a name="syntax"></a>Syntax  
 **VSPerfASPNETCmd** [/*Options*] *Web sitesi*  
  
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|**/Sample** veya   **/s**|Örnekleme yöntemini kullanarak Profiles Web sitesi. **/Sample** varsayılan yöntemdir. /Sample, **/Trace**ile birlikte kullanılamaz.|  
|**/Trace** veya   **/t**|İzleme yöntemini kullanarak profiller Web sitesi. /Trace, **/Sample**ile kullanılamaz.|  
|**/Memory**[**:** `Type` ] veya **/m**[**:**{**a**&#124;**l**}]|Profiller bellek ayırma ve isteğe bağlı olarak profiller nesne yaşam süreleri (çöp toplama). **/Memory** , örnekleme veya izleme yöntemiyle birlikte kullanılabilir.<br /><br /> *Tür* aşağıdakilerden biri olabilir:<br /><br /> -   **ayırma** (veya **a**) yalnızca bellek ayırma verilerini toplar.<br />-   **yaşam süresi** (veya **l**), bellek ayırma ve nesne yaşam süresi verilerini toplar.<br /><br /> Varsayılan değer `Type` **ayırma**' dır.|  
|**/Ipucu** veya   **/i**|Profil oluşturma verilerine ayrıntılı ASP.NET isteği ve ADO.NET çağrı bilgisi ekler. **/Tıp** , örnekleme veya izleme yöntemiyle birlikte kullanılabilir ve **/Memory** seçeneğiyle birlikte kullanılabilir.|  
|**/Output:** `File` veya   **/o:**`File`|Profil oluşturma verileri (. vsp) dosyasının yolunu ve dosya adını belirtir.|  
|**/Nowait** veya   **/n**|Komut istemi penceresinde ek komutların kullanılabilmesi için, komut istemi ' ni hemen döndürür. Profil oluşturmayı devre dışı bırakmak için ayrı bir komut satırına **VSPerfASPNETCmd/Shutdown** yazmanız gerekir.|  
|**/Packsymbols**[: {**on**&#124;**off**} veya   **/p**[: {**on**&#124;**off**}|Profil oluşturma verileri (. vsp) dosyasındaki sembolleri (işlev ve parametre adları, vb.) katıştırır.|  
|**/Shutdown:** `Website` or   **/d:**`Website`|Profil oluşturmayı devre dışı bırakır. Profil oluşturmayı başlatmak için **ya da profil** Oluşturucu beklenmedik bir şekilde sona erdiğinde, bir komut satırında tek seçenek olarak kullanın. Özgün **VSPerfASPNETCmd** komutunda kullandığınız URL 'yi belirtin.|  
|`Website`|Profili oluşturulacak Web sitesinin URL 'si.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfASPNETCmd ile hızlı web sitesi profili oluşturma](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [ASP.NET Web Uygulamalarında Profil Oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
