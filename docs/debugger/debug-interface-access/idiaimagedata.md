---
description: Modülün veya görüntünün temel konumunun ve bellek uzaklarının ayrıntılarını gösterir.
title: IDiaImageData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData interface
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4d2a74f6cc8ffa1c79938ab061d59ed2273a3a9220864632a0e37f1d482e8e13
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121455018"
---
# <a name="idiaimagedata"></a>IDiaImageData
Modülün veya görüntünün temel konumunun ve bellek uzaklarının ayrıntılarını gösterir.

## <a name="syntax"></a>Syntax

```
IDiaImageData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaImageData` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaImageData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Modülün sanal belleğindeki konumunu uygulamaya göre alır.|
|[IDiaImageData::get_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Görüntünün sanal belleğindeki konumunu alır.|
|[IDiaImageData::get_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Görüntünün dayanmanız gereken bellek konumunu alır.|

## <a name="remarks"></a>Açıklamalar
Bazı hata ayıklama akışları (XDATA, PDATA) de görüntüde depolanan verilerin kopyalarını içerir. Bu akış veri nesneleri arabirim için sorgulanabilir `IDiaImageData` . Ayrıntılar için bu konudaki "çağıranlar için Notlar" bölümüne bakın.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
`QueryInterface`Bir [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) nesnesini çağırarak bu arabirimi edinin. Tüm hata ayıklama akışlarının arabirimi desteklemediğini unutmayın `IDiaImageData` . Örneğin, şu anda yalnızca XDATA ve PDATA akışları `IDiaImageData` arabirimi destekler.

## <a name="example"></a>Örnek
Bu örnekte, arabirimi destekleyen tüm akışlar için hata ayıklama akışlarının hepsi aranır `IDiaImageData` . Böyle bir akış bulunursa, bu akış hakkında bazı bilgiler görüntülenir.

```C++
void ShowImageData(IDiaSession *pSession)
{
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumDebugStreams> pStreamsList;
        HRESULT hr;

        hr = pSession->getEnumDebugStreams(&pStreamsList);
        if (SUCCEEDED(hr))
        {
            LONG numStreams = 0;
            hr = pStreamsList->get_Count(&numStreams);
            if (SUCCEEDED(hr))
            {
                ULONG fetched = 0;
                for (LONG i = 0; i < numStreams; i++)
                {
                    CComPtr<IDiaEnumDebugStreamData> pStream;
                    hr = pStreamsList->Next(1,&pStream,&fetched);
                    if (fetched == 1)
                    {
                        CComPtr<IDiaImageData> pImageData;
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),
                                                     (void **)&pImageData);
                        if (SUCCEEDED(hr))
                        {
                            CComBSTR name;
                            hr = pStream->get_name(&name);
                            if (SUCCEEDED(hr))
                            {
                                wprintf(L"Stream %s:\n",(BSTR)name);
                            }
                            else
                            {
                                wprintf(L"Failed to get name of stream\n");
                            }

                            ULONGLONG imageBase = 0;
                            if (pImageData->get_imageBase(&imageBase) == S_OK)
                            {
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);
                            }

                            DWORD relVA = 0;
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)
                            {
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);
                            }

                            ULONGLONG va = 0;
                            if (pImageData->get_virtualAddress(&va) == S_OK)
                            {
                                wprintf(L"  virtual address = 0x%0I64x\n", va);
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)
