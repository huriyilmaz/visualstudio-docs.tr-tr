---
title: Çağrı yığını penceresinde karışık kod ve eksik bilgiler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3995e14379fa4bd3ebd5cc276613c288b4437d35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193285"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Çağrı Yığını Penceresinde Karışık Kod ve Eksik Bilgiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yönetilen ve yerel kod için çağrı yığınları arasındaki farklılıklar nedeniyle, kod türü karışımında hata ayıklayıcı her zaman tüm çağrı yığınını gösteremez. Yerel kod yönetilen kodu çağırdığında, **çağrı yığını** penceresinde aşağıdaki tutarsızlıkları fark edebilirsiniz:  
  
- Yönetilen kodun hemen üzerindeki yerel çerçeve **çağrı yığını** penceresinde eksik olabilir. Daha fazla bilgi için bkz. [nasıl yapılır: yerel çerçeveler çağrı yığını penceresinde olmadığında yönetilen kodun dışına adım atın](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Hata ayıklayıcı dışında başlatılan karma mod uygulamaları için **çağrı yığını** penceresi yalnızca yönetilen kodu görüntüleyebilir ve yerel çerçevelerin hiçbiri görünür olmayacaktır.  
  
  Her iki durum da oldukça nadir. Yönetilen koda yapılan çoğu yerel çağrıda, çağrı yığınları doğru şekilde görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma](../debugger/how-to-use-the-call-stack-window.md)
