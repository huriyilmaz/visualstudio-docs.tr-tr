---
title: Kodunuzda birim testi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, unit tests
- unit tests, verifying code with
- testing code, automated tests
ms.assetid: c191de3e-3f3b-471e-b828-29ec24e80e2c
caps.latest.revision: 64
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7a8b9a4b52fce5fb838c12ccf057fd0e80619cd7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851252"
---
# <a name="unit-test-your-code"></a>Kodunuza Birim Testi Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birim testleri, geliştiricilere ve test edicilere,, ve projeleri içindeki sınıfların yöntemlerinde mantık hataları aramak için hızlı bir yol sağlar [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)] [!INCLUDE[cpp_current_short](../includes/cpp-current-short-md.md)] .

 Birim testi araçları şunları içerir:

1. **Test Gezgini.** Test Gezgini, birim testleri çalıştırmanıza ve sonuçları görüntülemenize izin verir. Test Gezgini, üçüncü taraf çerçeve dahil, Gezgin için bağdaştırıcısı olan herhangi bir test çerçevesini kullanabilir.

2. **Yönetilen kod için Microsoft birim testi çerçevesi.** Yönetilen kod için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve .NET kodunu test etmek için bir çerçeve sağlar.

3. **C++ için Microsoft birim testi çerçevesi.** C++ için Microsoft birim testi çerçevesi Visual Studio ile yüklenir ve yerel kodu test etmek için bir çerçeve sağlar.

4. **Kod kapsamı araçları.** Test Gezgini'nde bir tek komuttan birim testlerinizin çalıştıracağı ürün kodu miktarını belirleyebilirsiniz.

5. **Microsoft Fakes yalıtım çerçevesi.** Microsoft Fakes yalıtım çerçevesi, test edilen kodda bağımlılıklar oluşturan üretim ve sistem kodunun yerine geçecek sınıflar ve yöntemler oluşturabilir. Bir işlev için sahte temsilciler uygulayarak, bağımlılık nesnesinin davranışını ve çıkışını denetlersiniz.

   Ayrıca, test verileri ve birim testleri paketi oluşturmak üzere .NET kodunuzu araştırmak için [IntelliTest](../test/generate-unit-tests-for-your-code-with-intellitest.md) ' i de kullanabilirsiniz. Koddaki her deyimin için, bu ifadeyi yürütecek bir test girişi oluşturulur. Koddaki her koşullu dal için bir olay Analizi gerçekleştirilir.

## <a name="key-tasks"></a>Ana görevler
 Birim testlerini anlamaya ve oluşturmaya yardımcı olmaları için aşağıdaki konuları kullanın:

