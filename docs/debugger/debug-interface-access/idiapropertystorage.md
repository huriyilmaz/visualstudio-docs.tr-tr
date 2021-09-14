---
description: DIA özellik kümesi kalıcı özelliklerini okumana olanak sağlar.
title: IDiaPropertyStorage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage interface
ms.assetid: d3197a38-5973-4e56-873e-4f1b84c3f674
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 670c669f80661128b9255456c410c784f0e1f65e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629517"
---
# <a name="idiapropertystorage"></a>IDiaPropertyStorage
DIA özellik kümesi kalıcı özelliklerini okumana olanak sağlar.

## <a name="syntax"></a>Syntax

```
IDiaPropertyStorage : IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaPropertyStorage` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaPropertyStorage::Enum](../../debugger/debug-interface-access/idiapropertystorage-enum.md)|Bu küme içindeki özellikler için bir numaralayıcı işaretçisi alır.|
|[IDiaPropertyStorage::ReadBOOL](../../debugger/debug-interface-access/idiapropertystorage-readbool.md)|Bir `BOOL` özellik kümesinde değerleri okur.|
|[IDiaPropertyStorage::ReadBSTR](../../debugger/debug-interface-access/idiapropertystorage-readbstr.md)|Bir `BSTR` özellik kümesinde değerleri okur.|
|[IDiaPropertyStorage::ReadDWORD](../../debugger/debug-interface-access/idiapropertystorage-readdword.md)|Bir `DWORD` özellik kümesinde değerleri okur.|
|[IDiaPropertyStorage::ReadLONG](../../debugger/debug-interface-access/idiapropertystorage-readlong.md)|Bir `LONG` özellik kümesinde değerleri okur.|
|[IDiaPropertyStorage::ReadMultiple](../../debugger/debug-interface-access/idiapropertystorage-readmultiple.md)|Özellik kümesinde özellik değerlerini okur.|
|[IDiaPropertyStorage::ReadPropertyNames](../../debugger/debug-interface-access/idiapropertystorage-readpropertynames.md)|Verilen özellik tanımlayıcıları için karşılık gelen dize adlarını alır.|
|[IDiaPropertyStorage::ReadULONGLONG](../../debugger/debug-interface-access/idiapropertystorage-readulonglong.md)|Bir `ULONGLONG` özellik kümesinde değerleri okur.|

## <a name="remarks"></a>Açıklamalar
Bir özellik kümesi içindeki her özellik, bu kümeye özgü dört baytlık bir değer olan bir `ULONG` özellik tanımlayıcısı (ID) ile tanımlanır. Arabirim aracılığıyla açığa `IDiaPropertyStorage` çıkarilen özellikler, üst arabirimde kullanılabilen özelliklere karşılık geliyor. Örneğin, [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) arabiriminin özelliklerine arabirim üzerinden ad ile erişilebilir (ancak, özelliğin erişilebilir olmasına rağmen özelliğin belirli bir nesne için geçerli olduğu anlamına gelebilemez). `IDiaPropertyStorage` `IDiaSymbol`

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Yöntemini başka bir arabirimde `QueryInterface` çağırarak bu arabirimi alın. Arabirim için aşağıdaki arabirimler sorgu `IDiaPropertyStorage` olabilir:

- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)

- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)

- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)

- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)

- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)

## <a name="example"></a>Örnek
Bu örnekte, nesnesi tarafından ortaya çıkaran tüm özellikleri görüntüleyen bir işlev `IDiaPropertyStorage` görüntülenir. Arabirimin [IDiaInjectedSource](../../debugger/debug-interface-access/idiaenuminjectedsources.md) arabiriminden nasıl elde edildiklerinin bir örneği için `IDiaPropertyStorage` [bkz. IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiainjectedsource.md) arabirimi.

```C++
void PrintPropertyStorage(IDiaPropertyStorage* pPropertyStorage)
{
    IEnumSTATPROPSTG* pEnumProps;
    STATPROPSTG       prop;
    DWORD             celt = 1;

    if (pPropertyStorage->Enum(&pEnumProps) == S_OK)
    {
        while (pEnumProps->Next(celt, &prop, &celt) == S_OK)
        {
            PROPSPEC pspec = { PRSPEC_PROPID, prop.propid };
            PROPVARIANT vt = { VT_EMPTY };

            if (pPropertyStorage->ReadMultiple( 1, &pspec, &vt) == S_OK)
            {
                switch( vt.vt ){
                    case VT_BOOL:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bVal ? L"true" : L"false" );
                        break;
                    case VT_I2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.iVal );
                        break;
                    case VT_UI2:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.uiVal );
                        break;
                    case VT_I4:
                        wprintf( L"%32s:\t %d\n", prop.lpwstrName, vt.intVal );
                        break;
                    case VT_UI4:
                        wprintf( L"%32s:\t 0x%0x\n", prop.lpwstrName, vt.uintVal );
                        break;
                    case VT_UI8:
                        wprintf( L"%32s:\t 0x%x\n", prop.lpwstrName, vt.uhVal.QuadPart );
                        break;
                    case VT_BSTR:
                        wprintf( L"%32s:\t %s\n", prop.lpwstrName, vt.bstrVal );
                        break;
                    case VT_UNKNOWN:
                        wprintf( L"%32s:\t %p\n", prop.lpwstrName, vt.punkVal );
                        break;
                    case VT_SAFEARRAY:
                        break;
                    default:
                       break;
                }
                VariantClear((VARIANTARG*) &vt);
            }
        }
        pEnumProps->Release();
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)
