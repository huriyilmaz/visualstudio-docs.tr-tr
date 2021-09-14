---
description: .pdb dosyasındaki bilgileri kullanarak yığında adım adım yol yapmaya yönelik yöntemler sağlar.
title: IDiaStackWalker | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c27a18923ae5b305702994e4d76be7dd291eb8c5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636793"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
.pdb dosyasındaki bilgileri kullanarak yığında adım adım yol yapmaya yönelik yöntemler sağlar.

## <a name="syntax"></a>Syntax

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaStackWalker` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|x86 platformları için yığın çerçevesi numaralayıcısını verir.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Belirli bir platform türü için yığın çerçevesi numaralayıcısını alma.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, yüklenen bir modül için yığın çerçevelerinin listesini almak için kullanılır. Yöntemlerin her biri, yığın çerçevelerinin listesini oluşturmak için gerekli bilgileri sağlayan [bir IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) nesnesine (istemci uygulaması tarafından uygulanır) geçirildi.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirim, sınıf tanımlayıcısı ve `CoCreateInstance` arabirim kimliği ile yöntemi `CLSID_DiaStackWalker` çağrılarak elde `IID_IDiaStackWalker` edilir. Örnek, bu arabirimin nasıl alınarak elde edilenleri gösterir.

## <a name="example"></a>Örnek
Bu örnekte arabirimin nasıl alınarak elde `IDiaStackWalker` edilir?

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
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
