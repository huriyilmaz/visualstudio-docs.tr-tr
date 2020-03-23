---
title: Args | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779824"
---
# <a name="args"></a>Bağımsız Değişkenler
VSPerfCmd.exe **Args** seçeneği, **Başlat** alt komutunun hedef uygulamasına geçirilen bağımsız değişkenlerin listesini belirtir.

 **Args** yalnızca Komut Satırında **Başlatma** da belirtildiğinde kullanılabilir. **Başlatma** belirtildiğinde **Args** isteğe bağlıdır.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Launch:AppName /Args:Arguments [Options]
```

#### <a name="parameters"></a>Parametreler
 `Arguments`**Başlat** komutunun hedef uygulamasına yönelik bağımsız değişkenlerin listesi.

## <a name="required-options"></a>Gerekli Seçenekler
 **Başlatma:** `AppName` Belirtilen uygulamayı başlatır ve örnekleme yöntemiyle profil oluşturmaya başlar.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, bağımsız değişkenleri TestApp.exe'ye geçirmek için **Args** seçeneği kullanÝlýr.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe /Args:"123, 'Hello World'"
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamaların profilini çıkarma](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Web uygulamaları ASP.NET profil oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)
