---
title: XAML Tasarımcısı proje kodunu hata ayıklama veya devre dışı bırakma | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e7de0b3985e09f61fd0c63d1764304b150503883
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657927"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>XAML Tasarımcısı'nda Proje Kodu Hatalarını Ayıklama veya Proje Kodunu Devre Dışı Bırakma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Çoğu durumda, XAML tasarımcısında işlenmemiş özel durumlara, farklı değerler döndüren veya uygulamanız tasarımcıda çalışırken farklı yollarla çalışan özelliklere veya yöntemlere erişmeye çalışan proje kodu neden olabilir. Bu özel durumları, Visual Studio 'nun başka bir örneğindeki proje kodunda hata ayıklaarak veya tasarımcıda proje kodunu devre dışı bırakarak geçici olarak önleyebilecek şekilde çözebilirsiniz.

 Proje kodu şunları içerir:

- Özel denetimler ve Kullanıcı denetimleri

- Sınıf kitaplıkları

- Değer dönüştürücüler

- Proje kodundan oluşturulan tasarım zamanı verilerine yönelik bağlamalar

  Proje kodu devre dışı bırakıldığında, Visual Studio, verilerin artık kullanılamadığı bir bağlamanın özelliğin adı gibi yer tutucuları gösterecektir; ya da artık çalıştırmayan bir denetim için yer tutucu.

  ![İşlenmeyen özel durum iletişim kutusu](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")

#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Proje kodunun bir özel duruma neden olup olmadığını belirleme

1. İşlenmeyen özel durum iletişim kutusunda **Tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

2. Uygulama derlemek ve çalıştırmak için menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat** ' ı seçin.

     Uygulama başarılı bir şekilde oluşturulup çalışırsa, tasarım zamanı özel durumuna tasarımcıda çalışan proje kodunuz neden olmuş olabilir.

#### <a name="to-debug-project-code-running-in-the-designer"></a>Tasarımcıda çalışan proje kodunda hata ayıklamak için

1. İşlenmeyen özel durum iletişim kutusunda, **Çalışan proje kodunu devre dışı bırakmak ve tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

2. Windows Görev Yöneticisi 'nde, şu anda çalışmakta olan tüm Visual Studio XAML Tasarımcısı örneklerini kapatmak için **Görevi Sonlandır** düğmesini seçin.

     ![TaskManager 'da XAML Tasarımcısı örnekleri](../designers/media/xaml-taskmanager.png "XAML_TaskManager")

3. Visual Studio 'da, hata ayıklamak istediğiniz kodu veya denetimi içeren XAML sayfasını açın.

4. Visual Studio 'nun yeni bir örneğini açın ve ardından projenizin ikinci bir örneğini açın.

5. Proje kodunuzda bir kesme noktası ayarlayın.

6. Visual Studio 'nun yeni örneğinde, menü çubuğunda **Hata Ayıkla**, **İşleme İliştir**' i seçin.

7. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinde **XDesProc.exe**' yi seçin ve ardından **Ekle** düğmesini seçin.

     ![XAML Tasarımcısı işlemi](../designers/media/xaml-attach.png "XAML_Attach")

     Bu işlem, Visual Studio 'nun ilk örneğindeki XAML Tasarımcısı işlemidir.

8. Visual Studio 'nun ilk örneğinde, menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat**' ı seçin.

     Artık tasarımcıda çalışan kodunuzda bir adım adım ekleyebilirsiniz.

#### <a name="to-disable-project-code-in-the-designer"></a>Tasarımcıda proje kodunu devre dışı bırakmak için

- İşlenmeyen özel durum iletişim kutusunda, **Çalışan proje kodunu devre dışı bırakmak ve tasarımcı bağlantısını yeniden yüklemek için buraya tıklayın ' ı** seçin.

- Alternatif olarak, XAML Tasarımcısı 'ndaki araç çubuğunda, **proje kodunu devre dışı bırak** düğmesini seçin.

     ![Proje kodunu devre dışı bırak düğmesi](../designers/media/xaml-disablecode.png "XAML_DisableCode")

     Proje kodunu yeniden etkinleştirmek için düğmeye tekrar geçiş yapabilirsiniz.

    > [!NOTE]
    > ARM veya x64 işlemcileri hedefleyen projeler için, Visual Studio tasarımcıda proje kodunu çalıştıramıyor, bu nedenle **proje kodunu devre dışı bırak** düğmesi tasarımcıda devre dışı bırakılır.

- Her iki seçenek de tasarımcı 'nın yeniden yüklenmesini sağlar ve ardından ilişkili projenin tüm kodlarını devre dışı bırakır.

    > [!NOTE]
    > Proje kodunu devre dışı bırakmak, tasarım zamanı verilerinin kaybedilmesine neden olabilir. Alternatif olarak, tasarımcıda çalışan kodda hata ayıklaması yapılır.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio ve Visual Studio İçin Blend Uygulamalarında XAML Tasarlama](../designers/designing-xaml-in-visual-studio.md)