|Görevler|İlişkili Konular|
|-----------|-----------------------|
|**Hızlı başlar ve izlenecek yollar:** Kod örneklerinden Visual Studio 'da birim testini öğrenmek için aşağıdaki konuları kullanın.|-   [İzlenecek yol: yönetilen kod için birim testleri oluşturma ve çalıştırma](../test/walkthrough-creating-and-running-unit-tests-for-managed-code.md)<br />-   [Hızlı başlangıç: Test Gezgini ile test temelli geliştirme](../test/quick-start-test-driven-development-with-test-explorer.md)<br />-   [Mevcut C++ uygulamalarına birim testleri ekleme](../test/unit-testing-existing-cpp-applications-with-test-explorer.md)<br />-   [Test Gezgini ile yerel kod birim testi](https://msdn.microsoft.com/8a09d6d8-3613-49d8-9ffe-11375ac4736c)|
|**Test Gezgini Ile birim testi:** Test Gezgini 'nin daha üretken ve verimli birim testleri oluşturmaya nasıl yardımcı olabileceğini öğrenin.|-   [Birim testi temelleri](../test/unit-test-basics.md)<br />-   [Birim testi projesi oluşturma](../test/create-a-unit-test-project.md)<br />-   [Test Gezgini ile birim testleri çalıştırma](../test/run-unit-tests-with-test-explorer.md)<br />-   [Üçüncü taraf birim testi çerçeveleri 'ni yükler](../test/install-third-party-unit-test-frameworks.md)<br />-   [Visual Studio 2010 ' den birim testlerini yükseltme](https://msdn.microsoft.com/9bb75856-f68a-4de2-a084-b08a947a1172)|
|**Birim testi yönetilen kodu:**|-   [Yönetilen kod için Microsoft birim testi çerçevesi ile .NET Framework için birim testleri yazma](../test/writing-unit-tests-for-the-dotnet-framework-with-the-microsoft-unit-test-framework-for-managed-code.md)|
|**Birim testi C++ kodu**|-   [C++ için Microsoft birim testi çerçevesi ile C/C++ için birim testleri yazma](../test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp.md)|
|**Birim testlerini yalıtma**|-   [Microsoft Fakes ile test edilen kodu yalıtma](../test/isolating-code-under-test-with-microsoft-fakes.md)|
|**Proje kodunuzun birim testleri kullanılarak ne oranda test edildiğini belirlemek için kod kapsamını kullanın:** Test araçlarının kod kapsamı özelliği hakkında bilgi edinin [!INCLUDE[vsprvsts](../includes/vsprvsts-md.md)] .|-   [Ne kadar kodun test edildiğini öğrenmek için kod kapsamını kullanma](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md)|
|**Birim testleriniz için yük testlerini kullanarak stres ve performans analizini gerçekleştirin:** Uygulamanızdaki performans ve stres sorunlarını yalıtmaya yardımcı olmak için bir yük testi oluşturabilir ve birim testlerinizi buna ekleyebilirsiniz. **Note:**  Yük testlerinin oluşturulması ve kullanılması Visual Studio Enterprise gerekir.|-   [Yük testleri oluşturma ve bunları Düzenle](https://msdn.microsoft.com/e2985d15-60a7-4177-93b4-f986c2936337)<br />-   [Nasıl yapılır: yük testi senaryosuna Web performans testleri ve birim testleri ekleme](https://msdn.microsoft.com/03cc073e-9bdf-4530-ae46-504a51884594)<br />-   [Nasıl yapılır: yük testi senaryosundan Web testlerini ve birim testlerini kaldırma](https://msdn.microsoft.com/3d6128d2-82b0-42fc-bda2-23a8aa03be07)|
|**Kalite kapıları ayarlama ve zorlama:** Kodun kalitesini sağlamaya yardımcı olmak için testlerin kod iade etmeden önce çalıştırılmasını zorlamak için kalite kapıları oluşturabilirsiniz.|-   [Kalite kapıları ayarlama ve zorlama](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)|
|**Birim test türünü genişletin:** Testlerinizi, birim testi çerçevesinde bulunmayabilir, testleriniz için işlevler ekleyebilirsiniz. Örneğin, bir testin normal kullanıcı olarak çalışıp çalışmayacağını belirten bir test özelliği ekleyebilirsiniz. Veya çerçeveyi, bir yönteme satır öznitelikleri eklemek ve bu satırda bulunan verileri testin içinde kullanmak üzere genişletebilirsiniz.|Birim testi çerçevesinin nasıl genişletileceği hakkında örnek kod için aşağıdaki [Microsoft Web sitesine](https://msdn.microsoft.com/vstudio/ff420671.aspx)bakın.|
|**Test seçeneklerini ayarla:** Örneğin, test sonuçlarının nerede depolandığını belirtebilirsiniz.|[.runsettings dosyasını kullanarak birim testlerini yapılandırma](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)|

## <a name="related-tasks"></a>İlişkili görevler
 [Microsoft Test Yöneticisi Test Sonuçları gözden geçirme](https://msdn.microsoft.com/9fb3e429-78df-4fe2-89ed-0ad1db0738f4)

 Test sonuçları ve nasıl görüntülendiği, kaydedildiği ve silindiği de dahil bunlarla çalışma yollarını açıklar.

 [Microsoft Visual Studio kullanarak sistem testlerini çalıştırma](https://msdn.microsoft.com/library/19fae5c4-5798-4c4c-b531-3e8f901b1130)

 Otomatikleştirilmiş testleri çalıştırmak için kullanarak Visual Studio 'Yu kullanmayla ilgili bilgilere bağlantılar sağlar [!INCLUDE[TCMext](../includes/tcmext-md.md)] .

## <a name="reference"></a>Başvuru
 <xref:Microsoft.VisualStudio.TestTools.UnitTesting> Öznitelikleri, özel durumları, onayları ve birim testini destekleyen diğer sınıfları sağlayan UnitTesting Ad alanını açıklar.

 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Web> Ve Web hizmeti birim testleri için destek sağlayarak UnitTesting Ad alanını genişleten UnitTesting. Web ad alanını açıklar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .

## <a name="external-resources"></a>Dış kaynaklar

### <a name="videos"></a>Videolar
 [Channel 9: XAML kullanılarak oluşturulan Windows Mağazası uygulamalarınızı birim testi yapma](https://channel9.msdn.com/Events/BUILD/BUILD2011/TOOL-529T)

### <a name="forums"></a>Forumlar
 [Visual Studio birim testi](https://social.msdn.microsoft.com/Forums/en/vsunittest/threads)

### <a name="guidance"></a>Rehber
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 2: birim testi: Içini test etme](https://msdn.microsoft.com/library/jj159340.aspx)

### <a name="reference"></a>Başvuru
 [Birim testleri için içerik dizini](https://blogs.msdn.com/b/mathew_aniyan/archive/2012/05/17/content-index-for-unit-test.aspx)

## <a name="see-also"></a>Ayrıca Bkz.
 Uygulamanın [kod kalitesi](https://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945) [sınamasını](https://msdn.microsoft.com/library/796b7d6d-ad45-4772-9719-55eaf5490dac) geliştirme
