---
title: DebugStackFrameDescriptor yapısı | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugStackFrameDescriptor
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugStackFrameDescriptor structure
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 910e08ec6d9982354eb71b50d5e916917808f140
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576547"
---
# <a name="debugstackframedescriptor-structure"></a>DebugStackFrameDescriptor Yapısı
Yığın çerçevelerini listeler ve aynı iş parçacığındaki çeşitli listeleyicilerden alınan çıktıyı birleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## <a name="members"></a>Üyeler  
 `pdsf`  
 Yığın çerçeve nesnesi.  
  
 `dwMin`  
 Bu yığın çerçevesiyle ilişkili olan alt fiziksel adres aralığının makineye bağlı bir gösterimi.  
  
 `dwLim`  
 Bu yığın çerçevesiyle ilişkili olan üst düzey fiziksel adres aralığının makineye bağlı bir gösterimi.  
  
 `fFinal`  
 Çerçevenin işlendiğini belirten bayrak.  
  
 `punkFinal`  
 Bu parametre `NULL` değilse, geçerli numaralandırıcı birleştirme durdurulur ve yeni bir tane başlatılmalıdır. Nesnesi, yeni numaralandırmanın nasıl başlatılacağını gösterir.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlem hata ayıklama Yöneticisi, yığın çerçevelerini birden çok betik altyapılarından sıralamak için bu yapıyı kullanır. Kurala göre, yığınlar aşağı doğru artar. Sonuç olarak, yığınların büyümesi durumunda adresler Twos-tamamlanmalı olmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Sabitleri, Sabit Listeleri ve Yapıları](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)