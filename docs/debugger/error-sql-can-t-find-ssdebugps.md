---
description: SSDEBUGPS.dll, SQL Server hata ayıklama konak bileşenidir.
title: SQL, &apos; SSDEBUGPS 'Yi bulabilir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.sqlde_cant_find_ssdebugps
dev_langs:
- CSharp
- VB
- FSharp
- C++
- SQL
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a746759f294a1d8ac6b13350efd56976a1f3ae21
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146762"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Hata: SQL&#39;SSDEBUGPS bulamıyor

SSDEBUGPS.dll, SQL Server hata ayıklama konak bileşenidir.

Bu hata, hata ayıklamayı başlatmaya çalışırken oluşur ve belirtilen dosyanın makinede mevcut olmadığını gösterir [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] . Olası nedenler, uzaktan hata ayıklama kurulumunun hiçbir şekilde çalıştırılmamış olması veya bu dosyanın bir şekilde silinmiş olması olabilir.

Bu hatayı çözmek için iki yol vardır: uzaktan hata ayıklama kurulumu 'nu yeniden çalıştırarak ve dosyayı [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] makineye kopyalayarak.

Uzaktan hata ayıklama kurulumunu yeniden çalıştırmak için [Uzaktan hata ayıklama](../debugger/remote-debugging.md)bölümündeki yönergeleri izleyin.

ssdebugps.dll bir kopyasını bulabilirseniz, bunu [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] makineye kopyalayabilirsiniz. Varsa, dosya \Program Files \ Common Files\Microsoft Shared\SQL hata ayıklaması dizinine eklenecektir. Bunu başka bir [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] makinede veya Visual Studio 2005 yüklü bir makinede bulabilirsiniz.

SSDEBUGPS.dll SQL Server 2005 makinesine kopyalamak için:

1. Dosyayı, makinede aynı ada ve yola sahip dizine kopyalayın [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] .

2. Bir **komut istemi** açıp aşağıdaki komutu çalıştırarak kaydedin:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
