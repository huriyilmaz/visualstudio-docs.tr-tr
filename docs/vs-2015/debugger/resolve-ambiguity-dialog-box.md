---
title: Belirsizlik Iletişim kutusunu çöz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.Disambig
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b35d305bbd011adc02692cd7c9c687ac0bfc7d45
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148783"
---
# <a name="resolve-ambiguity-dialog-box"></a>Belirsizliği Çöz İletişim Kutusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Resolve Ambiguity`Hata ayıklayıcı görüntülenecek konumu seçeolmadığında iletişim kutusu görüntülenir. Örneğin, C++ şablonları kullanıyorsanız, tek bir işlev şablonundan birden çok işlev oluşturabilirsiniz. Hata ayıklayıcı şablondaki bir kaynak konumda durakalıyorsa ve `Go To Disassembly` ' yi seçerseniz, hata ayıklayıcıda birden çok seçenek bulunur. Şablondan oluşturulan her bir işlev kendi ayrıştırma koduna sahiptir ve hata ayıklayıcı hangi kodu görüntülemek istediğinizi bilmez. `Resolve Ambiguity`İletişim kutusu, tüm karşılık gelen konumların listesinden istediğiniz konumu seçmenizi sağlar.  
  
 `Choose the specific location`  
 Komutlarınıza karşılık gelen tüm konumları listeler.  
  
 `Address`  
 Her işlev için bellek adreslerini gösterir.  
  
 `Function`  
 Her işlevin adını gösterir.  
  
 `Module`  
 İşlevin nesne kodunu içeren modülü (EXE veya DLL) gösterir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcıdaki İfadeler](../debugger/expressions-in-the-debugger.md)
