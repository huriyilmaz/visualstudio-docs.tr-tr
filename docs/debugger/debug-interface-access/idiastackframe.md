---
title: IDiaStackFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame interface
ms.assetid: 486d25b8-a590-41c1-bdb5-faff3ae35632
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a54bd52f3783bb0bedc279cffafab2f21e0b0f39
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741551"
---
# <a name="idiastackframe"></a>IDiaStackFrame
Yığın çerçevesinin özelliklerini gösterir.

## <a name="syntax"></a>Sözdizimi

```
IDiaStackFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Bu arabirim tarafından desteklenen yöntemler aşağıda verilmiştir:

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaStackFrame::get_allocatesBasePointer](../../debugger/debug-interface-access/idiastackframe-get-allocatesbasepointer.md)|Temel işaretçinin bu adres aralığındaki kod için ayrıldığını belirten bir bayrak alır. Bu yöntem kullanım dışıdır.|
|[IDiaStackFrame::get_base](../../debugger/debug-interface-access/idiastackframe-get-base.md)|Çerçevenin adres temelini alır.|
|[IDiaStackFrame::get_cplusplusExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-cplusplusexceptionhandling.md)|C++ Özel durum işlemenin etkin olduğunu belirten bir bayrak alır.|
|[IDiaStackFrame::get_functionStart](../../debugger/debug-interface-access/idiastackframe-get-functionstart.md)|Bloğun bir işlevin giriş noktasını içerdiğini belirten bir bayrak alır.|
|[IDiaStackFrame::get_lengthLocals](../../debugger/debug-interface-access/idiastackframe-get-lengthlocals.md)|Yığına gönderilen yerel değişkenlerin bayt sayısını alır.|
|[IDiaStackFrame::get_lengthParams](../../debugger/debug-interface-access/idiastackframe-get-lengthparams.md)|Yığına gönderilen parametrelerin bayt sayısını alır.|
|[IDiaStackFrame::get_lengthProlog](../../debugger/debug-interface-access/idiastackframe-get-lengthprolog.md)|Bloktaki prolog kodunun bayt sayısını alır|
|[IDiaStackFrame::get_lengthSavedRegisters](../../debugger/debug-interface-access/idiastackframe-get-lengthsavedregisters.md)|Yığına gönderilen kaydedilmiş yazmaçların bayt sayısını alır.|
|[IDiaStackFrame::get_localsBase](../../debugger/debug-interface-access/idiastackframe-get-localsbase.md)|Yereller adres temelini alır.|
|[IDiaStackFrame::get_maxStack](../../debugger/debug-interface-access/idiastackframe-get-maxstack.md)|Çerçevedeki yığına gönderilen en fazla bayt sayısını alır.|
|[IDiaStackFrame::get_rawLVarInstanceValue](../../debugger/debug-interface-access/idiastackframe-get-rawlvarinstancevalue.md)|Belirtilen yerel değişkenin değerini ham bayt olarak alır.|
|[IDiaStackFrame::get_registerValue](../../debugger/debug-interface-access/idiastackframe-get-registervalue.md)|Belirtilen kaydın değerini alır.|
|[IDiaStackFrame::get_returnAddress](../../debugger/debug-interface-access/idiastackframe-get-returnaddress.md)|Çerçevenin dönüş adresini alır.|
|[IDiaStackFrame::get_size](../../debugger/debug-interface-access/idiastackframe-get-size.md)|Çerçevenin boyutunu bayt cinsinden alır.|
|[IDiaStackFrame::get_systemExceptionHandling](../../debugger/debug-interface-access/idiastackframe-get-systemexceptionhandling.md)|Sistem özel durum işlemenin etkin olduğunu belirten bir bayrak alır.|
|[IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)|Çerçeve türünü alır.|

## <a name="remarks"></a>Açıklamalar
Yığın çerçevesi, yürütmesi sırasında işlev çağrısının soyutlamasıdır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
[IDiaEnumStackFrames:: Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md) metodunu çağırarak bu arabirimi elde edin. @No__t_1 arabirimini edinme hakkında bir örnek için bkz. [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) arabirimi.

## <a name="example"></a>Örnek
Bu örnek, yığın çerçevesinin çeşitli özniteliklerini görüntüler.

```C++
void PrintStackFrame(IDiaStackFrame* pFrame)
{
    if (pFrame != NULL)
    {
        ULONGLONG bottom = 0;
        ULONGLONG top    = 0;

        if (pFrame->get_base(&bottom) == S_OK &&
            pFrame->get_registerValue( CV_REG_ESP, &top ) == S_OK )
        {
            printf("range = 0x%08I64x - 0x%08I64x\n", bottom, top);
        }

        ULONGLONG returnAddress = 0;
        if (pFrame->get_returnAddress(&returnAddress) == S_OK)
        {
            printf("return address = 0x%08I64x\n", returnAddress);
        }

        DWORD lengthFrame     = 0;
        DWORD lengthLocals    = 0;
        DWORD lengthParams    = 0;
        DWORD lengthProlog    = 0;
        DWORD lengthSavedRegs = 0;
        if (pFrame->get_size(&lengthFrame) == S_OK &&
            pFrame->get_lengthLocals(&lengthLocals) == S_OK &&
            pFrame->get_lengthParams(&lengthParams) == S_OK &&
            pFrame->get_lengthProlog(&lengthProlog) == S_OK &&
            pFrame->get_lengthSavedRegisters(&lengthSavedRegs) == S_OK)
        {
            printf("stack frame size          = 0x%08lx bytes\n", lengthFrame);
            printf("length of locals          = 0x%08lx bytes\n", lengthLocals);
            printf("length of parameters      = 0x%08lx bytes\n", lengthParams);
            printf("length of prolog          = 0x%08lx bytes\n", lengthProlog);
            printf("length of saved registers = 0x%08lx bytes\n", lengthSavedRegs);
        }
    }
}
```

## <a name="requirements"></a>Gereksinimler
Üstbilgi: dia2. h

Kitaplık: diaguid. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)
- [IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
