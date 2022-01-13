---
title: "Öğretici: bir oyuncu WINS 'i olduğunda bir ileti görüntüleme"
description: Bu öğreticide, eşleşen çiftleri görünür tutmak için kod ekleyerek ve bir oyuncu WINS olduğunda bir ileti görüntüleyerek eşleşen oyunu tamamlayacaksınız.
dev_langs:
- CSharp
- VB
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.date: 01/07/2022
ms.custom:
- vs-acquisition
ms.openlocfilehash: faf624f10a9618f152427d17c4fb616d29a3af31
ms.sourcegitcommit: 9b1c1cceab4c59f0b91e19ae46a51969f72fcc34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "136806075"
---
# <a name="tutorial-display-a-message-in-your-matching-game-winforms-app"></a>Öğretici: eşleşen oyun WinForms uygulamanızda bir ileti görüntüleme

Bu dört öğretici serisinde, Player 'ın gizli simge çiftlerini eşleştiği eşleşen bir oyun oluşturursunuz.

Bu öğreticide, eşleşen çiftleri görünür tutmak ve oyuncu kazanır bir tebrik iletisi göstermek için eşleşen oyununuzu gözden geçirin.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
> - Çiftleri görünür tutun.
> - Bir oyuncunun kazandığını doğrulayın.
> - Diğer özellikleri deneyin.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici önceki öğreticilerle, [eşleşen bir oyun uygulaması oluşturma](tutorial-windows-forms-create-match-game.md), [eşleşen oyununuza simgeler ekleme](tutorial-windows-forms-match-game-icons.md)ve [eşleşen oyununuza bir Zamanlayıcı ekleme](tutorial-windows-forms-match-game-labels.md) hakkında daha önce bu öğreticilerden birini oluşturur.

## <a name="keep-pairs-visible"></a>Çiftleri görünür durumda tutma

Bir oyuncu bir çifle eşleştiğinde, oyunun kendisini sıfırlaması gerekir, böylece, `firstClicked` ve başvuru değişkenlerini kullanan etiketleri artık takip eder `secondClicked` .
Bu, eşleşen iki etiket için renkleri sıfırlamamalıdır.
Bu Etiketler gösterilmeye devam eder.

1. Aşağıdaki `if` ifadeyi `label_Click()` olay işleyicisi yöntemine ekleyin.
   Zamanlayıcıyı başlattığınız deyimin hemen üstündeki kodun sonuna yakın bir yere yerleştirin.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step7/cs/form1.cs" id="Snippet9":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step7/vb/form1.vb" id="Snippet9":::

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   `if`İfade, Player 'ın seçtiği ilk etiketteki simgenin ikinci etiketteki simgeyle aynı olup olmadığını denetler.
   Simgeler aynıysa, program üç deyimini çalıştırır.
   İlk iki deyim `firstClicked` ve `secondClicked` başvuru değişkenlerini sıfırlar.
   Artık etiketlerin hiçbirini izlememek zorunda kalmazlar.
   Üçüncü deyim, `return` metodu çalıştırmadan deyimlerin geri kalanını atlayan bir ifadedir.

1. Programı çalıştırın ve ardından formda kareler seçmeye başlayın.

   ![Bu öğreticide oluşturduğunuz eşleşen oyunun ekran görüntüsü.](../ide/media/tutorial-windows-forms-create-match-game/match-game-final.png)

Eşleşmeyen bir çift seçerseniz, zamanlayıcının Tick olayı tetikler.
Her iki simge de kaybolur.

Eşleşen bir çift seçerseniz, yeni `if` ifade çalışır.
Return deyimleri, yönteminin zamanlayıcıyı başlatan kodu atlamasına neden olur.
Simgeler görünür kalır.

## <a name="verify-if-a-player-won"></a>Bir oyuncunun kazandığını doğrulama

Eğlenceli bir oyun oluşturdunuz.
Oynatıcı bir oyuncu olduktan sonra oyunun bitmesi gerekir.
Bu bölüm, oynatıcının kazanıldığını doğrulamak için bir yöntem ekler.

