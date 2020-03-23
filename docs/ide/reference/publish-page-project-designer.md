---
title: Yayın Sayfası, Proje Tasarımcısı
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6bbb43408dc12c55b72eb0ca0909d8b261198a5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926165"
---
# <a name="publish-page-project-designer"></a>Yayın Sayfası, Proje Tasarımcısı

**Proje Tasarımcısı'nın** **Yayımlama** sayfası ClickOnce dağıtımı için özellikleri yapılandırmak için kullanılır.

**Yayımla** sayfasına erişmek için Çözüm **Gezgini'nde**bir proje düğümü seçin ve ardından **Proje** menüsünde **Özellikler'i**tıklatın. Proje **Tasarımcısı** göründüğünde, **Yayımla** sekmesini tıklatın.

> [!NOTE]
> Burada açıklanan ClickOnce özelliklerinden bazıları, **Yapı** menüsünden veya bu sayfadaki **PublishWizard** düğmesine tıklayarak **PublishWizard'da**da ayarlanabilir.

## <a name="uielement-list"></a>UIElement Listesi

 **Klasör Konumunu Yayımlama**

Uygulamanın yayımlandığı yeri belirtir. Bir sürücü yolu`C:\deploy\myapplication`( ), bir`\\server\myapplication`dosya paylaşımı (`ftp://ftp.microsoft.com/myapplication`), veya FTP sunucusu ( ). Gözatma (**...**) düğmesinin çalışması için metnin **Yayımlama Konumu** kutusunda bulunması gerektiğini unutmayın.

 **Yükleme Klasörü URL**

İsteğe bağlı. Kullanıcıların uygulamayı yüklemek için gittiği bir web sitesini belirtir. Bu, yalnızca **Yayımlama Konumu'ndan**(örneğin, uygulama bir evreleme sunucusuna yayımlandığında) farklı olduğunda gereklidir.

 **Yükleme Modu ve Ayarlar**

Uygulamanın doğrudan **Yayımlama Konumu'ndan** çalıştırılıp çalıştırılmadığını **(uygulama yalnızca çevrimiçi** olduğunda seçili olduğunda) veya **Başlat** menüsüne yüklenip eklenir ve **Denetim Masası'ndaki** Programları Ekle **veya Kaldır** öğesine eklenir **(uygulama çevrimdışı** olduğunda da seçilir).

WPF web tarayıcısı uygulamaları için uygulama **çevrimdışı olarak kullanılabilir ve** bu tür uygulamalar yalnızca çevrimiçi olarak kullanılabildiği için devre dışı bırakılır.

 **Başvuru Dosyaları**

Tek tek dosyaların nasıl ve nerede yüklenir olduğunu belirtmek için kullanılan Uygulama Dosyaları iletişim kutusunu açar.

 **Önkoşullar**

.NET Framework gibi ön koşul bileşenlerini belirtmek için kullanılan Önkoşullar iletişim kutusunu uygulamayla birlikte yüklenecek şekilde açar.

 **Güncelleştirmeler**

Uygulama için güncelleştirme davranışını belirtmek için kullanılan Uygulama Güncelleştirmeleri iletişim kutusunu açar. **Uygulama çevrimiçi** olduğunda kullanılamaz yalnızca seçilir.

 **Seçenekler**

Ek gelişmiş yayımlama seçenekleri belirtmek için kullanılan Yayımlama Seçenekleri iletişim kutusunu açar.

 **Sürüm Yayımla**

Uygulama için yayımlama sürüm numarasını ayarlar; sürüm numarası değiştirildiğinde, uygulama güncelleştirme olarak yayımlanır. Yayımlama sürümünün her bölümü **(Major**, **Minor**, **Build**, **Revision**)<xref:System.UInt16.MaxValue>maksimum değeri 65355 (), en fazla . <xref:System.Version>

ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yüklediğinizde, yükleme uygulamanın önceki sürümlerini belirttiğiniz yayımlama konumunda Arşiv adlı bir klasöre taşır. Önceki sürümleri bu şekilde arşivleme, yükleme dizinini önceki sürümdeki klasörlerden uzak tutar.

 **Her yayımlamaile otomatik olarak artış düzeltmesi**

İsteğe bağlı. Bu seçenek seçildiğinde (varsayılan), yayımlama sürüm numarasının **Düzeltme** bölümü, uygulama her yayımlandığında bir tane ile artımlanır. Bu, uygulamanın güncelleştirme olarak yayımlanmasını neden olur.

 **Yayımlama Sihirbazı**

Yayımlama Sihirbazı'nı açar. Yayımlama Sihirbazı'nı tamamlamak, **Yapı** menüsünde **Yayımla** komutunu çalıştırmakla aynı etkiye sahiptir.

 **Şimdi Yayınla**

Geçerli ayarları kullanarak uygulamayı yayımlar. **PublishWizard'daki** **Bitiş** düğmesine eşdeğerdir.

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
- [ClickOnce Güvenliği ve Dağıtımı](../../deployment/clickonce-security-and-deployment.md)
