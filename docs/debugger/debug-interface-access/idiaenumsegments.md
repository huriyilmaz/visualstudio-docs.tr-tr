---
description: Veri kaynağında bulunan çeşitli segmentleri numaralar.
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 87ac9dd98c1df125f029ff4b790548326200401c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154610"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Veri kaynağında bulunan çeşitli segmentleri numaralar.

## <a name="syntax"></a>Syntax

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaEnumSegments` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Bu [numaralayıcının IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) Arabirimi sürümünü alın.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Segment sayısını alın.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Bir segmenti dizin ile alma.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Numaralama dizisinde belirtilen sayıda segmenti alan.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Bir numaralama dizisinde belirtilen sayıda segmenti atlar.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Bir numaralama dizisini en başta sıfırlar.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Geçerli numaralayıcıyla aynı numaralama durumunu içeren bir numaralayıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bir `QueryInterface` [IDiaTable](../../debugger/debug-interface-access/idiatable.md) nesne üzerinde yöntemini çağırarak bu arabirimi alın. Ayrıntılar için örneğine bakın.

## <a name="example"></a>Örnek
Bu örnekte, bir tablodan `IDiaEnumSections` arabirimin nasıl alınarak elde edilen bilgiler yer alır. Segmentleri kullanma hakkında daha eksiksiz bir örnek için bkz. [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) arabirimi.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
