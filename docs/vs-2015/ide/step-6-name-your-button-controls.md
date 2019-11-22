---
title: '6\. Adım: düğme denetimlerinizi adlandırma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ebe3813ad01566e2994b0a16b4a3fdc735de8c8c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295715"
---
# <a name="step-6-name-your-button-controls"></a>6\. Adım: Düğme Denetimlerinizi Adlandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Formunuzda yalnızca bir PictureBox vardır. Bunu eklediğinizde, IDE otomatik olarak **PictureBox1**olarak adlandırılır. Yalnızca **CheckBox1**adlı bir onay kutusu vardır. Yakında bazı kodlar yazacaksınız ve bu kod CheckBox ve PictureBox öğesine başvuracaktır. Bu denetimlerden yalnızca biri olduğundan, kodunuzda **PictureBox1** veya **CheckBox1** gördüğünüz zaman ne anlama geldiğini bilirsiniz.

> [!NOTE]
> Visual Basic, herhangi bir denetim adının varsayılan ilk harfi ilk tepdir, bu nedenle adlar **PictureBox1**, **CheckBox1**vb. olur.

 Formunuzda dört düğme vardır ve bunları **button1**, **button2**, **BUTTON3**ve **Button4**olarak adlandırılan IDE. Yalnızca geçerli adlarına bakarak, hangi düğmenin **kapatma** düğmesi olduğunu ve hangilerinin **resim göster** düğmesi olduğunu bilemezsiniz. Bu nedenle, düğme denetimlerinizi daha bilgilendirici adlar yararlı olur.

 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 3](https://go.microsoft.com/fwlink/?LinkId=205213) veya [öğretici 1: video 3 ' te C# resim görüntüleyici oluşturma](https://go.microsoft.com/fwlink/?LinkId=205202). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-name-your-button-controls"></a>Düğme denetimlerinizi adlandırmak için

1. Formda, **Kapat** düğmesini seçin. (Tüm düğmeler seçiliyse, seçimi iptal etmek için ESC tuşunu seçin.) **(Ad)** özelliğini görene kadar **Özellikler** penceresinde kaydırma yapın. ( **(Ad)** özelliği, Özellikler alfabetik olduğunda üst kısımdaki bir yakındır.) Aşağıdaki resimde gösterildiği gibi, adı **CloseButton**olarak değiştirin.

     ![CloseButton adıyla Özellikler penceresi](../ide/media/express-setnameproperty.png "Express_SetNameProperty") CloseButton adıyla Özellikler penceresi

    > [!NOTE]
    > Düğmenize ilişkin adı kapat ve düğme arasındaki boşluk ile değiştirmeyi **denerseniz, IDE**bir hata iletisi görüntüler: "özellik değeri geçerli değil." Denetim adlarında boşluklara (ve diğer birkaç karaktere) izin verilmez.

2. Diğer üç düğmeyi **backgroundButton**, **clearButton**ve **showButton**olarak yeniden adlandırın. **Özellikler** penceresinde denetim Seçicisi açılan listesini seçerek adları doğrulayabilirsiniz. Yeni düğme adları görüntülenir.

3. Formdaki **resim göster** düğmesine çift tıklayın. Alternatif olarak, formda **bir resim göster** düğmesini seçin ve ardından Enter tuşunu seçin. Bunu yaptığınızda IDE, **Form1.cs** adlı ana pencerede ek bir sekme açar (Visual Basic kullanıyorsanız**Form1. vb** ). Bu sekme, aşağıdaki resimde gösterildiği gibi, formun arkasındaki kod dosyasını gösterir.

     ![Görsel kod içeren Visual C&#35; Code Form1.cs sekmesi ile Form1.cs sekmesi](../ide/media/express-showbuttoncode.png "Express_ShowButtonCode") C#

4. Kodun bu bölümüne odaklanın. (Kodun Visual Basic sürümünü görüntülemek için Visual Basic kullanıyorsanız aşağıdaki **vb** sekmesini seçin.)

     [!code-csharp[VbExpressTutorial1Step6#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial1Step6#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#1)]

     `showButton_Click()`adlı koda bakıyorsunuz. IDE bunu, **showButton** düğmesi için kod dosyasını açtığınızda formun koduna eklemiştir. Tasarım zamanında, bir formdaki denetim için kod dosyasını açtığınızda, zaten mevcut değilse denetim için kod oluşturulur. *Yöntem*olarak bilinen bu kod, programınızı çalıştırdığınızda çalışır ve bu durumda, **bir resim göster** düğmesi.

    > [!NOTE]
    > Bu öğreticide, otomatik olarak oluşturulan Visual Basic kodu, () ayraçları arasındaki her şeyi kaldırarak basitleştirilmiştir. Bu her gerçekleştiğinde, aynı kodu kaldırabilirsiniz. Programınız her iki şekilde de çalışır. Öğreticilerin geri kalanı için, mümkün olduğunda otomatik olarak oluşturulan tüm kodlar basitleştirilir.

5. Windows Form Tasarımcısı sekmesini bir kez daha seçin (**Form1.cs [Design]** with C#Visual, **Form1. vb [Design]** Visual Basic) ve ardından formun kodunda bir yöntem oluşturmak için **Resmi Temizle** düğmesini açmak üzere kod dosyasını açın. Bunu kalan iki düğme için tekrarlayın. Her seferinde IDE, formun kod dosyasına yeni bir yöntem ekler.

6. Bir başka yöntem eklemek için, IDE 'nin bir `checkBox1_CheckedChanged()` yöntemi eklemesini sağlamak üzere Windows Form Tasarımcısı onay kutusu denetimi için kod dosyasını açın. Bu yöntem, Kullanıcı onay kutusunu seçtiğinde veya temizlediğinde çağrılır.

    > [!NOTE]
    > Bir program üzerinde çalışırken genellikle kod Düzenleyicisi ve Windows Form Tasarımcısı arasında geçiş yapabilirsiniz. IDE, projenizde gezinmeyi kolaylaştırır. Windows Form Tasarımcısı açmak için **Çözüm Gezgini** kullanın Visual Basic, Visual C# veya **Form1. vb** içindeki **Form1.cs** çift tıklayarak ya da menü çubuğunda **Görünüm**, **Tasarımcı**' yı seçin.

     Aşağıdaki kod düzenleyicisinde gördüğünüz yeni kodu gösterir.

     [!code-csharp[VbExpressTutorial1Step6#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step6/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step6#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step6/vb/form1.vb#2)]

     Eklediğiniz beş yöntem *olay işleyicileri*olarak adlandırılır, çünkü bir olay (Kullanıcı bir düğme seçme veya bir kutu seçme gibi) olduğunda programınız bunları çağırır.

     Tasarım zamanında IDE 'deki bir denetimin kodunu görüntülediğinizde, Visual Studio bir tane değilse denetim için bir olay işleyici yöntemi ekler. Örneğin, bir düğmeye çift tıkladığınızda IDE, Click olayı (Kullanıcı düğmeyi seçtiğinde çağrılır) için bir olay işleyicisi ekler. Bir onay kutusuna çift tıkladığınızda, IDE, CheckedChanged olayı (Kullanıcı kutuyu seçtiğinde veya temizlediğinde çağrılır) için bir olay işleyicisi ekler.

     Bir denetim için bir olay işleyicisi ekledikten sonra, denetime çift tıklayarak ya da menü çubuğunda **Görünüm**, **kod**' ı seçerek Windows Form Tasarımcısı istediğiniz zaman bu nesneye dönebilirsiniz.

     Programlar oluştururken adlar önemlidir ve Yöntemler (olay işleyicileri dahil) istediğiniz herhangi bir ada sahip olabilir. IDE ile bir olay işleyicisi eklediğinizde, denetimin adına ve işlenmekte olan olaya göre bir ad oluşturur. Örneğin, **showButton** adlı bir düğmenin click olayına `showButton_Click()` olay işleyicisi yöntemi denir. Ayrıca, yöntemlerin açıklanmakta olduğunu göstermek için, açma ve kapatma parantezleri () genellikle yöntem adından sonra eklenir. Kod değişkeni adını değiştirmek istediğinize karar verirseniz, koddaki değişkene sağ tıklayıp yeniden **Düzenle**, **Yeniden Adlandır**' ı seçin. Koddaki bu değişkenin tüm örnekleri yeniden adlandırılır. Daha fazla bilgi için bkz. [yeniden düzenleme (C#)](../csharp-ide/rename-refactoring-csharp.md) veya [yeniden düzenleme ve yeniden adlandırma iletişim kutusu](https://msdn.microsoft.com/library/001d2d81-9bb6-4e8e-ae3a-20c0daaa3959) .

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına geçmek için, bkz. [7. Adım: formunuza Iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md).

- Önceki öğretici adımına dönmek için bkz. 5. [Adım: Formunuza denetim ekleme](../ide/step-5-add-controls-to-your-form.md).
