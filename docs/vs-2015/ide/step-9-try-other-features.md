---
title: '9. Adım: diğer özellikleri deneyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 379fc9c28b8d36f7bd606719a443b16108f0095d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299981"
---
# <a name="step-9-try-other-features"></a>9. Adım: Diğer Özellikleri Deneme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Daha fazla bilgi edinmek için simgeleri ve renkleri değiştirmeyi, oyun zamanlayıcısı ve sesler eklemeyi deneyin. Oyunu daha zorlu hale getirmek için tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.

### <a name="to-try-other-features"></a>Diğer özellikleri denemek için

- Simgelerin ve renklerin yerine kendi tercih ettiklerinizi kullanın.

    > [!TIP]
    > Etiketin [ForeColor](https://msdn.microsoft.com/library/system.windows.forms.control.forecolor%28v=vs.110%29.aspx) özelliğine bakmaya çalışın.

- Oyuncunun oyunu kazanmasının ne kadar sürdüğünü izleyen bir oyun zamanlayıcısı ekleyin.

    > [!TIP]
    > Bunun için, TableLayoutPanel üzerindeki forma geçen süreyi gösterecek bir etiket ekleyebilir ve süreyi izlemek için de forma bir diğer zamanlayıcı ekleyebilirsiniz. Oyuncu oyuna başladığında zamanlayıcıyı başlatmak ve son iki simgeyi eşleştirdikten sonra zamanlayıcıyı durdurmak için kod kullanın.

- Oyuncu bir eşleşme bulduğunda çalacak bir ses, eşleşmeyen iki simgeyi açtığında çalacak başka bir ses ve program simgeleri yeniden gizlediğinde çalacak üçüncü bir ses ekleyin.

    > [!TIP]
    > Sesleri çalmak için System.media ad alanını kullanabilirsiniz. Daha fazla bilgi için bkz. Windows Forms uygulamasında ses [yürütme (C# .NET)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) veya [Visual Basic ses yürütme](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) .

- Oyun tahtasını büyüterek oyunu zorlaştırın.

    > [!TIP]
    > TableLayoutPanel denetimine satır ve sütunları eklemekten fazlasını yapmanız ve oluşturduğunuz simge sayısını da düşünmeniz gerekir.

- Oyuncunun tepki verirken çok yavaş davranması ve belirli bir süre dolmadan önce ikinci simgeyi seçmemesi durumunda ilk simgeyi gizleyerek oyunu daha zorlu hale getirin.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir yerde tıkanıp kalırsanız veya programlamayla ilgili sorularınız olursa, MSDN forumlarından birinde sorunuzu göndermeyi deneyin. Bkz. forum ve [Visual C# forumu](https://social.msdn.microsoft.com/Forums/en-US/home) [Visual Basic](https://social.msdn.microsoft.com/Forums/en-US/home) .

- Yararlanabileceğiniz harika ve ücretsiz video öğrenme kaynakları vardır. Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). Visual C# ' de programlama hakkında daha fazla bilgi edinmek için bkz. [C# temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Önceki öğretici adımına dönmek için bkz. 8. [Adım: oyuncunun kazandığını doğrulamak Için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
