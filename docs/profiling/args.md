---
title: Bağımsız değişkenler | Microsoft Docs
description: Bir bağımsız değişken listesini Launch alt komutunun hedef uygulamasına geçirmek için VSPerfCmd.exe ARGS seçeneğini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 20c35949-1f29-4282-ac75-4e6c237d71bc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b91d00896b72f95b3340e8741867b58d4c2494b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142422"
---
# <a name="args"></a>Bağımsız Değişkenler
VSPerfCmd.exe **args** seçeneği, **Launch** alt komutunun hedef uygulamasına geçirilen bağımsız değişkenlerin bir listesini belirtir.

 **Bağımsız değişkenler** yalnızca **başlatma** komut satırında de belirtildiğinde kullanılabilir. **Başlatma** belirtildiğinde **args** isteğe bağlıdır.

## <a name="syntax"></a>Sözdizimi

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
- [ASP.NET web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)
