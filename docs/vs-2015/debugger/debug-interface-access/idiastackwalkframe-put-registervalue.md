---
title: IDiaStackWalkFrame::p ut_registerValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b090e85005ffcab6498adb6f85885cd86c9813fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150187"
---
# <a name="idiastackwalkframeput_registervalue"></a>IDiaStackWalkFrame::put_registerValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir kaydın değerini ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `index`  
 'ndaki Yazılacak kaydı belirten [CV_HREG_e sabit listesi](../../debugger/debug-interface-access/cv-hreg-e.md) numaralandırmasından bir değer.  
  
 `NewVal`  
 'ndaki Yeni kayıt değeri.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV_HREG_e Numaralandırması](../../debugger/debug-interface-access/cv-hreg-e.md)
