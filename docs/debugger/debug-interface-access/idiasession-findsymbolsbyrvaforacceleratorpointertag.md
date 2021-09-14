---
description: Karşılık gelen bir etiket değeri verilmelidir, bu yöntem belirtilen bir göreli sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde yer alan sembollerin bir numaralama döndürür.
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 74c6990599fdf75e05b9f009f20a5ea4a6e201a9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629120"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Karşılık gelen bir etiket değeri verilmelidir, bu yöntem belirtilen bir göreli sanal adreste belirtilen üst Hızlandırıcı saplama işlevinde yer alan sembollerin bir numaralama döndürür.

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

[in] Aranacak `IDiaSymbol` Hızlandırıcı saplama işlevine karşılık gelen bir.

 `tagValue`

[in] İşaretçi etiketi değeri.

 `rva`

[in] Göreli sanal adres.

 `ppResult`

[out] Sonuçla başlatılan `IDiaEnumSymbols` bir arabirim işaretçisinin işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi yalnızca Hızlandırıcı `IDiaSymbol` saplama işlevine karşılık gelen bir arabirimde çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
