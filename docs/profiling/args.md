---
title: Bağımsız değişkenler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b6d01a95b7e0872d6bb36c6d9f3917bc6a05b3b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74779824"
---
# <a name="args"></a>Bağımsız Değişkenler
VSPerfCmd.exe **args** seçeneği, **Launch** alt komutunun hedef uygulamasına geçirilen bağımsız değişkenlerin bir listesini belirtir.

 **Bağımsız değişkenler** yalnızca **başlatma** komut satırında de belirtildiğinde kullanılabilir. **Başlatma** belirtildiğinde **args** isteğe bağlıdır.

## <a name="syntax"></a>Söz dizimi

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametreler
 `Arguments`**Başlatma** komutunun hedef uygulamasına yönelik bağımsız değişkenlerin listesi.

## <a name="required-options"></a>Gerekli seçenekler
 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, TestApp.exe bağımsız değişkenleri geçirmek için **args** seçeneğini kullanır.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)
