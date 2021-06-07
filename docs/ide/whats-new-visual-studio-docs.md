---
title: "Visual Studio belgeleri: 2021 Mayıs 'ta yenilikler"
titleSuffix: ''
description: Mayıs 2021 için Visual Studio docs 'daki yenilikler.
ms.date: 06/01/2021
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: aaba340bd6e7136f8d629077fa2daec657135e3c
ms.sourcegitcommit: fc05a763b59e212c86350d117a1900a1f2686ec8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2021
ms.locfileid: "111551273"
---
# <a name="visual-studio-docs-whats-new-for-may-2021"></a>Visual Studio belgeleri: 2021 Mayıs 'ta yenilikler

Mayıs 2021 için Visual Studio docs 'daki yenilikler 'e hoş geldiniz. Bu makalede, bu süre boyunca docs 'ta yapılan önemli değişikliklerden bazıları listelenir. Önceki aylarda nelerin yeni olduğu hakkında daha fazla bilgi için bkz. yenilikler [geçmişi](#whats-new-history) bölümü.

## <a name="code-quality"></a>Kod kalitesi

**Yeni makaleler**

- [Kod ölçümleri-döngüsel karmaşıklığı](../code-quality/code-metrics-cyclomatic-complexity.md) -döngüsel karmaşıklık ve devralma derinliğine yönelik kod ölçümleri güncelleştirmeleri
- [Kod ölçümleri-devralım (DIT)](../code-quality/code-metrics-depth-of-inheritance.md) -döngüsel karmaşıklığı ve devralma derinliğine yönelik kod ölçümleri güncelleştirmeleri
- [Kod ANALIZI SSS](../code-quality/analyzers-faq.yml) -FAQ.MD, yıml 'ye dönüştürüldü
- [Eski FxCop ve .net Çözümleyicileri hakkında sık sorulan sorular](../code-quality/net-analyzers-faq.yml) -FAQ.MD, yıml 'ye dönüştürüldü

**Güncelleştirilmiş makaleler**

- [Kod Analizi Ihlallerini gösterme](../code-quality/in-source-suppression-overview.md) -CA kurallarının gizlemesi sırasında belgeleri yeniden düzenleme

## <a name="containers"></a>Kapsayıcılar

**Yeni makaleler**

- [Docker Compose (Önizleme) için başlatma profillerini yönetme](../containers/launch-profiles.md) -kapsayıcı araçları-başlatma ayarları

## <a name="debugger"></a>Hata Ayıklayıcısı

**Yeni makaleler**

