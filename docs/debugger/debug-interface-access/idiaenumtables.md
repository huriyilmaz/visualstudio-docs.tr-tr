---
title: IDiaEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d505219468f802a3eff9df0ad766fd1a353d5166
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743700"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Veri kaynağında bulunan çeşitli tabloları numaralandırır.

## <a name="syntax"></a>Sözdizimi

```
IDiaEnumTables : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda `IDiaEnumTables` yöntemleri gösterilmektedir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Bu Numaralandırıcının [IEnumVARIANT arabirimi](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) sürümünü alır.|
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Tablo sayısını alır.|
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Bir tabloyu bir dizin veya bir ad yoluyla alır.|
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Sabit Listesi dizisinde belirtilen sayıda tabloyu alır.|
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Sabit Listesi dizisinde belirtilen sayıda tabloyu atlar.|
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|

## <a name="remarks"></a>Açıklamalar

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
[IDiaSession:: getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md) metodunu çağırarak bu arabirimi edinin.

## <a name="example"></a>Örnek
Bu örnek, `IDiaEnumTables` arabiriminin bir oturumdan nasıl alınacağını gösterir. Tablo kullanmayla ilgili daha ayrıntılı bir örnek için bkz. [IDiaTable](../../debugger/debug-interface-access/idiatable.md) arabirimi.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    // Do something with table
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
