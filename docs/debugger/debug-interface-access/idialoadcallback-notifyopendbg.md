---
title: 'Ialoadcallback:: NotifyOpenDBG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70607af90469594491223afa5f316dc63bf935b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743077"
---
# <a name="idialoadcallbacknotifyopendbg"></a>IDiaLoadCallback::NotifyOpenDBG
Bir aday. dbg dosyası açıldığında çağırılır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT NotifyOpenDBG ( 
   LPCOLESTR dbgPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Parametreler
 `dbgPath`

'ndaki . Dbg dosyasının tam yolu.

 `resultCode`

'ndaki Bu dosyaya uygulanan yükün başarısını (`S_OK`) veya başarısızlığını belirten kod.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür. Dönüş kodu genellikle yok sayılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)