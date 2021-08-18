---
title: Belirsizlik Iletişim kutusunu çöz | Microsoft Docs
description: hata ayıklayıcı görüntülenecek konumu seçemezse görünen belirsizliği çöz iletişim kutusunu Visual Studio gözden geçirin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c94742816f2149b53947fa3475c33b14ed7367c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122120783"
---
# <a name="resolve-ambiguity-dialog-box"></a>Belirsizliği Çöz İletişim Kutusu
`Resolve Ambiguity`Hata ayıklayıcı görüntülenecek konumu seçeolmadığında iletişim kutusu görüntülenir. Örneğin, C++ şablonları kullanıyorsanız, tek bir işlev şablonundan birden çok işlev oluşturabilirsiniz. Hata ayıklayıcı şablondaki bir kaynak konumda durakalıyorsa ve `Go To Disassembly` ' yi seçerseniz, hata ayıklayıcıda birden çok seçenek bulunur. Şablondan oluşturulan her bir işlev kendi ayrıştırma koduna sahiptir ve hata ayıklayıcı hangi kodu görüntülemek istediğinizi bilmez. `Resolve Ambiguity`İletişim kutusu, tüm karşılık gelen konumların listesinden istediğiniz konumu seçmenizi sağlar.

 `Choose the specific location` Komutlarınıza karşılık gelen tüm konumları listeler.

 `Address` Her işlev için bellek adreslerini gösterir.

 `Function` Her işlevin adını gösterir.

 `Module` İşlevin nesne kodunu içeren modülü (EXE veya DLL) gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcıdaki İfadeler](../debugger/expressions-in-the-debugger.md)