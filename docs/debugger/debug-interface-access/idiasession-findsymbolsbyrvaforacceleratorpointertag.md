---
title: 'IDiaSession:: Findsymbolsbyrvaforivatorpointertag | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1b24d24de35de30b24937a6cfbf59d12f69482
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741998"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Karşılık gelen bir etiket değeri verildiğinde, bu yöntem belirtilen bir ilişkili sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde bulunan simgelerin bir listesini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag ( 
   IDiaSymbol*           parent,
   DWORD                 tagValue,
   DWORD                 rva,
   IDiaEnumSymbols**     ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

'ndaki Aranmak üzere Hızlandırıcı saplama işlevine karşılık gelen bir `IDiaSymbol`.

 `tagValue`

'ndaki İşaretçi etiketi değeri.

 `rva`

'ndaki Göreli sanal adres.

 `ppResult`

dışı Sonuçla başlatılan `IDiaEnumSymbols` arabirimi işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi yalnızca bir Hızlandırıcı saplama işlevine karşılık gelen bir `IDiaSymbol` arabiriminde çağırın.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)