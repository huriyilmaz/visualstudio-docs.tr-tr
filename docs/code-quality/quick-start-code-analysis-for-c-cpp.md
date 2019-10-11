---
title: 'Hızlı Başlangıç: C/C++ için Kod Analizi'
description: Yaygın kodlama sorunlarını ve C++ kusurlarını algılamak Için Visual Studio 'daki kodda statik analiz çalıştırın.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: b14737c09cf7ff2b14eda1f61408b531b9c22c14
ms.sourcegitcommit: 535ef05b1e553f0fc66082cd2e0998817eb2a56a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72018374"
---
# <a name="quickstart-code-analysis-for-cc"></a>Hızlı Başlangıç: C/C++ için kod analizi

Kod analizini, C veya C++ Code 'da düzenli olarak çalıştırarak uygulamanızın kalitesini artırabilirsiniz. Bu, yaygın sorunları, iyi programlama uygulaması ihlallerini veya test aracılığıyla bulmanın zor olduğu kusurları bulmanıza yardımcı olabilir. Geçerli olan, ancak yine de siz veya kodunuzu kullanan diğer kişilerin sorunlarına neden olabilir, belirli bir kod desenleri için Kod Analizi arar çünkü kod çözümleme uyarıları derleyici hataları ve Uyarıları farklılık gösterir.

## <a name="configure-rule-sets-for-a-project"></a>Bir proje için kural kümelerini yapılandırma

1. **Çözüm Gezgini**, proje adı için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

2. Aşağıdaki adımlar isteğe bağlıdır:

    1. **Yapılandırma** ve **Platform** listelerinde, derleme yapılandırması ve hedef platform ' u seçin.

    2. Varsayılan olarak, Kod Analizi uyarıları otomatik olarak dış araçları tarafından oluşturulan kodu raporlamaz. Üretilen koddan gelen uyarıları görüntülemek için temizleyin **üretilen koddan gelen sonuçları Gizle** onay kutusu.

        > [!NOTE]
        > Bu seçenek hataları ve Uyarıları formları ve şablonlar görüntülendiğinde kod çözümleme hataları ve Uyarıları üretilen koddan gelen engellemez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.

3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için, **derlemede C/C++ Için kod analizini etkinleştir** onay kutusunu seçin. Ayrıca, **Çözümle** menüsünü açıp *ProjectName* **üzerinde Kod analizini Çalıştır '** ı seçerek Kod analizini el ile de çalıştırabilirsiniz.

4. İçinde **bu kural kümesini Çalıştır** listesinde, aşağıdakilerden birini yapın:

    - Kullanmak istediğiniz kural kümesini seçin.

    - Listede olmayan mevcut bir özel kural kümesini belirtmek için **\<Zat >** öğesini seçin.

    - Tanımlayan bir [özel kural kümesi](../code-quality/how-to-create-a-custom-rule-set.md).

### <a name="standard-cc-rule-sets"></a>Standart C/C++ kural kümeleri

Visual Studio yerel kod için iki standart kural kümesi içerir:

|Kural kümesi|Açıklama|
|--------------|-----------------|
|Microsoft yerel en düşük önerilen kurallar|Bu kural kümesi, olası güvenlik delikleri ve uygulama kilitlenmeleri dahil olmak üzere yerel kodunuzda en kritik sorunlara odaklanır. Bu kural kümesini yerel projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmelisiniz.|
|Microsoft yerel önerilen kurallar|Bu kural kümesi, çok çeşitli sorunları ele alır. Microsoft yerel en düşük önerilen kuralların tüm kurallarını içerir.|

## <a name="run-code-analysis"></a>Kod analizini Çalıştır

Proje özellikleri sayfalarının kod analizi sayfasında, Kod analizini projenizi her oluşturduğunuzda çalışacak şekilde yapılandırabilirsiniz. Ayrıca, Kod analizini el ile de çalıştırabilirsiniz.

Bir çözümde Kod Analizi çalıştırmak için:

- Üzerinde **derleme** menüsünde seçin **çözüm üzerinde kod analizini Çalıştır**.

Bir projede kod analizini çalıştırmak için:

1. Çözüm Gezgini, projenin adını seçin.

2. **Yapı** menüsünde, *Proje adı* **üzerinde Kod analizini Çalıştır** ' ı seçin.

   Proje veya çözüm derlenir ve kod analizi çalışır. Sonuçlar Hata Listesi görüntülenir.

