---
title: Durum | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bf5e0fdf478e067f61b1d0e259cb1624380e4f02
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778251"
---
# <a name="status"></a>Durum
*VSPerfCmd.exe* **Durum** seçeneği, profil oluşturucunun durumu ve şu anda profili üzerinde bulunan işlemler hakkında bilgi görüntüler.

 **Durum** seçeneği komut satırında belirtilen tek seçenek olmalıdır. Herhangi bir durum görüntülenmeden önce profil oluşturucu *VSPerfCmd.exe* **Başlat** seçeneği ile başlatılmalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametreler
 None

## <a name="remarks"></a>Açıklamalar
 **Durum** seçeneği profil oluşturucu için aşağıdaki durum bilgilerini görüntüler.

 **Çıktı Dosya Adı** Geçerli profil oluşturucu veri dosyasının yol ve dosya adı.

 **Toplama Modu** ÖRNEK veya TRACE

 **Maksimum Süreçler** Aynı anda profillenebilen maksimum işlem sayısı ve şu anda etkin olan işlemlerin sayısı.

 **Maksimum İş Parçacıkları** Aynı anda profillenebilen maksimum iş parçacığı sayısı.

 **Arabellek Sayısı** Profil oluşturma verilerini yazmaya adanmış bellek arabelleklerinin sayısı.

 **Arabellek Boyutu** Bellek arabelleği baytboyutu.

 **Durum** seçeneği, şu anda profili üzerinde olan her işlem için aşağıdaki durum bilgilerini görüntüler.

 **İşlem** Profilli işlemin adı.

 **İşlem Kimliği** İşlemin sistem tanımlayıcısı.

 **Num Konuları** Şu anda çalıştırılabilen iş parçacığı sayısı.

 **Başlat/Durdur Sayısı** Birincil iç profil oluşturucu, bu işlem için veri toplamayı denetlemek için sayılır. Veri toplamak için sayım bire eşit olmalıdır. Start/Stop sayısı profilci API'leri ve VSPerfCmd seçenekleri **GlobalOn,** **GlobalOff,** **ProcessOn**, **ProcessOff**, **ThreadOn**ve **ThreadOff**tarafından manipüle edilebilir.

 **Askıya Alma/Devam Sayısı** Bu işlem için veri toplamayı denetlemek için ikincil dahili profil oluşturucu sayısı. Veri toplamak için sayım sıfırdan az veya eşit olmalıdır. **Askıya Alma/Devam** sayısı yalnızca profilci API'leri tarafından işlenebilir.

 **İzlemek için erişim hakkına sahip kullanıcılar** Profil oluşturucuya erişimi olan kullanıcıların adlarını listeler. Ek kullanıcılara VSPerfCmd.exe **Admin** seçeneğini kullanarak erişim hakkı verilebilir

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
