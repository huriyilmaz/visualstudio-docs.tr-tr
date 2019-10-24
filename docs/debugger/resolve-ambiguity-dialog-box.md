---
title: Belirsizlik Iletişim kutusunu çöz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.Disambig
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Resolve Ambiguity dialog box
- debugger, Resolve Ambiguity dialog box
- debugging [C++], resolving ambiguity
ms.assetid: d9f47455-a116-4c84-8bad-2dfbf4d77f74
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4257fd213d6401de381e25c74c126b8468b76057
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729838"
---
# <a name="resolve-ambiguity-dialog-box"></a>Belirsizliği Çöz İletişim Kutusu
Hata ayıklayıcı görüntülenecek konumu seçe, `Resolve Ambiguity` iletişim kutusu görüntülenir. Örneğin, şablonlar kullanıyorsanız C++ , tek bir işlev şablonundan birden çok işlev oluşturabilirsiniz. Hata ayıklayıcı şablondaki bir kaynak konumda durakalıyorsa ve `Go To Disassembly`seçerseniz, hata ayıklayıcının birden çok seçeneği vardır. Şablondan oluşturulan her bir işlev kendi ayrıştırma koduna sahiptir ve hata ayıklayıcı hangi kodu görüntülemek istediğinizi bilmez. `Resolve Ambiguity` iletişim kutusu, tüm karşılık gelen konumların listesinden istediğiniz konumu seçmenizi sağlar.

 `Choose the specific location` komutlarınıza karşılık gelen tüm konumları listeler.

 `Address` her bir işlevin bellek adreslerini gösterir.

 `Function` her işlevin adını gösterir.

 `Module`, işlevin nesne kodunu içeren modülü (EXE veya DLL) gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısındaki İfadeler](../debugger/expressions-in-the-debugger.md)