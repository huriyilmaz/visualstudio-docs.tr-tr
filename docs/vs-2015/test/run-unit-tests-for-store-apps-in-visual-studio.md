---
title: Mağaza uygulamaları için birim testlerini çalıştırma
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b70e3a24cd4cb05dc1a28ff855498496f5665ddc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542863"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Visual Studio 'da Mağaza uygulamaları için birim testleri çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu başlığı altında, test Gezgini kullanılarak birim testlerinin nasıl çalıştırılacağı açıklanmaktadır Microsoft Visual Studio

> [!NOTE]
> Bu bölümdeki konularda, Windows 8 ' in Visual Studio Express işlevleri açıklanır. Visual Studio Community, Enterprise ve Professional birim testi için ek özellikler sağlar.
>
> - Microsoft Test Gezgini için bir eklenti bağdaştırıcısı oluşturmuş olan herhangi bir üçüncü taraf veya açık kaynak birim testi çerçevesini kullanın. Ayrıca, testleriniz için kod kapsamı bilgilerini çözümleyebilir ve görüntüleyebilirsiniz.
>   - Her derlemeden sonra testlerinizi çalıştırın. Ayrıca, sistem ve üçüncü taraf işlevselliği için test kodunu değiştirerek testlerinizi kendi kodunuzda odaklamak üzere yönetilen kod için bir yalıtım çerçevesi olan Microsoft Fakes 'i de kullanabilirsiniz.
>
>   Daha fazla bilgi için bkz. MSDN Kitaplığı 'nda [kodunuzda birim testi](../test/unit-test-your-code.md) .

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konuda
 [Birim test çerçeveleri ve test projeleri](#BKMK_Unit_test_frameworks_and_test_projects)

 [Test Gezgini 'nde testleri çalıştırma](#BKMK_Running_tests_in_Test_Explorer)

- [Testleri çalıştırma](#BKMK_Running_tests)

  [Test sonuçlarını görüntüleme](#BKMK_Viewing_test_results)

- [Test ayrıntılarını görüntüleme](#BKMK_Viewing_test_details)

- [Test yönteminin kaynak kodunu görüntüleme](#BKMK_Viewing_the_source_code_of_a_test_method)

  [Test listesini düzenleme](#BKMK_Organizing_the_test_list)

- [Testleri Gruplandırma](#BKMK_Grouping_tests)

- [Test listesini arama ve filtreleme](#BKMK_Searching_and_filtering_the_test_list)

  [Birim testlerinde hata ayıklama](#BKMK_Debugging_unit_tests)

## <a name="unit-test-frameworks-and-test-projects"></a><a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Birim test çerçeveleri ve test projeleri
 Windows Mağazası uygulamaları için Visual Studio Express, yönetilen ve yerel C++ kodu için Microsoft birim testi çerçeveleri içerir. Test Gezgini, bir çözümde ve üretim kodu projelerinin parçası olan test sınıflarından birden çok test projesinin testlerini çalıştırabilir. Test projeleri Visual C++ veya Visual C# ve Visual Basic birim test çerçevelerinin herhangi bir birleşimi olabilir. Test altındaki kod .NET Framework için yazıldığında, hedef kodun dilinden bağımsız olarak test projesi herhangi bir .NET Framework dilinde yazılabilir. Yerel C/C++ kod projeleri bir C++ birim testi çerçevesi kullanılarak test edilmiş olmalıdır.

## <a name="running-tests-in-test-explorer"></a><a name="BKMK_Running_tests_in_Test_Explorer"></a> Test Gezgini 'nde testleri çalıştırma
 Test projesi oluşturduğunuzda, testler test Gezgini 'nde görünür. Test Gezgini görünür değilse, Visual Studio menüsünden **Test** ' i seçin, **Windows**' u ve ardından **Test Gezgini**' ni seçin.

 ![Birim test Gezgini](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

 Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler, **Atlanan** testler ve **çalıştırma**testleri için varsayılan gruplar halinde görüntüler. Test Gezgini 'nin testlerinizi gruplandırma yöntemini değiştirebilirsiniz.

 Test Gezgini araç çubuğundan testleri bulma, düzenleme ve çalıştırma işinin çoğunu yapabilirsiniz.

 ![Testleri test Gezgini araç çubuğundan Çalıştır](../test/media/ute-toolbar.png "UTE_ToolBar")

### <a name="running-tests"></a><a name="BKMK_Running_tests"></a> Testleri çalıştırma
 Çözümdeki tüm testleri, bir gruptaki tüm testleri veya seçtiğiniz bir test kümesini çalıştırabilirsiniz. Şunlardan birini yapın:

- Bir Çözümdeki tüm testleri çalıştırmak için **Tümünü Çalıştır**' ı seçin.

- Varsayılan bir gruptaki tüm testleri çalıştırmak için **Çalıştır...** öğesini seçin ve ardından menüdeki grubu seçin.

- Çalıştırmak istediğiniz bireysel testleri seçin, seçili bir test için kısayol menüsünü açın ve ardından **Seçili Testleri Çalıştır**' ı seçin.

  Test Gezgini penceresinin en üstündeki geçiş/başarısızlık çubuğu, testler çalışırken hareketlendirilir. Test çalıştırmasının sonunda, herhangi bir test başarısız olursa tüm testler başarılı veya Red durumunda, geçiş/başarısızlık çubuğu yeşile dönüşür.

## <a name="viewing-test-results"></a><a name="BKMK_Viewing_test_results"></a> Test sonuçlarını görüntüleme
 Testlerinizi çalıştırırken, yazarken ve yeniden çalıştırdığınızda, test Gezgini sonuçları **başarısız testler**, **başarılı**testler, **Atlanan testler** ve **çalıştırma testleri**gruplarında görüntüler. Test Gezgini ' nin altındaki Ayrıntılar bölmesi Test çalıştırmasının bir özetini görüntüler.

### <a name="viewing-test-details"></a><a name="BKMK_Viewing_test_details"></a> Test ayrıntılarını görüntüleme
 Tek bir testin ayrıntılarını görüntülemek için, testi seçin.

 Test ayrıntıları bölmesi aşağıdaki bilgileri görüntüler:

- Test yönteminin kaynak dosya adı ve satır numarası.

- Testin durumu.

- Test yönteminin çalışması için geçen geçen süre.

  Test başarısız olursa, Ayrıntılar bölmesi şunları da görüntüler:

- Test için birim test çerçevesi tarafından döndürülen ileti.

- Testin başarısız olduğu zamanda yığın izlemesi.

### <a name="viewing-the-source-code-of-a-test-method"></a><a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Test yönteminin kaynak kodunu görüntüleme
 Visual Studio düzenleyicisinde bir test yönteminin kaynak kodunu göstermek için, testi seçin ve ardından kısayol menüsünde **testi aç** ' ı seçin (klavye: F12).

## <a name="organizing-the-test-list"></a><a name="BKMK_Organizing_the_test_list"></a> Test listesini düzenleme

### <a name="grouping-tests"></a><a name="BKMK_Grouping_tests"></a> Testleri Gruplandırma
 Varsayılan olarak, test Gezgini testlerinizi **başarısız testlerin**alt düğümleri olarak görüntüler, **başarılı testler**, **Atlanan** testler ve **çalıştırma testleri değildir**.

|Görüntü|Description|
|-|-|
|![Test Gezgini Grup düğmesi](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Testlerinizi yürütmek için gereken zamana göre gruplandırmak için **Gruplandırma ölçütü** listesini açın ve **süre**' yi seçin. Özgün gruplandırmaya geçiş yapmak için **test sonucu** ' nı seçin.|

### <a name="searching-and-filtering-the-test-list"></a><a name="BKMK_Searching_and_filtering_the_test_list"></a> Test listesini arama ve filtreleme
 Çok sayıda testiniz olduğunda, listeyi belirtilen dizeye göre filtrelemek için test Gezgini arama kutusunu yazabilirsiniz. Arama dizesini girmeden önce filtre listesinden seçim yaparak filtrenizi belirli tür dizeler ile kısıtlayabilirsiniz.

 ![Filtre kategorilerini ara](../test/media/ute-searchfilter.png "UTE_SearchFilter")

## <a name="debugging-unit-tests"></a><a name="BKMK_Debugging_unit_tests"></a> Birim testlerinde hata ayıklama
 Testleriniz için bir hata ayıklama oturumu başlatmak üzere test Gezgini ' ni kullanabilirsiniz. Visual Studio hata ayıklayıcı ile kodunuzda adım adım geçiş, birim testleri ve test edilen proje arasında sorunsuz bir şekilde geri ve ileri doğru bir şekilde gerçekleşir. Hata ayıklamayı başlatmak için:

1. Visual Studio düzenleyicisinde, hata ayıklamak istediğiniz bir veya daha fazla test yöntemlerinde bir kesme noktası ayarlayın.

   > [!NOTE]
   > Test yöntemleri herhangi bir sırada çalıştırılabildiğinden, hata ayıklamak istediğiniz tüm test yöntemlerinde kesme noktaları ayarlayın.

2. Test Gezgini 'nde test yöntemlerini seçin ve ardından kısayol menüsünde **Seçili testlerin hatalarını ayıkla** ' yı seçin.

   Hata ayıklayıcı hakkında daha fazla bilgi için bkz. [Visual Studio 'Da hata ayıklama](../debugger/debugging-in-visual-studio.md).
