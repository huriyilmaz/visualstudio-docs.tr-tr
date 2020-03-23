---
title: Etkinlikler (VSPerfCmd) | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 46b47f9b615c824d25e931cd3d05f5d2a04257ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777327"
---
# <a name="events-vsperfcmd"></a>Olaylar (VSPerfCmd)
*VSPerfCmd.exe* **Events** seçeneği, Windows (ETW) günlüğe kaydetme için Olay İzleme'yi denetler. ETW verileri profil oluşturucu veri dosyasından ayrı bir .etl dosyasına kaydedilir. Veriler [VSPerfReport](../profiling/vsperfreport.md) /summary:etw komutu kullanılarak bir raporda görüntülenebilir.

 **Olaylar** seçeneği, profil oluşturmayı durdurmak için VSPerfCmd **Kapatma** komutu çağrılmadan önce istediği zaman çağrılabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametreler
 **&#124;** **Kapalı** Başlar'da veya olay verilerini toplamayı durdurur.

 `Guid`Sağlayıcı denetiminin GUID'i.

 `ProviderName`Windows Yönetim Araçları (WMI) ile kayıtlı sağlayıcının adı.

 `Flags`Olay sağlayıcısı tarafından tanımlanan "0x" önceden belirlenmiş hexadecimal bayraklar değeri.

 `Level`Toplanan veri miktarını belirtir. `Level`olay sağlayıcısı tarafından tanımlanır.

 **Etkinlikler** seçeneği sağlayıcı adları olarak aşağıdaki çekirdek anahtar kelimeleri anlar:

 **İşlem** Olayları işleme

 **İş Parçacığı** İş parçacığı olayları

 **Resim** Görüntü yükleme ve boşaltma olayları

 **Disk** Disk G/Ç olayları

 **Dosya** Dosya G/Ç olayları

 **Sert hata** Sabit sayfa hataları

 **Pagefault** Yumuşak sayfa hataları

 **Ağ** Ağ olayları

 **Kayıt Defteri** Kayıt defteri erişim olayları

 Çekirdek Sağlayıcının yalnızca etkinleştirilebileceğine dikkat edin. İzleyici kapanana kadar devre dışı tutulamaz ve bayrakları değiştirilemez.

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> CLR ETW olayları etkinleştirildiğinde, İzleme Görünümü raporunda ek başlangıç verileri de toplanır. Başlangıç olaylarının raporda görünmesini engellemek için aşağıdaki komutu kullanın:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Başlangıç olaylarını hariç tutmazsanız, bu olaylar Yönetilen Nesne Biçimi (MOF) dosyasında listelenmediği için, bunlar raporda GUID olarak görünür. Daha fazla bilgi için Microsoft Web sitesindeki bu sayfaya bakın: [Örnek Yönetilen Nesne Biçimi (MOF) dosyası.](https://msdn.microsoft.com/library/default.aspx)

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
