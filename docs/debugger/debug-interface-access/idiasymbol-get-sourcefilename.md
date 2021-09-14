---
description: Compiland kaynak dosyasının dosya adını alır.
title: 'IDiaSymbol:: get_sourceFileName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sourceFileName method
ms.assetid: 0f5dce88-829e-4df3-8acd-8d71076ad167
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 72be035d9a56a1ff7a837a9bff98ce358ba49773
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635369"
---
# <a name="idiasymbolget_sourcefilename"></a>IDiaSymbol::get_sourceFileName
Compiland kaynak dosyasının dosya adını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT get_sourceFileName ( 
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametreler
 `pRetVal`

dışı Compiland kaynak dosyasının dosya adını döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
