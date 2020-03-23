---
title: LineOff | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 76082063-20ef-47ae-ad64-81b43b654865
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ac671c3b0ba40c462403b2afa850c3936156d6d2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774132"
---
# <a name="lineoff"></a>LineOff
Varsayılan olarak, örnekleme profil oluşturma yöntemini kullanırken profil oluşturucu kaynak kod satırı numarasını ve satır numarası mahsup verilerini toplar. VSPerfCmd **LineOff** seçeneği, uygulamayı başlatmak için VSPerfCmd kullanıldığında satır numarası veri toplamayı devre dışı bırak. Profil oluşturma **verileri, LineOff** belirtildiğinde işlev düzeyine toplanır.

 **LineOff'u** yalnızca **Başlat** seçeneğiyle ve yalnızca profil oluşturucu **Başlat**:**Örnekle** seçeneği kullanılarak örnekleme için başlatıldığında kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /LineOff [Options]
```

#### <a name="parameters"></a>Parametreler
 None

## <a name="required-options"></a>Gerekli Seçenekler
 **LineOff** seçeneği yalnızca **Başlat** seçeneğini içeren bir komut satırında kullanılabilir.

 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

## <a name="example"></a>Örnek
 Bu örnek, uygulamayı ve profiloluşturucuyu başlatır ve satır düzeyinde örneklemeyi devre dışı kılabilir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /LineOff
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
