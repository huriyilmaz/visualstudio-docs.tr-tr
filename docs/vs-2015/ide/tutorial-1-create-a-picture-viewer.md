---
title: 'Öğretici 1: resim görüntüleyici oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66988fa88ae347a2db08bf2f6d1b79ba3bcd80b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851318"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Eğitmen 1: Resim Görüntüleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticide, bir dosyadan resim yükleyen ve onu bir pencerede görüntüleyen bir program oluşturacaksınız. Formunuza düğmeler ve resim kutuları gibi denetimleri nasıl sürükleyeceğinizi, özelliklerini ayarlamanıza ve formu düzgün şekilde yeniden boyutlandırmak için kapsayıcıları nasıl kullanacağınızı öğreneceksiniz. Ayrıca kod yazmaya başlayın. Aşağıdakileri nasıl yapacağınızı öğrenirsiniz:

- Yeni bir proje oluşturma.

- Bir uygulamayı test etme (hata ayıklama).

- Bir forma onay kutuları ve düğmeler gibi temel denetimleri ekleyin.

- Düzenleri kullanarak bir formdaki denetimleri konumlandırın.

- Bir forma **Açık dosya** ve **renk** iletişim kutuları ekleyin.

- IntelliSense ve kod parçacıkları kullanarak kod yazın.

- Olay işleyicisi yöntemlerini yazın.

  Bitirdiğinizde, programınız aşağıdaki resme benzer şekilde görünür.

  ![Bu öğreticide oluşturduğunuz resim](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone") Bu öğreticide oluşturduğunuz resim

  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz. [nasıl yapılır: Visual Basic bir resim görüntüleyici oluşturma?](https://msdn.microsoft.com/vstudio/gg315352) ya da [nasıl yaparım: C# içinde resim görüntüleyici oluşturma?](https://msdn.microsoft.com/vcsharp/gg278960.aspx).

> [!NOTE]
> Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır. Visual C# ve Visual Basic her ikisi de bu öğreticide ele alınmıştır, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.
>
> Visual Basic kodunu görmek için, kod bloklarının en üstündeki **vb** sekmesini seçin ve Visual C# için kodu görmek üzere **c#** sekmesini seçin. Visual C++ [hakkında bilgi edinmek](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) istiyorsanız bkz. Başlarken ve [C++ dil Öğreticisi](http://www.cplusplus.com/doc/tutorial/).
>
> Windows Mağazası için Visual C# veya Visual Basic uygulamaları yazmayı öğrenmek istiyorsanız bkz. [C# veya Visual Basic kullanarak Ilk Windows mağazası uygulamanızı oluşturma](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Windows Mağazası için JavaScript uygulamaları oluşturma hakkında daha fazla bilgi için bkz. [JavaScript kullanarak Ilk Windows mağazası uygulamanızı oluşturma](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Windows Forms Uygulaması Projesi Oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)|Windows Forms bir uygulama projesi oluşturarak başlayın.|
|[2. Adım: Programınızı Çalıştırma](../ide/step-2-run-your-program.md)|Önceki adımda oluşturduğunuz Windows Forms uygulama programını çalıştırın.|
|[3. Adım: form özelliklerinizi ayarlama](../ide/step-3-set-your-form-properties.md)|**Özellikler** penceresini kullanarak formunuzun görünme şeklini değiştirin.|
|[4. Adım: TableLayoutPanel denetimi ile formunuzu düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Formunuza bir `TableLayoutPanel` denetim ekleyin.|
|[5. Adım: formunuza denetimler ekleme](../ide/step-5-add-controls-to-your-form.md)|`PictureBox`Formunuza denetim ve denetim gibi denetimler ekleyin `CheckBox` . Formunuza düğmeler ekleyin.|
|[6. Adım: düğme denetimlerinizi adlandırma](../ide/step-6-name-your-button-controls.md)|Düğmelerinizi daha anlamlı bir şekilde yeniden adlandırın.|
|[7. Adım: formunuza Iletişim kutusu bileşenleri ekleme](../ide/step-7-add-dialog-components-to-your-form.md)|Formunuza bir **OpenFileDialog** bileşeni ve bir **ColorDialog** bileşeni ekleyin.|
|[8. Adım: resim göster düğmesi olay Işleyicisi için kod yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense aracını kullanarak kod yazın.|
|[9. Adım: kodunuzu gözden geçirme, açıklama ve test etme](../ide/step-9-review-comment-and-test-your-code.md)|Kodunuzu gözden geçirin ve test edin. Gerektiğinde Yorumlar ekleyin.|
|[10. Adım: ek düğmeler ve onay kutusu için kod yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|IntelliSense kullanarak diğer düğmeleri ve onay kutusunu çalışacak şekilde kod yazın.|
|[11. Adım: Programınızı Çalıştırma ve Diğer Özellikleri Deneme](../ide/step-11-run-your-program-and-try-other-features.md)|Programınızı çalıştırın ve arka plan rengini ayarlayın. Renkleri, yazı tiplerini ve kenarlıkları değiştirme gibi diğer özellikleri deneyin.|
