---
title: 'IDiaSession:: findLines | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6f2949eaca7e6f3a18a121e7b92ecb5db88a2156
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855160"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Belirtilen compiland ve kaynak dosya tanımlayıcılarının içindeki satır numaralarını alır.

## <a name="syntax"></a>Sözdizimi

```C++
HRESULT findLines ( 
   IDiaSymbol*           compiland,
   IDiaSourceFile*       file,
   IDiaEnumLineNumbers** ppResult
);
```

#### <a name="parameters"></a>Parametreler
 `compiland`

'ndaki Compiland 'yi temsil eden bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi. Bu arabirimi, satır numaralarının aranacağı bir bağlam olarak kullanın.

 `file`

'ndaki Satır numaralarının aranacağı kaynak dosyayı temsil eden bir [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) nesnesi.

 `ppResult`

dışı Alınan satır numaralarının bir listesini içeren bir [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)