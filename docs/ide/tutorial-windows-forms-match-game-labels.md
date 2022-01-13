---
title: 'Öğretici: Eşleştirme oyununa zamanlayıcı ekleme'
description: Bu öğreticide, C# veya VB Visual Studio Forms kullanarak Windows kullanırsanız. Eşleştirme Oyun'larınızı çalıştırmak için bir zamanlayıcı eklersiniz.
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
ms.openlocfilehash: 6ce2cb57087d70be2858ce625289edfdc2d87a7c
ms.sourcegitcommit: 9b1c1cceab4c59f0b91e19ae46a51969f72fcc34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "136806082"
---
# <a name="tutorial-add-reference-variables-and-a-timer-control-to-your-matching-game-winforms-app"></a>Öğretici: Eşleşen winForms uygulamanıza başvuru değişkenleri ve zamanlayıcı denetimi ekleme

Bu dört öğretici serisinde, oyuncunun gizli simge çiftlerini eşleştiren bir eşleştirme oyunu derlemek.

Eşleştirme Oyunu programınız, oyuncunun hangi Etiket denetimlerini seçeceklerini izlemesi gerekir.
Oyuncu ilk etiketi seçtikten sonra program simgeyi göstermektedir.
İkinci etiket seçildikten sonra program kısa bir süre için her iki simgeyi de görüntülemeli.
Ardından iki simgeyi de gizler.

Programınız, başvuru değişkenlerini kullanarak hangi Etiketi ilk ve ikinci *seçtiğinizi takip eder.*
Süreölçer simgeleri gizler ve simgelerin ne kadar süreyle göster masaüstünde göster

> [!div class="checklist"]
> - Etiket başvuruları ekleyin.
> - Zamanlayıcı ekleyin.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici önceki öğreticileri, Eşleşen bir [oyun uygulaması oluşturma ve](tutorial-windows-forms-create-match-game.md) Eşleştirme [oyunnize simgeler ekleme öğreticilerini içerir.](tutorial-windows-forms-match-game-icons.md)
Önce bu öğreticileri izleyin.

## <a name="add-label-references"></a>Etiket başvuruları ekleme

Bu bölümde kodunuz için iki *başvuru değişkeni* eksersiniz.
Nesneleri takip eder veya Etiket nesnelerine başvurur.

1. Aşağıdaki kodu kullanarak formunuza etiket başvuruları ekleyin.

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet5":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet5":::

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Bu deyimler, anahtar sözcük yoktur çünkü etiket denetimlerinin formda görünmesine neden `new` olmaz.
   Program başlatıldığında, hem hem `firstClicked` de `secondClicked` `null` C# için veya `Nothing` Visual Basic.

1. Yeni başvuru <xref:System.Windows.Forms.Control.Click> değişkenini kullanmak için olay işleyicinizi `firstClicked` değiştirme.
   Olay işleyicisi `label_Click()` yönteminde () son deyimini `clickedLabel.ForeColor = Color.Black;` kaldırın ve bunu aşağıdaki `if` deyimle değiştirin.

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step5/vb/form1.vb" id="Snippet6":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step5/cs/form1.cs" id="Snippet6":::

1. Programınızı kaydedin ve çalıştırın. Etiket denetimlerinden birini seçtiğinizde ilgili denetimin simgesi görünür.
   Bir sonraki etiket denetimini seçin ve hiçbir olay gerçekleşmediğine dikkat edin.

   ![Bir simgeyi gösteren Eşleştirme Oyununu gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-match-game-icons/match-game-start.png)

   Yalnızca seçilen ilk simge siyaha döner.
   Diğer simgeler görünmez.

Program zaten oyuncunun seçtiği ilk etiketi takip ediyor.
Başvuru `firstClicked` C# veya `null` `Nothing` Visual Basic.
deyiminiz `if` veya `firstClicked` ile eşit olmadığını `null` bulduğunda `Nothing` deyimlerini çalıştırmaz.

## <a name="add-a-timer"></a>Süreölçer ekleme

Eşleştirme Oyunu, uygulama <xref:System.Windows.Forms.Timer> üzerinde bir denetim kullanır.
Süreölçer bekler ve ardından tick olarak adlandırılan bir olayı *etkinler.*
Zamanlayıcı bir eylemi düzenli olarak başlatarak veya tekrarlar.

