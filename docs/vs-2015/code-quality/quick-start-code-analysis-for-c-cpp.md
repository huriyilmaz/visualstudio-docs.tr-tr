---
title: 'Hızlı başlangıç: C için kod analizi-C++ | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++ code analysis
- code analysis,C/C++
ms.assetid: 6110b8ba-0af6-4acd-b1ba-bb0551f90e44
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: e9db06ec0748ce4499afb423fac03886cd763301
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278488"
---
# <a name="quick-start-code-analysis-for-cc"></a>Hızlı Başlangıç: C/C++ İçin Kod Analizi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod analizini, C veya C++ Code 'da düzenli olarak çalıştırarak uygulamanızın kalitesini artırabilirsiniz. Bu, yaygın sorunları, iyi programlama uygulaması ihlallerini veya test aracılığıyla bulmanın zor olduğu kusurları bulmanıza yardımcı olabilir. Geçerli olan, ancak yine de siz veya kodunuzu kullanan diğer kişilerin sorunlarına neden olabilir, belirli bir kod desenleri için Kod Analizi arar çünkü kod çözümleme uyarıları derleyici hataları ve Uyarıları farklılık gösterir.  
  
## <a name="in-this-topic"></a>Bu konuda  
  
- [Bir proje için kural kümelerini yapılandırma](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Kod analizini Çalıştır](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Kod Analizi uyarılarını çözümleyin ve çözümleyin](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Kod Analizi uyarılarını gizleme](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Kod Analizi uyarıları için iş öğeleri oluşturma](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Kod analizi sonuçlarını arama ve filtreleme](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="BKMK_ConfigureRuleSets"></a>Bir proje için kural kümelerini yapılandırma  
  
1. **Çözüm Gezgini**, proje adı için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. Aşağıdaki adımlar isteğe bağlıdır:  
  
    1. **Yapılandırma** ve **Platform** listelerinde, derleme yapılandırması ve hedef platform ' u seçin.  
  
    2. Varsayılan olarak, Kod Analizi uyarıları otomatik olarak dış araçları tarafından oluşturulan kodu raporlamaz. Oluşturulan koddan gelen uyarıları görüntülemek için, **oluşturulan koddan sonuçları bastır** onay kutusunun işaretini kaldırın.  
  
        > [!NOTE]
        > Bu seçenek hataları ve Uyarıları formları ve şablonlar görüntülendiğinde kod çözümleme hataları ve Uyarıları üretilen koddan gelen engellemez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.  
  
3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için, **derlemede C/C++ Için kod analizini etkinleştir** onay kutusunu seçin. Ayrıca, **Çözümle** menüsünü açıp *ProjectName* **üzerinde Kod analizini Çalıştır '** ı seçerek Kod analizini el ile de çalıştırabilirsiniz.  
  
4. **Bu kural kümesini Çalıştır** listesinde aşağıdakilerden birini yapın:  
  
    - Kullanmak istediğiniz kural kümesini seçin.  
  
    - **\<gözatmaya seç...** listede olmayan mevcut bir özel kural kümesini belirtmek için >.  
  
    - Özel bir kural kümesi tanımlayın.  
  
         Daha fazla bilgi için bkz. [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Standart C/C++ kural kümeleri  
 Visual Studio yerel kod için iki standart kural kümesi içerir:  
  
|Kural kümesi|Açıklama|  
|--------------|-----------------|  
|Microsoft yerel en düşük önerilen kurallar|Bu kural kümesi, olası güvenlik delikleri ve uygulama kilitlenmeleri dahil olmak üzere yerel kodunuzda en kritik sorunlara odaklanır. Bu kural kümesini yerel projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmelisiniz.|  
|Microsoft yerel önerilen kurallar|Bu kural kümesi, çok çeşitli sorunları ele alır. Microsoft yerel en düşük önerilen kuralların tüm kurallarını içerir.|  
  
## <a name="BKMK_Run"></a>Kod analizini Çalıştır  
 Proje özellikleri sayfalarının kod analizi sayfasında, Kod analizini projenizi her oluşturduğunuzda çalışacak şekilde yapılandırabilirsiniz. Ayrıca, Kod analizini el ile de çalıştırabilirsiniz.  
  
 Bir çözümde Kod Analizi çalıştırmak için:  
  
- **Build** menüsünde, **çözüm üzerinde Kod analizini Çalıştır**' ı seçin.  
  
  Bir projede kod analizini çalıştırmak için:  
  
- Çözüm Gezgini, projenin adını seçin.  
  
- **Yapı** menüsünde, *Proje adı* **üzerinde Kod analizini Çalıştır** ' ı seçin.  
  
  Proje veya çözüm derlenir ve kod analizi çalışır. Sonuçları Kod Analizi penceresinde görünür.  
  
## <a name="BKMK_Analyze"></a>Kod Analizi uyarılarını çözümleyin ve çözümleyin  
 Belirli bir uyarıyı çözümlemek için Kod Analizi penceresi içinde uyarı başlığı seçin. Uyarı, sorunla ilgili ek bilgileri görüntüleyecek şekilde genişler. Mümkün olduğunda, kod analizi uyarıya yol gösteren satır numaralarını ve analiz mantığını görüntüler. Soruna yönelik olası çözümler dahil olmak üzere uyarı hakkında ayrıntılı bilgi için, ileti için MSND kitaplığındaki yardım konusunu göstermek üzere uyarı kimliğini seçin.  
  
 Bir uyarı genişlettiğinizde, Visual Studio Kod Düzenleyicisi'nde uyarıya yol açan kod satırının vurgulanır.  
  
 Sorun anladıktan sonra kodunuzu çözebilirsiniz. Ardından uyarı artık Kod Analizi penceresi açılır ve düzeltmenizi henüz yeni uyarılar ortaya emin olmak için kod analizini yeniden çalıştırın.  
  
> [!TIP]
> Kod analizinden kaynaklanan Kod Analizi penceresi yeniden çalıştırabilirsiniz. **Çözümle** düğmesini seçin ve analizin kapsamını seçin. Seçilen proje veya çözümün tamamını üzerinde analiz yeniden çalıştırabilirsiniz.  
  
## <a name="BKMK_Suppress"></a>Kod Analizi uyarılarını gizleme  
 Kod Analizi uyarısı düzeltmemeyi ne zaman karar verebilirsiniz zamanlar vardır. Uyarı çözümleme sorunu kodunuzun tüm gerçek uygulamasında ortaya çıkacağını olasılık ile ilgili çok fazla değiştirilemeyen gerektirir karar verebilirsiniz. Veya uyarıda kullanılan analiz belirli bir içerik için uygun olduğunu düşündüğünüz. Artık Kod Analizi penceresinde görünecekleri bireysel uyarıları gösterilmemesini sağlayabilirsiniz.  
  
 Bir uyarıyı bastırmak için:  
  
1. Ayrıntılı bilgiler görüntülenmiyorsa, genişletilecek uyarının başlığını seçin.  
  
2. Uyarının altındaki **Eylemler** bağlantısını seçin.  
  
3. **Iletiyi Gizle** ' yi ve ardından **kaynak '** ı seçin.  
  
   İletiyi gizleme, kod satırı için uyarıyı gösteren `#pragma warning (disable:`*Warnıngıd*`)` ekler.  
  
## <a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a>Kod Analizi uyarıları için iş öğeleri oluşturma  
 Visual Studio içinden hataları günlüğe kaydetmek için çalışma öğesi izleme özelliğini kullanabilirsiniz. Bu özelliği kullanmak için bir Team Foundation Server örneğine bağlanmanız gerekir.  
  
 **Bir veya daha fazla C/C++ kod uyarısı için bir iş öğesi oluşturmak için**  
  
1. Kod Analizi penceresinde, uyarıları genişletip seçin  
  
2. Uyarıların kısayol menüsünde, **Iş öğesi oluştur**' u seçin ve sonra iş öğesi türünü seçin.  
  
3. Visual Studio Seçili uyarılar için tek bir iş öğesi oluşturur ve iş öğesini IDE 'nin bir belge penceresinde görüntüler.  
  
4. Ek bilgileri ekleyin ve sonra **Iş öğesini kaydet**' i seçin.  
  
## <a name="BKMK_Search"></a>Kod analizi sonuçlarını arama ve filtreleme  
 Uzun listesi uyarı iletilerini arayabilir ve çoklu proje çözümlerinde uyarıları filtreleyebilirsiniz.  
  
1. **Uyarıları başlığa veya uyarı kimliğine göre filtrelemek için**: **filtre** metin kutusuna anahtar sözcüğünü girin.  
  
2. **Uyarıları projeye göre filtrelemek için**: çoklu proje çözümünde, kod analizi penceresinin sağ üst kısmındaki listeden bir veya daha fazla proje seçin. Tüm uyarıları göstermek için çözüm adını seçin.  
  
3. **Uyarıları önem derecesine göre filtrelemek için**: varsayılan olarak, kod analizi Iletilerine bir **Uyarı**önem derecesi atanır. Bir veya daha fazla iletinin önem derecesini özel bir kural kümesinde **hata** olarak atayabilirsiniz. Yalnızca ilgili önem derecesine atanmış iletileri göstermek için **Uyarı** ya da **hata** ' ı seçin. Tüm iletileri göstermek için **Tümü** ' ni seçin.