## <a name="analyze-and-resolve-code-analysis-warnings"></a>Kod Analizi uyarılarını çözümleyin ve çözümleyin

Belirli bir uyarıyı çözümlemek için Hata Listesi uyarının başlığını seçin. Uyarı, sorunla ilgili ek bilgileri görüntüleyecek şekilde genişler. Mümkün olduğunda, kod analizi uyarıya yol gösteren satır numaralarını ve analiz mantığını görüntüler. Soruna yönelik olası çözümler dahil olmak üzere uyarı hakkında ayrıntılı bilgi için, ilgili çevrimiçi Yardım konusunu göstermek üzere uyarı KIMLIĞINI seçin.

Bir uyarı seçtiğinizde, uyarıya neden olan kod satırı, Visual Studio kod Düzenleyicisi 'nde vurgulanır.

Sorun anladıktan sonra kodunuzu çözebilirsiniz. Ardından, uyarının artık Hata Listesi göründüğünden ve Düzeltmelerinizin yeni bir uyarı gerçekleştirmediğinden emin olmak için kod analizini yeniden çalıştırın.

## <a name="suppress-code-analysis-warnings"></a>Kod Analizi uyarılarını gösterme

Kod Analizi uyarısı düzeltmemeyi ne zaman karar verebilirsiniz zamanlar vardır. Uyarı çözümleme sorunu kodunuzun tüm gerçek uygulamasında ortaya çıkacağını olasılık ile ilgili çok fazla değiştirilemeyen gerektirir karar verebilirsiniz. Veya uyarıda kullanılan analiz belirli bir içerik için uygun olduğunu düşündüğünüz. Uyarıları artık Hata Listesi görünmeyecek şekilde tek tek izleyebilirsiniz.

Bir uyarıyı bastırmak için:

1. Ayrıntılı bilgiler görüntülenmiyorsa, genişletilecek uyarının başlığını seçin.

2. Seçin **eylemleri** Uyarı alt kısmındaki bağlantı.

3. **Iletiyi Gizle** ' yi ve ardından **kaynak '** ı seçin.

   Bir ileti, kod satırı için uyarıyı belirten `#pragma warning (disable:[warning ID])` ' y i gizler.

## <a name="create-work-items-for-code-analysis-warnings"></a>Kod Analizi uyarıları için iş öğeleri oluşturma

Visual Studio içinden hataları günlüğe kaydetmek için çalışma öğesi izleme özelliğini kullanabilirsiniz. Bu özelliği kullanmak için bir Team Foundation Server örneğine bağlanmanız gerekir.

**Bir veya daha fazla C/C++ kod uyarısı için bir iş öğesi oluşturmak için**

1. Hata Listesi, Genişlet ve uyarıları Seç

2. Uyarıların kısayol menüsünde, **Iş öğesi oluştur**' u seçin ve sonra iş öğesi türünü seçin.

3. Visual Studio Seçili uyarılar için tek bir iş öğesi oluşturur ve iş öğesini IDE 'nin bir belge penceresinde görüntüler.

4. Ek bilgileri ekleyin ve sonra **Iş öğesini kaydet**' i seçin.

## <a name="search-and-filter-code-analysis-results"></a>Kod analizi sonuçlarını arama ve filtreleme

Uzun listesi uyarı iletilerini arayabilir ve çoklu proje çözümlerinde uyarıları filtreleyebilirsiniz.

- **Uyarıları başlığa veya uyarı kimliğine göre filtrelemek için**: Arama kutusuna anahtar sözcüğü girin.

- **Uyarıları önem derecesine göre filtrelemek için**: Varsayılan olarak, kod analizi iletilerine bir **Uyarı**önem derecesi atanır. Bir veya daha fazla iletinin önem derecesini özel bir kural kümesinde **hata** olarak atayabilirsiniz. **Hata listesi** **önem derecesi** sütununda, açılan oku ve ardından filtre simgesini seçin. Yalnızca ilgili önem derecesine atanmış iletileri göstermek için **Uyarı** veya **hata** ' ı seçin. Tüm iletileri göstermek için **Tümünü Seç ' i** seçin.

## <a name="see-also"></a>Ayrıca bkz.

[C/için kod analiziC++](../code-quality/code-analysis-for-c-cpp-overview.md)