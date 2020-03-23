---
title: 'Adım 7: Çiftleri görünür tutun'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eeca594849625b548857a23b9d5c8e278dcdf07c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579298"
---
# <a name="step-7-keep-pairs-visible"></a>Adım 7: Çiftleri görünür tutun
Oyuncu yalnızca eşleşmeyen simge çiftlerini seçtiği sürece oyun düzgün çalışır. Ancak oyuncu eşleşen bir çift seçtiğinde ne olması gerektiğini bir düşünün. Oyun, zamanlayıcıyı açarak simgeleri yok etmek <xref:System.Windows.Forms.Timer.Start> yerine (yöntemi kullanarak), seçilen iki etiketin renklerini sıfırlamadan, `firstClicked` `secondClicked` referans değişkenlerini kullanarak etiketleri artık izlememesi için kendisini sıfırlamalıdır.

## <a name="to-keep-pairs-visible"></a>Çiftleri görünür durumda tutmak için

1. Zamanlayıcıyı `if` `label_Click()` çalıştırdığınız ifadenin hemen üstündeki kodun sonuna yakın olay işleyicisi yöntemine aşağıdaki deyimi ekleyin. Kodu programa eklerken yakından inceleyin. Kodun nasıl çalıştığını bir düşünün.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

       > [!IMPORTANT]
       > Use the programming language control at the top right of this page to view either the C# code snippet or the Visual Basic code snippet.<br><br>![Programming language control for Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Ekladığınız ifadenin `if` ilk satırı, oyuncunun seçtiği ilk etiketteki simgenin ikinci etiketteki simgeyle aynı olup olmadığını denetler. Simgeler aynıysa, program C#'daki kıvırcık ayraçlar veya Visual Basic'teki `if` deyimiçindeki üç deyim arasındaki üç ifadeyi yürütür. İlk iki deyim, `firstClicked` etiketlerin hiçbirini artık izlememelerini sağlayacak şekilde ve `secondClicked` başvuru değişkenlerini sıfırlar. (Bu iki ifadeyi zamanlayıcının <xref:System.Windows.Forms.Timer.Tick> olay işleyicisinden tanıyabilirsiniz.) Üçüncü deyim, `return` programa yöntemdeki diğer ifadeleri yürütmeden atlamasını söyleyen bir ifadedir.

     C#'da programlama yapıyorsanız, kodun bazılarının tek bir eşit`=`işaret (), diğer ifadeler`==`ise iki eşit işaret kullandığını fark etmiş olabilirsiniz. Neden `=` bazı yerlerde kullanılan `==` ancak diğer yerlerde kullanılan düşünün.

     Bu örnek, aradaki farkı gösteren güzel bir örnektir. İfadedeki parantezler arasındaki koda dikkatlice `if` bakın.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Daha sonra ifadeden sonra kod bloğundaki ilk `if` ifadeye yakından bakın.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     Bu deyimlerden birincisi iki simgenin aynı olup olmadığını denetler. İki değer karşılaştırıldığı için, C# `==` programı eşitlik işleci kullanır. İkinci deyim aslında değeri değiştirir *(atama* `firstClicked` olarak adlandırılır), `null` başvuru değişkenini sıfırlamak için eşit ayarlar. Bu yüzden atama işleci `=` yerine kullanır. C# `=` değerleri ayarlamak ve `==` karşılaştırmak için kullanır. Visual Basic `=` hem değişken atama hem de karşılaştırma için kullanır.

2. Programı kaydedip çalıştırın ve sonra formdaki simgeleri seçmeye başlayın. Eşleşmeyen bir çift seçerseniz, zamanlayıcının Tick olayı tetiklenir ve iki simge de kaybolur. Eşleşen bir çift seçerseniz, `if` yeni deyim yürütür ve iade deyimi yöntemin zamanlayıcıyı başlatan kodu atlatır, böylece simgeler aşağıdaki resimde gösterildiği gibi görünür kalır.

     ![Bu öğreticide oluşturduğunuz oyun](../ide/media/express_finishedgame.png)<br/>
***Görünür*** *simge çiftleri ile* eşleştirme oyunu

## <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Bir sonraki öğretici adıma gitmek için bkz: **[Adım 8: Oyuncunun kazanıp kazanmadığını doğrulamak için bir yöntem ekleyin.](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md)**

- Önceki öğretici adıma dönmek için [bkz.](../ide/step-6-add-a-timer.md)
