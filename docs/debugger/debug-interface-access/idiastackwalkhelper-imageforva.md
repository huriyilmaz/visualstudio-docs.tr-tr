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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8ad55d62007c139f1a14e6c93b34797110b47557
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626823"
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
