---
title: Hata ayıklama sayfası, proje Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 006662d7c07ba0498fff4617eca3fdc7c631d37b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660794"
---
# <a name="debug-page-project-designer"></a>Hata Ayıklama Sayfası, Proje Tasarımcısı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!WARNING]
> Bu konu, Windows Mağazası uygulamaları için geçerlidir. Bkz. Windows Geliştirme Merkezi 'nde [hata ayıklama C#oturumu C++ başlatma (vb, ve XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) .

 Visual Basic veya C# projede hata ayıklama davranışının özelliklerini ayarlamak Için **Proje Tasarımcısı** 'nın **hata ayıklama** sayfasını kullanın.

 **Hata ayıklama** sayfasına erişmek için **Çözüm Gezgini**bir proje düğümü seçin. **Proje** menüsünde, _ProjectName_**Özellikler**' i seçin. **Proje Tasarımcısı** göründüğünde, **Hata Ayıkla** sekmesine tıklayın.

## <a name="configuration-and-platform"></a>Yapılandırma ve platform
 Aşağıdaki seçenekler, görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmenizi sağlar.

 **Yapılandırma** Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**veya **Tüm yapılandırmalarda**olabilir. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

 **Platform** Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. Seçenekler **herhangi BIR CPU** (varsayılan), **x64**ve **x86**içerebilir. Daha fazla bilgi için bkz. [hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e).

## <a name="start-action"></a>Başlatma eylemi
 **Başlangıç eylemi** , uygulamanın hatası ayıklandığında başlatılacak öğeyi gösterir: proje, özel program, URL veya Nothing. Varsayılan olarak, bu seçenek **Project 'ı başlatacak**şekilde ayarlanır. **Hata ayıklama** sayfasındaki **başlangıç eylemi** ayarı `StartAction` özelliğinin değerini belirler.

 **Projeyi Başlat** Uygulamanın hatası ayıklandığında yürütülebilir dosyanın (Windows uygulama ve konsol uygulaması projeleri için) başlatılıp başlatılabileceğini belirtmek için bu seçeneği belirleyin. Bu seçenek varsayılan olarak seçilidir.

 **Dış programı Başlat** Uygulamanın hatası ayıklandığında belirli bir programın başlatılmasını belirtmek için bu seçeneği belirleyin.

 **TARAYıCıYı URL Ile Başlat** Uygulamanın hatası ayıklandığında belirli bir URL 'ye erişilmesi gerektiğini belirtmek için bu seçeneği belirleyin.

## <a name="start-options"></a>Başlatma seçenekleri
 **Komut satırı bağımsız değişkenleri** Bu metin kutusuna hata ayıklama için kullanılacak komut satırı bağımsız değişkenlerini girin.

 **Çalışma dizini** Bu metin kutusuna projenin başlatılacağı dizini girin. Veya bir dizin seçmek için ( **...** ) düğmesine tıklayın.

 **Uzak makineyi kullan** Uygulamanın uzak bir bilgisayardan hata ayıklaması yapmak için, bu onay kutusunu işaretleyin ve metin kutusuna uzak bilgisayarın yolunu girin.

## <a name="enable-debuggers"></a>Hata ayıklayıcıları etkinleştir
 **Yönetilmeyen kod hata ayıklamayı etkinleştir** Bu seçenek, yerel kod hata ayıklamanın desteklenip desteklenmediğini belirtir. COM nesnelerine çağrılar yapıyorsanız veya projenizi çağıran yerel kodda yazılmış özel bir program başlatırsanız ve yerel kodda hata ayıklaması yapmanız gerekiyorsa bu onay kutusunu işaretleyin. Yönetilmeyen kodun hata ayıklamasını devre dışı bırakmak için bu onay kutusunu temizleyin. Bu onay kutusu varsayılan olarak temizlenir.

 **SQL Server hata ayıklamayı etkinleştir** Visual Basic uygulamanızdan SQL yordamlarının hata ayıklamasını etkinleştirmek veya devre dışı bırakmak için bu onay kutusunu işaretleyin veya temizleyin. Bu onay kutusu varsayılan olarak temizlenir.

 **Visual Studio barındırma Işlemini etkinleştir** Visual Studio barındırma işlemini etkinleştirmek için bu onay kutusunu işaretleyin. Bu onay kutusu varsayılan olarak seçilidir. Daha fazla bilgi için bkz. [barındırma süreci (VSHost. exe)](../../ide/hosting-process-vshost-exe.md).

 Bir güvenlik bölgesinde hata ayıklamak için, bu seçeneği etkinleştirmeniz ve [Gelişmiş güvenlik ayarları Iletişim kutusunda](../../ide/reference/advanced-security-settings-dialog-box.md) **Seçilen izin kümesiyle bu uygulamada hata ayıklaması** yapmanız gerekir.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Basic hata ayıklama [Yapılandırması Proje ayarları](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md) Için [](../../debugger/debugging-in-visual-studio.md) [ C# Visual Studio proje ayarlarında](../../debugger/project-settings-for-csharp-debug-configurations.md) hata ayıklama yapılandırma hata ayıklama [özellikleri yönetimi](https://msdn.microsoft.com/92474d16-e7fe-4fac-9287-6bd6b3a7eb68) [nasıl yapılır: ile bir ClickOnce uygulamasında hata ayıklama Kısıtlı Izinler](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md) [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../../ide/how-to-create-and-edit-configurations.md)
