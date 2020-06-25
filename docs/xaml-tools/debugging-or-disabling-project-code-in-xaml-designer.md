---
title: XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: fba240c29cb8142a9ec4b4d28c71112c1974a5b1
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331063"
---
# <a name="debug-or-disable-project-code-in-xaml-designer"></a>XAML Tasarımcısı’nda proje kodu hatalarını ayıklama veya proje kodunu devre dışı bırakma

Birçok durumda, XAML Tasarımcısı işlenmemiş özel durumlara, farklı değerler döndüren veya uygulamanız tasarımcıda çalışırken farklı bir şekilde çalışan özelliklere veya yöntemlere erişmeye çalışan proje kodu neden olabilir. Bu özel durumları, Visual Studio 'nun başka bir örneğindeki proje kodunda hata ayıklaarak veya tasarımcıda proje kodunu devre dışı bırakarak geçici olarak engelleyebilirsiniz.

Proje kodu şunları içerir:

- Özel denetimler ve Kullanıcı denetimleri

- Sınıf kitaplıkları

- Değer dönüştürücüler

- Proje kodundan oluşturulan tasarım zamanı verilerine yönelik bağlamalar

Proje kodu devre dışı bırakıldığında, Visual Studio yer tutucular gösterir. Örneğin, Visual Studio, verilerin artık kullanılamadığı veya artık çalıştırmayan bir denetim için yer tutucu olan bir bağlama için özelliğin adını gösterir.

![İşlenmeyen özel durum iletişim kutusu](media/xaml_unhandledexception.png)

## <a name="to-determine-if-project-code-is-causing-an-exception"></a>Proje kodunun bir özel duruma neden olup olmadığını belirleme

1. İşlenmeyen özel durum iletişim kutusunda **Tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

2. Menü çubuğunda, **hata**  >  **ayıklamayı Başlat** ' ı seçerek uygulamayı derleyin ve çalıştırın.

     Uygulama başarılı bir şekilde oluşturulup çalışırsa, tasarım zamanı özel durumuna tasarımcıda çalışan proje kodunuz neden olmuş olabilir.

## <a name="to-debug-project-code-running-in-the-designer"></a>Tasarımcıda çalışan proje kodunda hata ayıklamak için

1. İşlenmeyen özel durum iletişim kutusunda, **Çalışan proje kodunu devre dışı bırakmak ve tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

2. Windows Görev Yöneticisi 'nde, şu anda çalışmakta olan tüm Visual Studio XAML Tasarımcısı örneklerini kapatmak için **Görevi Sonlandır** düğmesini seçin.

     ![TaskManager 'da XAML Tasarımcısı örnekleri](media/xaml_taskmanager.png)

3. Visual Studio 'da, hata ayıklamak istediğiniz kodu veya denetimi içeren XAML sayfasını açın.

4. Visual Studio 'nun yeni bir örneğini açın ve ardından projenizin ikinci bir örneğini açın.

5. Proje kodunuzda bir kesme noktası ayarlayın.

6. Visual Studio 'nun yeni örneğinde, menü çubuğunda, **Debug**  >  **işleme Ekle**Hata Ayıkla ' yı seçin.

7. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinde **XDesProc.exe**' yi seçin ve ardından **Ekle** düğmesini seçin.

     ![XAML Tasarımcısı işlemi](media/xaml_attach.png)

     Bu işlem, Visual Studio 'nun ilk örneğindeki XAML Tasarımcısı işlemidir.

8. Visual Studio 'nun ilk örneğinde, menü çubuğunda **Hata Ayıkla**  >  **Başlat hata**Ayıkla ' yı seçin.

     Artık tasarımcıda çalışan kodunuzda bir adım adım ekleyebilirsiniz.

## <a name="to-disable-project-code-in-the-designer"></a>Tasarımcıda proje kodunu devre dışı bırakmak için

- İşlenmeyen özel durum iletişim kutusunda, **Çalışan proje kodunu devre dışı bırakmak ve tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

- Alternatif olarak, **XAML Tasarımcısı**'ndaki araç çubuğunda, **proje kodunu devre dışı bırak** düğmesini seçin.

     ![Proje kodunu devre dışı bırak düğmesi](media/xaml_disablecode.png)

     Proje kodunu yeniden etkinleştirmek için düğmeye tekrar geçiş yapabilirsiniz.

    > [!NOTE]
    > ARM veya x64 işlemcileri hedefleyen projeler için, Visual Studio tasarımcıda proje kodunu çalıştıramıyor, bu nedenle **proje kodunu devre dışı bırak** düğmesi tasarımcıda devre dışı bırakılır.

- Her iki seçenek de tasarımcı 'nın ilişkili proje için tüm kodu yeniden yüklemesine ve sonra devre dışı bırakmasına neden olur.

    > [!NOTE]
    > Proje kodunu devre dışı bırakmak, tasarım zamanı verilerinin kaybedilmesine neden olabilir. Alternatif olarak, tasarımcıda çalışan kodda hata ayıklaması yapılır.

## <a name="control-display-options"></a>Denetim görüntüleme seçenekleri

> [!NOTE]
> **Denetim görüntüleme seçenekleri** yalnızca Windows 10 Fall Creators Update (derleme 16299) veya üstünü hedefleyen Evrensel Windows platformu uygulamalar için kullanılabilir. **Denetim görüntüleme seçenekleri** özelliği, Visual Studio 2017 sürüm 15,9 veya sonraki sürümlerinde kullanılabilir.

XAML tasarımcısında, denetim görüntüleme seçeneklerinizi yalnızca Windows SDK platform denetimlerini görüntüleyecek şekilde değiştirebilirsiniz. Bu, XAML tasarımcısının güvenilirliğini iyileştirebilecek.

Denetim görüntüleme seçeneklerini değiştirmek için, tasarımcı penceresinin sol alt kısmındaki simgeye tıklayın ve sonra **denetim görüntüleme seçenekleri**altında bir seçenek belirleyin:

![Denetim görüntüleme seçenekleri](media/control_display_options.png)

**Yalnızca platform denetimlerini göster**' i seçtiğinizde, SDK 'lardan, müşteri Kullanıcı denetimlerinden ve daha fazlasına ait tüm özel denetimler tamamen işlenmeyecektir. Bunun yerine, denetimin boyutunu ve konumunu göstermek için geri dönüş denetimleriyle değiştirilirler.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ve Visual Studio için Blend XAML tasarlama](designing-xaml-in-visual-studio.md)
