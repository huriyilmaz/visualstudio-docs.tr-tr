---
title: Ekle | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 482b3e80bce796910860cb7eab1e5a0066854238
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85329865"
---
# <a name="attach"></a>İliştir
*VSPerfCmd.exe* **Attach** seçeneği, işlem kimliği (PID) tarafından belirtilen çalışan işlemin örnek profilini oluşturmaya başlar.

 **Attach** seçeneğini kullanmak Için, başlangıç seçeneğinde **örnek** yöntemi belirtmeniz gerekir.

> [!NOTE]
> **Başlangıç** seçeneği **CrossSession** seçeneğiyle belirtilmişse, **VSPerfCmd/Attach** veya **VSPerfCmd/detach** öğesine yapılan çağrılar de **CrossSession**belirtmelidir.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametreler
 `ProcessID`Çalışan işlemin işlem KIMLIĞI (PID). Çalışan bir işlemin PID 'SI Windows Görev Yöneticisi 'nin Işlemler sekmesinde listelenir.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki **VSPerfCmd** seçenekleri tek bir komut satırında **Attach** seçeneğiyle birleştirilebilir.

 **CrossSession** , Oturum açma oturumu dışındaki oturumlarda profil oluşturma uygulamalarına izin vermez. **CrossSession** seçeneğiyle **Start** seçeneği belirtilmişse gereklidir.

 **Başlangıç:** `Method` Komut satırı profil oluşturucu oturumunu başlatır ve belirtilen profil oluşturma yöntemini ayarlar.

 **Targetclr** Profil oluşturma oturumunda birden fazla sürüm yüklendiğinde profile yapılacak .NET Framework ortak dil çalışma zamanının (CLR) sürümünü belirtir. Varsayılan olarak, ilk yüklenen sürüm profili oluşturulur.

 **GlobalOn GlobalOn** Profil oluşturmayı sürdürür (**GlobalOn**) veya duraklatır (**globaloff**), ancak profil oluşturma oturumunu sonlandırmaz.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Belirtilen işlem için devam eder (**ProcessOn**) veya duraklar (**ProcessOff**) profili oluşturma.

## <a name="interval-options"></a>Aralık seçenekleri
 Aşağıdaki örnekleme aralığı seçeneklerinden biri, Attach komut satırında belirlenebilir. Varsayılan örnekleme aralığı 10.000.000 işlemci saat döngülerinde bulunur.

 **Süreölçer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[<strong>:</strong>Events]**sayaç**[**:** `Name` , `Reload` , `FriendlyName` ] örnekleme aralığının sayısını ve türünü belirtir.

- **Zamanlayıcı** -her `Cycles` işlemci saati döngüsünü örnekler. `Cycles`Belirtilmezse, 10.000.000 döngüsü kullanılır.

- **PF** -her `Events` sayfa hatalarını örnekler. `Events`Belirtilmezse, 10 sayfa hatası kullanılır.

- **Sys** - `Events` işletim sistemine yapılan her çağrının örnekleri. `Events`Belirtilmezse, 10 sistem çağrısı kullanılır.

- **Sayaç** -örnekleri `Reload` tarafından BELIRTILEN her sayıdaki CPU performans sayacı `Name` . İsteğe bağlı olarak, `FriendlyName` profil oluşturucu raporlarında sütun üst bilgisi olarak kullanılacak bir dize belirtebilir.

## <a name="example"></a>Örnek
 Bu örnek, 12345 işlem KIMLIĞIYLE uygulamanın çalışan bir örneğine nasıl ekleneceğini gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
