---
description: SSDEBUGPS.dll, hata SQL Server bileşenidir.
title: SQL &apos;SSDEBUGPS dosyası | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 75ab62def371ef1fa210b39a23dc62d33f98cd39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154459"
---
# <a name="error-sql-can39t-find-ssdebugps"></a>Hata: SQL SSDEBUGPS&#39;Bulamıyorum

SSDEBUGPS.dll, hata SQL Server bileşenidir.

Hata ayıklamayı başlatmaya çalışırken bu hata oluşur ve belirtilen dosyanın makinede mevcut olmadığını [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] gösterir. Olası nedenler, Uzaktan Hata Ayıklama kurulumunun hiç çalışmamış veya bir şekilde bu dosyanın silinmesidir.

Bu hatayı çözmenin iki yolu vardır: Uzaktan Hata Ayıklama kurulumunu yeniden çalıştırarak ve dosyayı makineye [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] kopyalayıp.

Uzaktan Hata Ayıklama kurulumunu yeniden çalıştırma için Uzaktan Hata [Ayıklama'da verilen yönergeleri izleyin.](../debugger/remote-debugging.md)

Bir dosyanın kopyasını ssdebugps.dll makineye [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] kopyalarız. Varsa, dosya \Program Files\ Common Files\Microsoft Shared\SQL Debugging dizininde olur. Bunu başka bir [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] makinede veya 2005'Visual Studio makinede bulabilirsiniz.

2005 SSDEBUGPS.dll SQL Server kopyalamak için:

1. Dosyayı makinede aynı ad ve yola sahip dizine [!INCLUDE[sqprsqlong](../debugger/includes/sqprsqlong_md.md)] kopyalayın.

2. Bir Komut İstemi **açarak ve** aşağıdaki komutu çalıştırarak bunu kaydettirin:

    ```cmd
    regsvr32 ssdebugps.dll
    ```
