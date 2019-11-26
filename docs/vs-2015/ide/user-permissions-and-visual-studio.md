---
title: Kullanıcı izinleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dc49a628cdf5695df7744295d2c1d990986bcfbe
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295631"
---
# <a name="user-permissions-and-visual-studio"></a>Kullanıcı İzinleri ve Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Güvenlik nedenleriyle, mümkün oldukça Visual Studio'yu normal bir kullanıcı olarak çalıştırmanız gerekir.

> [!WARNING]
> Ayrıca güvenilir bir kişi ya da güvenilir bir konumdan gelmeyen herhangi bir Visual Studio çözümüyle derleme, başlatma veya hata ayıklama yapmadığınızdan emin olmalısınız.

 Normal bir kullanıcı olarak Visual Studio IDE içinde hemen her şeyi yapabilirsiniz, ancak şu görevleri tamamlamak için yönetici izinlerine sahip olmanız gerekir:

|Alan|Görev|Daha fazla bilgi için|
|----------|----------|--------------------------|
|Yükleme|Visual Studio'yu Yükleme.|[Visual Studio 2015 yükleniyor](../install/install-visual-studio-2015.md)|
||Visual Studio deneme sürümünden yükseltme.|[Nasıl Yapılır. Visual Studio Deneme Sürümünden Yükseltme](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Yerel Yardım içeriğini yükleme, güncelleştirme veya kaldırma.|[Yerel İçeriği Yükleme ve Yönetme](../ide/install-and-manage-local-content.md)|
|Uygulama türleri|SharePoint 2010 çözümleri geliştirme.|[SharePoint Çözümleri Geliştirmek için Gereksinimler](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||[!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)]için bir geliştirici lisansı alınıyor.|[Geliştirici lisansı edinme (Windows Mağazası uygulamaları)](https://go.microsoft.com/fwlink/?LinkID=241313)|
|Araç Kutusu|**Araç kutusuna**klasik com denetimleri ekleme.|[Araç Kutusunu Kullanma](../ide/using-the-toolbox.md)|
|Eklentiler|IDE'de klasik COM kullanılarak yazılmış eklentileri yükleme ve kullanma.|[Eklentiler ve Sihirbazlar oluşturma](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Oluşturma|Bir bileşeni kayıt ettiren oluşturma sonrası olayları kullanma.|[Özel Derleme Adımlarını ve Derleme Olaylarını Anlama](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||C++ projeleri oluşturduğunuzda kayıt adımı ekleme.|[Özel Derleme Adımlarını ve Derleme Olaylarını Anlama](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Hata Ayıklama|Yükseltilmiş izinlerle çalışan uygulamalarda hata ayıklama.|[Hata Ayıklayıcısı Ayarları ve Hazırlığı](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET web siteleri gibi farklı bir kullanıcı hesabı altında çalışan uygulamalarda hata ayıklama.|[ASP.NET ve AJAX Uygulamalarında Hata Ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)|
||XAML Tarayıcı Uygulamaları (XBAP) için bölgede hata ayıklama.|[WPF Konağı (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Microsoft Azure için bulut hizmeti projelerinde hata ayıklamak için öykünücü kullanma.|[Visual Studio 'da bir bulut hizmetinde hata ayıklama](https://go.microsoft.com/fwlink/?LinkId=266725)|
||Uzaktan hata ayıklama için bir güvenlik duvarı yapılandırma.|[Cihazda uzak araçları ayarlama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Performans araçları|Uygulama profili oluşturma.|[Performans Profili Oluşturma Başlangıç Kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)|
|Dağıtım|Yerel bir bilgisayarda Internet Information Services'a (IIS) web uygulaması dağıtma.|[Visual Studio veya Visual Web Developer kullanarak bir barındırma sağlayıcısına ASP.NET Web uygulaması dağıtma: IIS 'ye bir test ortamı olarak dağıtma](https://go.microsoft.com/fwlink/?LinkId=266478)|
|Microsoft'a geri bildirim sağlama|Visual Studio Müşteri Deneyimi Programı'na katılım şeklinizi değiştirme.|[Nasıl yapılır: geri bildirim gönderme](../misc/how-to-send-feedback-about-visual-studio.md)|

## <a name="running-visual-studio-as-an-administrator"></a>Visual Studio'yu Yönetici olarak çalıştırma
 IDE'yi her başlattığınızda Visual Studio'yu yönetim izinleri ile başlatabilir veya uygulama kısayolunu her zaman yönetim izinleriyle çalışacak şekilde değiştirebilirsiniz. Daha fazla bilgi için bkz. Windows Yardımı.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblue_server_2includeswinblue-server-2-mdmd"></a>Visual Studio 'Yu [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)]veya [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)] üzerinde yönetici izinleriyle çalıştırmak için

1. **Başlangıç** ekranında **Visual Studio**yazın. Yüklediğiniz Visual Studio sürümünü veya sürümlerini görmeniz gerekir.

2. Başlatmak istediğiniz Visual Studio sürümünü seçin ve kısayol menüsünü görüntüleyin (ekranın en altında görünür). **Yönetici olarak çalıştır**' ı seçin.

     Visual Studio başladığında, başlık çubuğunda ürün adından sonra **(yönetici)** görüntülenir.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08_r2includeswinsvr08-r2-mdmd"></a>[!INCLUDE[win7](../includes/win7-md.md)] veya [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)] üzerinde yönetim izinleriyle Visual Studio 'Yu çalıştırmak için

1. **Başlat** menüsünde **tüm programlar**' ı seçin.

2. **Microsoft Visual Studio** *Sürüm* klasörü ' nde, **Visual Studio** *sürümü* ' nü seçin, kısayol menüsünü açın ve **yönetici olarak çalıştır**' ı seçin.

     Visual Studio başladığında, başlık çubuğunda ürün adından sonra **(yönetici)** görüntülenir.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio [projelerini taşıma, geçirme ve yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Visual Studio 2015](../install/install-visual-studio-2015.md)
