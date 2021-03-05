---
description: Bir aday. dbg dosyası açıldığında çağırılır.
title: 'Ialoadcallback:: NotifyOpenDBG | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenDBG method
ms.assetid: dbc4dcf0-4ace-4dce-9790-0fdaf3a23d3b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7f1dfdc36f66a883f1c66d37eb6f4ff48b8962a0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157450"
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

'ndaki `S_OK`Bu dosyaya uygulanan yükün başarısını () veya başarısızlığını belirten kod.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Dönüş kodu genellikle yok sayılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
