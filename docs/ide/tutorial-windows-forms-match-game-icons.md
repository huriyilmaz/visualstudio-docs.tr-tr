---
title: 'Öğretici: eşleşen oyuna simgeler ekleme'
description: bu öğreticide, eşleşen Windows oyununuzda her etikete rastgele bir simge atayacaksınız ve Visual Studio C# veya VB kullanarak simgeleri görüntülemesi için bir olay işleyicisi uygulamalısınız.
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
ms.openlocfilehash: 0796cdc0dd7c9bbb5ee98eca00371e21d8cb70b2
ms.sourcegitcommit: 9b1c1cceab4c59f0b91e19ae46a51969f72fcc34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "136806083"
---
# <a name="tutorial-add-icons-to-your-matching-game-winforms-app"></a>Öğretici: eşleşen oyun WinForms uygulamanıza simgeler ekleme

Bu dört öğretici serisinde, Player 'ın gizli simge çiftlerini eşleştiği eşleşen bir oyun oluşturursunuz.

Eşleşen oyunda bir oyuncu, bir simgeyi görmek için bir kare seçer ve ardından başka bir kare seçer.
Simgeler eşleşirse görünür olarak kalırlar.
Aksi takdirde, oyun her iki simgeyi de gizler.
Bu öğreticide, etiketlere rastgele simgeler atarsınız.
Bunları gizli olacak şekilde ayarlarsınız ve sonra seçildiğinde görüntülenir.

Bu ikinci öğreticide şunları yapmayı öğreneceksiniz:

> [!div class="checklist"]
> - Rastgele bir nesne ve simge listesi ekleyin.
> - Her etikete rastgele bir simge atayın.
> - Etiketlere simgeler gösteren olay işleyicileri ekleyin.

## <a name="prerequisites"></a>Önkoşullar

Bu öğretici, önceki öğreticide derleme yaparken, [eşleşen bir oyun uygulaması oluşturur](tutorial-windows-forms-create-match-game.md).
Bu öğreticiyi yapmadıysanız, önce bunlardan birine gidin.

## <a name="add-a-random-object-and-a-list-of-icons"></a>Rastgele bir nesne ve simge listesi ekleme

Bu bölümde, oyun için bir dizi eşleşen simge oluşturursunuz.
Her simge, form üzerindeki TableLayoutPanel denetiminde rasgele iki hücreye eklenir.

`new`İki nesne oluşturmak için deyimlerini kullanırsınız.
Birincisi, <xref:System.Random> TableLayoutPanel içindeki hücreleri rastgele seçen bir nesnedir.
İkinci nesne bir <xref:System.Collections.Generic.List%601> nesnedir.
Rastgele seçilen sembolleri depolar.

1. Visual Studio'yu açın. Eşleşen oyun projeniz **yakın zamanda aç** altında görüntülenir.

1. C# kullanıyorsanız *Form1. cs* veya Visual Basic kullanıyorsanız *Form1. vb* öğesini seçin. Sonra kodu **görüntüle**' yi seçin  >  . 
   Alternatif olarak, **F7** tuşunu veya **Form1**' i çift tıklayın.
   Visual Studio ıde, Form1 için kod modülünü görüntüler.

1. Varolan kod içine aşağıdaki kodu ekleyin.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet1":::

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   C# kullanıyorsanız, kodu açılış küme ayracından sonra ve Sınıf bildiriminden hemen sonra () yerleştirdiğinizden emin olun `public partial class Form1 : Form` . Visual Basic kullanıyorsanız, kodu sınıf bildiriminden () hemen sonra koyun `Public Class Form1` .

Farklı öğe türlerini izlemek için liste nesnelerini kullanabilirsiniz.
Bir liste; sayıları, doğru/yanlış değerlerini, metinleri veya diğer nesneleri barındırabilir.
Eşleşen oyununuzda liste nesnesi, TableLayoutPanel panelindeki her hücre için bir tane olmak üzere 16 dizelere sahiptir.
Her dize, etiketlerde simgelere karşılık gelen tek bir harftir.
Bu karakterler, veri yolu, Bisiklet ve diğerleri olarak Web 'e ilişkin yazı tipinde görüntülenir.

