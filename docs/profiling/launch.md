---
title: Fırlatma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9834c10c58fb343de0707fa0b805586a6cdebcb3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778615"
---
# <a name="launch"></a>Başlat
**Başlatma** seçeneği örnekleme yöntemini kullanarak profilleyiciyi başlatır ve belirtilen uygulamayı da başlatır.

 **Başlat** seçeneğini kullanmak için **Başlat** seçeneğinde **Örnek** yöntemini belirtmeniz gerekir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName [Options]
```

#### <a name="parameters"></a>Parametreler
 `AppName`Başlatılan uygulamanın adı. Geçerli dizinden tam ve kısmi yollar desteklenir.

## <a name="valid-options"></a>Geçerli Seçenekler
 Aşağıdaki VSPerfCmd seçenekleri, tek bir komut satırında **Başlat** seçeneğiyle birleştirilebilir.

 **Başlangıç:** `Method` Komut satırı profil oluşturucu oturumunu başlatir ve belirtilen profil oluşturma yöntemini ayarlar.

 **GlobalOn** ve **GlobalOff** Devam Eder (**GlobalOn**) veya duraklar **(GlobalOff**) profil oluşturma, ancak profil oluşturma oturumu sona erdirmez.

 **ProcessOn:** `PID` and **ProcessOff**:`PID` Belirtilen işlem için devam eder (**ProcessOn**) veya duraklar (**ProcessOff**) profil oluşturma.

 **Hedef CLR** Bir profil oluşturma oturumunda birden fazla sürüm yüklendiğinde .NET Framework Common Language Runtime (CLR) sürümünü profillemek için belirtir. Varsayılan olarak, ilk yüklenen sürüm profillenir.

## <a name="exclusive-options"></a>Özel Seçenekler
 Aşağıdaki seçenekler yalnızca **Başlat** seçeneğiyle kullanılabilir.

 **Konsol** Belirtilen komut satırı uygulamasını yeni bir pencerede başlatıyor.

 **Args:** `ArgList` Uygulamaya geçirilen bağımsız değişkenlerin listesini belirtir.

 **LineOff** Satır düzeyinde profil oluşturma verilerinin toplanmasını devre dışı kılabilir.

## <a name="sampling-options"></a>Örnekleme Seçenekleri
 Aşağıdaki örnekleme aralığı seçeneklerinden biri **Başlat** komut satırında belirtilebilir. Varsayılan örnekleme aralığı 10.000.000 işlemci saat döngüsüdür.

 **Zamanlayıcı**[**: ]**`Cycles`**PF**[**[ [**`Events`]**Sys**[**:**`Events`]**Sayaç**[**,**`Name`,`Reload``FriendlyName`]**GC**[:**tahsis**&#124;**ömür boyu**] Örnekleme aralığının sayısını ve türünü belirtir.

- **Zamanlayıcı** - `Cycles` Durdurulmayan her işlemci saat döngüsünü örnekler. `Cycles` Belirtilmemişse, 10.000.000 döngü kullanılır.

- **PF** - `Events` Her sayfa hatalarını örnekler. `Events` Belirtilmemişse, 10 sayfa hataları.

- **Sys** - `Events` İşletim sistemine yapılan her çağrıyı örnekler. `Events` Belirtilmemişse, 10 sistem çağrısı kullanılır.

- **Sayaç** - `Reload` Cpu performans sayacının `Name`her sayısını örnekler. İsteğe `FriendlyName` bağlı olarak, profil oluşturucu raporlarında sütun üstbilgi olarak kullanılacak bir dize belirtebilirsiniz.

- **GC** - .NET bellek verilerini toplar. Varsayılan olarak **(ayırma),** veriler her bellek ayırma olayında toplanır. Yaşam **boyu** parametresi belirtildiğinde, her çöp toplama olayında veriler de toplanır.

## <a name="example"></a>Örnek
 Bu örnek, bir uygulamayı başlatmak için **Başlat'ın** kullanımını gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
