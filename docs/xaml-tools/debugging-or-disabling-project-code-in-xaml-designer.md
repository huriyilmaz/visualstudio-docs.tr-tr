---
title: XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma
description: XAML Tasarımcısı başka bir Visual Studio örneğinde çalışan proje kodunun hatalarını ayıklama da dahil olmak üzere, proje kodunu hata ayıklamayı veya devre dışı bırakmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/17/2021
ms.topic: how-to
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: 4d260fb5afdc70d333b4e7ec7707148f2244f986
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135374916"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma

Birçok durumda, XAML Tasarımcısı işlenmemiş özel durumlara, farklı değerler döndüren veya uygulamanız tasarımcıda çalışırken farklı bir şekilde çalışan özelliklere veya yöntemlere erişmeye çalışan proje kodu neden olabilir. bu özel durumları, başka bir Visual Studio örneğindeki proje kodunda hata ayıklaarak veya tasarımcıda proje kodunu devre dışı bırakarak geçici olarak engelleyebilirsiniz.

Project kod şunları içerir:

- Özel denetimler ve Kullanıcı denetimleri

- Sınıf kitaplıkları

- Değer dönüştürücüler

- Proje kodundan oluşturulan tasarım zamanı verilerine yönelik bağlamalar

proje kodu devre dışı bırakıldığında, Visual Studio yer tutucuları gösterir. örneğin, Visual Studio, verilerin artık kullanılamadığı bir bağlama için özelliğin adını veya artık çalıştırmayan bir denetim için yer tutucuyu gösterir.

![İşlenmeyen özel durum iletişim kutusu](media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Proje kodunun bir özel duruma neden olup olmadığını belirleme

1. İşlenmeyen özel durum iletişim kutusunda **Tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

2. Menü çubuğunda, **hata**  >  **ayıklamayı Başlat** ' ı seçerek uygulamayı derleyin ve çalıştırın.

     Uygulama başarılı bir şekilde oluşturulup çalışırsa, tasarım zamanı özel durumuna tasarımcıda çalışan proje kodunuz neden olmuş olabilir.

## <a name="to-debug-project-code-running-in-the-designer"></a>Tasarımcıda çalışan proje kodunda hata ayıklamak için

1. İşlenmeyen özel durum iletişim kutusunda, **Çalışan proje kodunu devre dışı bırakmak ve tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

2. Windows görev yöneticisi 'nde, şu anda çalışmakta olan Visual Studio XAML Tasarımcısı örneklerini kapatmak için **görevi sonlandır** düğmesini seçin.

     ![TaskManager 'da XAML Tasarımcısı örnekleri](media/xaml_taskmanager.png)

3. Visual Studio, hata ayıklamak istediğiniz kodu veya denetimi içeren XAML sayfasını açın.

4. Visual Studio yeni bir örneğini açın ve ardından projenizin ikinci bir örneğini açın.

5. Proje kodunuzda bir kesme noktası ayarlayın.

6. yeni Visual Studio örneğinde, menü çubuğunda,   >  **işleme ekle** hata ayıkla ' yı seçin.

7. **işleme iliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinde, kullanmakta olduğunuz Visual Studio sürümü ve geliştirmekte olduğunuz platform (aşağıdaki tabloya bakın) ile eşleşen işlemi seçin ve ardından **ekle** düğmesini seçin.

    |Visual Studio sürüm | Platform      | İşlem adı   |
    |----------------------|---------------|----------------|
    |2017 &ndash; 2022       | UWP uygulamaları      | UwpSurface.exe |
    |2017 &ndash; 2022       | WPF çekirdek uygulamaları | WpfSurface.exe |
    |yalnızca 2019             | WPF çerçevesi | xDesProc.exe   |
    |yalnızca 2022             | WPF çerçevesi | WpfSurface.exe |

    > [!IMPORTANT]
    > Visual Studio 2019 ' de, **araçlar** seçenekler   >    >  **ortam**  >  **önizleme özellikleri**' nde yeni WPF XAML Tasarımcısı etkinse WpfSurface.exe.

8. Visual Studio ilk örneğinde, menü çubuğunda **hata ayıkla**  >  **başlat hata** ayıkla ' yı seçin.

     Artık tasarımcıda çalışan kodunuzda bir adım adım ekleyebilirsiniz.

## <a name="to-disable-project-code-in-the-designer"></a>Tasarımcıda proje kodunu devre dışı bırakmak için

- İşlenmeyen özel durum iletişim kutusunda, **Çalışan proje kodunu devre dışı bırakmak ve tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

- Alternatif olarak, **XAML Tasarımcısı**'ndaki araç çubuğunda, **proje kodunu devre dışı bırak** düğmesini seçin.

     ![Project kodu devre dışı bırak düğmesi](media/xaml_disablecode.png)

     Proje kodunu yeniden etkinleştirmek için düğmeye tekrar geçiş yapabilirsiniz.

    > [!NOTE]
    > ARM veya X64 işlemcileri hedefleyen projeler için Visual Studio tasarımcı 'da proje kodu çalıştırılamaz, bu nedenle **proje kodunu devre dışı bırak** düğmesi tasarımcıda devre dışı bırakılır.

- Her iki seçenek de tasarımcı 'nın ilişkili proje için tüm kodu yeniden yüklemesine ve sonra devre dışı bırakmasına neden olur.

    > [!NOTE]
    > Proje kodunu devre dışı bırakmak, tasarım zamanı verilerinin kaybedilmesine neden olabilir. Alternatif olarak, tasarımcıda çalışan kodda hata ayıklaması yapılır.

## <a name="control-display-options"></a>Denetim görüntüleme seçenekleri

> [!NOTE]
> **denetim görüntüleme seçenekleri** yalnızca Windows 10 Fall Creators Update (derleme 16299) veya üstünü hedefleyen Evrensel Windows Platformu uygulamalarda kullanılabilir. **denetim görüntüleme seçenekleri** özelliği Visual Studio 2017 sürüm 15,9 veya üzeri sürümlerde kullanılabilir.

XAML tasarımcısında, denetim görüntüleme seçeneklerinizi yalnızca Windows SDK platform denetimlerini görüntüleyecek şekilde değiştirebilirsiniz. Bu, XAML tasarımcısının güvenilirliğini iyileştirebilecek.

Denetim görüntüleme seçeneklerini değiştirmek için, tasarımcı penceresinin sol alt kısmındaki simgeye tıklayın ve sonra **denetim görüntüleme seçenekleri** altında bir seçenek belirleyin:

![Denetim görüntüleme seçenekleri](media/control_display_options.png)

**Yalnızca platform denetimlerini göster**' i seçtiğinizde, SDK 'lardan, müşteri Kullanıcı denetimlerinden ve daha fazlasına ait tüm özel denetimler tamamen işlenmeyecektir. Bunun yerine, denetimin boyutunu ve konumunu göstermek için geri dönüş denetimleriyle değiştirilirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ve Visual Studio için Blend XAML tasarlama](designing-xaml-in-visual-studio.md)
