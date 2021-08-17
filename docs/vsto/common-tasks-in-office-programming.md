---
title: Office programlamada ortak görevler
description: Microsoft Office Word veya Office Excel nesne modelini kullanmak zorunda kalmadan belge düzeyi özelleştirmesindeki verilere karşı nasıl programlama yapabileceğinizi öğrenin.
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
ms.openlocfilehash: e7282fbd105491edb0aac45e116d10da5abf3d1ca77f16a75ae63d6b8c863f04
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424469"
---
# <a name="common-tasks-in-office-programming"></a>Office programlamada ortak görevler
  bu konu, Visual Studio kullanarak Office çözümlerin programlanması hakkında aşağıdaki yaygın soruların yanıtlarını bulmanıza yardımcı olmak için tasarlanmıştır.

- [Kurulum ve genel görevler](#projects).

- [Kullanıcı arabirimi özelleştirme görevleri](#ui).

- [otomasyon görevlerini Excel](#excel).

- [Word otomasyon görevleri](#word).

- [Veri görevleri](#data).

- [Sunucu tarafı belge yönetimi görevleri](#server).

- [Güvenlik görevleri](#security).

- [Dağıtım görevleri](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Kurulum ve genel görevler

- [nasıl yapılır: Visual Studio Office projeler oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [nasıl yapılır: Office çözümlerini yükseltme](/previous-versions/4bez6837(v=vs.140)).

- [nasıl yapılır: birincil birlikte çalışma derlemelerini Office yüklemesi](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [nasıl yapılır: birincil birlikte çalışma bütünleştirilmiş kodları aracılığıyla Office uygulamaları hedefleme](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [nasıl yapılır: Office projelerinde olay işleyicileri oluşturma](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [nasıl yapılır: kod çalıştırmadan Office çözümleri açma](../vsto/how-to-open-office-solutions-without-running-code.md).

- [nasıl yapılır: Office çözümü için yapılandırma bilgilerini ayarlama](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Nasıl yapılır: eklenti Kullanıcı arayüzü hatalarını gösterme](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Kullanıcı arabirimi özelleştirme görevleri

### <a name="controls-on-documents-and-worksheets"></a>Belge ve çalışma sayfalarındaki denetimler

- [nasıl yapılır: Office belgelere Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Nasıl yapılır: çalışma sayfalarına NamedRange denetimleri ekleme](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Nasıl yapılır: çalışma sayfalarına ListObject denetimleri ekleme](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [nasıl yapılır: Office belgelere Windows Forms denetimleri ekleme](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Nasıl yapılır: Word belgelerine yer işareti denetimleri ekleme](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Belge düzeyi özelleştirmelerde görev bölmeleri

- [nasıl yapılır: Word belgelerine veya Excel çalışma kitaplarına eylemler bölmesi ekleme](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>VSTO eklentilerdeki görev bölmeleri

- [Nasıl yapılır: uygulamaya özel görev bölmesi ekleme](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Şerit özelleştirmeleri

- [Nasıl yapılır: Şeriti özelleştirmeye başlama](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Nasıl yapılır: Şeritteki sekmenin konumunu değiştirme](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Nasıl yapılır: yerleşik bir sekmeyi özelleştirme](../vsto/how-to-customize-a-built-in-tab.md).

- [Nasıl yapılır: Backstage görünümüne denetimler ekleme](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Nasıl yapılır: Şerit Tasarımcısından ŞERIT XML 'Ine şerit dışa aktarma](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Outlook form bölgeleri

- [nasıl yapılır: Outlook eklentisi projesine form bölgesi ekleme](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [nasıl yapılır: Outlook form bölgesi görüntülemesini engelleme](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Özel menüler

- [Nasıl yapılır: Kısayol menülerine komut ekleme](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a>otomasyon görevlerini Excel

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

- [nasıl yapılır: program aracılığıyla Excel hesaplamaları çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

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

- [nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Özel XML verileri

- [Nasıl yapılır: belge düzeyi özelleştirmelerine özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [nasıl yapılır: VSTO eklentilerini kullanarak belgelere özel XML bölümleri ekleme](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Sunucu tarafı belge yönetimi görevleri

- [Nasıl yapılır: belgelerden yönetilen kod uzantılarını kaldırma](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Nasıl yapılır: belgelere yönetilen kod uzantıları iliştirme](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Güvenlik görevleri

- [nasıl yapılır: Office çözümlerini imzalama](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Dağıtım görevleri

- [Nasıl Office: ClickOnce](/previous-versions/bb386095(v=vs.110))kullanarak bir ClickOnce.

- [Nasıl kullanılır: ClickOnce kullanarak Office düzeyinde bir SharePoint sunucusuna belge düzeyi ClickOnce.](/previous-versions/bb608595(v=vs.110))

- [Nasıl kurulur: Bir ClickOnce Office yükleyin.](/previous-versions/bb608592(v=vs.110))

- [Nasıl kurulur: Son kullanıcı bilgisayarlarına önkoşulları yük Office çalıştırın.](/previous-versions/bb608608(v=vs.110))

- [Nasıl olur: Iis'yi, çözümlerini Office hazırlama.](/previous-versions/bb608629(v=vs.110))

- [Nasıl güncelleştirmesi: Dağıtılan Office güncelleştirme.](/previous-versions/bb157871(v=vs.110))

- [Nasıl olur: Bir Office çözümünün yükleme yolunu değiştirme.](/previous-versions/bb608626(v=vs.110))

## <a name="see-also"></a>Ayrıca bkz.
- [Kullanmaya başlayın &#40;Office geliştirme Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Uygulama ve Office tarafından kullanılabilen özellikler](../vsto/features-available-by-office-application-and-project-type.md)
- [Office örnekleri ve izlenecek yollar](../vsto/office-development-samples-and-walkthroughs.md)