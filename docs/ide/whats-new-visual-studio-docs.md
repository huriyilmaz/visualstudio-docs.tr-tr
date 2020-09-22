---
title: "Visual Studio belgeleri: Ağustos 2020 ' deki yenilikler "
titleSuffix: ''
description: Ağustos 2020 için Visual Studio docs 'daki yenilikler.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808987"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Visual Studio belgeleri: Ağustos 2020 ' deki yenilikler

Ağustos 2020 için Visual Studio docs 'daki yenilikler 'e hoş geldiniz. Bu makalede, bu süre boyunca docs 'ta yapılan önemli değişikliklerden bazıları listelenir. Önceki aylardaki yenilikler hakkında daha fazla bilgi için bkz. yenilikler [geçmişi](whats-new-visual-studio-docs-history.md) konusu.

## <a name="azure"></a>Azure

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

## <a name="code-quality"></a>Kod kalitesi

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

## <a name="containers"></a>Kapsayıcılar

**Güncelleştirilmiş makaleler**

- Visual [Studio 'da ASP.net kapsayıcısını bir kapsayıcı kayıt defterine dağıtma](../containers/hosting-web-apps-in-docker.md) visual Studio 16,7 yayımlama Kullanıcı arabirimi Için kapsayıcı Araçları güncelleştirmeleri
- [Visual Studio Kubernetes araçları ile çalışmaya başlama](../containers/tutorial-kubernetes-tools.md) -Kubernetes öğreticisi: kaldırma adımlarını ekleme

## <a name="deployment"></a>Dağıtım

**Yeni makaleler**

- [Visual Studio yükleyicisi projeler uzantısı ve .net core 3,1](../deployment/installer-projects-net-core.md) -Yükleyici projeleri için yeni yardım sayfası oluşturma .net Core 3,1 özellikleri

**Güncelleştirilmiş makaleler**

- [Uygulamanızı bir klasöre, IIS 'ye, Azure 'a veya başka bir hedef](../deployment/deploying-applications-services-and-components-resources.md) dağıtım güncelleştirmelerine dağıtın
- [Visual Studio 'Da dağıtım](../deployment/index.yml) -dağıtım güncelleştirmeleri

## <a name="extensibility"></a>Genişletilebilirlik

**Güncelleştirilmiş makaleler**
- [Proje alt türleri](../extensibility/internals/project-subtypes.md) -liste öğelerini girintileme girintisini çözme
- [Visual Studio Için renk değeri başvurusu](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) -AB # 1759333 düzeltilmesi eksik sütun başlıkları

## <a name="get-started"></a>Kullanmaya başlayın

**Güncelleştirilmiş makaleler**

- 5. Adım: yeni bağlı hizmetler kullanıcı arabirimi için [ASP.NET Core uygulamanızı Azure 'A dağıtma](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) -video öğreticisi güncelleştirmeleri

## <a name="ide"></a>IDE

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

## <a name="rtvs"></a>RTVS

**Güncelleştirilmiş makaleler**

- Sütun üstbilgilerini dahil etmek için [SQL Server ve R ile](../rtvs/integrating-sql-server-with-r.md) düzeltilen tablolarla çalışma

## <a name="community-contributors"></a>Topluluk katkı sağlayanlar

Aşağıdaki kişiler bu süre boyunca Visual Studio belgelerine katkıda bulunanlar. Teşekkür ederiz! [Katkıda bulunan kılavuzundaki](/contribute/)Kılavuzu Izleyerek Visual Studio belgelerine nasıl katkıda bulunabileceğinizi öğrenin.

- [Alexb-Sheldonürt](https://github.com/AlexB-SheldonMFG) -Alex Black (11)
- [Youssef1313](https://github.com/Youssef1313) -Youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) -Hiroshi Yoshioka (3)
- [Astrochoco](https://github.com/AstroChoco) -Qian lu (çikolata) (1)
- [athyunnath](https://github.com/athyunnath) -Athyunnath eleti (1)
- [Caro-Oviedo](https://github.com/caro-oviedo) -Caro oviewdo (1)
- [Evangelink](https://github.com/Evangelink) -Amaury levé (1)
- [jetas-bennettjones](https://github.com/jethas-bennettjones) -Shafiq Jeta (1)
- [nebuk89](https://github.com/nebuk89) -ben de St paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) -Petr Kulikov (1)
- [Riqq](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) -Timo Cornelius Metzger (1)
- [Weitzhandler](https://github.com/weitzhandler) -Shimmy (1)