---
title: XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma
description: Proje kodunun başka bir örneğinde çalışan proje XAML Tasarımcısı hata ayıklama da dahil olmak üzere proje kodunda hata ayıklamayı veya devre dışı bırakmayı Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 8e0563318600c30d595d6fd193aff48f4171d31ae95e39c48c8bb5dd02c154ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121393290"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma

Çoğu durumda, XAML Tasarımcısı uygulama tasarımcısında çalışırken farklı değerler veya farklı bir şekilde çalışan özelliklere veya yöntemlere erişmeye çalışan proje kodu nedeniyle XAML Tasarımcısı'daki işlanmamış özel durumlar olabilir. Bu özel durumları çözmek için projenin başka bir örneğinde proje kodunda hata Visual Studio veya tasarımcıda proje kodunu devre dışı bırakarak özel durumları geçici olarak önleyebilirsiniz.

Project kod şunları içerir:

- Özel denetimler ve kullanıcı denetimleri

- Sınıf kitaplıkları

- Değer dönüştürücüleri

- Proje kodundan oluşturulan tasarım zamanı verilerine karşı bağlamalar

Proje kodu devre dışı bırak Visual Studio yer tutucuları gösterir. Örneğin, Visual Studio artık kullanılabilir olmayan bir bağlama için özelliğin adını veya artık çalışmayan bir denetim için yer tutucuyu gösterir.

![İşlenemeyen özel durum iletişim kutusu](media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Proje kodunun bir özel duruma neden olup olmadığını belirlemek için

1. İşlenemeyen özel durum iletişim kutusunda **Tasarımcıyı yeniden yüklemek için buraya tıklayın bağlantısını** seçin.

2. Uygulamayı derlemek ve çalıştırmak **için menü çubuğunda**  >  **Hata** AyıklamaYı Başlat Hata Ayıklama'ya tıklayın.

     Uygulama başarıyla oluşturur ve çalışırsa tasarım zamanı özel durumuna tasarımcıda çalışan proje kodunuz neden olabilir.

## <a name="to-debug-project-code-running-in-the-designer"></a>Tasarımcıda çalışan proje kodunda hata ayıklamak için

1. İşlenemeyen özel durum iletişim kutusunda, Çalışan proje kodunu devre **dışı bırakmak ve tasarımcıyı** yeniden yüklemek için buraya tıklayın bağlantısını seçin.

2. Görev Windows'nde, görev yöneticisinin  o anda çalışan tüm örneklerini kapatmak Visual Studio XAML Tasarımcısı Düğmesini seçin.

     ![TaskManager'da XAML tasarımcısı örnekleri](media/xaml_taskmanager.png)

3. Bu Visual Studio, hata ayıklamak istediğiniz kodu veya denetimi içeren XAML sayfasını açın.

4. Yeni bir Visual Studio açın ve ardından projenizin ikinci bir örneğini açın.

5. Proje kodunda bir kesme noktası ayarlayın.

6. Yeni uygulama örneği Visual Studio çubuğunda İşleme Eklemede Hata **Ayıkla'ya**  >  **tıklayın.**

7. İşleme **Ekle iletişim kutusundaki** Kullanılabilir **İşlemler** listesinde **XDesProc.exe'ı ve** ardından Ekle **düğmesini** seçin.

     ![XAML tasarımcısı işlemi](media/xaml_attach.png)

     Bu, XAML tasarımcısının Visual Studio.

8. İlk hata ayıklama Visual Studio menü çubuğunda Hata AyıklamaYı   >  **Başlat'ı seçin.**

     Artık tasarımcıda çalışan kodunuz içine adım atabilirsiniz.

## <a name="to-disable-project-code-in-the-designer"></a>Tasarımcıda proje kodunu devre dışı bırakmak için

- İşlenemeyen özel durum iletişim kutusunda, Çalışan proje kodunu devre **dışı bırakmak ve tasarımcıyı** yeniden yüklemek için buraya tıklayın bağlantısını seçin.

- Alternatif olarak, **XAML** tasarımcısındaki araç çubuğunda Proje kodunu devre **dışı bırak düğmesini** seçin.

     ![Kod Project Devre Dışı Bırak düğmesi](media/xaml_disablecode.png)

     Proje kodunu yeniden etkinleştirmek için düğmeyi yeniden etkinleştirebilirsiniz.

    > [!NOTE]
    > ARM veya X64 işlemcileri hedef alan projeler için Visual Studio proje kodunu tasarımcıda çalıştıramaz, bu nedenle Proje kodunu **devre** dışı bırak düğmesi tasarımcıda devre dışı bırakılır.

- Her iki seçenek de tasarımcının yeniden yüklemesini ve ardından ilişkili proje için tüm kodu devre dışı bırakmasını sağlar.

    > [!NOTE]
    > Proje kodunun devre dışı bırakılması tasarım zamanı veri kaybına neden olabilir. Alternatif olarak, tasarımcıda çalışan kodda hata ayıklaması da olabilir.

## <a name="control-display-options"></a>Denetim görüntüleme seçenekleri

> [!NOTE]
> **Denetim Görüntüleme Seçenekleri** yalnızca Windows (derleme 16299) veya sonraki bir Windows 10 Fall Creators Update platform uygulamaları için kullanılabilir. Denetim **Görüntüleme Seçenekleri özelliği,** 2017 Visual Studio 15.9 veya sonraki bir sürümde kullanılabilir.

XAML tasarımcısında, denetim görüntüleme seçeneklerinizi yalnızca Windows SDK'dan platform denetimlerini görüntü Windows değiştirebilirsiniz. Bu, XAML tasarımcısının güvenilirliğini geliştirmektedir.

Denetim görüntüleme seçeneklerini değiştirmek için tasarımcı penceresinin sol alt köşesindeki simgeye tıklayın ve ardından Denetim Görüntüleme **Seçenekleri'nin altında bir seçenek belirleyin:**

![Denetim Görüntüleme Seçenekleri](media/control_display_options.png)

Yalnızca Platform **Denetimlerini Görüntüle'yi seçerek,** SDK'lardan, müşteri kullanıcı denetimlerinden ve daha pek çok özel denetimden gelen tüm özel denetimler tamamen işlanmaz. Bunun yerine, denetimin boyutunu ve konumunu göstermek için geri dönüş denetimleriyle değiştirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XAML'i Visual Studio ve Visual Studio için Blend](designing-xaml-in-visual-studio.md)
