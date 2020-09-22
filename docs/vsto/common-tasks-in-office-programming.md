---
title: Office programlamada ortak görevler
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c82b4dec0c92f19933b045040ed0f1fcecb5b10b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809865"
---
# <a name="common-tasks-in-office-programming"></a>Office programlamada ortak görevler
  Bu konu, Visual Studio kullanarak Office çözümlerini programlamaya yönelik aşağıdaki yaygın soruların yanıtlarını bulmanıza yardımcı olmak için tasarlanmıştır.

- [Kurulum ve genel görevler](#projects).

- [Kullanıcı arabirimi özelleştirme görevleri](#ui).

- [Excel otomasyon görevleri](#excel).

- [Word otomasyon görevleri](#word).

- [Veri görevleri](#data).

- [Sunucu tarafı belge yönetimi görevleri](#server).

- [Güvenlik görevleri](#security).

- [Dağıtım görevleri](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Kurulum ve genel görevler

- [Nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Nasıl yapılır: Office çözümlerini yükseltme](/previous-versions/4bez6837(v=vs.140)).

- [Nasıl yapılır: Office birincil birlikte çalışma derlemelerini yüklemek](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [Nasıl yapılır: birincil birlikte çalışma Derlemeleriyle Office uygulamalarını hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [Nasıl yapılır: Office projelerinde olay Işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Nasıl yapılır: kod çalıştırmadan Office çözümlerini açma](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Nasıl yapılır: bir Office çözümü için yapılandırma bilgilerini ayarlama](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Kullanıcı arabirimi özelleştirme görevleri

### <a name="controls-on-documents-and-worksheets"></a>Belge ve çalışma sayfalarındaki denetimler

- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Nasıl yapılır: Office belgelerine Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Nasıl yapılır: Word belgelerine yer işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerde görev bölmeleri

- [Nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>VSTO Eklentilerindeki görev bölmeleri

- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Şerit özelleştirmeleri

- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md).

- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Nasıl yapılır: Şerit Tasarımcısından ŞERIT XML 'Ine şerit dışa aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Outlook form bölgeleri

- [Nasıl yapılır: Outlook eklenti projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Nasıl yapılır: Outlook 'un form bölgesini görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Özel menüler

- [Nasıl yapılır: Kısayol menülerine komut ekleme](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Excel otomasyon görevleri

- [Nasıl yapılır: çalışma sayfası hücresinde program aracılığıyla bir dizeyi görüntüleme](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Nasıl yapılır: program aracılığıyla yeni çalışma kitapları oluşturma](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını açma](../vsto/how-to-programmatically-open-workbooks.md).

- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kaydetme](../vsto/how-to-programmatically-save-workbooks.md).

- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını kapatma](../vsto/how-to-programmatically-close-workbooks.md).

- [Nasıl yapılır: program aracılığıyla çalışma kitaplarına yeni çalışma sayfaları ekleme](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Nasıl yapılır: çalışma sayfalarını program aracılığıyla gizleme](../vsto/how-to-programmatically-hide-worksheets.md).

- [Nasıl yapılır: çalışma sayfalarını program aracılığıyla çalışma kitapları içinde taşıma](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Nasıl yapılır: program aracılığıyla çalışma kitaplarını koruma](../vsto/how-to-programmatically-protect-workbooks.md).

- [Nasıl yapılır: koddaki çalışma sayfası aralıklarına program aracılığıyla başvurma](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Nasıl yapılır: program aracılığıyla çalışma kitaplarındaki aralıklara stil uygulama](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Nasıl yapılır: seçili hücreleri içeren çalışma sayfası satırlarında program aracılığıyla biçimlendirmeyi değiştirme](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- [Nasıl yapılır: çalışma sayfası aralıklarında program aracılığıyla metin arama](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Nasıl yapılır: program aracılığıyla çalışma sayfalarını yazdırma](../vsto/how-to-programmatically-print-worksheets.md).

- [Nasıl yapılır: program aracılığıyla Excel hesaplamalarını çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Nasıl yapılır: çalışma sayfalarındaki verileri program aracılığıyla sıralama](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Word otomasyon görevleri

- [Nasıl yapılır: program aracılığıyla yeni belgeler oluşturma](../vsto/how-to-programmatically-create-new-documents.md).

- [Nasıl yapılır: program aracılığıyla varolan belgeleri açma](../vsto/how-to-programmatically-open-existing-documents.md).

- [Nasıl yapılır: program aracılığıyla belgeleri kaydetme](../vsto/how-to-programmatically-save-documents.md).

- [Nasıl yapılır: program aracılığıyla belgeleri kapatma](../vsto/how-to-programmatically-close-documents.md).

- [Nasıl yapılır: program aracılığıyla Word belgelerine metin ekleme](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Nasıl yapılır: belgelerde aralıkları program aracılığıyla tanımlama ve seçme](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- [Nasıl yapılır: Word belgelerinde aralıkları program aracılığıyla sıfırlama](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Nasıl yapılır: belgelerde metni program aracılığıyla biçimlendirme](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Nasıl yapılır: Word belgelerine XmlNode denetimleri ekleme](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Nasıl yapılır: yer işareti metnini program aracılığıyla güncelleştirme](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Nasıl yapılır: belgelerde metni program aracılığıyla arama ve değiştirme](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Nasıl yapılır: program aracılığıyla belgeleri yazdırma](../vsto/how-to-programmatically-print-documents.md).

- [Nasıl yapılır: program aracılığıyla Word tabloları oluşturma](../vsto/how-to-programmatically-create-word-tables.md).

- [Nasıl yapılır: Word tablolarına program aracılığıyla satır ve sütun ekleme](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Nasıl yapılır: belgelerdeki karakterleri program aracılığıyla sayma](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data-tasks"></a><a name="data"></a> Veri görevleri

### <a name="data-bound-controls"></a>Veri bağlantılı denetimler

- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Belge düzeyi çözümlerinde önbelleğe alınmış veriler

- [Nasıl yapılır: çevrimdışı veya bir sunucuda kullanmak üzere verileri önbelleğe alma](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Özel XML verileri

- [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Nasıl yapılır: VSTO Eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Sunucu tarafı belge yönetimi görevleri

- [Nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Nasıl yapılır: belgelere yönetilen kod uzantıları iliştirme](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Güvenlik görevleri

- [Nasıl yapılır: Office çözümlerini imzalama](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Dağıtım görevleri

- [Nasıl yapılır: ClickOnce kullanarak bir Office çözümünü yayımlama](/previous-versions/bb386095(v=vs.110)).

- [Nasıl yapılır: ClickOnce kullanarak belge düzeyi Office çözümünü SharePoint sunucusuna yayımlama](/previous-versions/bb608595(v=vs.110)).

- [Nasıl yapılır: ClickOnce Office çözümünü yüklemek](/previous-versions/bb608592(v=vs.110)).

- [Nasıl yapılır: Office çözümlerini çalıştırmak için son kullanıcı bilgisayarlarına önkoşulları yükler](/previous-versions/bb608608(v=vs.110)).

- [Nasıl yapılır: Office çözümlerini dağıtmak IÇIN IIS 'ı hazırlama](/previous-versions/bb608629(v=vs.110)).

- [Nasıl yapılır: dağıtılan Office çözümlerini güncelleştirme](/previous-versions/bb157871(v=vs.110)).

- [Nasıl yapılır: bir Office çözümünün yükleme yolunu değiştirme](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio 'da Office geliştirme &#40;kullanmaya başlama&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office uygulaması ve proje türü tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md)
- [Office geliştirme örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)