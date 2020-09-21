---
title: Karma kodda çağrı yığını penceresinde eksik bilgi &
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32fe52b31daa384718eae629d3051bade93959d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808161"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Çağrı Yığını Penceresinde Karışık Kod ve Eksik Bilgiler
Yönetilen ve yerel kod için çağrı yığınları arasındaki farklılıklar nedeniyle, kod türü karışımında hata ayıklayıcı her zaman tüm çağrı yığınını gösteremez. Yerel kod yönetilen kodu çağırdığında, **çağrı yığını** penceresinde aşağıdaki tutarsızlıkları fark edebilirsiniz:

- Yönetilen kodun hemen üzerindeki yerel çerçeve **çağrı yığını** penceresinde eksik olabilir. Daha fazla bilgi için bkz. [nasıl yapılır: yerel çerçeveler çağrı yığını penceresinde olmadığında yönetilen kodun dışına adım atın](how-to-use-the-call-stack-window.md).

- Hata ayıklayıcı dışında başlatılan karma mod uygulamaları için **çağrı yığını** penceresi yalnızca yönetilen kodu görüntüleyebilir ve yerel çerçevelerin hiçbiri görünür olmayacaktır.

  Her iki durum da oldukça nadir. Yönetilen koda yapılan çoğu yerel çağrıda, çağrı yığınları doğru şekilde görünür.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl Yapılır: Çağrı Yığını Penceresini Kullanma](../debugger/how-to-use-the-call-stack-window.md)