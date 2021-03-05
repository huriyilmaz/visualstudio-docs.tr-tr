---
description: Sembol türü sınıflandırıcısını alır.
title: 'IDiaSymbol:: get_symTag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symTag method
ms.assetid: 139a35bd-faeb-4878-be72-394dedfbb18f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5d8988efac8f29ec587a48568a9b61a40d7c710b
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155735"
---
# <a name="idiasymbolget_symtag"></a>IDiaSymbol::get_symTag
Sembol türü sınıflandırıcısını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_symTag ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) numaralandırmasından sembol türü sınıflandırıcısını belirten bir değer döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="example"></a>Örnek

```C++
IDiaSymbol* pType;
DWORD       tag = 0;
pType->get_symTag( &tag );
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
