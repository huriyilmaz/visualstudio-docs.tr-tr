---
title: '8. Adım: resim göster düğmesi olay Işleyicisi için kod yazma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f5d58533f6f2207d1b07883ab741eb900cdfbbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851109"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>8. Adım: Resim Göster Düğmesi Olay İşleyicisi için Kod Yazma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu adımda, **bir resim göster** düğmesinin şu şekilde çalıştığını yaparsınız:

- Bir Kullanıcı bu düğmeyi seçtiğinde, program **açık bir dosya** iletişim kutusu açar.

- Bir Kullanıcı bir resim dosyası açarsa, program PictureBox 'da bu resmi gösterir.

  IDE 'de kod yazmanıza yardımcı olan, IntelliSense adlı güçlü bir araç vardır. Kod girerken, IDE, girdiğiniz kısmi sözcüklerin önerilen tamamlarla bir kutu açar. Bundan sonra ne yapmak istediğinizi belirlemeyi dener ve listeden seçtiğiniz son öğeyi otomatik olarak atlar. Listede gezinmek için yukarı veya aşağı okları kullanabilir veya seçimleri daraltmak için harfleri yazmaya devam edebilirsiniz. İstediğiniz seçeneği gördüğünüzde, seçmek için sekme tuşunu seçin. Veya gerekmiyorsa, önerileri yoksayabilirsiniz.

  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 4](https://msdn.microsoft.com/vbasic/gg315355.aspx) veya [öğretici 1: C# içinde resim görüntüleyici oluşturma-video 4](https://msdn.microsoft.com/vcsharp/gg278412.aspx). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Resim göster düğmesi olay işleyicisi için kod yazmak için

1. Windows Form Tasarımcısı gidin ve **resim göster** düğmesine çift tıklayın. IDE hemen kod tasarımcısına gider ve imlecinizi, `showButton_Click()` daha önce eklediğiniz yöntemin içinde olacak şekilde taşıdır.

2. `i`İki küme ayracı {} arasına boş satıra bir yazın. (Visual Basic, özel sub arasında boş satıra yazın... ve End Sub.) Aşağıdaki resimde gösterildiği gibi bir **IntelliSense** penceresi açılır.

     ![Visual C&#35; Code Ile IntelliSense](../ide/media/express-ifintellisense.png "Express_IfIntellisense") Visual C# kodu ile IntelliSense

3. **IntelliSense** penceresi, **if**sözcüğünü vurgulamalıdır. (Değilse, küçük harf girin `f` ve bu işlem olur.) **IntelliSense** penceresinin yanındaki küçük bir *araç ipucu* kutusunun Açıklama, **if ifadesi için kod parçacığı**gibi göründüğünü fark edebilirsiniz. (Visual Basic araç ipucu, bunun bir parçacık olduğunu ancak biraz farklı bir ifade olduğunu da belirtir.) Bu kod parçacığını kullanmak istiyorsanız, **kodunuza eklemek IÇIN** sekme tuşunu seçin. Ardından, **IF** kod parçacığını kullanmak için Tab tuşunu yeniden seçin. (Başka bir yerde seçerseniz ve **IntelliSense** penceresiz kaybolduysa, **ı** ve yeniden yazın ve **IntelliSense** penceresi yeniden açılır.)

     ![Visual C&#35; kodu](../ide/media/express-highlighttrue.png "Express_HighlightTrue") Visual C# kodu

4. Daha sonra, bir **Dosya Aç** iletişim kutusunu açmak için daha fazla kod girmek üzere IntelliSense 'i kullanırsınız. Kullanıcı **Tamam** düğmesini seçerse, PictureBox kullanıcının seçtiği dosyayı yükler. Aşağıdaki adımlarda kodun nasıl girilmesi gösterilmektedir ve çok sayıda adım olsa da yalnızca birkaç tuş vuruşu vardır:

    1. Kod parçacığında **doğru** seçili metinle başlayın. `op`Üzerine yazmak için yazın. (Visual Basic, ilk Cap ile başlayıp yazın `Op` .)

    2. **IntelliSense** penceresi açılır ve **OpenFileDialog1**görüntüler. Seçmek için sekme tuşunu seçin. (Visual Basic bir başlangıç üst sınırı ile başlar, bu nedenle **OpenFileDialog1**görürsünüz. **OpenFileDialog1** seçildiğinden emin olun.)

         Hakkında daha fazla bilgi için `OpenFileDialog` bkz. [OpenFileDialog](https://msdn.microsoft.com/library/system.windows.forms.openfiledialog.aspx).

    3. Bir nokta ( `.` ) yazın (birçok programcı bu noktayı çağırır.) **OpenFileDialog1**sonrasında bir nokta yazdığınızdan, bir **IntelliSense** penceresi açılır ve tüm **OpenFileDialog** bileşeni özellikleri ve yöntemleri ile doldurulur. Bunlar, Windows Form Tasarımcısı ' de seçerken **Özellikler** penceresinde görüntülenen özelliklerden aynıdır. Ayrıca, bileşene bir şeyler (bir iletişim kutusu aç gibi) yapacağını söyleyen yöntemler de seçebilirsiniz.

        > [!NOTE]
        > **IntelliSense** penceresi her iki özelliği ve yöntemi gösterebilir. Neyin gösterilmekte olduğunu belirlemek için, **IntelliSense** penceresindeki her öğenin sol tarafındaki simgeye bakın. Her yöntemin yanında bir bloğun bir resmini ve her bir özelliğin yanındaki bir wrana (ya da Spanner) resmini görürsünüz. Her olayın yanında bir şimşek simgesi de vardır. Bu resimler aşağıda gösterildiği gibi görüntülenir.

         ![Yöntem simgesi](../ide/media/express-iconmethod.png "Express_IconMethod") Yöntem simgesi

         ![Özellik simgesi](../ide/media/express-iconproperty.png "Express_IconProperty") Özellik simgesi

         ![Olay simgesi](../ide/media/express-iconevent.png "Express_IconEvent") Olay simgesi

    4. Başlangıç türü `ShowDialog` (büyük/küçük harf, IntelliSense için önemli değildir). `ShowDialog()`Yöntemi **Dosya Aç** iletişim kutusunu gösterecektir. Pencerede **ShowDialog**VURGULANDıKTAN sonra SEKME tuşunu seçin. Ayrıca, "ShowDialog" ifadesini vurgulayabilir ve yardım almak için F1 tuşunu seçebilirsiniz.

         Yöntemi hakkında daha fazla bilgi edinmek için `ShowDialog()` bkz. [ShowDialog yöntemi](https://msdn.microsoft.com/library/c7ykbedk.aspx).

    5. Bir denetim veya bileşen üzerinde bir yöntem kullandığınızda ( *bir yöntemi çağırmak*olarak adlandırılır), parantez eklemeniz gerekir. Bu nedenle, içindeki "g" dan hemen sonra açma ve kapatma parantezleri girin `ShowDialog` : `()` Şimdi "OpenFileDialog1. ShowDialog ()" şeklinde görünmelidir.

        > [!NOTE]
        > Yöntemler, herhangi bir programın önemli bir parçasıdır ve bu öğretici, yöntemlerin kullanılması için çeşitli yollar göstermiştir. Bir bileşenin yöntemini çağırmak için, **OpenFileDialog** bileşeni yöntemini nasıl adlandırmış olursunuz `ShowDialog()` . Bir `showButton_Click()` Kullanıcı bir düğme seçtiğinde bir iletişim kutusu ve resim açan yöntemi olarak adlandırılan, programınızın sizin oluşturduğunuz gibi işlemler yapması için kendi yöntemlerinizi oluşturabilirsiniz.

    6. Visual C# için bir boşluk ekleyin ve ardından iki eşittir işareti ( `==` ) ekleyin. Visual Basic için bir boşluk ekleyin ve sonra tek bir eşittir işareti ( `=` ) kullanın. (Visual C# ve Visual Basic farklı eşitlik işleçleri kullanır.)

    7. Başka bir boşluk ekleyin. Bunu yaptığınızda, başka bir **IntelliSense** penceresi açılır. Yazın `DialogResult` ve bu sekmeyi eklemek IÇIN sekme tuşunu seçin.

        > [!NOTE]
        > Bir yöntemi çağırmak için kod yazdığınızda bazen bir değer döndürür. Bu durumda, **OpenFileDialog** bileşeninin `ShowDialog()` yöntemi bir DialogResult değeri döndürür. DialogResult, iletişim kutusunda ne olduğunu belirten özel bir değerdir. Bir **OpenFileDialog** bileşeni, kullanıcının **Tamam** veya **iptal**' i seçmelerini sağlayabilir, bu nedenle `ShowDialog()` yöntemi DialogResult. ok veya DialogResult. Cancel öğesini döndürür.

    8. DialogResult değeri **IntelliSense** penceresini açmak için bir nokta yazın. Harfi girin `O` ve **Tamam 'ı**eklemek için sekme tuşunu seçin.

         Hakkında daha fazla bilgi edinmek için `DialogResult` bkz. [DialogResult](https://msdn.microsoft.com/library/system.windows.forms.dialogresult.aspx).

        > [!NOTE]
        > Kodun ilk satırı tamamlanmalıdır. Visual C# için aşağıdaki olmalıdır.
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
