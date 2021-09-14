---
title: Yayın Sayfası, Proje Tasarımcısı
description: Project Tasarımcısı'nın Yayımla sayfası, dağıtım dağıtımınıza ClickOnce kullanılır.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625868"
---
# <a name="publish-page-project-designer"></a>Yayın Sayfası, Proje Tasarımcısı

Project  **Tasarımcısı'nın Yayımla sayfası,** dağıtım için ClickOnce kullanılır.

Yayımla sayfasına **erişmek** için, Çözüm Gezgini'de bir proje düğümü seçin ve  **Project'ye** **tıklayın.** Project **Tasarımcısı** göründüğünde Yayımla **sekmesine** tıklayın.

> [!NOTE]
> Burada açıklanan ClickOnce özelliklerden bazıları, Derleme menüsünden veya bu sayfada PublishWizard düğmesine tıklayarak kullanılabilen  **PublishWizard** içinde de ayarlayabilirsiniz. 

## <a name="uielement-list"></a>UIElement Listesi

 **Klasör Konumu Yayımlama**

Uygulamanın yayımladığı konumu belirtir. Sürücü yolu ( `C:\deploy\myapplication` ), dosya paylaşımı ( ) `\\server\myapplication` veya FTP sunucusu ( ) `ftp://ftp.microsoft.com/myapplication` olabilir. Gözat ( ... ) düğmesinin **çalışması için** Yayımlama Konumu kutusunda **metin** olması gerektiğini unutmayın.

 **Yükleme Klasörü URL'si**

İsteğe bağlı. Kullanıcıların uygulamayı yüklemek için gidecekleri bir web sitesi belirtir. Bu yalnızca Yayımlama Konumu'dan farklı **olduğunda (örneğin,** uygulama bir hazırlama sunucusunda yayımlanırken) gereklidir.

 **Yükleme Modu ve Ayarlar**

Uygulamanın doğrudan Yayımlama Konumu'na **(Uygulama**  yalnızca çevrimiçi olduğunda kullanılabilir olduğunda) veya yükleniyor ve  Başlat menüsüne ekleniyor ve **Denetim Masası'daki** Program  Ekle veya Kaldır öğesinden (Uygulama çevrimdışı kullanılabilir olduğunda da seçili olduğunda) çalışıp çalışmay olmadığını belirler. 

WPF web tarayıcısı uygulamaları  için Uygulama çevrimdışı kullanılabilir ve bu tür uygulamalar yalnızca çevrimiçi olduğundan devre dışı bırakılmıştır.

 **Uygulama Dosyaları**

Tek tek dosyaların nasıl ve nereye yük olduğunu belirtmek için kullanılan Uygulama Dosyaları iletişim kutusunu açar.

 **Önkoşullar**

Uygulamayla birlikte yüklenmek için .NET Framework gibi önkoşul bileşenlerini belirtmek için kullanılan Önkoşullar iletişim kutusunu açar.

 **Güncelleştirmeler**

Uygulamanın güncelleştirme davranışını belirtmek için kullanılan Uygulama Güncelleştirmeleri iletişim kutusunu açar. Uygulama yalnızca **çevrimiçi kullanılabilir olduğunda** kullanılamaz.

 **Seçenekler**

Ek gelişmiş yayımlama seçeneklerini belirtmek için kullanılan Yayımlama Seçenekleri iletişim kutusunu açar.

 **Yayımlama Sürümü**

Uygulama için yayımlama sürüm numarasını ayarlar; sürüm numarası değiştiriken uygulama bir güncelleştirme olarak yayımlanır. Yayımlama sürümünün her parçası (**Ana**, **İkincil** **,** Derleme , **Düzeltme**) tarafından izin verilen maksimum değer olan 65355 ( ), maksimum <xref:System.UInt16.MaxValue> değere sahip <xref:System.Version> olabilir.

ClickOnce kullanarak bir uygulamanın birden fazla sürümünü yükleyebilirsiniz. Yükleme, uygulamanın önceki sürümlerini belirttiğiniz yayımlama konumu olan Arşiv adlı bir klasöre taşır. Önceki sürümlerin bu şekilde arşivlenmesi, yükleme dizinini önceki sürümden klasörlerden uzak tutar.

 **Her yayımlamada düzeltmeyi otomatik olarak artırma**

İsteğe bağlı. Bu seçenek seçildiğinde (varsayılan), yayımlama **sürüm** numarasının Düzeltme bölümü, uygulama her yayımlanırken bir artırılır. Bu, uygulamanın güncelleştirme olarak yayımlanır.

 **Yayımlama Sihirbazı**

Yayımlama Sihirbazı'nı açar. Yayımlama Sihirbazı'nın tamamlanması, Derleme menüsündeKi Yayımla **komutunu** çalıştırmayla **aynı etkiye** sahiptir.

 **Şimdi Yayımla**

Geçerli ayarları kullanarak uygulamayı yayımlar. **PublishWizard'daki Son düğmesine eşdeğerdir.** 

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
- [ClickOnce Güvenlik ve Dağıtım](../../deployment/clickonce-security-and-deployment.md)
