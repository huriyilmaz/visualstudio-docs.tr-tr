---
title: 'Visual Studio belgeleri: yenilikler geçmişi '
titleSuffix: ''
description: Visual Studio belgelerindeki yeniliklerin geçmişi
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 6d0b60c548e4e5d42a10e82754d045073f016f8b
ms.sourcegitcommit: ea3c985a23851b424127f2205f617446b6536578
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91621756"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Visual Studio belgelerindeki yeniliklerin geçmişi

Visual Studio docs 'taki yenilikler geçmişine hoş geldiniz. Bu konu, 2020 Eylül 'de (2020 ' den itibaren) önce docs üzerinde yapılan büyük değişiklikleri içerir. En son yenilikler için bkz. [Visual Studio docs: docs 'taki](whats-new-visual-studio-docs.md)yenilikler.

## <a name="august-2020"></a>Ağustos 2020
### <a name="azure"></a>Azure

**Yeni makaleler**

- VS 2019 16,7 için [Visual Studio bağlı hizmetler 'e bağlı hizmetleri kullanarak Azure Application Insights ekleme](../azure/azure-app-insights-add-connected-service.md)
- VS 2019 16,7 için [Visual Studio bağlı hizmetler 'e bağlı hizmetleri kullanarak redsıs Için Azure önbelleği ekleme](../azure/azure-cache-for-redis-add-connected-service.md)
- VS 2019 16,7 için [Visual Studio bağlı hizmetler 'e bağlı hizmetleri kullanarak uygulamanıza Azure Cosmos DB ekleyin](../azure/azure-cosmosdb-add-connected-service.md)
- VS 2019 16,7 için [Visual Studio bağlı hizmetler 'e bağlı hizmetleri kullanarak Azure SignalR ekleme](../azure/azure-signalr-add-connected-service.md)
- VS 2019 16,7 için [Azure SQL veritabanı 'na bağlı hizmetlere bağlantı ekleme](../azure/azure-sql-database-add-connected-service.md)

**Güncelleştirilmiş makaleler**

- [Visual Studio bağlı hizmetler 'i kullanarak Azure depolama ekleme](../azure/vs-azure-tools-connected-services-storage.md)
  - VS 2019 için bağlı hizmetler 16,7
  - Azure depolama bağlı hizmetler makalesi: desteklenen Kullanıcı arabirimini ve proje türlerini güncelleştirme

### <a name="code-quality"></a>Kod kalitesi

**Yeni makaleler**

- [CA1310: doğruluk Için StringComparison belirtin](../code-quality/ca1310.md) -CA1307 için CA1310 ve güncelleştirme belgelerine belge ekleyin
- [CA1837: Process. GetCurrentProcess () yerine Environment. ProcessId kullanın. ](../code-quality/ca1837.md) CA1837 için kimlik-belgeler
- [CA1838: `StringBuilder` P/Invoke Için parametrelerden KAÇıNıN](../code-quality/ca1838.md) -CA1838 için belge ekleyin
- [CA2008: TaskScheduler geçirmeden görev oluşturma](../code-quality/ca2008.md) -CA2008 için belge ekleme
- [CA2249: CA2249 Için String. IndexOf-docs yerine String. Contains kullanmayı düşünün](../code-quality/ca2249.md)
- [CA2361: DataSet. ReadXml () içeren bir otomatik oluşturulan sınıfın güvenilmeyen verilerle kullanılmadığından emin olun](../code-quality/ca2361.md) -daha fazla veri kümesi/DataTable kuralları
- [CA2362: otomatik olarak oluşturulabilen seri hale getirilebilir türde veri kümesi veya DataTable, uzaktan kod yürütme saldırılarına karşı savunmasız](../code-quality/ca2362.md) olabilir-daha fazla veri kümesi/DataTable kuralları
- [IL3000: tek dosya olarak yayımlarken derleme dosyası yoluna erişim kullanmaktan KAÇıNıN](../code-quality/il3000.md) IL3000 için belge Ekle
- [IL3001: tek bir dosya olarak yayımlarken derleme dosya yoluna erişmenin önüne kaçının](../code-quality/il3001.md) -IL3001 için belge ekleyin

**Güncellendi**

- [CA1002: genel listeleri](../code-quality/ca1002.md) gösterme-yapılandırılabilirlik-API yüzeyi bölümü ekleme
- [CA1046: Başvuru türlerinde eşittir işlecini aşırı yüklemeyin](../code-quality/ca1046.md) -yapılandırılabilirliği-API yüzeyi bölümüne ekleyin
- [CA1307: açıklık Için StringComparison belirtin](../code-quality/ca1307.md) -CA1307 için CA1310 ve güncelleştirme belgelerine belge ekleyin
- [CA1700: Enum değerlerini &#39;ayrılmış&#39;](../code-quality/ca1700.md) -yapılandırılabilirlik-API yüzeyi bölümü ekleme
- [CA1707: tanımlayıcılar alt çizgi](../code-quality/ca1707.md) -yapılandırma yapılandırması-API yüzeyi bölümü içermemelidir
- [CA1822: üyeleri statik olarak işaretle](../code-quality/ca1822.md) -yapılandırılabilirlik-API Surface Bölümü Ekle
- [CA2351: DataSet. ReadXml () girişinin güvenilir olduğundan](../code-quality/ca2351.md) ve daha fazla veri kümesi/DataTable kuralı olduğundan emin olun
- [Üçüncü taraf Çözümleyicileri](../code-quality/install-roslyn-analyzers.md) , kod analizi belgeleri için değiştirilen yapıyı ve başlıkları yükler

### <a name="containers"></a>Kapsayıcılar

**Güncelleştirilmiş makaleler**

- Visual [Studio 'da ASP.net kapsayıcısını bir kapsayıcı kayıt defterine dağıtma](../containers/hosting-web-apps-in-docker.md) visual Studio 16,7 yayımlama Kullanıcı arabirimi Için kapsayıcı Araçları güncelleştirmeleri
- [Visual Studio Kubernetes araçları ile çalışmaya başlama](../containers/tutorial-kubernetes-tools.md) -Kubernetes öğreticisi: kaldırma adımlarını ekleme

### <a name="deployment"></a>Dağıtım

**Yeni makaleler**

- [Visual Studio yükleyicisi projeler uzantısı ve .net core 3,1](../deployment/installer-projects-net-core.md) -Yükleyici projeleri için yeni yardım sayfası oluşturma .net Core 3,1 özellikleri

**Güncelleştirilmiş makaleler**

- [Uygulamanızı bir klasöre, IIS 'ye, Azure 'a veya başka bir hedef](../deployment/deploying-applications-services-and-components-resources.md) dağıtım güncelleştirmelerine dağıtın
- [Visual Studio 'Da dağıtım](../deployment/index.yml) -dağıtım güncelleştirmeleri

### <a name="extensibility"></a>Genişletilebilirlik

**Güncelleştirilmiş makaleler**
- [Proje alt türleri](../extensibility/internals/project-subtypes.md) -liste öğelerini girintileme girintisini çözme
- [Visual Studio Için renk değeri başvurusu](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 düzeltilmesi eksik sütun başlıkları

### <a name="get-started"></a>başlarken

**Güncelleştirilmiş makaleler**

- 5. Adım: yeni bağlı hizmetler kullanıcı arabirimi için [ASP.NET Core uygulamanızı Azure 'A dağıtma](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -video öğreticisi güncelleştirmeleri

### <a name="ide"></a>IDE

**Yeni makaleler**

- [Visual Studio 'Da F1 Yardım anahtarını değiştirme](./not-in-toc/change-f1-help-key.md) -yeniden düzenleme varsayılan F1 Yardım sayfası
- [Metin Düzenleyicisi Için F1 yardımı](./not-in-toc/default-f1-text-editor.md) -yeniden düzenleme varsayılan F1 Yardım sayfası
- -Convert typeof öğesini yeniden düzenleme adına [Dönüştür `typeof` `nameof` ](./reference/convert-typeof-to-nameof.md)
- [LINQ Ifadesini Basitleştir](./reference/simplify-linq-expression.md) -LINQ ifade yeniden düzenlemeyi basitleştirme

**Güncelleştirilmiş makaleler**

- [Visual Studio 'da pencere düzenlerini özelleştirme](./customizing-window-layouts-in-visual-studio.md) -pencere düzenlerini özelleştirme konusunda monikered dikey belge sekmeleri ekleme bilgileri
- [Visual Studio veya Visual Studio Yükleyicisi ilgili bir sorunu bildirme](./how-to-report-a-problem-with-visual-studio.md)
  - NMI 'ye daha fazla bilgi eklendi
  - Sorun bildir sayfasının tamamını yeniden oldu
- [F1 Yardım](./not-in-toc/default.md) -yeniden düzenleme varsayılan F1 Yardım sayfası
- [Otomatik kurtarma, ortam, Seçenekler iletişim kutusu](./reference/autorecover-environment-options-dialog-box.md) -güncelleştirilmiş otomatik kaydetme dosya konumları hakkında bilgi ekleme
- [Seçenekler, metin düzenleyici, temel (Visual Basic),](./reference/options-text-editor-basic-visual-basic.md) satır içi parametre adı Ipuçları için gelişmiş-eklenen temel belgeler
- [Seçenekler, metin düzenleyici, C#, gelişmiş](./reference/options-text-editor-csharp-advanced.md) -satır içi parametre adı ipuçları için temel belgeler eklendi
- [Visual Studio performans ipuçları ve püf noktaları](./visual-studio-performance-tips-and-tricks.md) -' harita modunu devre dışı bırak ' ve ' sözcük kaydırmayı devre dışı bırak ' bilgilerini
- [Visual studio 2019 ' deki](./whats-new-visual-studio-2019.md) yenilikler-visual Studio 2019 ' deki yenılıklerı 16,7 GA bilgiyle güncelleştirme

### <a name="rtvs"></a>RTVS

**Güncelleştirilmiş makaleler**

- Sütun üstbilgilerini dahil etmek için [SQL Server ve R ile](../rtvs/integrating-sql-server-with-r.md) düzeltilen tablolarla çalışma

## <a name="july-2020"></a>Temmuz 2020
### <a name="code-quality"></a>Kod kalitesi

**Yeni makaleler**

- [CA1417: `OutAttribute` P/Invoke için dize parametrelerinde KULLANMAYıN](../code-quality/ca1417.md) -CA1417 için belge ekleyin
- [CA1805: gereksiz yere başlatma.](../code-quality/ca1805.md) -CA1805 için belgeler ekleme
- [CA1836: kullanılabilir olduğunda sayı üzerinde IsEmpty tercih et](../code-quality/ca1836.md) -CA1836 için belge ekleme (Count üzerinde IsEmpty tercih et)
- [CA2016: CancellationToken parametresini tek bir belge alan yöntemlere Iletme](../code-quality/ca2016.md) CA2016-CancellationToken parametresini bir tane alacak yöntemlere iletme
- [CA2350: DataTable. ReadXml () girişinin güvenilir olduğundan emin olun](../code-quality/ca2350.md) -Ilk veri kümesi/DataTable serisini kaldırma kuralları belgeleri
- [CA2351: DataSet. ReadXml () girişinin güvenilir olduğundan](../code-quality/ca2351.md) ve Ilk veri kümesi/DataTable serisini kaldırma kuralları belgeleri olduğundan emin olun
- [CA2352: serileştirilebilir türdeki güvenli olmayan veri kümesi veya DataTable, uzaktan kod yürütme saldırılarına karşı savunmasız](../code-quality/ca2352.md) olabilir-Ilk veri kümesi/DataTable serisini kaldırma kuralları belgeleri
- CA2353: Serializable tür-ilk veri kümesi/DataTable serisini kaldırma kuralları belgeleri için [güvenli olmayan veri kümesi veya DataTable](../code-quality/ca2353.md)
- [CA2354: Serisi kaldırılan nesne grafiğinde güvenli olmayan veri kümesi veya DataTable, uzaktan kod yürütme saldırısında savunmasız](../code-quality/ca2354.md) olabilir-Ilk veri kümesi/DataTable serisini kaldırma kuralları belgeleri
- [CA2355: Serisi kaldırılan nesne grafiğinde güvenli olmayan veri kümesi veya DataTable](../code-quality/ca2355.md) -Ilk veri kümesi/DataTable serisini kaldırma kuralları belgeleri
- [CA2356: web serisi kaldırılan nesne grafiğinde güvenli olmayan veri kümesi veya DataTable türü,](../code-quality/ca2356.md) Ilk veri kümesi/DataTable serisini kaldırma kuralları belgeleri

### <a name="containers"></a>Kapsayıcılar

**Yeni makaleler**

- Kubernetes: YAML yapılandırması ile [Yerel Işlemi Kubernetes](../containers/configure-local-process-with-kubernetes.md) -yerel işlemle yapılandırma
- [Kubernetes (Önizleme) Ile yerel Işlem kullanma](../containers/local-process-kubernetes.md) -dev Spaces geçişi
- [Kubernetes ile Yerel İşlem nasıl çalışır?](../containers/overview-local-process-kubernetes.md)
  - Kubernetes için yerel Işlem: yönlendirme ekleme bölümü
  - Geliştirme alanları geçişi

### <a name="cross-platform"></a>Platformlar arası

**Güncelleştirilmiş makaleler**

- [Değişiklik günlüğü (Unity için Visual Studio Araçları, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) -kabartma VSTU changelog 4.7.1.0
- [Değişiklik günlüğü (Unity için Visual Studio Araçları, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) -kabartma vstum changelog, 2.7.1.0

### <a name="get-started"></a>başlarken

**Yeni makaleler**

- [Öğretici: basit bir C# konsol uygulamasını genişletme](../get-started/csharp/tutorial-console-part-2.md) -yayın genişletme öğreticisi ilk sürümü

### <a name="ide"></a>IDE

**Yeni makaleler**

- [Geliştirici topluluğu yönergeleri](./developer-community-guidelines.md) -eklenen Devcom yönergeleri
- [İçeri aktarılmamış türler ve genişletme yöntemleri için IntelliSense tamamlama](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>Yükleme

**Yeni makaleler**

- [En düşük düzeyde çevrimdışı düzen kullanarak Visual Studio 'Yu güncelleştirme](../install/update-minimal-layout.md) -belge en az düzen özelliği
- [Visual Studio kurumsal kılavuzu](../install/visual-studio-enterprise-guide.md) -kurumsal kılavuz

### <a name="javascript"></a>JavaScript

**Yeni makaleler**

- [TypeScript kodu derleme (Node.js)](../javascript/compile-typescript-code-npm.md) -TypeScript derleme ve derleme
- [TypeScript kodu derleme (ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) -TypeScript derleme ve derleme

### <a name="msbuild"></a>MSBuild

**Yeni makaleler**

- [Ortak MSBuild öğe meta verileri](../msbuild/common-msbuild-item-metadata.md) -MSBuild: bağlantı ve bağlantı tabanı ile isteğe bağlı meta veriler için tablo ekleme
- [MSBuild 'de çözüm filtreleri](../msbuild/solution-filters.md) -MSBuild çözüm filtreleri

### <a name="test"></a>Test etme

**Yeni makaleler**

- Test Gezgini-test Gezgini performans çalışması [ile birim testlerini hata ayıklama ve çözümleme](../test/debug-unit-tests-with-test-explorer.md)

**Güncelleştirilmiş makaleler**

- [*. Runsettings* dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - Bir runsettings dosyası kullanarak birim testlerini yapılandırmaya yönelik güncelleştirmeler
  - Blame seçeneği açıklaması değiştirildi ve örnek eklendi.