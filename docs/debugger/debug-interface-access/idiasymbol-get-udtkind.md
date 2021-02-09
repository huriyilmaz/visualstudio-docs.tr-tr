---
title: 'IDiaSymbol:: get_udtKind | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0b93f8369b4cc1e733b89c9aa25e04150849b2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99853452"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
Kullanıcı tanımlı bir tür (UDT) alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Bir UDT türünü belirten [UdtKind numaralandırma](../../debugger/debug-interface-access/udtkind.md) numaralandırmasından bir değer döndürür: Structure, Class veya Union.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, döndürür `S_FALSE` veya hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [UdtKind Numaralandırması](../../debugger/debug-interface-access/udtkind.md)