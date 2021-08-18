---
description: Karşılık gelen bir etiket değeri verilmelidir, bu yöntem belirtilen bir göreli sanal adreste bu saplama işlevinde yer alan sembollerin bir numaralama döndürür.
title: IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3d1c469d99149bdd21435d7e5b99dd1c193f4659
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128794"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
Karşılık gelen bir etiket değeri verilmelidir, bu yöntem belirtilen bir göreli sanal adreste bu saplama işlevinde yer alan sembollerin bir numaralama döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findSymbolsByRVAForAcceleratorPointerTag (
   DWORD             tagValue,
   DWORD             rva,
   IDiaEnumSymbols** ppResult);
```

#### <a name="parameters"></a>Parametreler
 `tagValue`

[in] İşaret simgesi kayıtlarının bulunduğu işaretçi etiketi değeri.

 `rva`

[in] Belirtilen etiket değeriyle pointee değişkenine karşılık gelen sembolleri filtrelemek için kullanılan rva.

 `ppResult`

[out] Sonuçla `IDiaEnumSymbols` başlatılan arabirim işaretçisinin işaretçisi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde veya `S_FALSE` bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemi yalnızca Hızlandırıcı `IDiaSymbol` saplama işlevine karşılık gelen bir arabirimde çağırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
