---
title: Programlamada ortak Office görevler
description: Word veya Microsoft Office nesne modelini kullanmak zorunda kalmadan belge düzeyi özelleştirmede verilere karşı program Office Excel.
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 152af5d3be5385e6f5c91fb510d62ea7bc336218
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725609"
---
# <a name="common-tasks-in-office-programming"></a>Programlamada ortak Office görevler
  Bu konu, programlama ve programlama çözümleri hakkında aşağıdaki yaygın soruların yanıtlarını bulmak için Office yardımcı Visual Studio.

- [Kurulumu ve genel görevler.](#projects)

- [Kullanıcı arabirimi özelleştirme görevleri.](#ui)

- [Excel otomasyon görevleri.](#excel)

- [Word otomasyonu görevleri.](#word)

- [Veri görevleri.](#data)

- [Sunucu tarafı belge yönetimi görevleri.](#server)

- [Güvenlik görevleri.](#security)

- [Dağıtım görevleri.](#deployment)

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Kurulum ve genel görevler

- [Nasıl Visual Studio: Office projelerini Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

- [Nasıllı: Office yükseltme.](/previous-versions/4bez6837(v=vs.140))

- [Nasıl kurulur: Birincil birlikte Office derlemelerini yükleme.](../vsto/how-to-install-office-primary-interop-assemblies.md)

- [Nasıl kullanılır: Birincil Office derlemeleri aracılığıyla uygulamaları hedefle.](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)

- [Nasıllı: Projelerinde olay Office oluşturma.](../vsto/how-to-create-event-handlers-in-office-projects.md)

- [Nasıl: Kod Office çözümlerini açma.](../vsto/how-to-open-office-solutions-without-running-code.md)

- [Nasıl: Bir çözüm için yapılandırma bilgilerini Office.](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md)

- [Nasıl: Şeritte geliştirici sekmesini gösterme.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

- [Nasıl kullanılır: Eklenti kullanıcı arabirimi hatalarını gösterme.](../vsto/how-to-show-add-in-user-interface-errors.md)

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Kullanıcı arabirimi özelleştirme görevleri

### <a name="controls-on-documents-and-worksheets"></a>Belgeler ve çalışma sayfaları üzerinde denetimler

- [Nasıl kullanılır: Windows Formlar denetimleri Office ekleme.](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)

- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına NamedRange denetimleri ekleme.](../vsto/how-to-add-namedrange-controls-to-worksheets.md)

- [Nasıl ekleyebilirsiniz: Çalışma sayfalarına ListObject denetimleri ekleme.](../vsto/how-to-add-listobject-controls-to-worksheets.md)

- [Nasıl kullanılır: Windows Formlar denetimleri Office ekleme.](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)

- [Nasıl kullanılır: Word belgelerine İçerik denetimleri ekleme.](../vsto/how-to-add-content-controls-to-word-documents.md)

- [Nasıl kullanılır: Word belgelerine Yer İşareti denetimleri ekleme.](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

### <a name="task-panes-in-document-level-customizations"></a>Belge düzeyinde özelleştirmelerde görev bölmeleri

- [Nasıl kullanılır: Word belgelerine veya çalışma kitaplarını Excel bölmesi ekleme.](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)

### <a name="task-panes-in-vsto-add-ins"></a>Eklentilerde VSTO bölmeleri

- [Nasıl ekleyebilirsiniz: Uygulamaya özel görev bölmesi ekleme.](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)

### <a name="ribbon-customizations"></a>Şerit özelleştirmeleri

- [Nasıl Kullanmaya başlayın: Şerit'i özelleştirme.](../vsto/how-to-get-started-customizing-the-ribbon.md)

- [Nasıl: Şeritteki bir sekmenin konumunu değiştirme.](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)

- [Nasıl yapılır: Yerleşik bir sekmeyi özelleştirme.](../vsto/how-to-customize-a-built-in-tab.md)

- [Nasıl olur: Backstage görünümüne denetimler ekleme.](../vsto/how-to-add-controls-to-the-backstage-view.md)

- [Nasıl kullanılır: Şerit Tasarımcısından Şerit XML'ine Şerit Dışarı Aktarma.](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)

### <a name="outlook-form-regions"></a>Outlook bölgeleri oluşturma

- [Nasıl yapılanlar: Bir form bölgesi Outlook projesine ekleme.](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)

- [Nasıl Outlook: Outlook bir form bölgesi görüntülemesini engelleme.](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)

### <a name="custom-menus"></a>Özel menüler

- [Nasıl kullanılır: Kısayol menülerine komut ekleme.](../vsto/how-to-add-commands-to-shortcut-menus.md)

## <a name="excel-automation-tasks"></a><a name="excel"></a>Excel otomasyon görevleri

- [Nasıl gösterilir: Çalışma sayfası hücresinde program aracılığıyla bir dize görüntüleme.](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md)

- [Nasıl musunuz: Program aracılığıyla yeni çalışma kitapları oluşturma.](../vsto/how-to-programmatically-create-new-workbooks.md)

- [Nasıl: Çalışma kitaplarını program aracılığıyla açma.](../vsto/how-to-programmatically-open-workbooks.md)

- [Nasıl: Çalışma kitaplarını program aracılığıyla kaydetme.](../vsto/how-to-programmatically-save-workbooks.md)

- [Nasıl: Çalışma kitaplarını program aracılığıyla kapatma.](../vsto/how-to-programmatically-close-workbooks.md)

- [Nasıllı: Çalışma kitaplarında program aracılığıyla yeni çalışma sayfaları ekleme.](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)

- [Nasıl olur: Çalışma sayfalarını program aracılığıyla gizleme.](../vsto/how-to-programmatically-hide-worksheets.md)

- [Nasıllı: Çalışma kitaplarında program aracılığıyla çalışma sayfalarını taşıma.](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)

- [Nasıl olur: Çalışma kitaplarını program aracılığıyla koruma.](../vsto/how-to-programmatically-protect-workbooks.md)

- [Nasıl ekleyebilirsiniz: Kodda program aracılığıyla çalışma sayfası aralıklarını ifade etmek.](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md)

- [Nasıl yapılır: Çalışma kitaplarında aralıklara program aracılığıyla stil uygulama.](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)

- [Nasıl kullanılır: Seçilen hücreleri içeren çalışma sayfası satırlarında biçimlendirmeyi program aracılığıyla değiştirme.](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)

- [Nasıl ekleyebilirsiniz: Çalışma sayfası aralıklarında program aracılığıyla metin arama.](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md)

- [Nasıl olur: Çalışma sayfalarını program aracılığıyla yazdırma.](../vsto/how-to-programmatically-print-worksheets.md)

- [Nasıl yapılır: Program aracılığıyla Excel çalıştırma.](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md)

- [Nasıl kullanılır: Çalışma sayfalarındaki verileri program aracılığıyla sıralama.](../vsto/how-to-programmatically-sort-data-in-worksheets.md)

## <a name="word-automation-tasks"></a><a name="word"></a> Word otomasyonu görevleri

- [Nasıl kullanılır: Program aracılığıyla yeni belgeler oluşturma.](../vsto/how-to-programmatically-create-new-documents.md)

- [Nasıl kullanılır: Mevcut belgeleri program aracılığıyla açma.](../vsto/how-to-programmatically-open-existing-documents.md)

- [Nasıl kullanılır: Belgeleri program aracılığıyla kaydetme.](../vsto/how-to-programmatically-save-documents.md)

- [Nasıl kullanılır: Belgeleri program aracılığıyla kapatma.](../vsto/how-to-programmatically-close-documents.md)

- [Nasıl kullanılır: Word belgelerine program aracılığıyla metin ekleme.](../vsto/how-to-programmatically-insert-text-into-word-documents.md)

- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla tanımlama ve seçme.](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)

- [Nasıl kullanılır: Word belgelerde aralıkları program aracılığıyla sıfırlama.](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)

- [Nasıl kullanılır: Belgelerde metni program aracılığıyla biçimlendirme.](../vsto/how-to-programmatically-format-text-in-documents.md)

- [Nasıl kullanılır: Word belgelerine XMLNode denetimleri ekleme.](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)

- [Nasıl güncelleştirmesi: Yer işareti metnini program aracılığıyla güncelleştirme.](../vsto/how-to-programmatically-update-bookmark-text.md)

- [Nasıl kullanılır: Belgelerde program aracılığıyla metin arama ve değiştirme.](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)

- [Nasıl kullanılır: Belgeleri program aracılığıyla yazdırma.](../vsto/how-to-programmatically-print-documents.md)

- [Nasıl: Program aracılığıyla Word tabloları oluşturma.](../vsto/how-to-programmatically-create-word-tables.md)

- [Nasıl kullanılır: Word tablolarına program aracılığıyla satır ve sütun ekleme.](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)

- [Nasıl kullanılır: Belgelerde program aracılığıyla karakterleri sayma.](../vsto/how-to-programmatically-count-characters-in-documents.md)

## <a name="data-tasks"></a><a name="data"></a> Veri görevleri

### <a name="data-bound-controls"></a>Veriye bağlı denetimler

- [Nasıl kullanılır: Çalışma sayfalarını veritabanındaki verilerle doldurmak.](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Nasıl kullanılır: Belgeleri veritabanındaki verilerle doldurmak.](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Nasıl kullanılır: Belgeleri hizmetlerden verilerle doldurmak.](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak.](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Nasıl kullanılır: Belgeleri veritabanındaki verilerle doldurmak.](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Nasıl kullanılır: Belgeleri hizmetlerden verilerle doldurmak.](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Nasıl kullanılır: Bir veri kaynağını bir konak denetiminden verilerle güncelleştirme.](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)

### <a name="cached-data-in-document-level-solutions"></a>Belge düzeyi çözümlerde önbelleğe alınan veriler

- [Nasıl kullanılır: Verileri çevrimdışı veya bir sunucuda kullanmak üzere önbelleğe alın.](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)

- [Nasıl kullanılır: Bir veri kaynağını program aracılığıyla bir veri Office önbelleğe alın.](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)

- [Nasıl kullanılır: Parola korumalı bir belgede verileri önbelleğe alın.](../vsto/how-to-cache-data-in-a-password-protected-document.md)

### <a name="custom-xml-data"></a>Özel XML verileri

- [Nasıl yapılır: Belge düzeyi özelleştirmelerine özel XML parçaları ekleme.](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)

- [Nasıl kullanılır: Eklentilerini kullanarak belgelere VSTO XML bölümleri ekleme.](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Sunucu tarafı belge yönetimi görevleri

- [Nasıl yapabilirsiniz: Belgelerden yönetilen kod uzantılarını kaldırma.](../vsto/how-to-remove-managed-code-extensions-from-documents.md)

- [Nasıl kullanılır: Belgelere yönetilen kod uzantıları ekleme.](../vsto/how-to-attach-managed-code-extensions-to-documents.md)

## <a name="security-tasks"></a><a name="security"></a> Güvenlik görevleri

- [Nasıllı: Office imzalar.](../vsto/how-to-sign-office-solutions.md)

## <a name="deployment-tasks"></a><a name="deployment"></a> Dağıtım görevleri

- [nasıl yapılır: ClickOnce kullanarak Office çözümünü yayımlama](/previous-versions/bb386095(v=vs.110)).

- [nasıl yapılır: ClickOnce kullanarak SharePoint sunucusuna belge düzeyinde Office çözümü yayımlama](/previous-versions/bb608595(v=vs.110)).

- [nasıl yapılır: ClickOnce Office çözümü yüklemesi](/previous-versions/bb608592(v=vs.110)).

- [nasıl yapılır: Office çözümleri çalıştırmak için son kullanıcı bilgisayarlarına önkoşulları yükler](/previous-versions/bb608608(v=vs.110)).

- [nasıl yapılır: Office çözümlerin dağıtımı için ııs 'i hazırlama](/previous-versions/bb608629(v=vs.110)).

- [nasıl yapılır: dağıtılan Office çözümlerini güncelleştirme](/previous-versions/bb157871(v=vs.110)).

- [nasıl yapılır: Office çözümünün yükleme yolunu değiştirme](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio &#40;Office geliştirmeye başlayın&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office uygulama ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)