---
title: 'Hata: SQL&#39;SSDEBUGPS bulamıyor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- FSharp
- VB
- CSharp
- C++
- SQL
ms.assetid: 596425c8-14c7-4c05-8823-e1c52f420f5e
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 25462a99bd3e773f03af3918a9e25d11ed006c1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185201"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Hata: SQL&#39;SSDEBUGPS bulamıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

SSDEBUGPS.dll, SQL Server hata ayıklama konak bileşenidir.  
  
 Bu hata, hata ayıklamayı başlatmaya çalışırken oluşur ve belirtilen dosyanın makinede mevcut olmadığını gösterir [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] . Olası nedenler, uzaktan hata ayıklama kurulumunun hiçbir şekilde çalıştırılmamış olması veya bu dosyanın bir şekilde silinmiş olması olabilir.  
  
 Bu hatayı çözmek için iki yol vardır: uzaktan hata ayıklama kurulumu 'nu yeniden çalıştırarak ve dosyayı [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] makineye kopyalayarak.  
  
 Uzaktan hata ayıklama kurulumunu yeniden çalıştırmak için [Uzaktan hata ayıklama](../debugger/remote-debugging.md)bölümündeki yönergeleri izleyin.  
  
 ssdebugps.dll bir kopyasını bulabilirseniz, bunu [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] makineye kopyalayabilirsiniz. Varsa, dosya \Program Files \ Common Files\Microsoft Shared\SQL hata ayıklaması dizinine eklenecektir. Bunu başka bir [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] makinede veya yüklü bir makinede bulabilirsiniz [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] .  
  
### <a name="to-copy-ssdebugpsdll-onto-the-sql-server-2005-machine"></a>SSDEBUGPS.dll SQL Server 2005 makinesine kopyalamak için  
  
1. Dosyayı, makinede aynı ada ve yola sahip dizine kopyalayın [!INCLUDE[sqprsqlong](../includes/sqprsqlong-md.md)] .  
  
2. Bir **komut istemi**açıp aşağıdaki komutu çalıştırarak kaydedin:  
  
    ```  
    regsvr32 ssdebugps.dll  
    ```
