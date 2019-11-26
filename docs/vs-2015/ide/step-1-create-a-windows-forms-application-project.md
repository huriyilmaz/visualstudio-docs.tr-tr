---
title: '1\. Adım: Windows Forms uygulama projesi oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9651c04c1d94459052d92cdda0afa58e344b650
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295782"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>1\. Adım: Windows Forms Uygulaması Projesi Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir resim görüntüleyici oluşturduğunuzda, ilk adım Windows Forms bir uygulama projesi oluşturmaktır.

 ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz [. öğretici 1: Visual Basic resim görüntüleyici oluşturma-video 1](https://go.microsoft.com/fwlink/?LinkId=205209) veya [öğretici 1: video 1 ' de C# bir resim görüntüleyici oluşturma](https://go.microsoft.com/fwlink/?LinkId=205199). Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır.

### <a name="to-create-a-windows-forms-application-project"></a>Windows Forms uygulama projesi oluşturmak için

1. Menü çubuğunda **Dosya**, **Yeni**, **Proje**' yi seçin. İletişim kutusu şöyle görünmelidir.

     ![Yeni proje iletişim kutusu](../ide/media/newprojectdialogcallouts.png "Newprojectdialogbelirtme çizgileri") Yeni proje iletişim kutusu

2. **Yüklü şablonlar** listesinde **görsel C#**  veya **Visual Basic** seçin.

3. Şablonlar listesinde **Windows Forms uygulama** simgesini seçin. Yeni formu **PictureViewer olarak adlandırın**olarak adlandırın ve ardından **Tamam** düğmesini seçin.

     Visual Studio, programınız için bir çözüm oluşturur. Bir çözüm, programınızın gerektirdiği tüm proje ve dosyalar için bir kapsayıcı görevi görür. Bu terimler, Bu öğreticinin ilerleyen kısımlarında daha ayrıntılı olarak açıklanacaktır.

4. Aşağıdaki çizimde, Visual Studio arabiriminde neleri görmeniz gerektiği gösterilmektedir.

    > [!NOTE]
    > Pencere düzeniniz tam olarak bu çizim gibi görünmeyebilir. Kesin pencere düzeni, Visual Studio sürümüne, kullandığınız programlama diline ve diğer faktörlere bağlıdır. Ancak, üç pencerelerin de görüntülendiğini doğrulamanız gerekir.

     ![IDE penceresi](../ide/media/express-ideoverview-visio.png "Express_IDEOverview_Visio") IDE penceresi

     Arabirim üç pencere içerir: Ana pencere, **Çözüm Gezgini**ve **Özellikler** penceresi.

     Bu pencerelerin herhangi biri eksikse, menü çubuğunda **pencere**, pencere **düzeni Sıfırla**' yı seçerek varsayılan pencere yerleşimini geri yükleyin. Ayrıca, menü komutlarını kullanarak da Windows görüntüleyebilirsiniz. Menü çubuğunda **Görünüm**, **özellikler penceresi** veya **Çözüm Gezgini**öğesini seçin. Başka herhangi bir pencere açıksa, sağ üst köşelerindeki **Kapat** (x) düğmesini seçerek onları kapatın.

5. Çizimde aşağıdaki pencereler gösterilmektedir (sol üst köşeden saat yönünde):

    - **Ana pencere** Bu pencerede, yaptığınız gibi, formlarla çalışma ve kod düzenlemeyle ilgili birçok iş olacaktır. Çizimde pencere, form düzenleyicisinde bir form gösterir. Pencerenin üst kısmında, **Başlangıç sayfası** sekmesi ve **Form1.cs [Design]** sekmesi görüntülenir. (Visual Basic, sekme adı. cs yerine. vb ile biter.)

    - **Çözüm Gezgini penceresi** Bu pencerede, çözümünüzdeki tüm öğeleri görüntüleyebilir ve buna gidebilirsiniz. Bir dosya seçerseniz, **Özellikler** penceresinin içeriği değişir. Bir kod dosyası açarsanız (Visual C# üzerinde. cs ve. vb Visual Basic), kod dosyası veya kod dosyası Tasarımcısı görüntülenir. Tasarımcı, üzerinde düğme ve liste gibi denetimler ekleyebileceğiniz görsel bir yüzeydir. Visual Studio Forms için tasarımcı Windows Form Tasarımcısı olarak adlandırılır.

    - **Özellikler penceresi** Bu pencerede, diğer pencereler üzerinde seçtiğiniz öğelerin özelliklerini değiştirebilirsiniz. Örneğin, Form1 ' i seçerseniz, **Text** özelliğini ayarlayarak başlığını değiştirebilir ve **BackColor** özelliğini ayarlayarak arka plan rengini değiştirebilirsiniz.

    > [!NOTE]
    > **Çözüm Gezgini** en üstteki satır, Visual Studio 'nun sizin için bir çözüm oluşturduğu anlamına gelen **' PictureViewer olarak adlandırın ' (1 proje) çözümünü**gösterir. Bir çözüm birden fazla proje içerebilir, ancak şimdilik yalnızca bir proje içeren çözümlerle çalışırsınız.

6. Menü çubuğunda **Dosya**, **Tümünü Kaydet**seçeneklerini belirleyin.

     Alternatif olarak, aşağıdaki çizimin gösterdiği araç çubuğunda **Tümünü Kaydet** düğmesini seçin.

     ![Tümünü Kaydet araç çubuğu düğmesi](../ide/media/express-iconsaveall.png "Express_IconSaveAll") Tümünü Kaydet araç çubuğu düğmesi

     Visual Studio, klasör adı ve proje adını otomatik olarak doldurur ve projeyi projeler klasörünüze kaydeder.

### <a name="to-continue-or-review"></a>Devam etmek veya gözden geçirmek için

- Sonraki öğretici adımına gitmek için bkz. 2. [Adım: Programınızı çalıştırma](../ide/step-2-run-your-program.md).

- Genel bakış konusuna dönmek için bkz. [öğretici 1: resim görüntüleyici oluşturma](../ide/tutorial-1-create-a-picture-viewer.md).
