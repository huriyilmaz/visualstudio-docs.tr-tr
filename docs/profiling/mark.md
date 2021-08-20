---
title: İşaret | Microsoft Docs
description: VSPerfCmd.exe İşaretle seçeneğinin belirtilen bilgileri profil oluşturma veri dosyasına nasıl ekley olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3e37a739d5e6c799cbeaca0ddb5802be3a0a535b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122107452"
---
# <a name="mark"></a>İşaret
VSPerfCmd.exe **İşaretle** seçeneği, belirtilen bilgileri profil oluşturma veri dosyasına ekler. İşaret ayrı bir VSPerfReport raporunda veya profil oluşturma kullanıcı arabiriminin Raporu İşaretle görünümünde listelenmiş olabilir. **İşaret,** rapor ve görünüm filtrelerinin başlangıç ve bitiş noktalarını belirtmek için kullanılabilir.

 **İşaretle** seçeneği, komut satırı üzerinde belirtilen tek seçenek olması gerekir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Mark:MarkID,[MarkName]
```

#### <a name="parameters"></a>Parametreler
 `MarkID` Profil oluşturma görünüm ve raporlarında Mark ID olarak listelenen kullanıcı tanımlı bir tamsayı. `MarkID` benzersiz olması gerek değildir.

 `MarkName` (İsteğe bağlı) Profil oluşturma görünüm ve raporlarında İşaret Adı olarak listelenen kullanıcı tanımlı bir dize. `MarkName`Belirtilmezse, mark listesinin Mark Name alanı boştur. Boşluk veya eğik çizgi ("/") içeren dizeleri tırnak işaretleri içine alın.

## <a name="example"></a>Örnek
 Bu örnek, 123 kimliğine ve "TestMark" işareti adına sahip bir işaret ekler.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
VSPerfCmd.exe /Mark:123,TestMark
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
