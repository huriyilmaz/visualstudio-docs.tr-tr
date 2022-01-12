---
title: '9. Adım: Diğer özellikleri deneme'
description: Simgeleri ve renkleri değiştirme, oyun zamanlayıcısı ekleme, ses ekleme ve oyun panosunun daha büyük hale nasıl geldiğini öğrenin.
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
ms.openlocfilehash: 5c4da9c8afd48b165f3b9406219c92d2ced198ab
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135516784"
---
# <a name="step-9-try-other-features"></a>9. Adım: Diğer özellikleri deneme
Daha fazla bilgi edinmek için simgeleri ve renkleri değiştirmeyi, oyun zamanlayıcısı ve sesler eklemeyi deneyin. Oyunu daha zorlu hale getirmek için tahtayı büyütmeyi ve zamanlayıcıyı ayarlamayı deneyin.

Örneğin tamamlanmış bir sürümünü indirmek için bkz. [Eşleştirmeyi tamamlama öğreticisi örneği.](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba)

## <a name="to-try-other-features"></a>Diğer özellikleri denemek için

- Simgelerin ve renklerin yerine kendi tercih ettiklerinizi kullanın.

    > [!TIP]
    > Etiketin [Forecolor özelliğine bakabilirsiniz.](<xref:System.Windows.Forms.Control.ForeColor%2A>)

- Oyuncunun oyunu kazanmasının ne kadar sürdüğünü izleyen bir oyun zamanlayıcısı ekleyin.

    > [!TIP]
    > Bunu yapmak için, form üzerinde geçen zamanı görüntülemek için bir etiket ekleyebilir ve zamanı izlemek için forma başka bir <xref:System.Windows.Forms.TableLayoutPanel> zamanlayıcı eklersiniz. Oyuncu oyuna başladığında zamanlayıcıyı başlatmak ve son iki simgeyi eşleştirdikten sonra zamanlayıcıyı durdurmak için kod kullanın.

- Oyuncu bir eşleşme bulduğunda çalacak bir ses, eşleşmeyen iki simgeyi açtığında çalacak başka bir ses ve program simgeleri yeniden gizlediğinde çalacak üçüncü bir ses ekleyin.

    > [!TIP]
    > Sesleri oynatmak için ad alanını <xref:System.Media> kullanabilirsiniz. Daha fazla bilgi için bkz. Windows Forms uygulamasında ses çalma [(C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) [veya Visual Basic](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be) ses çalma.

- Oyun tahtasını büyüterek oyunu zorlaştırın.

    > [!TIP]
    > TableLayoutPanel'e satır ve sütun eklemekten başka bir şey yapmak zorundasınız. Ayrıca, oluşturydurarak simge sayısını da göz önünde bulundurabilirsiniz.

- Oyuncunun tepki verirken çok yavaş davranması ve belirli bir süre dolmadan önce ikinci simgeyi seçmemesi durumunda ilk simgeyi gizleyerek oyunu daha zorlu hale getirin.

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Önceki öğretici adımına dönmek için [bkz. 8. Adım: Oyuncunun kazanıp kazanıp kazana olmadığını doğrulamak için bir yöntem ekleme.](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)
