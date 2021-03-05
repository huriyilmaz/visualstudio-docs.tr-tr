---
description: . Pdb dosyasındaki bilgileri kullanarak bir yığın izlenecek yöntemler sağlar.
title: Idiastackdenetçisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a86609f43bb6e825dac1b595b5e32951c3313a34
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147340"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
. Pdb dosyasındaki bilgileri kullanarak bir yığın izlenecek yöntemler sağlar.

## <a name="syntax"></a>Syntax

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaStackWalker` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|X86 platformları için bir yığın çerçeve numaralandırıcısı alır.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Belirli bir platform türü için yığın çerçeve numaralandırıcısı alır.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, yüklü bir modül için yığın çerçevelerinin listesini almak için kullanılır. Yöntemlerin her birine, yığın çerçevelerinin listesini oluşturmak için gerekli bilgileri sağlayan bir [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) nesnesi (istemci uygulaması tarafından uygulanır) geçirilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, `CoCreateInstance` yöntemi sınıf tanımlayıcısıyla `CLSID_DiaStackWalker` ve arabirim kimliğiyle çağırarak elde edilir `IID_IDiaStackWalker` . Örnek, bu arabirimin nasıl elde edilildiği gösterilmektedir.

## <a name="example"></a>Örnek
Bu örnek, arabirimin nasıl alınacağını gösterir `IDiaStackWalker` .

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
