---
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eff457d539317d2f8c7d77dfc85eb16063650c14
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744153"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Veri kaynağında bulunan çeşitli kesimleri numaralandırır.

## <a name="syntax"></a>Sözdizimi

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda `IDiaEnumSegments` yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Bu Numaralandırıcının [IEnumVARIANT arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) sürümünü alır.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Segmentlerin sayısını alır.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Bir segmenti bir dizin aracılığıyla alır.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Sabit Listesi dizisinde belirtilen sayıda segment alır.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Bir numaralandırma dizisinde belirtilen sayıda parçayı atlar.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bir [IDiaTable](../../debugger/debug-interface-access/idiatable.md) nesnesi üzerinde `QueryInterface` yöntemini çağırarak bu arabirimi elde edin. Ayrıntılar için örneğe bakın.

## <a name="example"></a>Örnek
Bu örnek, bir tablodan `IDiaEnumSections` arabiriminin nasıl alınacağını gösterir. Segmentleri kullanma hakkında daha ayrıntılı bir örnek için bkz. [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) arabirimi.

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
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
