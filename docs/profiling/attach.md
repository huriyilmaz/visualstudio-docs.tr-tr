---
title: Ekle | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 634169607a7d581de1b1332d78e8d5abde1a722e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773745"
---
# <a name="attach"></a>İliştir
*VSPerfCmd.exe* **Ekle** seçeneği, işlem kimliği (PID) tarafından belirtilen çalıştırma işleminin örnek profiloluşturmasını başlatir.

 **Ekle** seçeneğini kullanmak için Başlangıç seçeneğinde **Örnek** yöntemini belirtmeniz gerekir.

> [!NOTE]
> **Başlangıç** seçeneği **Crosssession** seçeneğiile belirtilmişse, **VSPerfCmd /Attach veya VSPerfCmd** **/Detach'a** yapılan tüm aramalarda **Crosssession**belirtilmelidir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametreler
 `ProcessID`Çalıştırma işleminin işlem kimliği (PID). Çalışan bir işlemin PID'si, Windows Görev Yöneticisi'nin İşlemler sekmesinde listelenir.

## <a name="valid-options"></a>Geçerli seçenekler
 Aşağıdaki **VSPerfCmd** seçenekleri, tek bir komut satırında **Ekle** seçeneğiyle birleştirilebilir.

 **Çapraz oturum** Oturum açma oturumu dışındaki oturumlarda profil oluşturma uygulamalarını sağlar. **Başlangıç** seçeneği **Çapraz Oturum** seçeneğiyle belirtilmişse gereklidir.

 **Başlangıç:** `Method` Komut satırı profil oluşturucu oturumunu başlatir ve belirtilen profil oluşturma yöntemini ayarlar.

 **Hedef CLR** Bir profil oluşturma oturumunda birden fazla sürüm yüklendiğinde .NET Framework Common Language Runtime (CLR) sürümünü profillemek için belirtir. Varsayılan olarak, ilk yüklenen sürüm profillenir.

 **Globalon Globaloff** Devam eder (**GlobalOn**) veya duraklar **(GlobalOff**) profil oluşturma, ancak profil oluşturma oturumu sona erdirmez.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Resumes (**ProcessOn**) veya duraklar **(ProcessOff**) belirtilen işlem için profil oluşturma.

## <a name="interval-options"></a>Aralık seçenekleri
 Aşağıdaki örnekleme aralığı seçeneklerinden biri Ekle komut satırında belirtilebilir. Varsayılan örnekleme aralığı 10.000.000 işlemci saat döngüsüdür.

 **Zamanlayıcı**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**`FriendlyName`[<strong>:</strong>Olaylar]**Sayacı**[**:**`Name`,`Reload`, ] Örnekleme aralığının sayısını ve türünü belirtir.

- **Zamanlayıcı** - `Cycles` Her işlemci saat döngüsünü örnekler. `Cycles` Belirtilmemişse, 10.000.000 döngü kullanılır.

- **PF** - `Events` Her sayfa hatalarını örnekler. `Events` Belirtilmemişse, 10 sayfa hataları kullanılır.

- **Sys** - `Events` İşletim sistemine yapılan her çağrıyı örnekler. `Events` Belirtilmemişse, 10 sistem çağrısı kullanılır.

- **Sayaç** - `Reload` Cpu performans sayacının `Name`her sayısını örnekler. İsteğe `FriendlyName` bağlı olarak, profil oluşturucu raporlarında sütun üstbilgi olarak kullanılacak bir dize belirtebilirsiniz.

## <a name="example"></a>Örnek
 Bu örnek, 12345 işlem kimliği ile çalışan bir uygulama örneğine nasıl eklenir gösteriş gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
