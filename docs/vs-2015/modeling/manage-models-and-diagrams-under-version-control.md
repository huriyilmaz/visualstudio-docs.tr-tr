---
title: Sürüm denetimi altındaki modelleri ve diyagramları yönetme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30b13610cc59b8a0225e52abf47f9a4f2cc97d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657574"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Sürüm denetimi altındaki modelleri ve diyagramları yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[Team Foundation sürüm denetimi veya git](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314)kullanarak, modelleme projelerinizin ve diyagramlarınızın kod haritaları (. dgml dosyaları) dahil farklı sürümlerini yönetin Şirket içi Team Foundation Server veya bulutta Visual Studio Team Services.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!IMPORTANT]
> Birkaç kullanıcı aynı modelleme projesi üzerinde çalışırken dikkatli olun. [Orta veya büyük projelerde modelleri nasıl düzenleyebileceğinizi](../modeling/structure-your-modeling-solution.md)öğrenin.

## <a name="files-in-a-modeling-project"></a><a name="ModelingProjects"></a> Modelleme projesindeki dosyalar
 Birden fazla kullanıcı aynı anda bir modelleme projesi üzerinde çalışabilir ve farklı dosyalar üzerinde çalışır.

 Farklı kullanıcılar tarafından yapılan değişiklikler arasındaki çakışmaları önlemek veya çözmek için, modelin dosyalarda nasıl depolandığını anlamak önemlidir.

- Her paket, **ModelDefinition** proje klasöründe tutulan ayrı bir **. UML** dosyasında depolanır. Modelde bir **. UML** dosyası da vardır. Bu dosyalardan biri silinirse veya bozuksa, buna karşılık gelen paket veya model kaybedilir.

- Her diyagram iki dosyada depolanır. Örneğin, bir sınıf diyagramı şunları içerir:

  - **DiagramName. classdiagram** -bu dosya silinirse veya bozuksa, diyagram kaybedilir, ancak gösterilen sınıflar ve ilişkilendirmeler modelde olmaya devam eder ve UML Model Gezgini 'nde görünebilirler.

  - **DiagramName. classdiagram. Layout** -bu dosya silinirse, şekiller diyagramda görünmeye devam eder, ancak boyutlarını ve konumlarını kaybeder. Her düzen dosyası bir diyagram dosyasına bağlı olur. Bunu görmek için Çözüm Gezgini Diyagram dosyasının yanındaki [+] düğmesine tıklayın.

> [!NOTE]
> Dosyalar arasında tutarlılık sağlamak önemlidir. Örneğin, bir. uml dosyasında değişiklikleri geri almak için kaynak denetimini kullanırsanız,. * Diagram ve. Layout dosyalarındaki ilgili değişiklikleri aynı anda geri almanız gerekir. İçinde temsil edilen öğeler. \* Diyagram dosyası bir. uml dosyasında da temsil ediliyorlarsa kaybolacaktır.

## <a name="working-on-shared-modeling-projects"></a><a name="Shared"></a> Paylaşılan modelleme projeleri üzerinde çalışma
 Projenin farklı bölümlerinde eşzamanlı çalışma arasındaki çakışmaları en aza indirmek için:

- Modelleme projenizi farklı iş bölgelerini temsil eden paketlere bölün. Tüm modeli, kök modelde bırakmak yerine paketlere taşıyın. Daha fazla bilgi için bkz. [paketleri ve ad alanlarını tanımlama](../modeling/define-packages-and-namespaces.md).

- Farklı kullanıcılar aynı pakette veya diyagramda aynı anda çalışmamalıdır.

