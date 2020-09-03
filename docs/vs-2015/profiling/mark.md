---
title: İşaretle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d7902ec588af2687b048639a930847ec02b3fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155792"
---
# <a name="mark"></a>İşaret
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Mark** seçeneği, belirtilen bilgileri profil oluşturma veri dosyasına ekler. Mark, ayrı bir VSPerfReport raporunda veya profiler Kullanıcı arabiriminin Işaret raporu görünümünde listelenebilir. **İşaret** , rapor ve görüntüleme filtrelerinde başlangıç ve bitiş noktalarını belirtmek için kullanılabilir.  
  
 **Mark** seçeneği, komut satırında belirtilen tek seçenek olmalıdır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>Parametreler  
 `MarkID`  
 Profil Oluşturucu görünümlerinde ve raporlarında Işaret KIMLIĞI olarak listelenen kullanıcı tanımlı bir tamsayı. `MarkID` benzersiz olması gerekmez.  
  
 `MarkName`  
 Seçim Profil Oluşturucu görünümlerinde ve raporlarında Işaret adı olarak listelenen kullanıcı tanımlı bir dize. `MarkName`Belirtilmemişse, işaret listesinin Işaret adı alanı boştur. Boşluk veya eğik çizgi ("/") içeren dizeleri tırnak işaretleri içine alın.  
  
## <a name="example"></a>Örnek  
 Bu örnek, KIMLIĞI 123 ve işaret adı "TestMark" olan bir işaret ekler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Tek başına uygulamaların profilini oluşturma](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET Web uygulamalarının profilini oluşturma](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profil Oluşturma Hizmetleri](../profiling/command-line-profiling-of-services.md)
