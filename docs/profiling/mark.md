---
title: İşaretle | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4bf89469c4137052247b5a1fdfee7f8dc694fbcc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74774000"
---
# <a name="mark"></a>İşaret
*VSPerfCmd.exe* **İşareti** seçeneği, belirtilen bilgileri profil oluşturma veri dosyasına ekler. İşaret, ayrı bir VSPerfReport raporunda veya profiloluşturucu ui'nin İşaret Raporu görünümünde listelenebilir. **İşaret,** rapor ve görünüm filtrelerinde başlangıç ve bitiş noktalarını belirtmek için kullanılabilir.

 **İşaretle** seçeneği komut satırında belirtilen tek seçenek olmalıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametreler
 `MarkID`Profil oluşturucu görünümlerinde ve raporlarında İşaret Kimliği olarak listelenen kullanıcı tanımlı bir tamsayı. `MarkID`benzersiz olmak zorunda değildir.

 `MarkName`(İsteğe bağlı) Profil oluşturucu görünümlerinde ve raporlarında İşaret Adı olarak listelenen kullanıcı tanımlı dize. `MarkName` Belirtilmemişse, işaret listesinin İşaret Adı alanı boştur. Tırnak işaretlerine boşluk veya ileri kesikler ("/") içeren dizeleri içine alın.

## <a name="example"></a>Örnek
 Bu örnek, 123 kimliği ve "TestMark" işareti adı içeren bir işaret ekler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil tek başına uygulamalar](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
