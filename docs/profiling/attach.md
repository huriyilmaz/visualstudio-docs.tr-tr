---
title: Ekleme | Microsoft Docs
description: İşlem Kimliği (PID) VSPerfCmd.exe çalışan sürecin profilini oluşturmayı başlamak için Ekle seçeneğini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 2764b98e41b5f6261947c18b9cb0bede6bff0511
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136403"
---
# <a name="attach"></a>İliştir
Ekle *VSPerfCmd.exe,*  işlem kimliği (PID) tarafından belirtilen çalışan işlem için örnek profil oluşturma işlemiyle başlar.

 Ekle seçeneğini **kullanmak** için Başlat seçeneğinde **Örnek** yöntemi belirtmeniz gerekir.

> [!NOTE]
> Kesişim  seçeneğiyle Başlat  seçeneği belirtilmişse **VSPerfCmd /Attach veya VSPerfCmd** **/Detach** çağrıları da Çapraz Geçiş seçeneğini **belirtilmelidir.**

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametreler
 `ProcessID` Çalışan sürecin işlem kimliği (PID). Çalışan bir sürecin PID'i, Görev Yöneticisi'nin Windows listelenir.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki **VSPerfCmd** seçenekleri, tek bir komut satırı **üzerinde Ekle** seçeneğiyle birlikte kullanılabilir.

 **Çapraz geçiş** Oturum açma oturumu dışında oturumlarda uygulamaların profilini oluşturmayı sağlar. Başlat seçeneği **Çapraz** Geçiş **seçeneğiyle belirtilmişse** gereklidir.

 **Başlat:** `Method` Komut satırı profil oluşturma oturumunu başlatan ve belirtilen profil oluşturma yöntemini ayarlar.

 **TargetCLR** Profil oluşturma oturumunda birden .NET Framework profili oluşturmak için Ortak Dil Çalışma Zamanı 'nın (CLR) sürümünü belirtir. Varsayılan olarak, yüklenen ilk sürümün profili 4.0'tır.

 **GlobalOn GlobalOff** (**GlobalOn**) veya duraklatarak (**GlobalOff**) profil oluşturmayı sürdürür, ancak profil oluşturma oturumunu sona erer.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Belirtilen işlem için Resumes (**ProcessOn**) veya duraklatılır (**ProcessOff**) profili oluşturma.

## <a name="interval-options"></a>Aralık seçenekleri
 Aşağıdaki örnekleme aralığı seçenekleri, Ekle komut satırı üzerinde belirtilebilir. Varsayılan örnekleme aralığı 10.000.000 işlemci saat döngüsüdür.

 **Zamanlayıcı**[**:** `Cycles` ]**PF**[**:** `Events` ]**Sys**[<strong>:</strong>Events]**Counter**[**:**, ] Örnekleme `Name` `Reload` `FriendlyName` aralığının sayısını ve türünü belirtir.

- **Süreölçer** - Her işlemci `Cycles` saat döngüsü örneği. `Cycles`Belirtilmezse 10.000.000 döngü kullanılır.

- **PF** - Her sayfa `Events` hatalarını örnekler. `Events`Belirtilmezse, 10 sayfa hatası kullanılır.

- **Sys** - İşletim sistemine `Events` yapılan her çağrıyı örnekler. `Events`Belirtilmezse, 10 sistem çağrısı kullanılır.

- **Sayaç** - tarafından belirtilen `Reload` her sayıda CPU performans sayacını `Name` örnekler. İsteğe bağlı `FriendlyName` olarak, profil oluşturma raporlarında sütun üst bilgisi olarak kullanmak üzere bir dize belirtebilirsiniz.

## <a name="example"></a>Örnek
 Bu örnek, 12345 işlem kimliğine sahip bir uygulamanın çalışan örneğine nasıl ekli olduğunu gösteriyor.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
