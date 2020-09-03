---
title: 'Hızlı başlangıç: C için kod analizi-C + + | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278488"
---
# <a name="quick-start-code-analysis-for-cc"></a>Hızlı Başlangıç: C/C++ İçin Kod Analizi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod analizini düzenli olarak C veya C++ kodunda çalıştırarak uygulamanızın kalitesini artırabilirsiniz. Bu, yaygın sorunları, iyi programlama uygulaması ihlallerini veya test aracılığıyla bulmanın zor olduğu kusurları bulmanıza yardımcı olabilir. Kod Analizi, derleyici hatalarından ve uyarılarından farklıdır, ancak sizin için veya kodunuzu kullanan diğer kişiler için hala sorun oluşturabilir.  
  
## <a name="in-this-topic"></a>Bu konuda  
  
- [Bir proje için kural kümelerini yapılandırma](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_ConfigureRuleSets)  
  
- [Kod analizini Çalıştır](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Run)  
  
- [Kod Analizi uyarılarını çözümleyin ve çözümleyin](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Analyze)  
  
- [Kod Analizi uyarılarını gizleme](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Suppress)  
  
- [Kod Analizi uyarıları için iş öğeleri oluşturma](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Creating_work_items_for_code_analysis_warnings)  
  
- [Kod analizi sonuçlarını arama ve filtreleme](../code-quality/quick-start-code-analysis-for-c-cpp.md#BKMK_Search)  
  
## <a name="configure-rule-sets-for-a-project"></a><a name="BKMK_ConfigureRuleSets"></a> Bir proje için kural kümelerini yapılandırma  
  
1. **Çözüm Gezgini**, proje adı için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. Aşağıdaki adımlar isteğe bağlıdır:  
  
    1. **Yapılandırma** ve **Platform** listelerinde, derleme yapılandırması ve hedef platform ' u seçin.  
  
    2. Varsayılan olarak, kod analizi dış araçlar tarafından otomatik olarak oluşturulan koddan uyarı raporlamaz. Oluşturulan koddan gelen uyarıları görüntülemek için, **oluşturulan koddan sonuçları bastır** onay kutusunun işaretini kaldırın.  
  
        > [!NOTE]
        > Bu seçenek, hatalar ve uyarılar formlarda ve şablonlarda görüntülendiğinde, kod analizi hatalarını ve üretilen koddan gelen uyarıları göstermez. Bir form veya şablon için kaynak kodu görüntüleyebilir ve bakımını yapabilirsiniz.  
  
3. Projenin seçili yapılandırma kullanılarak oluşturulduğu her seferinde Kod analizini çalıştırmak için, **derlemede C/C++ Için kod analizini etkinleştir** onay kutusunu seçin. Ayrıca, **Çözümle** menüsünü açıp *ProjectName* **üzerinde Kod analizini Çalıştır '** ı seçerek Kod analizini el ile de çalıştırabilirsiniz.  
  
4. **Bu kural kümesini Çalıştır** listesinde aşağıdakilerden birini yapın:  
  
    - Kullanmak istediğiniz kural kümesini seçin.  
  
    - **\<Browse...>** Listede olmayan mevcut bir özel kural kümesini belirtmeyi seçin.  
  
    - Özel bir kural kümesi tanımlayın.  
  
         Daha fazla bilgi için bkz. [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
### <a name="standard-cc-rule-sets"></a>Standart C/C++ kural kümeleri  
 Visual Studio yerel kod için iki standart kural kümesi içerir:  
  
|Kural kümesi|Description|  
|--------------|-----------------|  
|Microsoft yerel en düşük önerilen kurallar|Bu kural kümesi, olası güvenlik delikleri ve uygulama kilitlenmeleri dahil olmak üzere yerel kodunuzda en kritik sorunlara odaklanır. Bu kural kümesini yerel projeleriniz için oluşturduğunuz herhangi bir özel kural kümesine dahil etmelisiniz.|  
|Microsoft yerel önerilen kurallar|Bu kural kümesi, çok çeşitli sorunları ele alır. Microsoft yerel en düşük önerilen kuralların tüm kurallarını içerir.|  
  
## <a name="run-code-analysis"></a><a name="BKMK_Run"></a> Kod analizini Çalıştır  
 Proje özellikleri sayfalarının kod analizi sayfasında, Kod analizini projenizi her oluşturduğunuzda çalışacak şekilde yapılandırabilirsiniz. Ayrıca, Kod analizini el ile de çalıştırabilirsiniz.  
  
 Bir çözümde Kod Analizi çalıştırmak için:  
  
- **Build** menüsünde, **çözüm üzerinde Kod analizini Çalıştır**' ı seçin.  
  
  Bir projede kod analizini çalıştırmak için:  
  
- Çözüm Gezgini, projenin adını seçin.  
  
- **Yapı** menüsünde, *Proje adı* **üzerinde Kod analizini Çalıştır** ' ı seçin.  
  
  Proje veya çözüm derlenir ve kod analizi çalışır. Sonuçlar Kod Analizi penceresinde görünür.  
  
## <a name="analyze-and-resolve-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Kod Analizi uyarılarını çözümleyin ve çözümleyin  
 Belirli bir uyarıyı çözümlemek için, Kod Analizi penceresinde uyarının başlığını seçin. Uyarı, sorunla ilgili ek bilgileri görüntüleyecek şekilde genişler. Mümkün olduğunda, kod analizi uyarıya yol gösteren satır numaralarını ve analiz mantığını görüntüler. Soruna yönelik olası çözümler dahil olmak üzere uyarı hakkında ayrıntılı bilgi için, ileti için MSND kitaplığındaki yardım konusunu göstermek üzere uyarı kimliğini seçin.  
  
 Bir uyarı genişlettiğinizde, uyarıya neden olan kod satırı, Visual Studio kod Düzenleyicisi 'nde vurgulanır.  
  
 Sorunu anladıktan sonra kodunuzda çözebilirsiniz. Daha sonra uyarının Kod Analizi penceresinde göründüğünden ve düzelmenizin yeni uyarılar gerçekleştirmediğinden emin olmak için kod analizini yeniden çalıştırın.  
  
> [!TIP]
> Kod Analizi penceresinden Kod analizini yeniden çalıştırabilirsiniz. **Çözümle** düğmesini seçin ve analizin kapsamını seçin. Çözümlemeyi çözümün tamamında veya seçili bir projede yeniden çalıştırabilirsiniz.  
  
## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Kod Analizi uyarılarını gizleme  
 Kod Analizi uyarısının düzeltilmeyeceğine karar verirken zamanlar olabilir. Uyarı çözmenin, kodunuzun gerçek hayatta herhangi bir uygulamada ortaya çıkması olasılığa göre çok fazla kaynak gerektirir. Ya da uyarıda kullanılan çözümlemenin belirli bir bağlam için uygun olmadığından emin olabilirsiniz. Kod Analizi penceresinde artık görünmemek için tek tek uyarıları bastırın.  
  
 Bir uyarıyı bastırmak için:  
  
1. Ayrıntılı bilgiler görüntülenmiyorsa, genişletilecek uyarının başlığını seçin.  
  
2. Uyarının altındaki **Eylemler** bağlantısını seçin.  
  
3. **Iletiyi Gizle** ' yi ve ardından **kaynak '** ı seçin.  
  
   Bir iletinin gizlenmesi `#pragma warning (disable:` *WarningId* `)` , kod satırıyla ilgili uyarıyı belirten warnıngıd öğesini ekler.  
  
## <a name="creating-work-items-for-code-analysis-warnings"></a><a name="BKMK_Creating_work_items_for_code_analysis_warnings"></a> Kod Analizi uyarıları için iş öğeleri oluşturma  
 Visual Studio içinden hataları günlüğe kaydetmek için çalışma öğesi izleme özelliğini kullanabilirsiniz. Bu özelliği kullanmak için bir Team Foundation Server örneğine bağlanmanız gerekir.  
  
 **Bir veya daha fazla C/C++ kod uyarısı için bir iş öğesi oluşturmak için**  
  
1. Kod Analizi penceresinde, uyarıları genişletip seçin  
  
2. Uyarıların kısayol menüsünde, **Iş öğesi oluştur**' u seçin ve sonra iş öğesi türünü seçin.  
  
3. Visual Studio Seçili uyarılar için tek bir iş öğesi oluşturur ve iş öğesini IDE 'nin bir belge penceresinde görüntüler.  
  
4. Ek bilgileri ekleyin ve sonra **Iş öğesini kaydet**' i seçin.  
  
## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Kod analizi sonuçlarını arama ve filtreleme  
 Uyarı iletilerinin uzun listelerinde arama yapabilir ve çok projeli çözümlerde uyarıları filtreleyebilirsiniz.  
  
1. **Uyarıları başlığa veya uyarı kimliğine göre filtrelemek için**: **filtre** metin kutusuna anahtar sözcüğünü girin.  
  
2. **Uyarıları projeye göre filtrelemek için**: çoklu proje çözümünde, kod analizi penceresinin sağ üst kısmındaki listeden bir veya daha fazla proje seçin. Tüm uyarıları göstermek için çözüm adını seçin.  
  
3. **Uyarıları önem derecesine göre filtrelemek için**: varsayılan olarak, kod analizi Iletilerine bir **Uyarı**önem derecesi atanır. Bir veya daha fazla iletinin önem derecesini özel bir kural kümesinde **hata** olarak atayabilirsiniz. Yalnızca ilgili önem derecesine atanmış iletileri göstermek için **Uyarı** ya da **hata** ' ı seçin. Tüm iletileri göstermek için **Tümü** ' ni seçin.
