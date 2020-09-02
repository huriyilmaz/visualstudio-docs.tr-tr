---
title: Başlat | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 83dc76e3e92a05f936d94c8cd0f6a2b9b69e4cc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192824"
---
# <a name="start"></a>Başlangıç
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Başlat** seçeneği, profil oluşturucuyu belirtilen profil oluşturma yöntemine başlatan bir VSPerfCmd.exe seçenektir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `Method`  
 Aşağıdaki anahtar sözcüklerden biri olmalıdır:  
  
- **Trace-izleme** yöntemini belirtir.  
  
- **Örnek** -örnekleme yöntemini belirtir.  
  
- **Kapsam** -kod kapsamını belirtir.  
  
- **Eşzamanlılık** -kaynak çekişme yöntemini belirtir.  
  
## <a name="required-options"></a>Gerekli seçenekler  
 Komut satırında **Start** belirtildiğinde **output** seçeneğinin belirtilmesi gerekir.  
  
 **Çıkış:**`filename`  
 Çıkış dosyası adını belirtir.  
  
## <a name="exclusive-options"></a>Dışlamalı seçenekler  
 Aşağıdaki seçenekler yalnızca bir komut satırındaki **Başlat** seçeneğiyle birlikte kullanılabilir.  
  
 **Çapraz oturum**&#124;**CS**  
 Çapraz işlem profili oluşturmayı mümkün. **CrossSession** ve **CS** seçeneklerinin her ikisi de desteklenir.  
  
 **Kullanıcı:**[ `domain\` ]`username`  
 Belirtilen hesaptan izleyiciye istemci erişimini sağlar.  
  
 **WinCounter:** `Path` [**Otomatik işaret**: `n` ]  
 **WinCounter** , profil oluşturma veri dosyasına işaret olarak eklenecek bir Windows performans sayacı belirtir. **Otomatik işaret** , veri dosyası koleksiyonları arasındaki aralığı milisaniye olarak belirtir.  
  
## <a name="invalid-options"></a>Geçersiz seçenekler  
 Aşağıdaki seçenekler, komut satırında **Start** seçeneğiyle birlikte kullanılamaz.  
  
 **Durum**  
 **Durum** , profili oluşturulan süreçler için geçerlidir. İşlem ve iş parçacıklarını ve geçerli profil durumunu (açık/kapalı) listeler. Örneğin, bir işlem durdurulmuşsa **durum** raporda bunu göstermez. **Durum** , işlemin profili oluşturulmuş olduğunu gösterir.  
  
 **Kapanıyor**[**:** `Timeout` ]  
 Profil oluşturucuyu kapatır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, profil oluşturucuyu başlatmak için VSPerfCmd.exe **Start** seçeneğinin nasıl kullanılacağını gösterir.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
