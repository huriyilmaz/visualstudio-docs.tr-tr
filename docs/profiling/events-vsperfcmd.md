---
title: Olaylar (VSPerfCmd) | Microsoft Docs
description: VSPerfCmd.exe komut satırı aracında olaylar seçeneğini kullanarak Windows (ETW) günlüğü için olay izlemeyi denetleme. Sözdizimi parametrelerini gözden geçirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 268efb7e76ea4b2357b0ef1047ee2076f340dc29
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122039000"
---
# <a name="events-vsperfcmd"></a>Olaylar (VSPerfCmd)
*VSPerfCmd.exe* **Events** seçeneği, Windows (ETW) günlüğe kaydetme için olay izlemeyi denetler. ETW verileri, profil oluşturucu veri dosyasından ayrı bir. etl dosyasına kaydedilir. Veriler [VSPerfReport](../profiling/vsperfreport.md) /Summary: ETW komutu kullanılarak bir raporda görüntülenebilir.

 Profil oluşturma işlemini durdurmak için VSPerfCmd **kapatmadan** önce herhangi bir zamanda **Olaylar** seçeneği çağrılabilir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametreler
 **&#124;** **kapalı** , olay verilerini toplamayı başlatır veya sonlandırır.

 `Guid` Sağlayıcı denetiminin GUID 'SI.

 `ProviderName`Windows Yönetim Araçları (wmı) ile kaydedilen sağlayıcının adı.

 `Flags` Olay sağlayıcısı tarafından tanımlanan bir "0x"-önekli onaltılık bayraklar değeri.

 `Level` Toplanan veri miktarını belirtir. `Level` Olay sağlayıcısı tarafından tanımlanır.

 **Olaylar** seçeneği, aşağıdaki çekirdek anahtar sözcüklerini sağlayıcı adları olarak anlamıştır:

 **İşlem** Olayları işle

 **Iş parçacığı** İş parçacığı olayları

 **Görüntü** Görüntü yükleme ve kaldırma olayları

 **Disk** Disk g/ç olayları

 **Dosya** Dosya g/ç olayları

 **Hardfault** Sabit sayfa hataları

 **Pagefault** Geçici sayfa hataları

 **Ağ** Ağ olayları

 **Kayıt defteri** Kayıt defteri erişim olayları

 Çekirdek sağlayıcının yalnızca etkinleştiğine de emin olun. İzleyici kapanana kadar devre dışı bırakılamaz veya bayrakları değiştirilemez.

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> CLR ETW olayları etkinleştirildiğinde, Izleme görünümü raporunda ek başlangıç verileri de toplanır. Raporda görünen başlangıç olaylarını dışlamak için aşağıdaki komutu kullanın:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Başlangıç olaylarını dışlayamazsınız, bu olaylar Yönetilen Nesne Biçimi (MOF) dosyasında listelenmediğinden raporda GUID olarak görünürler. Daha fazla bilgi için Microsoft Web sitesindeki şu sayfaya bakın: [örnek yönetilen nesne biçimi (MOF) dosyası](https://msdn.microsoft.com/library/default.aspx).

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