1. `CheckForWinner()`Kodunuzun altına, olay işleyicisinin altına bir yöntem ekleyin `timer1_Tick()` .

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet10":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet10":::

   yöntemi `foreach` `For Each` , içindeki her bir etikette gezinmek için C# veya Visual Basic içindeki döngüsünde başka bir döngü kullanır <xref:System.Windows.Forms.TableLayoutPanel> .
   Her etiketin simge rengini denetleyerek arka planla eşleşip eşleşmediğini doğrular.
   Renkler eşleşiyorsa simge görünmez halde kalır ve oyuncu kalan simgelerin tümünü eşleştirmemiştir.

   Bu durumda program, `return` yöntemin geri kalanını atlamak için bir ifade kullanır.
   Döngü, ifadeyi yürütmeden tüm etiketleri alırsa `return` , bu, formdaki tüm simgelerin eşleştirildiği anlamına gelir.
   Program, oyunu kazanmak için bir MessageBox gösterir ve ardından `Close()` oyunu sonlandırmak için yöntemini çağırır.

   Etiketin <xref:System.Windows.Forms.Control.Click> olay işleyicisinin yeni yöntemi aramasını sağlayabilirsiniz `CheckForWinner()` .

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step8/cs/form1.cs" id="Snippet11":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step8/vb/form1.vb" id="Snippet11":::

   Oyuncunun seçtiği ikinci simgeyi gösterdikten hemen sonra programınızın bir kazanan olup olmadığını denetlediğinden emin olun. İkinci seçili simgenin rengini ayarladığınız çizgiyi bulun ve ardından `CheckForWinner()` Bu satırın hemen ardından yöntemi çağırın.

1. Programı kaydedip çalıştırın. Oyunu oynayın ve tüm simgeleri eşleştirin. Kazandığınızda, program bir kutlama iletisi görüntüler.

   ![Ekran görüntüsü, bir MessageBox ile eşleşen oyunu gösterir.](../ide/media/tutorial-windows-forms-match-game-play/match-game-congratulations.png)

   **Tamam**' ı seçtikten sonra, eşleşen oyun kapanır.

## <a name="try-other-features"></a>Diğer özellikleri deneme

Eşleşen oyununuzun tamamı tamamlanmıştır.
Bu oyunu daha zor ve ilginç hale getirmek için daha fazla özellik ekleyebilirsiniz.
Bazı seçenekler aşağıda verilmiştir.

- Simgelerin ve renklerin yerine kendi tercih ettiklerinizi kullanın.

  Etiketin [ForeColor](<xref:System.Windows.Forms.Control.ForeColor%2A>) özelliğine bakmaya çalışın.

- Oyuncunun oyunu kazanmasının ne kadar sürdüğünü izleyen bir oyun zamanlayıcısı ekleyin.

  Formda geçen süreyi göstermek için bir etiket ekleyebilirsiniz.
  Bunu **TableLayoutPanel**'in üzerine koyun.
  Saati izlemek için forma başka bir zamanlayıcı ekleyin.
  Oyuncu oyuna başladığında zamanlayıcıyı başlatmak ve son iki simgeyi eşleştirdikten sonra zamanlayıcıyı durdurmak için kod kullanın.

- Oyuncu bir eşleşme bulduğunda çalacak bir ses, eşleşmeyen iki simgeyi açtığında çalacak başka bir ses ve program simgeleri yeniden gizlediğinde çalacak üçüncü bir ses ekleyin.

  Ses çalmak için <xref:System.Media> ad alanını kullanabilirsiniz. daha fazla bilgi için bkz. Windows Forms uygulamasında ses [yürütme (C#)](https://www.youtube.com/watch?v=qOh4ooHg1UU&feature=youtu.be) veya [Visual Basic ses yürütme](https://www.youtube.com/watch?v=-4oPDeQrtMs&feature=youtu.be).

- Oyun tahtasını büyüterek oyunu zorlaştırın.

  TableLayoutPanel 'e satırlar ve sütunlar eklemeniz yeterlidir.
  Ayrıca, oluşturduğunuz simgelerin sayısını göz önünde bulundurmanız gerekir.

- Oyuncunun yanıt vermesi çok yavaşsa, oyunu daha zorlayıcı hale getirin.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler!
Bu öğretici serisini tamamladınız.
Visual Studio ıde 'de bu programlama ve tasarım görevlerini tamamladınız:

- Listede simgeler gibi saklı nesneler
- bir liste içinde yinelemek için C# veya Visual Basic bir döngü kullanıldı
- Başvuru değişkenlerini kullanarak durumu takip tutma
- Birden çok nesne için olaylara yanıt vermek üzere bir olay işleyicisi oluşturuldu
- Bir olayı aşağı sayan ve harekete tetikleyen bir Zamanlayıcı eklendi

Windows Form Tasarımcısı derinlemesine bir bakış için bu makaleye ilerleyin.
> [!div class="nextstepaction"]
> [öğretici: Windows Form Tasarımcısı kullanmaya başlayın](../designers/walkthrough-windows-forms-designer.md)