- Profiller kullanıyorsanız, herkesin aynı profilleri yüklediğinizden emin olun. Bkz. [modelinizi profiller ve Stereotipler Ile özelleştirme](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

- Yalnızca üzerinde çalıştığınız paketi değiştirdiğinizden emin olmak için:

  - UML sınıf, bileşen veya kullanım örneği diyagramının **LinkedPackage** özelliğini ayarlayın.

  - UML Model Gezgini ' nde, bir etkinliği veya etkileşimi oluşturduktan hemen sonra paketinize sürükleyin. Bu öğe, etkinlik veya sıralı diyagramda ilk düğümü oluşturduğunuzda UML Model Gezgini 'nde görünür.

- Paketleri izlemenize yardımcı olması için paket dosyalarını gerçek paket adlarını yansıtacak şekilde yeniden adlandırın.

- ' De [!INCLUDE[esprscc](../includes/esprscc-md.md)] , her zaman tek tek dosyalarda **iade etme** ve **en son sürüm** işlemlerini tüm modelleme projesi üzerinde gerçekleştirin.

- Modelleme projesini iade etmeden hemen önce her zaman bir **Get** işlemi gerçekleştirin.

- **Get** işlemini gerçekleştirmeden önce her zaman tüm diyagramları kapatın.

    > [!NOTE]
    > Bir dosya **Al**işlemi gerçekleştirdiğinizde açıksa ve işlem yerel değişikliklerle sonuçlanırsa, dosyayı yeniden yüklemeniz istenir. Bu durumda **Hayır**' a tıklayın ve ardından tüm projeyi yeniden yükleyin. **Çözüm Gezgini**, modelleme projesi düğümüne sağ tıklayın, **Projeyi Kaldır**' a ve ardından **projeyi yeniden yükle**' ye tıklayın.

### <a name="changes-requiring-exclusive-access-to-the-model"></a><a name="Exclusive"></a> Modele özel erişim gerektiren değişiklikler
 Aşağıdaki değişiklik türlerini yapmadan önce tüm proje üzerinde bir kullanıma alma kilidine sahip olduğunuzdan emin olun.

- Diğer paketlerden başvurulan öğeleri yeniden adlandırma veya silme.

- Paket sınırlarını karşılıklı olan ilişkilerin özelliklerini değiştirme.

- Kullanıma alma kilitleri hakkında bilgi edinmek için bkz. [dosyaları kullanıma alma ve düzenleme](https://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).

##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Bir diyagram dosyasını proje klasörünün içine veya dışına taşımak için

1. **Visual Studio Için Geliştirici komut istemi**' ni başlatın.

2. Diyagram dosyasını ve **. Layout** dosyasını taşımak için **tf Rename** kullanın:

     `tf rename sourcePath targetPath`

3. Çözüm Gezgini, dosyaya sağ tıklayın ve ardından **projeden Dışla**' ya tıklayın.

4. Dosyayı hedef klasöre ekleyin.

     Çözüm Gezgini, hedef klasöre veya projeye sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **var olan öğe**' ye tıklayın. İletişim kutusunda, diyagram dosyasını seçin ve ardından **Ekle**' ye tıklayın. Düzen dosyası otomatik olarak eklenir.

    > [!NOTE]
    > Dosyayı farklı bir projeye taşıyamazsınız.

## <a name="merging-changes-in-model-files-and-diagrams"></a><a name="Merging"></a> Model dosyalarında ve diyagramlarda değişiklikleri birleştirme
 Bir modelde birden fazla kullanıcı aynı anda çalıştıktan sonra, [!INCLUDE[esprscc](../includes/esprscc-md.md)] değişiklikleri model dosyalarında birleştirmenizi ister. Yukarıdaki önceki bölümlerde açıklandığı gibi ayrı projeler üzerinde çalışmak, birleştirmelerinin çoğunun önüne engel olur. Normalde, kalan çakışmalar güvenli bir şekilde otomatik olarak birleştirilebilir. Aşağıdaki tür değişiklikler hiçbir zorluk oluşmasına neden olmaz:

- Yaşam çizgisi türleri. Bir etkileşime (sıralı diyagram) yaşam çizgisi eklediğinizde, yaşam çizgisini mevcut bir türden oluşturmadığınız müddetçe, türü kök modelde depolanır.

- Yeni etkinlikler ve etkileşimler başlangıçta kök modelde depolanır.

- Öğe ve ilişki ekleme.

- Yalnızca kendi paketleri içinde başvurulan öğeleri yeniden adlandırma veya silme.

## <a name="see-also"></a>Ayrıca Bkz.
 Mimari [paylaşma modellerini ve dışa aktarma diyagramlarını](../modeling/share-models-and-exporting-diagrams.md) [analiz etme ve modelleme](../modeling/analyze-and-model-your-architecture.md)
