---
title: Yayın Sayfası, Proje Tasarımcısı
description: Proje Tasarımcısı ' nın Yayımla sayfası ClickOnce dağıtımınızın özelliklerini yapılandırmak için kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32bbd09b087639c362fbb5d6a137241c1aab85af
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958329"
---
# <a name="publish-page-project-designer"></a>Yayın Sayfası, Proje Tasarımcısı

**Proje Tasarımcısı** ' nın **Yayımla** sayfası ClickOnce dağıtımı için özellikleri yapılandırmak üzere kullanılır.

**Yayımla** sayfasına erişmek için **Çözüm Gezgini**' de bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler**' e tıklayın. **Proje Tasarımcısı** göründüğünde, **Yayımla** sekmesine tıklayın.

> [!NOTE]
> Burada açıklanan bazı ClickOnce özellikleri, **derleme** menüsünde veya bu sayfadaki **publishwizard** düğmesine tıklanarak bulunan **publishwizard**'da da ayarlanabilir.

## <a name="uielement-list"></a>UIElement Listesi

 **Yayımlama klasörü konumu**

Uygulamanın yayımlandığı konumu belirtir. , Bir sürücü yolu ( `C:\deploy\myapplication` ), bir dosya paylaşma ( `\\server\myapplication` ) veya bir FTP sunucusu () olabilir `ftp://ftp.microsoft.com/myapplication` . Göz at (**...**) düğmesinin çalışması Için **Yayımlama konumu** kutusunda metnin mevcut olması gerektiğini unutmayın.

 **Yükleme klasörü URL 'SI**

İsteğe bağlı. Kullanıcıların uygulamayı yüklemek için gideceği Web sitesini belirtir. Bu, yalnızca **yayımlama konumundan** farklı olduğunda (örneğin, uygulama bir hazırlama sunucusuna yayımlandığında) gereklidir.

 **Modu ve ayarları yükler**

Uygulamanın doğrudan **yayımlama konumundan** çalıştırılıp çalıştırılmadığını ( **uygulama yalnızca çevrimiçi kullanılabilir** olduğunda) veya **yüklenip,** **Denetim Masası** 'ndaki **Program Ekle veya Kaldır** öğesine eklendiğini ( **uygulama çevrimdışı kullanılabilir** olduğunda) belirler.

WPF Web tarayıcısı uygulamaları için **uygulama çevrimdışı olarak kullanılabilir** , çünkü bu uygulamalar yalnızca çevrimiçi kullanılabilir.

 **Uygulama dosyaları**

Her bir dosyanın nasıl ve nerede yükleneceğini belirlemek için kullanılan uygulama dosyaları iletişim kutusunu açar.

 **Önkoşullar**

Uygulamayla birlikte yüklenecek .NET Framework gibi Önkoşul bileşenlerini belirtmek için kullanılan Önkoşullar iletişim kutusunu açar.

 **Güncelleştirmeler**

Uygulamanın güncelleştirme davranışını belirtmek için kullanılan uygulama güncelleştirmeleri iletişim kutusunu açar. **Uygulama yalnızca çevrimiçi kullanılabilir** olduğunda kullanılamaz.

 **Seçenekler**

Diğer gelişmiş yayımlama seçeneklerini belirtmek için kullanılan Yayımla Seçenekleri iletişim kutusunu açar.

 **Yayımlama sürümü**

Uygulama için yayımlama sürüm numarasını ayarlar; sürüm numarası değiştirildiğinde, uygulama bir güncelleştirme olarak yayımlanır. Yayımla sürümünün (**ana**, **İkincil**, **derleme**, **Düzeltme**) her bölümü <xref:System.UInt16.MaxValue> , izin verilen en yüksek 65355 () değerine sahip olabilir <xref:System.Version> .

ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yüklediğinizde yükleme, uygulamanın önceki sürümlerini belirttiğiniz Yayımla konumundaki arşiv adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerin temizlenmesini önler.

 **Her yayınla birlikte düzeltmeyi otomatik olarak artır**

İsteğe bağlı. Bu seçenek belirlendiğinde (varsayılan), yayımlama sürümü numarasının **Düzeltme** bölümü, uygulamanın her yayımlanışında bir artırılır. Bu, uygulamanın bir güncelleştirme olarak yayımlanmasına neden olur.

 **Yayımlama Sihirbazı**

Yayımla sihirbazını açar. Yayımla sihirbazının tamamlanması, **derleme** menüsündeki **Yayımla** komutunu çalıştırmasıyla aynı etkiye sahiptir.

 **Şimdi Yayımla**

Geçerli ayarları kullanarak uygulamayı yayımlar. **Publishwizard**'daki **son** düğmesine eşittir.

## <a name="see-also"></a>Ayrıca bkz.

- [ClickOnce Uygulamalarını Yayımlama](../../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: Yayımlama Sihirbazını Kullanarak ClickOnce Uygulaması Yayımlama](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Nasıl yapılır: Visual Studio'nun Dosyaları Nereye Kopyalayacağını Belirtme](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Nasıl yapılır: Son Kullanıcıların Yükleme Yapacakları Konumu Belirtme](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [Nasıl yapılır: Teknik Destek için bir Bağlantı Belirtme](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [Nasıl yapılır: ClickOnce Çevrimdışı veya Çevrimiçi Yükleme Modunu Belirtme](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [Nasıl yapılır: CD Yüklemeleri için AutoStart'ı Etkinleştirme](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [Nasıl yapılır: ClickOnce Yayım Sürümü'nü Ayarlama](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [Nasıl yapılır: ClickOnce Yayım Sürümünü Otomatik Olarak Artırma](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Nasıl yapılır: ClickOnce Tarafından Hangi Dosyaların Yayımlandığını Belirtme](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [Nasıl yapılır: ClickOnce Uygulamasıyla Önkoşulları Yükleme](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Yayımlama Dilini Değiştirme](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için Başlat Menüsü Adı Belirtme](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce Uygulaması için bir Yayımlama Sayfası Belirtme](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [ClickOnce güvenliği ve dağıtımı](../../deployment/clickonce-security-and-deployment.md)
