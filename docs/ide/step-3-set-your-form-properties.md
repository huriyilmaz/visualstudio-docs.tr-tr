---
title: '3. Adım: Form özelliklerinizi ayarlama'
description: Formunuzun görünüşünü değiştirmek için Özellikler penceresi nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b858ed302c7fe89049585edb7cc5c4391a4789b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480622"
---
# <a name="step-3-set-your-form-properties"></a>3. Adım: Form özelliklerinizi ayarlama

Daha sonra, formunuzun görünüşünü değiştirmek için **Özellikler** penceresini kullanın.

## <a name="how-to-set-your-form-properties"></a>Form özelliklerinizi ayarlama

1. **Windows Form Tasarımcısı** baktığınızdan emin olun. Visual Studio tümleşik geliştirme ortamında (IDE), **Form1.cs [Design]** (ya da **Form1. vb [Design]** ) sekmesini seçerek Visual Basic).

1. Seçmek için **Form1** form içinde herhangi bir yeri seçin. Şimdi form özelliklerini göstermeli **Özellikler** penceresine bakın. Formlarda çeşitli özellikler vardır. Örneğin, ön plan ve arka plan rengini, formun üstünde görünen başlık metnini, formun boyutunu ve diğer özellikleri ayarlayabilirsiniz.

   > [!NOTE]
   > **Özellikler** penceresi görünmezse, araç çubuğunda kare **ayıklamayı Durdur** düğmesini seçerek uygulamanızı durdurun veya yalnızca pencereyi kapatın. Uygulama durdurulmuşsa ve yine de **Özellikler** penceresini görmüyorsanız, menü çubuğunda **View**  >  **Özellikler penceresini** görüntüle ' yi seçin.

1. Form seçildikten sonra, **Özellikler** penceresinde **Text** özelliğini bulun. Listenin nasıl sıralandığına bağlı olarak aşağı kaydırmanız gerekebilir. **Metin**' i seçin, **resim görüntüleyici** yazın ve ardından **ENTER**' u seçin.  Formunuz artık başlık çubuğunda metin **resmi görüntüleyicisine** sahip olmalıdır ve **Özellikler** penceresi aşağıdaki ekran görüntüsüne benzer görünmelidir.

    ![Özellik penceresi](../ide/media/express_edittextproperty.png)<br>
   **_Özellikler_* _ _window *

   > [!NOTE]
   > Özellikler, **kategorilere ayrılmış** veya **alfabetik** bir görünüme göre sıralanabilir. **Özellikler** penceresindeki düğmeleri kullanarak bu iki görünüm arasında geçiş yapabilirsiniz. Bu öğreticide, **alfabetik** görünüm aracılığıyla özellikleri bulmak daha kolay.

1. **Windows Form Tasarımcısı**'e geri dönün. Formun sağ alt kısmındaki küçük beyaz kare olan ve aşağıdaki gibi görünen formun sağ alt sürükleme tutamacını seçin.

    ![Sürükleme tutamacı](../ide/media/express_bottomrt_drag.png)<br>
   *Sürükleme tutamacı*

    Formu daha geniş ve biraz uzun olacak şekilde yeniden boyutlandırmak için tutamacı sürükleyin.

1. **Özellikler** penceresine bakın ve **Boyut** özelliğinin değiştiğini unutmayın. Formu her yeniden boyutlandırışınızda **size** özelliği değişir. Formun tutamacını, yaklaşık **550, 350** (tam olması gerekmez) form boyutuyla yeniden boyutlandırmak için, bu proje için iyi bir şekilde çalışacak şekilde sürüklemeyi deneyin. Alternatif olarak, değerleri doğrudan **Boyut** özelliğine girebilir ve ardından **ENTER** tuşunu seçebilirsiniz.

1. Uygulamanızı yeniden çalıştırın. Uygulamanızı çalıştırmak için aşağıdaki yöntemlerden herhangi birini kullanacağınızı unutmayın.

   - **F5** tuşunu seçin.

   - Menü çubuğunda **hata**  >  **ayıklamayı Başlat hata** Ayıkla ' yı seçin.

   - Araç çubuğunda, aşağıdaki gibi görünen **hata ayıklamayı Başlat** düğmesini seçin.

      ![Hata ayıklamayı Başlat araç çubuğu düğmesi](../ide/media/express_icondebug.png)<br>
     **_Hata ayıklamayı Başlat_* _ _toolbar düğmesi *

     Daha önce olduğu gibi, IDE uygulamanızı oluşturup çalıştırır ve bir pencere görüntülenir.

1. Bir sonraki adıma geçmeden önce, IDE çalışırken uygulamanızı değiştirmenize izin vermediğinden uygulamanızı durdurun. Uygulamanızı durdurmak için aşağıdaki yöntemlerden herhangi birini kullanacağınızı unutmayın.

   - Araç çubuğunda **hata ayıklamayı Durdur** düğmesini seçin.

   - Menü çubuğunda **hata**  >  **ayıklamayı Durdur hata** Ayıkla ' yı seçin.

   - Klavyenizi kullanın ve **SHIFT** + **F5** tuşuna basın.

   - **Resim görüntüleyici** penceresinin üst köşesindeki **X** düğmesini seçin.

## <a name="next-steps"></a>Sonraki adımlar

* Sonraki öğretici adımına gitmek için bkz. 4. **[Adım: TableLayoutPanel denetimi ile formunuzu düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Önceki öğretici adımına dönmek için bkz. 2. [Adım: resim görüntüleyici uygulamanızı çalıştırma](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Öğretici 2: süreli bir matematik testi oluşturma](tutorial-2-create-a-timed-math-quiz.md)
* [Öğretici 3: eşleşen oyun oluşturma](tutorial-3-create-a-matching-game.md)
