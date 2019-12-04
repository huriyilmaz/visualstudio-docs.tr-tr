---
title: Başlat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: df3ccda9730be02bafb7f7d069a26193a4528d1e
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778277"
---
# <a name="start"></a>Başlangıç
**Start** seçeneği, profil oluşturucuyu belirtilen profil oluşturma yöntemine Başlatan bir *VSPerfCmd. exe* seçeneğidir.

## <a name="syntax"></a>Sözdizimi

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametreler
 `Method` aşağıdaki anahtar sözcüklerden biri olmalıdır:

- **Trace-izleme** yöntemini belirtir.

- **Örnek** -örnekleme yöntemini belirtir.

- **Kapsam** -kod kapsamını belirtir.

- **Eşzamanlılık** -kaynak çekişme yöntemini belirtir.

## <a name="required-options"></a>Gerekli seçenekler
 Komut satırında **Start** belirtildiğinde **output** seçeneğinin belirtilmesi gerekir.

 **Çıkış:** `filename` çıkış dosyası adını belirtir.

## <a name="exclusive-options"></a>Dışlamalı seçenekler
 Aşağıdaki seçenekler yalnızca bir komut satırındaki **Başlat** seçeneğiyle birlikte kullanılabilir.

 **CrossSession**&#124;**CS** , çapraz işlem profili oluşturma imkanı sunar. **CrossSession** ve **CS** seçeneklerinin her ikisi de desteklenir.

 **Kullanıcı:** [`domain\`]`username` belirtilen hesaptan izleyiciye Istemci erişimini sağlar.

 **WinCounter:** `Path` [**otomatik işaret**:`n`] **WinCounter** , profil oluşturma veri dosyasına işaret olarak eklenecek bir Windows performans sayacı belirtir. **Otomatik işaret** , veri dosyası koleksiyonları arasındaki aralığı milisaniye olarak belirtir.

## <a name="invalid-options"></a>Geçersiz seçenekler
 Aşağıdaki seçenekler, komut satırında **Start** seçeneğiyle birlikte kullanılamaz.

 **Durum** **durumu** profili oluşturulan süreçler için geçerlidir. İşlem ve iş parçacıklarını ve geçerli profil durumunu (açık/kapalı) listeler. Örneğin, bir işlem durdurulmuşsa **durum** raporda bunu göstermez. **Durum** , işlemin profili oluşturulmuş olduğunu gösterir.

 **Kapat**[ **:** `Timeout`] profil oluşturucuyu devre dışı bırakır.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, profil oluşturucuyu başlatmak için *VSPerfCmd. exe* **Start** seçeneğinin nasıl kullanılacağını gösterir.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Ayrıca bkz.
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
