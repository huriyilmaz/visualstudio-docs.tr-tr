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
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851318"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>Eğitmen 1: Resim Görüntüleyici Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu öğreticide, bir dosyadan resim yükleyen ve onu bir pencerede görüntüleyen bir program oluşturacaksınız. Formunuza düğmeler ve resim kutuları gibi denetimleri nasıl sürükleyeceğinizi, özelliklerini ayarlamanıza ve formu düzgün şekilde yeniden boyutlandırmak için kapsayıcıları nasıl kullanacağınızı öğreneceksiniz. Ayrıca kod yazmaya başlayın. Aşağıdakilerin nasıl yapıldığını öğreneceksiniz:

- Yeni bir proje oluşturun.

- Bir uygulamayı test etme (hata ayıklama).

- Bir forma onay kutuları ve düğmeler gibi temel denetimleri ekleyin.

- Düzenleri kullanarak bir formdaki denetimleri konumlandırın.

- Bir forma **Açık dosya** ve **renk** iletişim kutuları ekleyin.

- IntelliSense ve kod parçacıkları kullanarak kod yazın.

- Olay işleyicisi yöntemlerini yazın.

  Bitirdiğinizde, programınız aşağıdaki resme benzer şekilde görünür.

  ![Bu öğreticide oluşturduğunuz resim](../ide/media/express-pictureviewerdone.png "Express_PictureViewerDone") Bu öğreticide oluşturduğunuz resim

  ![video bağlantısı](../data-tools/media/playvideo.gif "PlayVideo") Bu konunun video sürümü için bkz. [nasıl yapılır: Visual Basic bir resim görüntüleyici oluşturma?](https://msdn.microsoft.com/vstudio/gg315352) veya [' C#de nasıl yapılır: bir resim görüntüleyici oluşturma?](https://msdn.microsoft.com/vcsharp/gg278960.aspx).

> [!NOTE]
> Bu videolar, Visual Studio 'nun önceki bir sürümünü kullanır, bu nedenle bazı menü komutlarında ve diğer kullanıcı arabirimi öğelerinde küçük farklılıklar vardır. Ancak, kavramlar ve yordamlar Visual Studio 'nun geçerli sürümünde benzer şekilde çalışır. Görsel C# ve Visual Basic her ikisi de bu öğreticide ele alınmıştır, bu nedenle kullandığınız programlama diline özgü bilgilere odaklanın.
>
> Visual Basic kodunu görmek için, kod bloklarının en üstündeki **vb** sekmesini seçin ve görsele C#yönelik kodu görmek için **C#** sekmeyi seçin. Görsel C++ [hakkında bilgi edinmek](../misc/getting-started-with-visual-cpp-in-visual-studio-2015.md) istiyorsanız bkz. Başlarken ve [ C++ dil Öğreticisi](http://www.cplusplus.com/doc/tutorial/).
>
> Windows Mağazası için Visual C# veya Visual Basic uygulamaları yazmayı öğrenmek istiyorsanız, bkz. [veya Visual Basic kullanarak C# ilk Windows mağazası uygulamanızı oluşturma](https://msdn.microsoft.com/library/windows/apps/hh974581.aspx). Windows Mağazası için JavaScript uygulamaları oluşturma hakkında daha fazla bilgi için bkz. [JavaScript kullanarak Ilk Windows mağazası uygulamanızı oluşturma](https://msdn.microsoft.com/library/windows/apps/br211385.aspx).

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[1. Adım: Windows Forms Uygulaması Projesi Oluşturma](../ide/step-1-create-a-windows-forms-application-project.md)|Windows Forms bir uygulama projesi oluşturarak başlayın.|
|[2. Adım: Programınızı Çalıştırma](../ide/step-2-run-your-program.md)|Önceki adımda oluşturduğunuz Windows Forms uygulama programını çalıştırın.|
|[3. Adım: Form Özelliklerinizi Ayarlama](../ide/step-3-set-your-form-properties.md)|**Özellikler** penceresini kullanarak formunuzun görünme şeklini değiştirin.|
|[4. Adım: TableLayoutPanel Denetimi ile Formunuzu Düzenleme](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|Formunuza `TableLayoutPanel` denetimi ekleyin.|
|[5. Adım: Formunuza Denetimler Ekleme](../ide/step-5-add-controls-to-your-form.md)|Formunuza `PictureBox` denetimi ve `CheckBox` denetimi gibi denetimler ekleyin. Formunuza düğmeler ekleyin.|
|[6. Adım: Düğme Denetimlerinizi Adlandırma](../ide/step-6-name-your-button-controls.md)|Düğmelerinizi daha anlamlı bir şekilde yeniden adlandırın.|
|[7. Adım: Formunuza İletişim Kutusu Bileşenleri Ekleme](../ide/step-7-add-dialog-components-to-your-form.md)|Formunuza bir **OpenFileDialog** bileşeni ve bir **ColorDialog** bileşeni ekleyin.|
|[8. Adım: Resim Göster Düğmesi Olay İşleyicisi için Kod Yazma](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|IntelliSense aracını kullanarak kod yazın.|
|[9. Adım: Kodunuzu Gözden Geçirme, Açıklama ve Test Etme](../ide/step-9-review-comment-and-test-your-code.md)|Kodunuzu gözden geçirin ve test edin. Gerektiğinde Yorumlar ekleyin.|
|[10. Adım: Ek Düğmeler ve Onay Kutusu için Kod Yazma](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|IntelliSense kullanarak diğer düğmeleri ve onay kutusunu çalışacak şekilde kod yazın.|
|[11. Adım: Programınızı Çalıştırma ve Diğer Özellikleri Deneme](../ide/step-11-run-your-program-and-try-other-features.md)|Programınızı çalıştırın ve arka plan rengini ayarlayın. Renkleri, yazı tiplerini ve kenarlıkları değiştirme gibi diğer özellikleri deneyin.|
