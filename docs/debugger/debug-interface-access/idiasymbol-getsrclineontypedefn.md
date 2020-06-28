---
title: 'IDiaSymbol:: getSrcLineOnTypeDefn | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ad554d18-9988-4b64-ad71-e7594c266e94
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e19ce48a8716952f53a1caa6a44fd5ba3d817f4e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461352"
---
# <a name="idiasymbolgetsrclineontypedefn"></a>IDiaSymbol::getSrcLineOnTypeDefn
Belirtilen kullanıcı tanımlı türün nerede tanımlandığını belirten kaynak dosya ve satır numarasını alır.

## <a name="syntax"></a>Söz dizimi

```C++
HRESULT getSrcLineOnTypeDefn(
   IDiaLineNumber **ppResult);
```

#### <a name="parameters"></a>Parametreler
 `ppResult`

dışı `IDiaLineNumber`Kullanıcı tanımlı olan kaynak dosyayı ve satır numarasını içeren bir nesne.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)