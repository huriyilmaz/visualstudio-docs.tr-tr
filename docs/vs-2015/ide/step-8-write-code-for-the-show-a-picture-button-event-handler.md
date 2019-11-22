---
title: '8\. Adım: resim göster düğmesi olay Işleyicisi için kod yazma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2c1b09d88de938ee4bc93b69b50d53c0d39006f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300007"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>8\. Adım: Resim Göster Düğmesi Olay İşleyicisi için Kod Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda, **bir resim göster** düğmesinin şu şekilde çalıştığını yaparsınız:

- Bir Kullanıcı bu düğmeyi seçtiğinde, program **açık bir dosya** iletişim kutusu açar.

- Bir Kullanıcı bir resim dosyası açarsa, program PictureBox 'da bu resmi gösterir.

  IDE 'de kod yazmanıza yardımcı olan, IntelliSense adlı güçlü bir araç vardır. Kod girerken, IDE, girdiğiniz kısmi sözcüklerin önerilen tamamlarla bir kutu açar. Bundan sonra ne yapmak istediğinizi belirlemeyi dener ve listeden seçtiğiniz son öğeyi otomatik olarak atlar. Listede gezinmek için yukarı veya aşağı okları kullanabilir veya seçimleri daraltmak için harfleri yazmaya devam edebilirsiniz. İstediğiniz seçeneği gördüğünüzde, seçmek için sekme tuşunu seçin. Veya gerekmiyorsa, önerileri yoksayabilirsiniz.

  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 4](https://go.microsoft.com/fwlink/?LinkId=205215) veya [öğretici 1: video 3 ' te C# resim görüntüleyici oluşturma](https://go.microsoft.com/fwlink/?LinkId=205203). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Resim göster düğmesi olay işleyicisi için kod yazmak için

1. Windows Form Tasarımcısı gidin ve **resim göster** düğmesine çift tıklayın. IDE hemen kod tasarımcısına gider ve imlecinizi, daha önce eklediğiniz `showButton_Click()` yönteminin içinde olacak şekilde taşıdır.

2. İki küme ayracı {} arasına boş satıra bir `i` yazın. (Visual Basic, özel sub arasında boş satıra yazın... ve End Sub.) Aşağıdaki resimde gösterildiği gibi bir **IntelliSense** penceresi açılır.

     ![Görsel kod ile Visual&#35; C Code IntelliSense ile IntelliSense](../ide/media/express-ifintellisense.png "Express_IfIntellisense") C#

3. **IntelliSense** penceresi, **if**sözcüğünü vurgulamalıdır. (Yoksa, küçük bir `f`girin ve bu işlem olur.) **IntelliSense** penceresinin yanındaki küçük bir *araç ipucu* kutusunun Açıklama, **if ifadesi için kod parçacığı**gibi göründüğünü fark edebilirsiniz. (Visual Basic araç ipucu, bunun bir parçacık olduğunu ancak biraz farklı bir ifade olduğunu da belirtir.) Bu kod parçacığını kullanmak istiyorsanız, **kodunuza eklemek IÇIN** sekme tuşunu seçin. Ardından, **IF** kod parçacığını kullanmak için Tab tuşunu yeniden seçin. (Başka bir yerde seçerseniz ve **IntelliSense** penceresiz kaybolduysa, **ı** ve yeniden yazın ve **IntelliSense** penceresi yeniden açılır.)

     ![Visual C&#35; Code](../ide/media/express-highlighttrue.png "Express_HighlightTrue") görsel C# kodu

4. Daha sonra, bir **Dosya Aç** iletişim kutusunu açmak için daha fazla kod girmek üzere IntelliSense 'i kullanırsınız. Kullanıcı **Tamam** düğmesini seçerse, PictureBox kullanıcının seçtiği dosyayı yükler. Aşağıdaki adımlarda kodun nasıl girilmesi gösterilmektedir ve çok sayıda adım olsa da yalnızca birkaç tuş vuruşu vardır:

    1. Kod parçacığında **doğru** seçili metinle başlayın. Üzerine yazmak için `op` yazın. (Visual Basic, ilk Cap ile başlayıp `Op`yazın.)

    2. **IntelliSense** penceresi açılır ve **OpenFileDialog1**görüntüler. Seçmek için sekme tuşunu seçin. (Visual Basic bir başlangıç üst sınırı ile başlar, bu nedenle **OpenFileDialog1**görürsünüz. **OpenFileDialog1** seçildiğinden emin olun.)

         `OpenFileDialog`hakkında daha fazla bilgi için bkz. [OpenFileDialog](https://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).

    3. Bir nokta (`.`) yazın (birçok programcı bu noktayı çağırır.) **OpenFileDialog1**sonrasında bir nokta yazdığınızdan, bir **IntelliSense** penceresi açılır ve tüm **OpenFileDialog** bileşeni özellikleri ve yöntemleri ile doldurulur. Bunlar, Windows Form Tasarımcısı ' de seçerken **Özellikler** penceresinde görüntülenen özelliklerden aynıdır. Ayrıca, bileşene bir şeyler (bir iletişim kutusu aç gibi) yapacağını söyleyen yöntemler de seçebilirsiniz.

        > [!NOTE]
        > **IntelliSense** penceresi her iki özelliği ve yöntemi gösterebilir. Neyin gösterilmekte olduğunu belirlemek için, **IntelliSense** penceresindeki her öğenin sol tarafındaki simgeye bakın. Her yöntemin yanında bir bloğun bir resmini ve her bir özelliğin yanındaki bir wrana (ya da Spanner) resmini görürsünüz. Her olayın yanında bir şimşek simgesi de vardır. Bu resimler aşağıda gösterildiği gibi görüntülenir.

         ![Yöntem simgesi](../ide/media/express-iconmethod.png "Express_IconMethod") Yöntem simgesi

         ![Özellik simgesi](../ide/media/express-iconproperty.png "Express_IconProperty") Özellik simgesi

         ![Olay simgesi](../ide/media/express-iconevent.png "Express_IconEvent") Olay simgesi

    4. `ShowDialog` yazın (büyük/küçük harfe dönüştürme, IntelliSense için önemli değildir). `ShowDialog()` yöntemi **Dosya Aç** iletişim kutusunu gösterecektir. Pencerede **ShowDialog**VURGULANDıKTAN sonra SEKME tuşunu seçin. Ayrıca, "ShowDialog" ifadesini vurgulayabilir ve yardım almak için F1 tuşunu seçebilirsiniz.

         `ShowDialog()` yöntemi hakkında daha fazla bilgi edinmek için bkz. [ShowDialog yöntemi](https://msdn.microsoft.com/library/c7ykbedk.aspx).

    5. Bir denetim veya bileşen üzerinde bir yöntem kullandığınızda ( *bir yöntemi çağırmak*olarak adlandırılır), parantez eklemeniz gerekir. Bu nedenle, `ShowDialog`içinde "g" den hemen sonra açma ve kapatma parantezleri girin: `()` şimdi "openFileDialog1. ShowDialog ()" şeklinde görünmelidir.

        > [!NOTE]
        > Yöntemler, herhangi bir programın önemli bir parçasıdır ve bu öğretici, yöntemlerin kullanılması için çeşitli yollar göstermiştir. Bir bileşenin yöntemini çağırmak için, **OpenFileDialog** bileşenin `ShowDialog()` yöntemini nasıl adlandırmış olursunuz. Bir Kullanıcı bir düğme seçtiğinde bir iletişim kutusu ve resim açan `showButton_Click()` yöntemi olarak, programınızın sizin oluşturduğunuz gibi işlemler yapmasını sağlamak için kendi yöntemlerinizi oluşturabilirsiniz.

    6. Görsel C#için bir boşluk ekleyin ve ardından iki eşittir işareti (`==`) ekleyin. Visual Basic için bir boşluk ekleyin ve sonra tek bir eşittir işareti (`=`) kullanın. (Görsel C# ve Visual Basic farklı eşitlik işleçleri kullanır.)

    7. Başka bir boşluk ekleyin. Bunu yaptığınızda, başka bir **IntelliSense** penceresi açılır. `DialogResult` yazın ve eklemek için sekme tuşunu seçin.

        > [!NOTE]
        > Bir yöntemi çağırmak için kod yazdığınızda bazen bir değer döndürür. Bu durumda, **OpenFileDialog** bileşeninin `ShowDialog()` yöntemi bir DialogResult değeri döndürür. DialogResult, iletişim kutusunda ne olduğunu belirten özel bir değerdir. Bir **OpenFileDialog** bileşeni, kullanıcının **Tamam** veya **iptal**' i seçmelerini sağlayabilir, bu nedenle `ShowDialog()` yöntemi DialogResult. ok veya DialogResult. Cancel öğesini döndürür.

    8. DialogResult değeri **IntelliSense** penceresini açmak için bir nokta yazın. `O` harfini girin ve **Tamam 'ı**eklemek için sekme tuşunu seçin.

         `DialogResult`hakkında daha fazla bilgi edinmek için bkz. [DialogResult](https://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).

        > [!NOTE]
        > Kodun ilk satırı tamamlanmalıdır. Görsel C#için aşağıdaki olmalıdır.
        >
        >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
        >
        >  Visual Basic için aşağıdaki olmalıdır.
        >
        >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

    9. Şimdi bir kod satırı ekleyin. Yazabilir (veya kopyalayabilir ve yapıştırabilirsiniz), ancak eklemek için IntelliSense kullanmayı düşünün. IntelliSense ile ne kadar tanıdık olduğunu öğrenin, kendi kodunuzu daha hızlı yazabilirsiniz. Son `showButton_Click()` yönteminiz aşağıdaki gibi görünür. (Kodun Visual Basic sürümünü görüntülemek için **vb** sekmesini seçin.)

         [!code-csharp[VbExpressTutorial1Step8#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step8/cs/form1.cs#1)]
         [!code-vb[VbExpressTutorial1Step8#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step8/vb/form1.vb#1)]

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. [adım 9: İnceleme, yorum ve test kodunuzu test](../ide/step-9-review-comment-and-test-your-code.md)etme.

- Önceki öğretici adımına dönmek için, bkz. [7. Adım: formunuza Iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md).
