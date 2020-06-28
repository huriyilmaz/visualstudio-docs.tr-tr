---
title: 'IDiaSession:: Findınlineframesbyrva | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8be9203b3ed22093863710eb7689b16226988efe
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465694"
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
Bir istemcinin belirtilen göreli sanal adreste (RVA) bulunan tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT findInlineFramesByRVA ( 
   IDiaSymbol*       parent,   DWORD             rva,
   IDiaEnumSymbols** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

'ndaki `IDiaSymbol`Üst öğeyi temsil eden nesne.

 `rva`

'ndaki Adresi RVA olarak belirtir.

 `ppResult`

dışı `IDiaEnumSymbols`Alınan çerçevelerin listesini içeren bir nesnesi tutar.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)