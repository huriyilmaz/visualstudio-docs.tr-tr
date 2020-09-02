---
title: IDiaEnumDebugStreamData | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData interface
ms.assetid: e2023c32-4c05-4d0c-a0be-f016a230c788
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 378fc75c3bd392f228ea30d1736f059e0def6d52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695890"
---
# <a name="idiaenumdebugstreamdata"></a>IDiaEnumDebugStreamData
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Hata ayıklama veri akışındaki kayıtlara erişim sağlar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaEnumDebugStreamData : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaEnumDebugStreamData` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaEnumDebugStreamData::get__NewEnum](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-newenum.md)|Bu Numaralandırıcının [IEnumVARIANT arabirimi](https://msdn.microsoft.com/139e3c93-faef-4003-9079-e0e94494db3e) sürümünü alır.|  
|[IDiaEnumDebugStreamData::get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)|Hata ayıklama veri akışındaki kayıt sayısını alır.|  
|[IDiaEnumDebugStreamData::get_name](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-name.md)|Hata ayıklama veri akışının adını alır.|  
|[IDiaEnumDebugStreamData::Item](../../debugger/debug-interface-access/idiaenumdebugstreamdata-item.md)|Belirtilen kaydı alır.|  
|[IDiaEnumDebugStreamData::Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)|Numaralandırılmış dizideki belirtilen sayıda kaydı alır.|  
|[IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)|Numaralandırılmış bir dizide belirtilen sayıda kaydı atlar.|  
|[IDiaEnumDebugStreamData::Reset](../../debugger/debug-interface-access/idiaenumdebugstreamdata-reset.md)|Numaralandırılmış sırayı başlangıca sıfırlar.|  
|[IDiaEnumDebugStreamData::Clone](../../debugger/debug-interface-access/idiaenumdebugstreamdata-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırılmış sırayı içeren bir Numaralandırıcı oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu arabirim bir hata ayıklama veri akışındaki kayıt akışını temsil eder. Her kaydın boyutu ve yorumu, kaydın geldiği veri akışına bağımlıdır. Bu arabirim, sembol dosyasındaki ham veri baytlarına etkin bir şekilde erişim sağlar.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bir nesne almak için [IDiaEnumDebugStreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md) veya [IDiaEnumDebugStreams:: Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md) yöntemlerini çağırın `IDiaEnumDebugStreamData` .  
  
## <a name="example"></a>Örnek  
 Bu örnekte, tek bir veri akışına ve kayıtlarına nasıl erişebileceğiniz gösterilmektedir.  
  
```cpp#  
void PrintStreamData(IDiaEnumDebugStreamData* pStream)  
{  
    BSTR  wszName;  
    LONG  dwElem;  
    ULONG celt    = 0;  
    DWORD cbData;  
    DWORD cbTotal = 0;  
    BYTE  data[1024];  
  
    if(pStream->get_name(&wszName) != S_OK)  
    {  
        wprintf_s(L"ERROR - PrintStreamData() get_name\n");  
    }  
    else  
    {  
        wprintf_s(L"Stream: %s", wszName);  
        SysFreeString(wszName);  
    }  
    if(pStream->get_Count(&dwElem) != S_OK)  
    {  
        wprintf(L"ERROR - PrintStreamData() get_Count\n");  
    }  
    else  
    {  
        wprintf(L"(%d)\n", dwElem);  
    }  
    while(pStream->Next(1, sizeof(data), &cbData, (BYTE *)&data, &celt) == S_OK)  
    {  
        DWORD i;  
        for (i = 0; i < cbData; i++)  
        {  
            wprintf(L"%02X ", data[i]);  
            if(i && i % 8 == 7 && i+1 < cbData)  
            {  
                wprintf(L"- ");  
            }  
        }  
        wprintf(L"| ");  
        for(i = 0; i < cbData; i++)  
        {  
            wprintf(L"%c", iswprint(data[i]) ? data[i] : '.');  
        }  
        wprintf(L"\n");  
        cbTotal += cbData;  
    }  
    wprintf(L"Summary :\n\tSizeof(Elem) = %d\n\tNo of Elems = %d\n\n",  
            cbTotal/dwElem, dwElem);  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: dia2. h  
  
 Kitaplık: diaguid. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (hata ayıklama arabirimi erişim SDK 'Sı)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreams:: öğe](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