- [Visual Studio 'da anlık görüntü hata ayıklaması Için sık sorulan sorular](../debugger/debug-live-azure-apps-faq.yml) -FAQ.MD, yıml 'ye dönüştürüldü
- [SSS-Visual Studio 'da ihtiyacınız olan hata ayıklama özelliğini bulma](../debugger/find-your-debugging-task.yml) -FAQ.MD, yıml 'ye dönüştürüldü

**Güncelleştirilmiş makaleler**

- [Veri kesme noktası hatalarını giderme](../debugger/troubleshoot-data-breakpoint-errors.md) -güncelleştirme sorunlarını giderme veri kesme hataları belge

## <a name="ide"></a>IDE

**Güncelleştirilmiş makaleler**

- [/ResetSettings (devenv.exe)](./reference/resetsettings-devenv-exe.md) -diğer düzeltmeler
- [Hızlı başlangıç: Visual Studio 'da önerilen düzenlemelerle ilk Node.js uygulamanızı oluşturma](./quickstart-nodejs.md)

## <a name="install"></a>Yükleme

**Güncelleştirilmiş makaleler**

- [En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme](../install/update-minimal-layout.md)
  - Mini düzen belgelerine birden çok ürün örneği ekleme
  - VS 2017 belgelerinden ve tüm örneklerde--ProductID öğesinin kaldırılmasını yansıtır
  - En az Allayout belgelerinden '--ProductIDs ' seçeneğinin kaldırılmasını yansıtma
- [Visual Studio iş yüklerini, bileşenlerini ve dil paketlerini değiştirme](../install/modify-visual-studio.md) -performans yönergelerini kolaylaştırma

## <a name="msbuild"></a>MSBuild

**Yeni makaleler**

- [MSB8006: ' proje-adı. vcxproj ' projesi için Platform geçersiz.](../msbuild/errors/msb8006.md) -MSB8xxx F1 içeriğini güncelleştirme
- [MSB8013: Bu proje, belirtilen yapılandırma ve platform bileşimini içermiyor.](../msbuild/errors/msb8013.md) -MSB8xxx F1 içeriğini güncelleştirme
- [MSB8027: filename adına sahip Iki veya daha fazla dosya aynı konuma çıkış üretir.](../msbuild/errors/msb8027.md) -MSB8xxx F1 içeriğini güncelleştirme
- [MSB8037: Masaüstü C++ uygulamaları için Windows SDK sürümü bulunamadı.](../msbuild/errors/msb8037.md) -MSB8xxx F1 içeriğini güncelleştirme
- [MSB8042: Bu proje için Spectre azaltmaları olan ATL veya MFC kitaplıkları gereklidir.](../msbuild/errors/msb8042.md) -MSB8xxx F1 içeriğini güncelleştirme
- [MSB3721: ' komut ' komutuna ' Error-Code '](../msbuild/errors/msb3721.md) -MSBuild hata sayfaları ile çıkıldı
- [MSB3821: ' Path ' dosyası, Internet veya kısıtlanmış bölgede olduğu veya dosya-MSBuild hata sayfalarında Web 'in işaretine sahip olduğundan işlenemedi](../msbuild/errors/msb3821.md)

**Güncelleştirilmiş makaleler**

- [MSBuild koşulları](../msbuild/msbuild-conditions.md) -MSBuild sürüm karşılaştırmaları
- [Özellik işlevleri](../msbuild/property-functions.md) -MSBuild sürüm karşılaştırmaları

## <a name="python"></a>Python

**Güncelleştirilmiş makaleler**

- [2. Adım: görünümler ve sayfa şablonlarıyla bir Docgo uygulaması oluşturma](../python/learn-django-in-visual-studio-step-02-create-an-app.md) -ayrılmış Visual Studio 2017 ve 2019 bilgileri
- [Python Için C++ uzantısı oluşturma](../python/working-with-c-cpp-python-in-visual-studio.md) -makale incelendi ve güncelleştirildi

## <a name="test"></a>Test etme

**Yeni makaleler**

- [Live Unit Testing sık sorulan sorular](../test/live-unit-testing-faq.yml) -FAQ.MD, yıml 'ye dönüştürüldü

## <a name="xaml-tools"></a>XAML araçları

**Yeni makaleler**

- Visual Studio ile eklenen XAML tasarım zamanı örnek veri belgeleri [içindeki XAML Tasarımcısı tasarım zamanı örnek verilerini kullanın](../xaml-tools/xaml-design-time-sample-data.md)

## <a name="community-contributors-in-may"></a>Mayıs 'ta topluluk katkı sağlayanlar

Aşağıdaki kişiler bu süre boyunca Visual Studio belgelerine katkıda bulunanlar. Teşekkür ederiz! Yenilikler [giriş sayfasında](index.yml)"katılım alma" başlığı altında yer alan bağlantıları izleyerek nasıl katkıda bulunabileceğinizi öğrenin.

- [7keskin9](https://github.com/7sharp9) -Dadve Thomas (1)
- [Hemi-hafreton](https://github.com/heath-hamilton) -hem hafreton (1)

## <a name="whats-new-history"></a>Yenilikler geçmişi

### <a name="april-2021"></a>2021 Nisan

#### <a name="azure"></a>Azure

**Güncelleştirilmiş makaleler**

- [Visual Studio 'da Cloud Services (genişletilmiş destek) oluşturma ve dağıtma](../azure/cloud-services-extended-support.md) -Cloud Services (genişletilmiş destek)-GA değişiklikleri

#### <a name="containers"></a>Kapsayıcılar

**Yeni makaleler**

- Kubernetes Köprüsü için [Kubernetes tarafından yönetilen kimliği olan köprü ile yönetilen kimlik kullan](../containers/managed-identity.md)

**Güncelleştirilmiş makaleler**

- [Docker Compose yapı özellikleri](../containers/docker-compose-properties.md) -özellik eklemeleri oluşturma
- [Visual Studio 'da Kapsayıcılı uygulamalar nasıl oluşturulur](../containers/container-build.md) -LTS için güncelleştirme

#### <a name="debugger"></a>Hata Ayıklayıcısı

**Yeni makaleler**

- [IDiaSymbol:: get_framePadOffset](../debugger/debug-interface-access/idiasymbol-get-framepadoffset.md) -DIA SDK eklemeleri
- [IDiaSymbol:: get_framePadSize](../debugger/debug-interface-access/idiasymbol-get-framepadsize.md) -DIA SDK eklemeleri
- [IDiaSymbol:: get_isRTCs](../debugger/debug-interface-access/idiasymbol-get-isrtcs.md) -DIA SDK eklemeleri
- [.Net tanılama Çözümleyicileri ile yönetilen bellek dökümünden hata ayıklama](../debugger/how-to-debug-managed-memory-dump.md) -vs bellek dökümü Çözümleyicileri

**Güncelleştirilmiş makaleler**

- [Visual Studio hata ayıklayıcısındaki döküm dosyaları](../debugger/using-dump-files.md) -vs bellek dökümü Çözümleyicileri
- [Mutlak yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md) -yeni başlayanlar kılavuzu 'na vb ekleme

#### <a name="get-started"></a>başlarken

**Güncelleştirilmiş makaleler**

- [Öğretici: basit bir C# konsol uygulamasını genişletme](../get-started/csharp/tutorial-console-part-2.md) -adımları belirginleştirme ve tam kod ekleme baryürüme öğreticisini Genişlet

#### <a name="ide"></a>IDE

**Güncelleştirilmiş makaleler**

- [F1 Yardımı: eşleşme bulunamadı](./not-in-toc/default.md) -güncelleştirme default.MD
- [Geliştirici komut istemi ve geliştirici PowerShell](./reference/command-prompt-powershell.md) -içerik performansı geliştirmeleri
- [Takım Gezgini projelere bağlanma](./connect-team-project.md) -"Takım Gezgini projelere Bağlan" sayfasında vs 2019 sürümünü gözden geçirin

#### <a name="install"></a>Yükleme

**Güncelleştirilmiş makaleler**

- [Çevrimdışı Visual Studio yüklemesi oluşturma](../install/create-an-offline-installation-of-visual-studio.md) -güncelleştirme Use-Command-Line-Parameters-to-install-Visual-Studio.MD
- [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](../install/use-command-line-parameters-to-install-visual-studio.md) -güncelleştirme Use-Command-Line-Parameters-to-install-Visual-Studio.MD
- [Visual Studio 'nun kurumsal dağıtımları için varsayılanlar ayarlama](../install/set-defaults-for-enterprise-deployments.md) -yönetici güncelleştirmeleriyle ilgili hataları giderme ve kurumsal dağıtımlar varsayılanlarından gereksiz desteklenmediği uyarısıyla kaldırma
- [Visual Studio numaraları ve yayın tarihleri -](../install/visual-studio-build-numbers-and-release-dates.md) Patch Tuesday güncelleştirmeleri ekleme
- [Microsoft Endpoint Configuration Manager kullanan yönetici güncelleştirmelerini](../install/applying-administrator-updates.md) uygulama - Yönetici güncelleştirmeleri
- [Ağ tabanlı dağıtımlarda güncelleştirmeleri Visual Studio -](../install/controlling-updates-to-visual-studio-deployments.md) Yönetici güncelleştirmeleri
- Visual Studio ağ [yüklemesi](../install/create-a-network-installation-of-visual-studio.md) oluşturma - Yönetici güncelleştirmeleri
- [Microsoft Endpoint Configuration Manager ile Visual Studio güncelleştirmelerini etkinleştirme](../install/enabling-administrator-updates.md) - Yönetici güncelleştirmeleri
- [Örnek algılama ve yönetme Visual Studio araçları](../install/tools-for-managing-visual-studio-instances.md) - Yönetici güncelleştirmeleri
- [Güncelleştirme Visual Studio en son sürüme güncelleştirme](../install/update-visual-studio.md) - Yönetici güncelleştirmeleri
- [Visual Studio kılavuzu](../install/visual-studio-administrator-guide.md) - Yönetici güncelleştirmeleri
- [Visual Studio kurumsal kılavuz](../install/visual-studio-enterprise-guide.md) - Yönetici güncelleştirmeleri

#### <a name="msbuild"></a>MSBuild

**Yeni makaleler**

- [MSB8066: 'item-list'](../msbuild/errors/msb8066.md) için özel derlemeden 'hata kodu' koduyla çıkıldı - msb8066 için yeni sayfa taslağı
- [MSB8040: Bu proje için Spectre-mitigated](../msbuild/errors/msb8040.md) kitaplıkları gerekiyor - MSBuild C++ hata iletileri
- [MSB8041: Bu proje için MFC](../msbuild/errors/msb8041.md) Kitaplıkları gerekiyor - MSBuild C++ hata iletileri
- [MSB3277: Çözümlenemedi farklı 'derleme'](../msbuild/errors/msb3277.md) sürümleri arasında çakışmalar bulundu - MSBuild hatası MSB3277

#### <a name="python"></a>Python

**Güncelleştirilmiş makaleler**

- [Python için C++ uzantısı oluşturma](../python/working-with-c-cpp-python-in-visual-studio.md)
  - GH sorunlarını ele almak için küçük güncelleştirmeler
  - Geliştirme working-with-c-cpp-python-in-visual-studio.md

#### <a name="sharepoint"></a>SharePoint

**Güncelleştirilmiş makaleler**

- [Varlıklar arasında ilişki oluşturma](../sharepoint/creating-an-association-between-entities.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Nasıl kullanılır: Özel bir SharePoint düğümünü Sunucu Gezgini](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Nasıl kullanılır: SharePoint proje hizmetini alma](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [SharePoint proje sisteminin uzantılarına veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Kılavuz: Öğe şablonu,](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) bölüm 2 ile özel eylem proje öğesi oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Kılavuz: SharePoint projeleri için özel dağıtım](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) adımı oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Kılavuz: SharePoint uygulama sayfası oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Kılavuz: Proje şablonuyla site sütunu](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md) proje öğesi oluşturma, 2. Bölüm - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Adım adım kılavuz: Tasarımcı kullanarak SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md) için web bölümü oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Adım adım kılavuz: SharePoint için web](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md) bölümü oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6
- [Adım adım kılavuz: Sunucu Gezgini bölümlerini görüntülemek için](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md) genişletme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 6

#### <a name="test"></a>Test etme

**Güncelleştirilmiş makaleler**

- [Kullanmaya başlayın testiyle ilgili bilgi](../test/getting-started-with-unit-testing.md) - Yeni başlayanlar için VB ekleme kılavuzu
- [Kullanmaya başlayın ile Live Unit Testing](../test/live-unit-testing-start.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7

#### <a name="vsto"></a>VSTO

**Güncelleştirilmiş makaleler**

- [Kılavuz: Outlook'ta e-posta iletileriyle](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) özel görev bölmelerini görüntüleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Adım adım kılavuz: Outlook'ta tasarlanmış bir form](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md) bölgesini içeri aktarma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Adım adım kılavuz: Sunucu üzerinde bir çalışma kitabına veri ekleme](../vsto/walkthrough-inserting-data-into-a-workbook-on-a-server.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Adım adım kılavuz: Eylemler bölmesinden belgeye](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) metin ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Adım adım kılavuz: NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md) denetimi olaylarına karşı programla - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Adım adım kılavuz: Sunucu üzerinde bir çalışma](../vsto/walkthrough-retrieving-cached-data-from-a-workbook-on-a-server.md) kitabından önbelleğe alınmış verileri alma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Adım adım kılavuz: Belge düzeyi projesinde](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) basit veri bağlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Kılavuz: VSTO Eklenti Projesinde](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) basit veri bağlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Kılavuz: Özel görev bölmesini Şerit düğmesiyle eşitleme](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Kılavuz: Radyo düğmelerini kullanarak](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) belgedeki grafiği güncelleştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Kılavuz: Radyo Düğmelerini Kullanarak](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) Çalışma Sayfasında Grafiği Güncelleştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Adım adım kılavuz: Çalışma zamanında şeritteki](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) denetimleri güncelleştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 11
- [Office çözümlerini sorunlarını giderme](../vsto/troubleshooting-errors-in-office-solutions.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) Eklentisinde çalışma zamanında belgeye denetim ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: VSTO eklenti](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) projesinde çalışma zamanında çalışma sayfasına denetimler ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: Özel görev bölmesinden bir uygulamayı otomatikleştirme](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: İçerik denetimlerini özel XML bölümlerine bağlama](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: Word eylemleri bölmesindeki](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) denetimlere veri bağlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: Excel eylemleri bölmesindeki](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) denetimlere veri bağlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md) Eklenti projesinde bir hizmetten verilere bağlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: VBA'dan VSTO](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md) Eklentisinde kod çağırma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: Sunucu üzerinde bir](../vsto/walkthrough-changing-cached-data-in-a-workbook-on-a-server.md) çalışma kitabındaki önbelleğe alınmış verileri değiştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: CheckBox denetimlerini kullanarak](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) belge biçimlendirmesini değiştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: CheckBox denetimlerini kullanarak](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) çalışma sayfası biçimlendirmesini değiştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: Windows Formu kullanarak veri toplama](../vsto/walkthrough-collecting-data-using-a-windows-form.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: Belge düzeyi projesinde](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) karmaşık veri bağlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: VSTO Eklenti projesinde karmaşık veri](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) bağlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: Şerit XML kullanarak özel sekme](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: Şerit Tasarımcısını kullanarak özel](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) sekme oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: Önbelleğe alınmış bir veri kümesi](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md) kullanarak ana ayrıntı ilişkisi oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: İçerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Kılavuz: Yer işaretleri için kısayol menüleri oluşturma](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Adım adım kılavuz: Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md) için ilk VSTO Eklentinizi oluşturma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 10
- [Nasıl kullanılır: Word tablolarını belge özellikleriyle program aracılığıyla doldurmak](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Belgeleri program aracılığıyla yazdırma](../vsto/how-to-programmatically-print-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Çalışma sayfalarını program aracılığıyla yazdırma](../vsto/how-to-programmatically-print-worksheets.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Belgeleri ve belgelerin bölümlerini](../vsto/how-to-programmatically-protect-documents-and-parts-of-documents.md) program aracılığıyla koruma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Çalışma kitaplarını program aracılığıyla koruma](../vsto/how-to-programmatically-protect-workbooks.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Word belgelerde aralıkları](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md) program aracılığıyla sıfırlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Aramadan sonra seçimleri program aracılığıyla geri yükleme](../vsto/how-to-programmatically-restore-selections-after-searches.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl yapılır: Program aracılığıyla Excel hesaplamaları çalıştırma](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Belgeleri program aracılığıyla kaydetme](../vsto/how-to-programmatically-save-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Visio belgelerini](../vsto/how-to-programmatically-save-visio-documents.md) program aracılığıyla kaydetme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Çalışma kitaplarını program aracılığıyla kaydetme](../vsto/how-to-programmatically-save-workbooks.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Belgelerde metinleri](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md) program aracılığıyla arama ve değiştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Çalışma sayfası aralıklarında program aracılığıyla Metin](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md) arama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Çalışma sayfalarındaki verileri program aracılığıyla sıralama](../vsto/how-to-programmatically-sort-data-in-worksheets.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Excel aralıklarında](../vsto/how-to-programmatically-store-and-retrieve-date-values-in-excel-ranges.md) tarih değerlerini program aracılığıyla depolama ve alma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Yer işareti metnini program aracılığıyla güncelleştirme](../vsto/how-to-programmatically-update-bookmark-text.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Word'de](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md) yerleşik iletişim kutularını program aracılığıyla kullanma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: İçerik denetimlerini kullanarak belgelerin bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Belge özelliklerinden okuma ve belge özelliklerine yazma](../vsto/how-to-read-from-and-write-to-document-properties.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Yer İşareti denetimlerini](../vsto/how-to-resize-bookmark-controls.md) yeniden boyutlandırma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: ListObject denetimlerini](../vsto/how-to-resize-listobject-controls.md) yeniden boyutlandırma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: NamedRange denetimlerini](../vsto/how-to-resize-namedrange-controls.md) yeniden boyutlandırma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl kullanılır: ListObject](../vsto/how-to-validate-data-when-a-new-row-is-added-to-a-listobject-control.md) denetimine yeni bir satır eklendiği zaman verileri doğrulama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Office çözümlerini geç bağlama](../vsto/late-binding-in-office-solutions.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Office çözümlerinde isteğe bağlı parametreler](../vsto/optional-parameters-in-office-solutions.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Office belgelerde dinamik denetimleri kalıcı](../vsto/persisting-dynamic-controls-in-office-documents.md) olarak taşıma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 9
- [Nasıl yapılır: Excel aralıklarında](../vsto/how-to-programmatically-apply-color-to-excel-ranges.md) program aracılığıyla renk uygulama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl yapılır: Çalışma kitaplarında aralıklara](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md) program aracılığıyla stil uygulama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Office belgesinde](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md) program aracılığıyla bir veri kaynağını önbelleğe ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Seçilen hücreleri içeren](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md) çalışma sayfası satırlarında biçimlendirmeyi program aracılığıyla değiştirme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Belgeleri program aracılığıyla kapatma](../vsto/how-to-programmatically-close-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Çalışma kitaplarını program aracılığıyla kapatma](../vsto/how-to-programmatically-close-workbooks.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Belgelerde aralıkları](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md) veya seçimleri program aracılığıyla daraltın - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Belgelerde program aracılığıyla karakter sayısı](../vsto/how-to-programmatically-count-characters-in-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Program aracılığıyla yeni Visio belgeleri oluşturma](../vsto/how-to-programmatically-create-new-visio-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Program aracılığıyla Word tabloları oluşturma](../vsto/how-to-programmatically-create-word-tables.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md) tanımlama ve seçme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Baskı Önizleme'de belgeleri](../vsto/how-to-programmatically-display-documents-in-print-preview.md) program aracılığıyla görüntüleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Aralık oluştururken paragraf işaretlerini](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md) program aracılığıyla dışlama - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Belgelerde aralıkları program aracılığıyla genişletme](../vsto/how-to-programmatically-extend-ranges-in-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Belgelerde metni program aracılığıyla gizleme](../vsto/how-to-programmatically-hide-text-in-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Word belgelerine program aracılığıyla](../vsto/how-to-programmatically-insert-text-into-word-documents.md) metin ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Nasıl kullanılır: Belgelerde bulunan öğelerde](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md) program aracılığıyla döngüye ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 8
- [Çalışma zamanında form bölgelerine erişme](../vsto/accessing-a-form-region-at-run-time.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Çalışma zamanında Şerit'e erişme](../vsto/accessing-the-ribbon-at-run-time.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Eylemler bölmesine genel](../vsto/actions-pane-overview.md) bakış - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Çalışma zamanında VSTO eklentilerine Word](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md) belgelerini ve Excel çalışma kitaplarını genişletme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Word Belgelerine veya Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) Çalışma Kitaplarında Eylemler Bölmesi Ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Word belgelerine Yer](../vsto/how-to-add-bookmark-controls-to-word-documents.md) İşareti denetimleri ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Word belgelerine İçerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: VSTO Eklentilerini](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md) kullanarak belgelere özel XML bölümleri ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: ListObject denetimlerini verilerle](../vsto/how-to-fill-listobject-controls-with-data.md) doldurma - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Eylemler bölmeleri üzerinde denetim düzenini yönetme](../vsto/how-to-manage-control-layout-on-actions-panes.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: ListObject sütunlarını verilerle eşleme](../vsto/how-to-map-listobject-columns-to-data.md) - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Program aracılığıyla çalışma sayfası açıklamalarını ekleme](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md) ve silme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Belgelere program aracılığıyla üst](../vsto/how-to-programmatically-add-headers-and-footers-to-documents.md) bilgiler ve alt bilgiler ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Belgelere program aracılığıyla resim](../vsto/how-to-programmatically-add-pictures-and-word-art-to-documents.md) ve Word Art ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7
- [Nasıl kullanılır: Word tablolarına](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md) program aracılığıyla satır ve sütun ekleme - Örnek dosyaları taşıma ve kod başvurularını güncelleştirme (bölüm 1) - 7

#### <a name="xaml-tools"></a>XAML Araçları

**Güncelleştirilmiş makaleler**

- [Tasarım Zamanı Verilerini XAML Tasarımcısı'de Visual Studio](../xaml-tools/xaml-designtime-data.md) - Listview'lar için UWP Örneği eklendi

### <a name="march-2021"></a>Mart 2021

#### <a name="code-quality"></a>Kod kalitesi

**Güncelleştirilmiş makaleler**

- [Birinci taraf .NET çözümleyicilerini etkinleştirme veya yükleme](../code-quality/install-net-analyzers.md) - GitHub sorun düzeltmeleri

#### <a name="containers"></a>Kapsayıcılar

**Güncelleştirilmiş makaleler**

- [Uygulama Bridge to Kubernetes](../containers/bridge-to-kubernetes.md) - Bridge to Kubernetes: .NET todo-app örneğini kullanma
- [Docker Compose özellikleri ekleme](../containers/docker-compose-properties.md) - ComposeProjectName Ekleme
- [Bridge to Kubernetes nasıl çalışır?](../containers/overview-bridge-to-kubernetes.md) Bridge to Kubernetes: Güncelleştirme Sınırlamaları bölümü
- [Öğretici: Docker Compose](../containers/tutorial-multicontainer.md) ile çok kapsayıcılı uygulama oluşturma - Kapsayıcı Araçları çok kapsayıcılı öğretici: görüntü bağlantısını düzeltme

#### <a name="debugger"></a>Hata Ayıklayıcısı

**Güncelleştirilmiş makaleler**

- Nasıl bilinir: Visual Studio'de DLL projesinde hata ayıklama [(C#, C++, Visual Basic, F#)](../debugger/how-to-debug-from-a-dll-project.md) - DLL'den hata ayıklamayı yenileme
- Visual Studio hata ayıklayıcısında sembol (.pdb) ve kaynak dosyaları [belirtme (C#, C++, Visual Basic, F#)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) - DLL'den hata ayıklamayı yenileme
- [C/C++ Onaylamaları](../debugger/c-cpp-assertions.md) - GitHub sorun düzeltmeleri
- [IDiaDataSource::loadDataForExe](../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) - GitHub sorunları çalışıyor
- Visual Studio hata [ayıklayıcısında C++ için biçim belirleyicileri](../debugger/format-specifiers-in-cpp.md) - GitHub sorunları çalışıyor
- [Uzaktan hata ayıklama için Windows Güvenlik Duvarı'nı yapılandırma](../debugger/configure-the-windows-firewall-for-remote-debugging.md) - GitHub sorun düzeltmeleri
- [Uzak IIS ASP.NET Uzaktan Hata Ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) - IIS ve Azure için uzaktan hata ayıklama belgelerde güncelleştirmeler
- [Visual Studio'ASP.NET Uzak IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) Bilgisayarında Uzaktan Hata Ayıklama - IIS ve Azure için uzaktan hata ayıklama belgelerde güncelleştirmeler
- [Visual Studio'de IIS'de IIS'de](../debugger/remote-debugging-azure.md) Uzaktan Hata Ayıklama ASP.NET Çekirdek - IIS ve Azure için uzaktan hata ayıklama belgelerde yapılan güncelleştirmeler

#### <a name="deployment"></a>Dağıtım

**Güncelleştirilmiş makaleler**

- [Nasıl yapabilirsiniz: Görsel stillerin etkin olduğu bir WPF uygulaması yayımlama](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md) - Geliştirici Komut İstemi ve Geliştirici PowerShell
- [Visual Studio kullanarak bir klasöre](../deployment/quickstart-deploy-to-local-folder.md) uygulama dağıtma - IIS ve Azure için uzaktan hata ayıklama belgelerini güncelleştirmeler

#### <a name="extensibility"></a>Genişletilebilirlik

**Güncelleştirilmiş makaleler**

- [Görsel dil sözlüğü -](../extensibility/ux-guidelines/visual-language-dictionary-for-visual-studio.md) simge işleme hatasını düzeltmek için eksik Markdown köşeli ayraçları ekleme
- [Şablon yükleme sorunlarını giderme](../extensibility/troubleshooting-template-discovery.md) - Geliştirici Komut İstemi Geliştirici PowerShell

#### <a name="get-started"></a>başlarken

**Güncelleştirilmiş makaleler**

- [Öğretici: Bir repodan proje açma](../get-started/tutorial-open-project-from-repo-visual-studio-2019.md)
  - Git güncelleştirme bağlantısının yan yana karşılaştırması ile & Takım Gezgini güncelleştirme
  - Oturum açma bölümüne daha fazla bilgi için oturum açma bağlantıları ekleme
- [Öğretici: Kullanmaya başlayın C# ve ASP.NET Core ile Visual Studio](../get-started/csharp/tutorial-aspnet-core.md) - Güncelleştirme tutorial-aspnet-core.md

#### <a name="ide"></a>IDE

**Yeni makaleler**
- [Kaynak Visual Studio nasıl kolay olur?](../version-control/git-visual-studio-source-control.md) - Kaynak Denetimi Visual Studio yeni oluşturma
- [Geliştirici Komut İstemi ve Geliştirici PowerShell](./reference/command-prompt-powershell.md) - Geliştirici Komut İstemi ve Geliştirici PowerShell
- [Git ve Takım Gezgini](../version-control/git-team-explorer-feature-comparison.md) yan yana karşılaştırma - Yeni Git özellikleri ve yeni Git özelliklerinin Takım Gezgini yan yana karşılaştırma sayfası ekleme

**Güncelleştirilmiş makaleler**

- [Visual Studio tarafından toplanan sistem tarafından oluşturulan günlükler](./diagnostic-data-collection.md) - Güncelleştirme diagnostic-data-collection.md
- [Visual Studio Müşteri Deneyimini Geliştirme Programı](./visual-studio-experience-improvement-program.md) - Güncelleştirme visual-studio-experience-improvement-program.md
- [Proje ve öğe şablonlarını özelleştirme](./customizing-project-and-item-templates.md) - şablonları özelleştirme ve komut satırı kullanma hakkında bağlantılar ekleme
- [Nasıl yapılanlar: Proje şablonları oluşturma](./how-to-create-project-templates.md) - şablonları özelleştirme ve komut satırı kullanma hakkında bağlantılar ekleme
- [Kod düzenleyicisi F1 yardımı](./not-in-toc/default-f1-text-editor.md) - F1 varsayılan sayfaları için bağlantı güncelleştirmeleri
- [F1 yardımı](./not-in-toc/default.md) - F1 varsayılan sayfaları için güncelleştirmeleri bağlama
- [Hızlı Başlangıç: Visual Studio uygulama oluşturmak için Node.js kullanma](./quickstart-nodejs.md) - AngularJS güncelleştirmeleri
- [Yöntem yeniden düzenlemesini ayıklama](./reference/extract-method.md) - Güncelleştirme extract-method.md
- [XAML Tasarımcısı seçenekleri sayfası](./reference/xaml-designer.md) - XAML tasarımcısına yeni eklenen seçenekler hakkında bilgi ekleme
- [Visual Studio 2019'daki yeniler](./whats-new-visual-studio-2019.md)
  - Akıllı Arama Hizmeti bilgileri ekleme
  - Ayrıca Bkz. bağlantısına yeni CSharp 9 bağlantısı ekleme
- [Geliştirici Komut İstemi ve Geliştirici PowerShell](./reference/command-prompt-powershell.md)
  - Özellik başlıklarını güncelleştirme ve ön bilgileri kaldırma bölümü
  - Başlık hiyerarşisini güncelleştirme
  - Geliştirici Komut İstemi ve Geliştirici PowerShell
- [Takım Gezgini'da projelere](./connect-team-project.md) bağlanma - Git güncelleştirme bağlantısının yan yana karşılaştırması ile & Takım Gezgini güncelleştirme
- [Visual Studio'de Git deneyimi](./git-with-visual-studio.md)
  - mevcut Azure DevOps deyimine dosya ekleme
  - Yeni Git özellikleri ve yeni Git özelliklerinin yeni Takım Gezgini karşılaştırma sayfası ekleme
  - -b bağımsız değişkeni git-with-visual-studio.md
- [Visual Studio'da](./default-keyboard-shortcuts-in-visual-studio.md) varsayılan klavye kısayolları - Eksik Kesme Noktası Koşullarını Ayarla klavye kısayolu ekleme
- [Kullanıcı izinleri ve Visual Studio](./user-permissions-and-visual-studio.md) - kısayolda Yönetici izinlerini ayarlama yordamı ekleyin
- [Çalışma zamanlarında Equals ve GetHashCode yöntemi geçersiz kılmaları Visual Studio](./reference/generate-equals-gethashcode-methods.md)
  - ekran görüntüsü boyutunu küçültün ve bir yönergeye küçük düzenleme ekleyin
  - ekran görüntüleriyle eşleştirmeye kod ekleme
- [Visual Studio 'da normal Ifadeler kullanma](./using-regular-expressions-in-visual-studio.md) -hatalı Regex çözme
- Açık klasör geliştirme-Geliştirici Komut İstemi ve geliştirici PowerShell [için derleme ve hata ayıklama görevlerini özelleştirme](./customize-build-and-debug-tasks-in-visual-studio.md)
- [C# geliştiricileri Için Visual Studio üretkenlik Kılavuzu](./csharp-developer-productivity.md) -VS2019 için kod inceleme uzantısı listesini güncelleştirme

#### <a name="install"></a>Yükleme

**Yeni makaleler**
- [Microsoft uç noktası kullanan yönetici güncelleştirmelerini uygulama Configuration Manager](../install/applying-administrator-updates.md) -yönetici güncelleştirmelerini uygulama hakkında yeni içerik oluşturuldu
- [Microsoft uç noktası Ile Visual Studio 'da yönetici güncelleştirmelerini etkinleştirme Configuration Manager](../install/enabling-administrator-updates.md) -yönetici güncelleştirmelerini etkinleştirme hakkında yeni içerik oluşturuldu

**Güncelleştirilmiş makaleler**

- [Visual Studio derleme numaraları ve yayın tarihleri](../install/visual-studio-build-numbers-and-release-dates.md)
  - Visual-studio-build-numbers-and-release-dates.md Güncelleştir
  - 16.9.2 sürüm verisi Ekle
  - Güncelleştirmeleri Salı Düzeltme Eki
  - derleme numaralarının tarihini güncelleştirme sayfası
  - 16,9 GA ve 16,10 Preview 1 için derleme numaraları
  - Yeni sürümler için güncelleştirme
- [Çevrimdışı Visual Studio yüklemesi oluşturma](../install/create-an-offline-installation-of-visual-studio.md) -yönetici belge düzenlemelerini güncelleştirme
- [Visual Studio çevrimdışı yükleme için gerekli sertifikaları yükleme](../install/install-certificates-for-visual-studio-offline.md) -yönetici güncelleştirme belge düzenlemeleri
- [Visual Studio sürümlerini yan](../install/install-visual-studio-versions-side-by-side.md) yana yönetici güncelleştirme belge düzenlemelerini yükler
- [Visual Studio ve Azure hizmetlerini bir güvenlik duvarı ya da ara sunucu ile güncelleştiren bir makalenin arkasına yükleyip kullanın](../install/install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md) .

#### <a name="javascript"></a>JavaScript

**Güncelleştirilmiş makaleler**

- [Visual Studio 'da JavaScript ve TypeScript # gerekli; arama sonuçlarında sayfa başlığı görüntülendi. Markasını ekleyin. < 60 karakter.](../javascript/index.yml) -AngularJS güncelleştirmeleri
- [Hızlı başlangıç: Visual Studio 'Yu kullanarak ilk Vue.js App](../javascript/quickstart-vuejs-with-nodejs.md) -AngularJS güncelleştirmelerini oluşturma
- [Öğretici: Visual Studio 'da TypeScript ile ASP.NET Core uygulaması oluşturma](../javascript/tutorial-aspnet-with-typescript.md)
  - AngularJS güncelleştirmeleri
  - VisualStudio-docs/sorunlar/6457--eksik sürüm
- [Öğretici: Visual Studio 'da Node.js ve Express uygulaması oluşturma](../javascript/tutorial-nodejs.md) -AngularJS Updates
- JavaScript-AngularJS güncelleştirmeleri [için kod düzenleyicisini kullanmayı öğrenin](../javascript/write-and-edit-code.md)
- [Visual Studio 'da JavaScript ve TypeScript ile birim testi](../javascript/unit-testing-javascript-with-visual-studio.md)
  - ASP.NET Core ve TypeScript için birim testleri
  - Geliştirici Komut İstemi ve geliştirici PowerShell
  - GitHub sorun düzeltmeleri
- [Visual Studio 'da NPM paketlerini yönetme](../javascript/npm-package-management.md) -GitHub sorun düzeltmeleri

#### <a name="msbuild"></a>MSBuild

**Güncelleştirilmiş makaleler**

- [MSBuild derleme projeleri](../msbuild/build-process-overview.md) -hatalı öğe adını düzeltir.
- [CreateCSharpManifestResourceName görevi](../msbuild/createcsharpmanifestresourcename-task.md) -hatalı çapraz başvuruyu çözme yanlış
- [Nasıl yapılır: Visual Studio derleme Işlemini genişletme](../msbuild/how-to-extend-the-visual-studio-build-process.md) -XML girintisini onarma
- [MIDL görevi](../msbuild/midl-task.md) -güncelleştirme Midl-Task.MD
- [Ortak MSBuild proje öğeleri](../msbuild/common-msbuild-project-items.md) -Makale içi İçindekiler ekleme ve biçimlendirmeyi iyileştirme
- [Öğe öğesi (MSBuild)](../msbuild/item-element-msbuild.md) -Makale içi İçindekiler ekleme ve biçimlendirmeyi iyileştirme
- [Exec görevi](../msbuild/exec-task.md) -Utf8Encoding parametresi için belge Ekle

#### <a name="profiling"></a>Profil Oluşturma

**Güncelleştirilmiş makaleler**

- [Uygulama performansını komut satırından ölçme](../profiling/profile-apps-from-command-line.md) -GitHub sorun düzeltmeleri
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md) -.net sayaçları için bulma çalışması aracı

#### <a name="python"></a>Python

**Güncelleştirilmiş makaleler**

- [Öğretici: Visual Studio 'da Flask Web çerçevesi ile çalışmaya başlama](../python/learn-flask-visual-studio-step-01-project-solution.md)
  - Sorgu parametreleriyle ilgili güncelleştirilmiş kod ve metin
  - Visual Studio 2019 Python öğreticilerinin şablon içeriğini yoklayıp kaldırma
- [Öğretici: Visual Studio 'Da Docgo Web çerçevesi ile çalışmaya başlama](../python/learn-django-in-visual-studio-step-01-project-and-solution.md) -kaldırıldı visual Studio 2019 Python öğreticilerinin şablon içeriği
- [5. Adım: Docgo 'da kullanıcıların kimliğini doğrulama](../python/learn-django-in-visual-studio-step-05-django-authentication.md) Visual Studio 2019 Python öğreticilerinde, şablon içeriğini yokladık
- 6. Adım: Visual Studio 2019 Python öğreticilerinde bulunan [Docgo Web projesi şablonu ' nu yokladığı şekilde kullanın](../python/learn-django-in-visual-studio-step-06-polls-django-web-project-template.md)
- [4. Adım: tam Flask Web projesi şablonunu kullanma](../python/learn-flask-visual-studio-step-04-full-flask-project-template.md) -kaldırıldı-Visual Studio 2019 Python öğreticilerinin şablon içeriğini kaldırma
- [5. Adım: Flask Web projesi şablonunu yoklayıp,](../python/learn-flask-visual-studio-step-05-polls-flask-web-project-template.md) kaldırılan Visual Studio 2019 Python öğreticilerinin şablon içeriğini
- [Docgo Web projesi şablonu](../python/python-django-web-application-project-template.md) -kaldırıldı Visual Studio 2019 Python öğreticilerinde şablon Içeriğini yoklamalar
- [Python web uygulaması proje şablonları](../python/python-web-application-project-templates.md) -kaldırıldı Visual Studio 2019 Python öğreticilerinde şablon Içeriğini yoklamalar
- [Python yorumlayıcıları için hata ayıklama sembolleri yükler](../python/debugging-symbols-for-mixed-mode-c-cpp-python.md) -Python 2,7 ' nin son 3 yüklemesini ekleyin

#### <a name="test"></a>Test etme

**Yeni makaleler**

- [ *. Testsettings* 'den *. runsettings* 'e Yükselt](../test/migrate-testsettings-to-runsettings.md) -runsettings belgesi 'ne geçiş Ekle
- [MSTestV1 'Den MSTestV2 'e yükseltme](../test/mstest-update-to-mstestv2.md) -MSTestV1 'den MSTestV2 'e yükseltme sırasında belge ekleme

**Güncelleştirilmiş makaleler**

- [Koddan birim testi yöntemi saplamaları oluşturma](../test/create-unit-tests-menu.md) -VisualStudio-docs/sorunlar/6484--Update link
- [Visual Studio 'da test araçlarına ilk bakış](../test/improve-code-quality.md) -VisualStudio-docs/sorunlar/6429--laboratuvar bağlantılarını Güncelleştir
- [*. Runsettings* dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Geliştirici Komut İstemi ve geliştirici PowerShell
  - Düzeltilen yazım hataları
- [VSTest.Console.exe komut satırı seçenekleri](../test/vstest-console-options.md) -Geliştirici komut istemi ve geliştirici PowerShell

### <a name="february-2021"></a>Şubat 2021

#### <a name="debugger"></a>Hata Ayıklayıcısı

**Güncelleştirilmiş makaleler**

- [Visual Studio hata ayıklayıcısında kesme noktaları kullan](../debugger/using-breakpoints.md) -erişilebilirlik güncelleştirmeleri

#### <a name="get-started"></a>başlarken

**Güncelleştirilmiş makaleler**

- [Öğretici: Visual Studio 2017 ' de bir depodan bir proje açın](../get-started/tutorial-open-project-from-repo-visual-studio-2017.md) -güncelleştirme ayrıca bkz. VS2017 Open Project in from the bir deposundan
- [Öğretici: bir depoyu bir depodan açın](../get-started/tutorial-open-project-from-repo-visual-studio-2019.md) -' bir depoyu bir VS2017 sürümüne ekleyin ' sayfasında ' bir proje açın ' sayfasından bir proje açın

#### <a name="ide"></a>IDE

**Güncelleştirilmiş makaleler**

- [MSBuild sorunları Için sorun giderme ve günlük oluşturma](./msbuild-logs.md) -proje sistemi araçları uzantısını kullanma hakkında yönergeler ekleme

#### <a name="install"></a>Yükleme

**Güncelleştirilmiş makaleler**

- [En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio'yu güncelleştirme](../install/update-minimal-layout.md)
  - Seçenekler tablosunda 2017 örnek ekleme
  - VS2017 için örnekler ekleme

#### <a name="msbuild"></a>MSBuild

**Yeni makaleler**

- [MSB3644: ' FrameworkVersion ' için başvuru derlemeleri bulunamadı](../msbuild/errors/msb3644.md) -MSBuild hataları
- [MSB8036: Windows SDK ' version ' bulunamadı](../msbuild/errors/msb8036.md) -MSBuild hataları

#### <a name="test"></a>Test etme

**Güncelleştirilmiş makaleler**

- [Visual Studio 'Da C++ Için Microsoft birim testi çerçevesini kullanma](../test/how-to-use-microsoft-test-framework-for-cpp.md) -küçük içerik yenileme ve düzenleme
- [Visual Studio 'Da C++ dll 'leri için birim testleri yazma](../test/how-to-write-unit-tests-for-cpp-dlls.md) -küçük içerik yenileme ve düzenleme
- [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md) -erişilebilirlik güncelleştirmeleri
- [Izlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md) -erişilebilirlik için güncelleştirmeler
- [Microsoft Fakes ile test edilen kodu yalıtın](../test/isolating-code-under-test-with-microsoft-fakes.md) -Fakes docs 'taki .NET 5,0 'yi açıkça belirleyin