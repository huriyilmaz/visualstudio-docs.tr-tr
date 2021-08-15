---
description: Bir yığın çerçevesinin ayrıntılarını gösterir.
title: IDiaFrameData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData interface
ms.assetid: 2f1b4986-341b-4641-89a4-226e261e9d93
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8ac61b50c01312c66f19ac44a3d2142a627a9c02ac7c2374f850c173eca821a2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121312167"
---
# <a name="idiaframedata"></a>IDiaFrameData
Bir yığın çerçevesinin ayrıntılarını gösterir.

## <a name="syntax"></a>Syntax

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable Sırasına Göre Yöntemler
Aşağıdaki tabloda yöntemlerini `IDiaFrameData` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Çerçevenin kod adresinin bölüm bölümünü alın.|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Çerçeve için kod adresinin uzaklık bölümünü alın.|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Çerçevenin kodunun görüntü göreli sanal adresini (RVA) alan.|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Çerçevenin kodunun sanal adresini (VA) alan.|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Çerçeve tarafından açıklanan kod bloğu için bayt cinsinden uzunluğu alınır.|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Yığına gönderilen yerel değişkenlerin bayt sayısını alın.|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Yığına gönderilen parametre bayt sayısını alın.|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Çerçevede yığına gönderilen en fazla bayt sayısını alan.|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Blokta prolog kodunun bayt sayısını alan.|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Yığına gönderilen kaydedilmiş yazmazların bayt sayısını alın.|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Geçerli işleve yapılan çağrıdan önce kayıt kümesi hesaplamak için kullanılan program dizesini alır.|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Sistem özel durum işlemenin geçerli olduğunu belirten bir bayrak alınır.|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|C++ özel durum işlemenin geçerli olduğunu belirten bir bayrak alınır.|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Bloğun bir işlevin giriş noktasını içerdiğini belirten bir bayrak verir.|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Bu adres aralığındaki kod için temel işaretçinin ayrılmış olduğunu belirten bir bayrak alınır. Bu yöntem kullanım dışıdır.|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Derleyiciye özgü çerçeve türünü alın.|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Kapsayan işlev için çerçeve veri arabirimini verir.|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Yığın geriye doğru izleme gerçekleştirir ve bir yığın adım adım çerçeve arabiriminde yazmaların geçerli durumunu döndürür.|

## <a name="remarks"></a>Açıklamalar
 Çerçeve için kullanılabilen ayrıntılar, adres ve blok uzunluğu ile belirtilen adres aralığındaki yürütme noktalarına ilişkindir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) veya [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) yöntemlerini çağırarak bu arabirimi alın. Ayrıntılar için [bkz. IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) arabirimi.

## <a name="example"></a>Örnek
 Bu örnek, bir nesnenin özelliklerini `IDiaFrameData` yazdırır. Arabirimin nasıl elde edildiklerinin bir örneği için bkz. [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) `IDiaFrameData` arabirimi.

```C++
void PrintFrameData(IDiaFrameData* pFrameData){
    DWORD dwSect;
    DWORD dwOffset;
    DWORD cbBlock;
    DWORD cbLocals; // Number of bytes reserved for the function locals
    DWORD cbParams; // Number of bytes reserved for the function arguments
    DWORD cbMaxStack;
    DWORD cbProlog;
    DWORD cbSavedRegs;
    BOOL  bSEH;
    BOOL  bEH;
    BOOL  bStart;
    BSTR  wszProgram;

    if(pFrameData->get_addressSection(&dwSect) == S_OK &&
       pFrameData->get_addressOffset(&dwOffset) == S_OK &&
       pFrameData->get_lengthBlock(&cbBlock) == S_OK &&
       pFrameData->get_lengthLocals(&cbLocals) == S_OK &&
       pFrameData->get_lengthParams(&cbParams) == S_OK &&
       pFrameData->get_maxStack(&cbMaxStack) == S_OK &&
       pFrameData->get_lengthProlog(&cbProlog) == S_OK &&
       pFrameData->get_lengthSavedRegisters(&cbSavedRegs) == S_OK &&
       pFrameData->get_systemExceptionHandling(&bSEH) == S_OK &&
       pFrameData->get_cplusplusExceptionHandling(&bEH) == S_OK &&
       pFrameData->get_functionStart(&bStart) == S_OK )
    {
        wprintf(L"Frame address  : %04X:%08X\n", dwSect, dwOffset);
        wprintf(L"Block size     : 0x%8X\n", cbBlock);
        wprintf(L"Locals size    : 0x%8X\n", cbLocals);
        wprintf(L"Parms size     : 0x%8X\n", cbParams);
        wprintf(L"Max stack used : 0x%8X\n", cbMaxStack);
        wprintf(L"Prolog size    : 0x%8X\n", cbProlog);
        wprintf(L"Saved regs size: 0x%8X\n", cbSavedRegs);
        wprintf(L"System Exception Handling: %c\n", bSEH ? L'Y' : L'N');
        wprintf(L"C++ Exception Handling   : %c\n", bEH ? L'Y' : L'N');
        wprintf(L"Function starts in block : %c\n", bStart ? L'Y' : L'N');

        if (pFrameData->get_program(&wszProgram) == S_OK)
        {
            wprintf(L"Program used for register set: %s\n", wszProgram);
            SysFreeString(wszProgram);
        }
        else
        {
            wprintf(L"\n");
        }
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üst bilgi: Dia2.h

Kitaplık: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)
- [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
