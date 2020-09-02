---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d80e20200966c65258485782fec5865158f114a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85464851"
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