Programda süreölçer, bir oyuncunun iki simge seçmesi için olanak sağlar.
Simgeler eşleşmezse, kısa bir süre sonra iki simgeyi yeniden gizler.

1. Araç Kutusu **sekmesini** seçin, Bileşenler **kategorisinde** Zamanlayıcı bileşenine çift tıklayın **veya formuna** sürükleyin.
   timer1 adlı **zamanlayıcı simgesi,** formun altındaki bir alanda görünür.

   ![Formun altındaki zamanlayıcı simgesini gösteren ekran görüntüsü.](../ide/media/tutorial-windows-forms-match-game-labels/timer-control-icon.png)

1. Zamanlayıcıyı **seçmek için Timer1** simgesini seçin.
   Özellikleri **görüntülemek** için Özellikler **penceresinde Özellikler** düğmesini seçin.

1. **Interval** özelliğini **750 olarak ayarlayın** ve bu da 750 milisaniyedir.

   **Interval özelliği** zamanlayıcıya, olayı tetikleyene kadar tıklar arasında ne kadar bekleyeceğini  <xref:System.Windows.Forms.Timer.Tick> söyler.
   Program, oyuncu <xref:System.Windows.Forms.Timer.Start> ikinci etiketi seçtikten sonra zamanlayıcıyı başlatmak için yöntemini çağırıyor.

1. Zamanlayıcı denetim simgesini seçin ve Enter tuşuna **basın** veya zamanlayıcıya çift tıklayın.
   IDE boş bir Tick olayı işleyicisi ekler.
   Kodu aşağıdaki kodla değiştirin.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet7":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet7":::

   Tick olayı işleyicisi üç şey yapar:

   - yöntemini çağırarak zamanlayıcının çalışmay olduğundan emin <xref:System.Windows.Forms.Timer.Stop> olur.
   - Oynatıcının seçtiği iki `firstClicked` etiketin simgelerini yeniden görünmez yapmak için ve olmak için iki başvuru değişkeni `secondClicked` kullanır.
   - Ve başvuru değişkenlerini C# içinde ve içinde `firstClicked` `secondClicked` olarak `null` `Nothing` Visual Basic.

1. Kod düzenleyicisine gidin ve olay işleyicisi yönteminin üst ve alt `label_Click()` kısmında aşağıdaki kodu ekleyin.
   İki deyimi `if` en üstüne, üç deyimini de en alta ekleyin.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step6/cs/form1.cs" id="Snippet8":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step6/vb/form1.vb" id="Snippet8":::

   - Yöntemin en üstünde yer alan kod, Enabled özelliğinin değerini kontrol ederek zamanlayıcının başlat olup **olmadığını** denetler.
     Oyuncu birinci ve ikinci Etiket denetimlerini seçerse ve süreölçer başlatılırsa, üçüncü bir etiket seçmek hiçbir şey yapmaz.

   - Yöntemin alt kısmında yer alan kod, başvuru `secondClicked` değişkenlerini ikinci Etiket denetimine göre ayarlar.
     Ardından etiket simgesinin rengini siyah olarak ayararak görünür hale gelir.
     Ardından zamanlayıcıyı tek atış modunda başlatır, böylece 750 milisaniye bekler ve ardından tek bir tık başlatır.
     Zamanlayıcının Tick olay işleyicisi iki simgeyi gizler ve ve başvuru `firstClicked` `secondClicked` değişkenlerini sıfırlar.
     Form, oyuncunun başka bir simge çifti seçmesi için hazırdır.

1. Programınızı kaydedin ve çalıştırın.
   Bir kare seçin ve simge görünür duruma gelir.
   Başka bir kare seçin.
   Simge kısa bir süre görünür ve her iki simge de kaybolur.

Programınız artık seçtiğiniz birinci ve ikinci simgeleri takip ediyor.
Simgelerin kaybolmasına neden olmadan önce duraklatmak için zamanlayıcıyı kullanır.

## <a name="next-steps"></a>Sonraki adımlar

Eşleştirme Oyunlarınızı nasıl bitireceklerini öğrenmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [Eşleşen Oyun için tebrikler iletisi göster](tutorial-windows-forms-match-game-play.md)
