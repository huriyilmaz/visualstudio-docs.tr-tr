---
title: IDiaEnumSourceFiles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8b095515be5e3c032667c96d8b13d92aa5995c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189723"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Veri kaynağında bulunan çeşitli kaynak dosyalarını numaralandırır.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDiaEnumSourceFiles : IUknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaEnumSourceFiles` .  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|`IEnumVARIANT Interface`Bu Numaralandırıcı sürümünü alır.|  
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|Kaynak dosya sayısını alır.|  
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Bir dizin aracılığıyla bir kaynak dosyası alır.|  
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Sabit Listesi dizisinde belirtilen sayıda kaynak dosyası alır.|  
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Sabit Listesi dizisinde belirtilen sayıda kaynak dosyasını atlar.|  
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Bir numaralandırma dizisini başlangıca sıfırlar.|  
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Geçerli numaralandırıcı ile aynı numaralandırma durumunu içeren bir Numaralandırıcı oluşturur.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 `QueryInterface`Yöntemi bir [IDiaTable](../../debugger/debug-interface-access/idiatable.md) nesnesi üzerinde çağırarak bu arabirimi elde edin. Ayrıntılar için örneğe bakın.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `IDiaEnumSourceFiles` BIR DIA oturum nesnesindeki Tablo listesinden arabirimin nasıl alınacağını gösterir. Kaynak dosya bilgilerine erişme örneği için, bkz. [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) arabirimi.  
  
```cpp#  
  
IDiaEnumSourceFiles* GetEnumSourceFiless(IDiaSession *pSession)  
{  
    IDiaEnumSourceFiles * pUnknown    = NULL;  
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);  
    IDiaEnumTables*       pEnumTables = NULL;  
    IDiaTable*            pTable      = NULL;  
    ULONG                 celt        = 0;  
  
    if (pSession->getEnumTables(&pEnumTables) != S_OK)  
    {  
        wprintf(L"ERROR - GetTable() getEnumTables\n");  
        return NULL;  
    }  
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)  
    {  
        // There is only one table that matches the given iid  
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);  
        pTable->Release();  
        if (hr == S_OK)  
        {  
            break;  
        }  
    }  
    pEnumTables->Release();  
    return pUnknown;  
}  
```  
  
## <a name="requirements"></a>Gereksinimler  
 Üstbilgi: dia2. h  
  
 Kitaplık: diaguid. lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Arabirimler (hata ayıklama arabirimi erişim SDK 'Sı)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaSession:: findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSession:: findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