> [!NOTE]
> Listelerin gerektiğinde daralabilmesi ve genişleyebilmesi bu programda önem taşır.

Listeler hakkında daha fazla bilgi için bkz <xref:System.Collections.Generic.List%601> .. C# dilinde bir örnek görmek için bkz. [temel liste örneği](/dotnet/csharp/tour-of-csharp/tutorials/arrays-and-collections#a-basic-list-example). Visual Basic bir örneği görmek için bkz. [basit koleksiyon kullanma](/dotnet/visual-basic/programming-guide/concepts/collections#using-a-simple-collection).

## <a name="assign-a-random-icon-to-each-label"></a>Her etikete rastgele bir simge atama

Programı her çalıştırdığınızda, bir yöntemi kullanarak, simgeleri formunuzdaki etiket denetimlerine rastgele atar `AssignIconsToSquares()` .
Bu kod, `foreach` C# veya Visual Basic içinde anahtar sözcüğünü kullanır `For Each` .

1. Yöntemini ekleyin `AssignIconsToSquares()` .

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet2":::

   Bu kodu, önceki bölümde eklediğiniz kodun hemen altına girebilirsiniz.

   > [!NOTE]
   > Satırlardan biri amaca göre yorumlanma.
   > Bu yordamı daha sonra bu yordamda eklersiniz.

   `AssignIconsToSquares()`Yöntemi TableLayoutPanel içindeki her etiket denetimi boyunca yinelenir.
   Her biri için aynı deyimleri çalıştırır.
   Deyimler listeden rastgele bir simge çeker.

   - İlk satır, **Denetim** değişkenini **iconLabel** adlı bir etikete dönüştürür. 
   - İkinci satır, `if` dönüştürmenin çalıştığından emin olmak için denetleyen bir ifadedir.
     Dönüştürme işe alıyorsa, `if` deyimindeki deyimler çalışır.
   - Deyimdeki ilk satır, `if` simgeler listesindeki öğelerden birine karşılık gelen rastgele bir sayı Içeren **rasgelenumber** adlı bir değişken oluşturur.
     <xref:System.Random.Next>Nesnenin yöntemini kullanır <xref:System.Random> .
     `Next`Yöntemi rastgele sayı döndürür.
     Bu satır, <xref:System.Collections.Generic.List%601.Count> rastgele sayının seçim aralığını belirlemek için **simgeler** listesinin özelliğini de kullanır.
   - Sonraki satır, simge listesi öğelerinden birini <xref:System.Windows.Forms.Label.Text> etiketin özelliğine atar.
   - Sonraki satır, simgeleri gizler.
     Devam etmeden önce kodun geri kalanını doğrulayabilmeniz için satırı burada yorumlarsınız.
   - Deyimdeki son satır, `if` forma eklenmiş olan simgeyi listeden kaldırır.

