---
title: Durum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f64364caf914c030fef806c5ae17e90a8368fa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157793"
---
# <a name="status"></a>Durum
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Status** seçeneği, profil oluşturucunun durumu ve şu anda profili oluşturulan tüm süreçler hakkındaki bilgileri görüntüler.  
  
 **Durum** seçeneği, komut satırında belirtilen tek seçenek olmalıdır. Herhangi bir durumun görüntülenebilmesi için profil oluşturucunun VSPerfCmd.exe **Start** seçeneğiyle başlatılması gerekir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### <a name="parameters"></a>Parametreler  
 Hiçbiri  
  
## <a name="remarks"></a>Açıklamalar  
 **Durum** seçeneği, Profil Oluşturucu için aşağıdaki durum bilgilerini görüntüler.  
  
 **Çıkış dosyası adı**  
 Geçerli profil oluşturucu veri dosyasının yolu ve dosya adı.  
  
 **Toplama modu**  
 ÖRNEK veya Izleme  
  
 **En fazla Işlem**  
 Tek seferde profili oluşturulabilecek en fazla işlem sayısı ve şu anda etkin olan işlem sayısı.  
  
 **En fazla Iş parçacığı**  
 Tek seferde profili oluşturulabilecek en fazla iş parçacığı sayısı.  
  
 **Arabellek sayısı**  
 Profil oluşturma verilerini yazmak için ayrılan bellek arabelleği sayısı.  
  
 **Arabelleklerin boyutu**  
 Bellek arabelleğinin bayt cinsinden boyutu.  
  
 **Durum** seçeneği, şu anda profili oluşturulan her işlem için aşağıdaki durum bilgilerini görüntüler.  
  
 **İşleme**  
 Profili oluşturulan işlemin adı.  
  
 **İşlem Kimliği**  
 İşlemin sistem tanımlayıcısı.  
  
 **Iş parçacığı sayısı**  
 Şu anda yürütülmekte olan iş parçacıklarının sayısı.  
  
 **Başlangıç/durdurma sayısı**  
 Bu işlem için veri toplamayı denetlemek üzere birincil iç profil oluşturucu sayısı. Sayım, veri toplamak için bire eşit olmalıdır. Başlat/Durdur sayısı profil oluşturucu API 'Leri ve VSPerfCmd seçenekleri **GlobalOn**, **globaloff**, **ProcessOn**, **ProcessOff**, **ThreadOn**ve **ThreadOff**tarafından yönetilebilir.  
  
 **Askıya alma/sürdürülme sayısı**  
 Bu işlem için veri toplamayı denetlemek üzere ikincil iç profil oluşturucu sayısı. Sayım, veri toplamak için sıfırdan küçük veya sıfıra eşit olmalıdır. **Askıya alma/sürdürülme** sayısı yalnızca profil oluşturucu API 'leri tarafından yönetilebilir.  
  
 **İzlemek için erişim haklarına sahip kullanıcılar**  
 Profil oluşturucuya erişimi olan kullanıcıların adlarını listeler. Ek kullanıcılara, VSPerfCmd.exe **yönetici** seçeneği kullanılarak erişim verilebilir  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
