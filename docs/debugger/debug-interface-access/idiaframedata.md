---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee2f68066de6a41e6fd6a1cf4143613a7597d6f1
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85467185"
---
# <a name="idiaframedata"></a>IDiaFrameData
Yığın çerçevesinin ayrıntılarını gösterir.

## <a name="syntax"></a>Syntax

```
IDiaFrameData : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaFrameData` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaFrameData::get_addressSection](../../debugger/debug-interface-access/idiaframedata-get-addresssection.md)|Çerçeveye ait kod adresinin bölüm kısmını alır.|
|[IDiaFrameData::get_addressOffset](../../debugger/debug-interface-access/idiaframedata-get-addressoffset.md)|Çerçeve için kod adresinin konum kısmını alır.|
|[IDiaFrameData::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiaframedata-get-relativevirtualaddress.md)|Çerçeveye ait kodun görüntü göreli sanal adresini (RVA) alır.|
|[IDiaFrameData::get_virtualAddress](../../debugger/debug-interface-access/idiaframedata-get-virtualaddress.md)|Çerçeve için kodun sanal adresini (VA) alır.|
|[IDiaFrameData::get_lengthBlock](../../debugger/debug-interface-access/idiaframedata-get-lengthblock.md)|Çerçeve tarafından tanımlanan kod bloğunun uzunluğunu bayt cinsinden alır.|
|[IDiaFrameData::get_lengthLocals](../../debugger/debug-interface-access/idiaframedata-get-lengthlocals.md)|Yığına gönderilen yerel değişkenlerin bayt sayısını alır.|
|[IDiaFrameData::get_lengthParams](../../debugger/debug-interface-access/idiaframedata-get-lengthparams.md)|Yığına gönderilen parametrelerin bayt sayısını alır.|
|[IDiaFrameData::get_maxStack](../../debugger/debug-interface-access/idiaframedata-get-maxstack.md)|Çerçevedeki yığına gönderilen en fazla bayt sayısını alır.|
|[IDiaFrameData::get_lengthProlog](../../debugger/debug-interface-access/idiaframedata-get-lengthprolog.md)|Bloktaki prolog kodunun bayt sayısını alır.|
|[IDiaFrameData::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiaframedata-get-lengthsavedregisters.md)|Yığına gönderilen kaydedilmiş yazmaçların bayt sayısını alır.|
|[IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)|Geçerli işleve yapılan çağrıdan önce kayıt kümesini hesaplamak için kullanılan program dizesini alır.|
|[IDiaFrameData::get_systemExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-systemexceptionhandling.md)|Sistem özel durum işlemenin etkin olduğunu belirten bir bayrak alır.|
|[IDiaFrameData::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiaframedata-get-cplusplusexceptionhandling.md)|C++ özel durum işlemenin etkin olduğunu belirten bir bayrak alır.|
|[IDiaFrameData::get_functionStart](../../debugger/debug-interface-access/idiaframedata-get-functionstart.md)|Bloğun bir işlevin giriş noktasını içerdiğini gösteren bir bayrak alır.|
|[IDiaFrameData::get_allocatesBasePointer](../../debugger/debug-interface-access/idiaframedata-get-allocatesbasepointer.md)|Taban işaretçisinin bu adres aralığındaki kod için ayrıldığını gösteren bir bayrak alır. Bu yöntem kullanım dışıdır.|
|[IDiaFrameData::get_type](../../debugger/debug-interface-access/idiaframedata-get-type.md)|Derleyiciye özgü çerçeve türünü alır.|
|[IDiaFrameData::get_functionParent](../../debugger/debug-interface-access/idiaframedata-get-functionparent.md)|Kapsayan işlev için çerçeve verisi arabirimini alır.|
|[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)|Yığın geriye doğru izleme gerçekleştirir ve bir yığın ilerleme çerçevesi arabirimindeki yazmaçların geçerli durumunu döndürür.|

## <a name="remarks"></a>Açıklamalar
 Bir çerçeve için kullanılabilen ayrıntılar, adres aralığı içindeki ve blok uzunluğu tarafından belirtilen yürütme noktaları içindir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 [IDiaEnumFrameData:: Next](../../debugger/debug-interface-access/idiaenumframedata-next.md) veya [IDiaEnumFrameData:: Item](../../debugger/debug-interface-access/idiaenumframedata-item.md) metotlarını çağırarak bu arabirimi elde edin. Ayrıntılar için bkz. [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) arabirimi.

## <a name="example"></a>Örnek
 Bu örnek, bir nesnenin özelliklerini yazdırır `IDiaFrameData` . Arabirimin nasıl alındıklarına ilişkin bir örnek için bkz. [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) arabirimi `IDiaFrameData` .

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
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
- [IDiaEnumFrameData::Item](../../debugger/debug-interface-access/idiaenumframedata-item.md)
- [IDiaEnumFrameData::Next](../../debugger/debug-interface-access/idiaenumframedata-next.md)