1. `AssignIconsToSquares()` **Form1** _oluşturucusuna_ yöntemine bir çağrı ekleyin.
   Bu yöntem oyun panosunu simgelerle doldurur.
   Oluşturucular bir nesne oluşturduğunuzda çağırılır.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet13":::

   Visual Basic için yöntem `AssignIconsToSquares()` çağrısını `Form1_Load` yöntemine ekleyin.

   ```vb
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
       AssignIconsToSquares()
   End Sub
   ```

   Daha fazla bilgi için bkz. [oluşturucular (C# Programlama Kılavuzu)](/dotnet/csharp/programming-guide/classes-and-structs/constructors) veya [oluşturucular ve Yıkıcılar kullanma](/previous-versions/visualstudio/visual-studio-2008/2z08e49e\(v\=vs.90\)).

1. Programınızı kaydedip çalıştırın. Her etikete rasgele simgelerin atandığı bir form gösterilmesi gerekir.

   > [!TIP]
   > Web 'in simgeleri formda düzgün şekilde görünmezse, formdaki etiketlerin **UseCompatibleTextRendering** özelliğini **true** olarak ayarlayın.

1. Programınızı kapatın ve yeniden çalıştırın. Her etikete farklı simgeler atanır.

   ![Ekran görüntüsü, rastgele simgeleri gösteren eşleşen oyunu gösterir.](../ide/media/tutorial-windows-forms-match-game-icons/display-random-icons.png)

   Henüz gizlemediğiniz için simgeler şimdilik görünmektedir. Bunları Player 'dan gizlemek için, her etiketin **ForeColor** özelliğini **BackColor** özelliği ile aynı renge ayarlayabilirsiniz.

1. Programı durdurun. Döngü içindeki açıklamalı kod satırı için açıklama işaretlerini kaldırın.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet15":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet15":::

Programı yeniden çalıştırırsanız, simgeler kayboldu gibi görünüyor.
Yalnızca mavi bir arka plan görüntülenir.
Simgeler rastgele atanır ve hâlâ orada kalır.

## <a name="add-event-handlers-to-labels"></a>Etiketlere olay işleyicileri ekleme

Bu eşleşen oyunda, bir oyuncu gizli bir simge, sonra ikinci bir simge ortaya koyar.
Simgeler eşleşirse görünür olarak kalırlar.
Aksi halde, her iki simge de tekrar gizlenir.

Oyununuzun bu şekilde çalışmasını sağlamak için, <xref:System.Windows.Forms.Control.Click> Seçilen etiketin rengini arka planla eşleşecek şekilde değiştiren bir olay işleyicisi ekleyin.

1. **Windows Form Tasarımcısı** formunu açın. **Form1. cs** veya **Form1. vb** öğesini seçin ve ardından tasarımcıyı **görüntüle**' yi seçin  >  .

1. İlk etiket denetimini belirleyip seçin. Ardından, diğer etiketlerin her birini seçerken **CTRL** tuşunu basılı tutun.
   Her etiketin seçildiğinden emin olun.

1. **Özellikler** penceresinde, bir açıklaştırma sürgüsü olan **Olaylar** düğmesini seçin.
   **Tıklama** olayı için, kutudan **label_Click** öğesini seçin.

     ![Ekran görüntüsü Click olayını gösteren Özellikler penceresi gösterir.](../ide/media/tutorial-windows-forms-match-game-icons/click-event.png)

1. **Enter** tuşuna basın. IDE, `Click` koda **label_Click ()** adlı bir olay işleyicisi ekler.
   Tüm etiketleri seçtiğinizden, işleyici etiketlerin her birine bağlanır.

1. Kodun geri kalanını girin.

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs" id="Snippet4":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb" id="Snippet4":::

   > [!NOTE]
   > Kodu `label_Click()` el ile girmek yerine kod bloğunu kopyalayıp yapıştırırsanız, var olan kodun değiştirilmesini unutmayın `label_Click()` .
   > Aksi takdirde, yinelenen bir kod bloğu ile karşı karşıya kalırsınız.

1.   >  Programınızı çalıştırmak için hata **ayıklamayı Başlat** ' ı seçin. Mavi arka planlı boş bir form görmeniz gerekir. Formdaki hücrelerden herhangi birini seçin. Simgelerden biri görünür hale gelmelidir. Formda farklı yerler seçmeye devam edin. Siz simgeleri seçtikçe görünmeleri gerekir.

   ![Ekran görüntüsü, eşleşen oyunu, tek bir simge görünür olarak gösterir.](../ide/media/tutorial-windows-forms-match-game-icons/match-game-start.png)

## <a name="next-steps"></a>Sonraki adımlar

Bir Zamanlayıcı kullanarak etiketleri değiştirme hakkında bilgi edinmek için sonraki öğreticiye ilerleyin.
> [!div class="nextstepaction"]
> [ Eşleşen oyununuzda bir zamanlayıcı kullanın](tutorial-windows-forms-match-game-labels.md)
