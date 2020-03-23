---
title: 'Adım 9: Diğer özellikleri deneyin'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32ac2f1977bb0b8b391651ed7ed459b9dc560330
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579737"
---
# <a name="step-9-try-other-features"></a>Adım 9: Diğer özellikleri deneyin
Daha fazla bilgi edinmek için simgeleri ve renkleri değiştirmeyi, oyun zamanlayıcısı ve sesler eklemeyi deneyin. Oyunu daha zorlu hale getirmek için tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.

Örneğin tamamlanmış bir sürümünü indirmek için, [tam eşleşen oyun öğretici örnek](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba)bakın.

## <a name="to-try-other-features"></a>Diğer özellikleri denemek için

- Simgelerin ve renklerin yerine kendi tercih ettiklerinizi kullanın.

    > [!TIP]
    > Etiketin [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) özelliğine bakmayı deneyin.

- Oyuncunun oyunu kazanmasının ne kadar sürdüğünü izleyen bir oyun zamanlayıcısı ekleyin.

    > [!TIP]
    > Bunu yapmak için, yukarıdaki <xref:System.Windows.Forms.TableLayoutPanel>formda geçen süreyi görüntülemek için bir etiket ekleyebilir ve zamanı izlemek için forma başka bir zamanlayıcı ekleyebilirsiniz. Oyuncu oyuna başladığında zamanlayıcıyı başlatmak ve son iki simgeyi eşleştirdikten sonra zamanlayıcıyı durdurmak için kod kullanın.

- Oyuncu bir eşleşme bulduğunda çalacak bir ses, eşleşmeyen iki simgeyi açtığında çalacak başka bir ses ve program simgeleri yeniden gizlediğinde çalacak üçüncü bir ses ekleyin.

    > [!TIP]
    > Sesleri çalmak için <xref:System.Media> ad alanını kullanabilirsiniz. Daha fazla bilgi için [Windows Forms uygulamasında (C#) veya](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) Visual [Basic'te ses çalma konusuna](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) bakın.

- Oyun tahtasını büyüterek oyunu zorlaştırın.

    > [!TIP]
    > TableLayoutPanel'e satır ve sütun eklemekten daha fazlasını yapmanız gerekir - ayrıca oluşturduğunuz simgelerin sayısını da göz önünde bulundurmanız gerekir.

- Oyuncunun tepki verirken çok yavaş davranması ve belirli bir süre dolmadan önce ikinci simgeyi seçmemesi durumunda ilk simgeyi gizleyerek oyunu daha zorlu hale getirin.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Yararlanabileceğiniz harika ve ücretsiz video öğrenme kaynakları vardır. Visual Basic'te programlama hakkında daha fazla bilgi edinmek [için Visual Basic temellerine bakın: Mutlak yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) C#'da programlama hakkında daha fazla bilgi edinmek [için C# temellerine bakın: Yeni başlayanlar için geliştirme.](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)

- Önceki öğretici adıma dönmek için bkz: [Adım 8: Oyuncunun kazanıp kazanmadığını doğrulamak için bir yöntem ekleyin.](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)
