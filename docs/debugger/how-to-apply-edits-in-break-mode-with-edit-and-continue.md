---
title: Düzenle ve devam et ile kesme modunda düzenlemeleri uygulama | Microsoft Docs
description: kesme modundayken Visual Basic kodunuzu düzenlemek için düzenle ve devam et ' i kullanma bölümüne bakın. Kesme moduna girmek için çeşitli yollar vardır.
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 2288bfadb5bbc2108d4ba5179b13274a151af880
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135804811"
---
# <a name="how-to-apply-edits-in-break-mode-with-edit-and-continue-visual-basic"></a>Nasıl yapılır: Düzenle ve devam et ile kesme modunda düzenleme uygulama (Visual Basic)
Kodunuzu kesme modunda düzenlemek için Düzenle ve devam et ' i kullanabilir ve sonra yürütmeyi durdurup yeniden başlatmadan devam edebilirsiniz.

Hata ayıklama sırasında Düzenle ve devam et ile ilgili sınırlamalar için bkz. [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

### <a name="to-edit-code-in-break-mode"></a>Kodu kesme modunda düzenlemek için

1. Aşağıdakilerden birini yaparak kesme moduna girin:

    - Kodunuzda bir kesme noktası ayarlayın, ardından **Hata Ayıkla** menüsünden **hata ayıklamayı Başlat** ' ı seçin ve uygulamanın kesme noktasına gelmesini bekleyin.

         -veya-

    - Hata ayıklamayı başlatın ve **Hata Ayıkla** menüsünden **Tümünü kes** ' i seçin.

         -veya-

    - Bir özel durum oluştuğunda, **özel durum Yardımcısı** üzerinde **düzenlemesi etkinleştir** ' i seçin.

2. İstediğiniz ve desteklenen kod değişikliklerini yapın.

     Daha fazla bilgi için bkz. [desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md).

    > [!NOTE]
    > Düzenle ve devam et tarafından izin verilmeyen bir kod değişikliği yapmaya çalışırsanız, düzenlemeniz mor dalgalı bir çizgiyle altı çizili olur ve Görev Listesi bir görev görüntülenir. Geçersiz kod değişikliğini geri yüklemediğiniz takdirde kod yürütmeye devam edemeyeceksiniz.

3. **Hata Ayıkla** menüsünde, yürütmeyi sürdürmek için **devam** ' a tıklayın.

     Kodunuz artık projeye eklenen ve uygulanan düzenlemelerinizle yürütülür.

## <a name="see-also"></a>Ayrıca bkz.
- [Desteklenen kod değişiklikleri (C# ve Visual Basic)](../debugger/supported-code-changes-csharp.md)
- [Düzenle ve Devam Et (Visual Basic)](../debugger/edit-and-continue-visual-basic.md)
