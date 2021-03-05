---
description: Yürütülebilir dosyanın bellek alanında bir sanal adres verildiğinde, bir yürütülebilir dosyanın belleğindeki görüntüsünün başlangıcını döndürür.
title: 'IDiaStackWalkHelper:: ımageforva | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::imageForVA method
ms.assetid: 8d4edabf-3c01-4fef-8b61-4779f3371067
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2459ed59f4b34befd893d25848de9482b39f9d70
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156848"
---
# <a name="idiastackwalkhelperimageforva"></a>IDiaStackWalkHelper::imageForVA
Yürütülebilir dosyanın bellek alanında bir sanal adres verildiğinde, bir yürütülebilir dosyanın belleğindeki görüntüsünün başlangıcını döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT imageForVA(
   ULONGLONG  vaContext,
   ULONGLONG *pvaImageStart
);
```

#### <a name="parameters"></a>Parametreler
 `vaContext`

'ndaki Yürütülebilir dosyanın alanında bir yerde yer alan sanal adres.

 `pvaImageStart`

dışı Yürütülebilir dosyanın başlangıç sanal adresini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
