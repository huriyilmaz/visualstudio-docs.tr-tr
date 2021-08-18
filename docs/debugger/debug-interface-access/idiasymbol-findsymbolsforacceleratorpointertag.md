---
description: C++ AMP saplama işlevindeki hızlandırıcı işaretçisi etiketlerinin sayısını döndürür.
title: 'IDiaSymbol:: Findsymbolsforivatorpointertag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: fb66852c-c5f7-4140-b9fe-20cb4e51a9fe
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 31dbdad20ec5d00ee08e817cfd0beebd3e02a994
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097807"
---
# <a name="idiasymbolfindsymbolsforacceleratorpointertag"></a>IDiaSymbol::findSymbolsForAcceleratorPointerTag
C++ AMP saplama işlevindeki hızlandırıcı işaretçisi etiketlerinin sayısını döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsForAccleratorPointerTag (
   DWORD             tagValue,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametreler
 `tagValue`

'ndaki Pointee sembol kayıtlarının bulunduğu işaretçi etiketi değeri.

 `ppResult`

dışı `IDiaEnumSymbols` Sonuçla başlatılan arabirim işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
