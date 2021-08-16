---
title: Düzenle ve Devam Edin ile kesme modunda Düzenleme | Microsoft Docs
description: Kesme modundayken düzenleme kodunuzu düzenlemek için Düzenle ve devam Visual Basic nasıl kullanabileceğinize bakın. Kesme moduna girmenin çeşitli yolları vardır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [Visual Basic], applying edits in break mode
- break mode, applying code changes
- Edit and Continue, applying edits in break mode
- editing, break mode
- coding, editing in break mode
- code, editing in break mode
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 46b444d7078fe3bfa103648d616128a5879a86dffe39213f494b67247222dd28
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362399"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Nasıl yapılır: Düzenle ve Devam Ile Kesme Modunda Düzenleme Uygulama (Visual Basic)
Kodunuzu Kesme modunda düzenlemek ve yürütmeyi durdurmadan ve yeniden başlatmadan devam etmek için Düzenle ve Devam'ı kullanabilirsiniz.

Hata ayıklama sırasında Düzenle ve Devam Edin'i kullanmaya ilişkin sınırlamalar için bkz. Desteklenen [Kod Değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Kodu Kesme modunda düzenlemek için

1. Aşağıdakilerden birini yaparak Kesme moduna girin:

    - Kodunda bir kesme noktası ayarlayın, sonra Hata  Ayıklama menüsünden Hata Ayıklamayı Başlat'ı seçin ve uygulamanın kesme noktasıyla birlikte isabetini bekleyin. 

         -veya-

    - Hata ayıklamayı başlat ve ardından Hata **Ayıkla menüsünden** Hepsini **Kır'ı** seçin.

         -veya-

    - Bir özel durum oluştuğunda, Özel Durum **Yardımcısı'nda** Düzenlemeyi **Etkinleştir'i seçin.**

2. İstenen ve desteklenen kod değişikliklerini yapın.

     Daha fazla bilgi için [bkz. Desteklenen Kod Değişiklikleri (C# ve Visual Basic).](../debugger/supported-code-changes-csharp.md)

    > [!NOTE]
    > Düzenle ve Devam' tarafından izin verilmiyor bir kod değişikliği yapmaya çalışırken, düzenlemenizin altı mor dalgalı çizgiyle altı çizili olur ve düzenleme Görev Listesi. Geçersiz kod değişikliğini geri almadıkça kod yürütmeye devam etmek mümkün olmayacaktır.

3. Hata **Ayıkla menüsünde Devam'a** **tıklar ve** yürütmeyi sürdürün.

     Kodunuz artık projeye dahil edilmiş uygulanan düzenlemeleriniz ile yürütülür.

## <a name="see-also"></a>Ayrıca bkz.
- [Desteklenen Kod Değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Düzenle ve Devam Et (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
