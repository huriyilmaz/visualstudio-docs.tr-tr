---
title: 'IDiaFrameData:: get_program | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_program method
ms.assetid: 9201409e-b4b1-4e2e-a9f8-d17678ac538b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d87f5c7fda25a901d44b9f511b9a92eb4471f845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180008"
---
# <a name="idiaframedataget_program"></a>IDiaFrameData::get_program
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli işleve yapılan çağrıdan önce kayıt kümesini hesaplamak için kullanılan program dizesini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_program (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı Program dizesini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Program dizesi, bir prolog oluşturmak için yorumlanan bir makro dizisidir. Örneğin, tipik bir yığın çerçevesi Program dizesini kullanabilir `"$T0 $ebp = $eip $T0 4 + ^ = $ebp $T0 ^ = $esp $T0 8 + ="` . Biçim, işleçlerin işlenenleri izlediği ters Lehçe gösterimidir. `T0` yığında geçici bir değişkeni temsil eder. Bu örnek aşağıdaki adımları gerçekleştirir:  
  
1. Kayıt içeriğini içine taşıyın `ebp` `T0` .  
  
2. `4` `T0` Bir adres oluşturmak, bu adresten değeri almak ve kayıt sırasında değeri depolamak için içindeki değerine ekleyin `eip` .  
  
3. İçinde depolanan adresten değeri alın `T0` ve bu değeri kayıt ' de saklayın `ebp` .  
  
4. `8`İçindeki değerine ekleyin `T0` ve bu değeri yazmaç içinde depolayın `esp` .  
  
   Program dizesinin CPU 'ya ve geçerli yığın çerçevesi tarafından temsil edilen işlev için ayarlanan çağırma kuralına özel olduğunu unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
