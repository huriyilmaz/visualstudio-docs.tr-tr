---
title: Başlat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c910ef1519181f1402cbec1d31686492e30f343d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154760"
---
# <a name="launch"></a>Başlat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Başlatma** seçeneği, örnekleme yöntemini kullanarak profil oluşturucuyu başlatır ve ayrıca belirtilen uygulamayı başlatır.  
  
 **Başlatma** seçeneğini kullanmak Için, **Başlangıç** seçeneğinde **örnek** yöntemi belirtmeniz gerekir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `AppName`  
 Başlatılacak uygulamanın adı. Geçerli dizinden gelen tam ve kısmi yollar desteklenir.  
  
## <a name="valid-options"></a>Geçerli seçenekler  
 Aşağıdaki VSPerfCmd seçenekleri tek bir komut satırında **başlatma** seçeneği ile birleştirilebilir.  
  
 **Başlangıç:**`Method`  
 Komut satırı profil oluşturucu oturumunu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.  
  
 **GlobalOn** ve **globaloff**  
 Profil oluşturmayı sürdürür (**GlobalOn**) veya duraklatır (**globaloff**), ancak profil oluşturma oturumunu sonlandırmaz.  
  
 **ProcessOn:** `PID` ve **ProcessOff**:`PID`  
 Belirtilen işlem için devam eder (**ProcessOn**) veya duraklar (**ProcessOff**) profili oluşturma.  
  
 **TargetCLR**  
 Profil oluşturma oturumunda birden fazla sürüm yüklendiğinde profile yapılacak .NET Framework ortak dil çalışma zamanının (CLR) sürümünü belirtir. Varsayılan olarak, ilk yüklenen sürüm profili oluşturulur.  
  
## <a name="exclusive-options"></a>Dışlamalı seçenekler  
 Aşağıdaki seçenekler yalnızca **başlatma** seçeneği ile kullanılabilir.  
  
 **Konsol**  
 Belirtilen komut satırı uygulamasını yeni bir pencerede başlatır.  
  
 **Bağımsız değişkenler:**`ArgList`  
 Uygulamaya geçirilecek bağımsız değişkenlerin listesini belirtir.  
  
 **LineOff**  
 Satır düzeyi profil oluşturma verilerinin koleksiyonunu devre dışı bırakır.  
  
## <a name="sampling-options"></a>Örnekleme seçenekleri  
 **Başlatma** komut satırında aşağıdaki örnekleme aralığı seçeneklerinden biri belirtilebilir. Varsayılan örnekleme aralığı 10.000.000 işlemci saat döngülerinde bulunur.  
  
 **Süreölçer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[**:** `Events` ]**Counter**[**:** `Name` , `Reload` , `FriendlyName` ]**GC**[:**ayırma**&#124;**ömrü**]  
 Örnekleme aralığının sayısını ve türünü belirtir.  
  
- **Zamanlayıcı** - `Cycles` durdurulmayan her işlemci saati döngüsünü örnekler. `Cycles`Belirtilmezse, 10.000.000 döngüsü kullanılır.  
  
- **PF** -her `Events` sayfa hatalarını örnekler. `Events`Belirtilmezse, 10 sayfa hatası.  
  
- **Sys** - `Events` işletim sistemine yapılan her çağrının örnekleri. `Events`Belirtilmezse, 10 sistem çağrısı kullanılır.  
  
- **Sayaç** -örnekleri `Reload` tarafından BELIRTILEN her sayıdaki CPU performans sayacı `Name` . İsteğe bağlı olarak, `FriendlyName` profil oluşturucu raporlarında sütun üst bilgisi olarak kullanılacak bir dize belirtebilir.  
  
- **GC** -.net bellek verilerini toplar. Varsayılan olarak,**allocation**veriler her bellek ayırma olayında toplanır. **Ömür** parametresi belirtildiğinde her çöp toplama olayında de veriler toplanır.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir uygulamayı başlatmak için **başlatma** kullanımını gösterir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
