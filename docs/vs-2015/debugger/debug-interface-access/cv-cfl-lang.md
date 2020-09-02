---
title: CV_CFL_LANG | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699356"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uygulamanın veya bağlı modülün kaynak kodu dilini belirtir.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
typedef enum CV_CFL_LANG {   
   CV_CFL_C       = 0x00,  
   CV_CFL_CXX     = 0x01,  
   CV_CFL_FORTRAN = 0x02,  
   CV_CFL_MASM    = 0x03,  
   CV_CFL_PASCAL  = 0x04,  
   CV_CFL_BASIC   = 0x05,  
   CV_CFL_COBOL   = 0x06,  
   CV_CFL_LINK    = 0x07,  
   CV_CFL_CVTRES  = 0x08,  
   CV_CFL_CVTPGD  = 0x09,  
   CV_CFL_CSHARP  = 0x0A,  
   CV_CFL_VB      = 0x0B,  
   CV_CFL_ILASM   = 0x0C,  
   CV_CFL_JAVA    = 0x0D,  
   CV_CFL_JSCRIPT = 0x0E,  
   CV_CFL_MSIL    = 0x0F,  
   CV_CFL_HLSL    = 0x10  
} CV_CFL_LANG;  
```  
  
## <a name="elements"></a>Öğeler  
 CV_CFL_C  
 Uygulama dili C 'dir.  
  
 CV_CFL_CXX  
 Uygulama dili C++ ' dır.  
  
 CV_CFL_FORTRAN  
 Uygulama dili FORTRAN.  
  
 CV_CFL_MASM  
 Uygulama dili Microsoft Macro Assembler ' dur.  
  
 CV_CFL_PASCAL  
 Uygulama dili Pascal.  
  
 CV_CFL_BASIC  
 Uygulama dili temel.  
  
 CV_CFL_COBOL  
 Uygulama dili COBOL.  
  
 CV_CFL_LINK  
 Uygulama, bağlayıcı tarafından oluşturulan bir modüldür.  
  
 CV_CFL_CVTRES  
 Uygulama, CVTRES aracıyla dönüştürülen bir kaynak modülüdür.  
  
 CV_CFL_CVTPGD  
 Uygulama, CVTPGD aracı ile oluşturulmuş bir POGO iyileştirilmiş modüldür.  
  
 CV_CFL_CSHARP  
 Uygulama dili C# ' dir.  
  
 CV_CFL_VB  
 Uygulama dili Visual Basic.  
  
 CV_CFL_ILASM  
 Uygulama dili, ara dil derlemesi (yani, ortak dil çalışma zamanı (CLR) derlemesi).  
  
 CV_CFL_JAVA  
 Uygulama dili Java.  
  
 CV_CFL_JSCRIPT  
 Uygulama dili JScript ' dir.  
  
 CV_CFL_MSIL  
 Uygulama dili bilinmeyen bir Microsoft ara dili (MSIL), büyük olasılıkla [/LTCG (bağlama zamanı kodu oluşturma)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) anahtarını kullanmanın bir sonucudur.  
  
 CV_CFL_HLSL  
 Uygulama dili yüksek düzey gölgelendirici dilidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu Numaralandırmadaki değerler [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) metoduna yapılan bir çağrı tarafından döndürülür.  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: cvconst. h  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Numaralandırmalar ve yapılar](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
