---
title: '9. Adım: Diğer özellikleri deneme'
description: Simgeleri ve renkleri değiştirme, oyun süreölçeri ekleme, ses ekleme ve oyun panosunu daha büyük hale getirme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6f542c2fe86b642a1d8cf53d9fe1bff4af611c9e
ms.sourcegitcommit: 3d1143b007bf0ead80bf4cb3867bf89ab0ab5b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2021
ms.locfileid: "123397674"
---
# <a name="step-9-try-other-features"></a>9. Adım: Diğer özellikleri deneme
Daha fazla bilgi edinmek için simgeleri ve renkleri değiştirmeyi, oyun zamanlayıcısı ve sesler eklemeyi deneyin. Oyunu daha zorlu hale getirmek için tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.

Örneğin tamamlanmış bir sürümünü indirmek için, bkz. [tüm eşleşen oyun öğreticisi örneği](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## <a name="to-try-other-features"></a>Diğer özellikleri denemek için

- Simgelerin ve renklerin yerine kendi tercih ettiklerinizi kullanın.

    > [!TIP]
    > Etiketin [ForeColor](<xref:System.Windows.Forms.Control.ForeColor%2A>) özelliğine bakmaya çalışın.

- Oyuncunun oyunu kazanmasının ne kadar sürdüğünü izleyen bir oyun zamanlayıcısı ekleyin.

    > [!TIP]
    > Bunu yapmak için, yukarıdaki formda geçen süreyi görüntüleyecek bir etiket ekleyebilirsiniz <xref:System.Windows.Forms.TableLayoutPanel> ve saati izlemek için forma başka bir zamanlayıcı ekleyebilirsiniz. Oyuncu oyuna başladığında zamanlayıcıyı başlatmak ve son iki simgeyi eşleştirdikten sonra zamanlayıcıyı durdurmak için kod kullanın.

- Oyuncu bir eşleşme bulduğunda çalacak bir ses, eşleşmeyen iki simgeyi açtığında çalacak başka bir ses ve program simgeleri yeniden gizlediğinde çalacak üçüncü bir ses ekleyin.

    > [!TIP]
    > Ses çalmak için <xref:System.Media> ad alanını kullanabilirsiniz. daha fazla bilgi için bkz. Windows Forms uygulamasında ses [yürütme (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) veya [Visual Basic ses yürütme](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) .

- Oyun tahtasını büyüterek oyunu zorlaştırın.

    > [!TIP]
    > TableLayoutPanel 'e satırlar ve sütunlar eklemeniz yeterlidir. Ayrıca, oluşturduğunuz simge sayısını göz önünde bulundurmanız gerekir.

- Oyuncunun tepki verirken çok yavaş davranması ve belirli bir süre dolmadan önce ikinci simgeyi seçmemesi durumunda ilk simgeyi gizleyerek oyunu daha zorlu hale getirin.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Yararlanabileceğiniz harika ve ücretsiz video öğrenme kaynakları vardır. Visual Basic 'da programlama hakkında daha fazla bilgi için bkz. [Visual Basic temelleri: mutlak yeni başlayanlar için geliştirme](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). C# dilinde programlama hakkında daha fazla bilgi edinmek için bkz. [C# temelleri: mutlak yeni başlayanlar Için geliştirme](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- Önceki öğretici adımına dönmek için bkz. 8. [Adım: oyuncunun kazandığını doğrulamak için yöntem ekleme](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).
