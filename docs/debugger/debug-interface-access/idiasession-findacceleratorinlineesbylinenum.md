---
title: 'IDiaSession:: findAcceleratorInlineesByLinenum | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d08168a83b9bb635fd6a0e22dc22f91a454001f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742318"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
Belirtilen kaynak konumuna karşılık gelen satır içi çerçeveler için simgelerin bir listesini döndürür.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findAcceleratorInlineeLinesByName ( 
   IDiaSymbol*           parent,
   IDiaSourceFile*       file,
   DWORD                 linenum,
   DWORD                 colnum,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `parent`

'ndaki Aranması gereken Hızlandırıcı saplama işlevine karşılık gelen bir `IDiaSymbol`.

 `file`

'ndaki Kaynak konumun `IDiaSourceFile`.

 `linenum`

'ndaki Kaynak konumun satır numarası.

 `colnum`

'ndaki Kaynak konumun sütun numarası.

 `ppResult`

dışı Sonuçla başlatılan `IDiaEnumLineNumbers` arabirimi işaretçisine yönelik bir işaretçi.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)