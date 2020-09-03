---
title: Statik kod analizini kullanarak Mağaza uygulamalarında Visual Basic ve C# kod kalitesini analiz etme
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb.express
ms.assetid: cab553fc-19a9-4cbf-858e-8200258ffe50
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cfe5ed57bfc361b711ed2aceceff2aabfc44cf4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660732"
---
# <a name="analyze-visual-basic-and-c-code-quality-in-store-apps-using-visual-studio-static-code-analysis"></a>Visual Studio statik Kod analizini kullanarak Mağaza uygulamalarında Visual Basic ve C# kod kalitesini analiz etme

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows ve Windows Phone] için geçerlidir (.. /Image/windows_and_phone_content.png "windows_and_phone_content")

 ' Visual Studio Express deki kod Analizi Aracı, kodunuzun bir dizi ortak kusur ve iyi programlama uygulaması ihlallerini inceler. Kod Analizi uyarıları derleyici hatalarından ve uyarılarından farklıdır, ancak siz veya kodunuzu kullanan diğer kişiler için hala sorun oluşturabilir. Kod Analizi, kodunuzda test aracılığıyla keşfedilmesi zor olan kusurları da bulabilir. Geliştirme işleminiz sırasında kod analizi aracını düzenli aralıklarla çalıştırmak, tamamlanmış uygulamanızın kalitesini artırabilir.

> [!NOTE]
> Visual Studio Ultimate, Visual Studio Premium ve Visual Studio Professional, kod analizinin tüm işlevselliğini kullanabilirsiniz. Bkz. MSDN kitaplığındaki [kod analizi araçlarını kullanarak uygulama kalitesini analiz etme](https://msdn.microsoft.com/library/dd264897.aspx) .

## <a name="in-this-topic"></a>Bu konuda
 Hakkında bilgi edinebilirsiniz:

 [Kod analizini çalıştırma](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Run)

 [Kod Analizi uyarılarını çözümleme ve çözme](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Analyze)

 [Kod Analizi uyarılarını gizleme](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Suppress)

 [Kod analizi sonuçlarını arama ve filtreleme](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Search)

 [Visual Basic ve C# kod analizi uyarıları](../test/analyze-visual-basic-and-csharp-code-quality-in-store-apps-using-visual-studio-static-code-analysis.md#BKMK_Warnings)

## <a name="running-code-analysis"></a><a name="BKMK_Run"></a> Kod analizini çalıştırma
 Visual Studio Çözümünüzde kod analizini çalıştırmak için:

- **Build** menüsünde, **çözüm üzerinde Kod analizini Çalıştır**' ı seçin.

  Her proje oluşturduğunuzda Kod analizini otomatik olarak çalıştırmak için:

1. Çözüm Gezgini ' de proje adına sağ tıklayın ve ardından **Özellikler**' i seçin.

2. Proje özelliği sayfasında, **Kod Analizi** ' ni seçin ve ardından **derlemede Kod analizini etkinleştir ' i SEÇIN (CodeAnalysis sabitini tanımlar)**.

   Çözüm derlenir ve kod analizi çalışır. Sonuçlar Kod Analizi penceresinde görünür.

   ![Kod Analizi penceresi](../test/media/ca-managed-collapsed.png "CA_Managed_Collapsed")

## <a name="analyzing-and-resolving-code-analysis-warnings"></a><a name="BKMK_Analyze"></a> Kod Analizi uyarılarını çözümleme ve çözme
 Belirli bir uyarıyı çözümlemek için, Kod Analizi penceresinde uyarının başlığına tıklayın. Uyarı, sorunla ilgili ayrıntılı bilgileri görüntüleyecek şekilde genişler.

 ![Genişletilmiş kod analizi uyarısı](../test/media/ca-managed-callouts.png "CA_Managed_Callouts")

 Bir uyarı genişlettiğinizde, uyarıya neden olan kod satırı, Visual Studio kod Düzenleyicisi 'nde vurgulanır.

 ![Kod Analizi metin vurgulama](../test/media/ca-managed-sourceline.png "CA_Managed_SourceLine")

 Sorunu anladıktan sonra kodunuzda çözebilirsiniz. Daha sonra uyarının Kod Analizi penceresinde göründüğünden ve düzelmenizin yeni uyarılar gerçekleştirmediğinden emin olmak için kod analizini yeniden çalıştırın.

> [!TIP]
> Kod Analizi penceresinden Kod analizini yeniden çalıştırabilirsiniz. **Çözümle** düğmesine tıklayın ve analizin kapsamını seçin. Çözümlemeyi çözümün tamamında veya seçili bir projede yeniden çalıştırabilirsiniz.

## <a name="suppressing-code-analysis-warnings"></a><a name="BKMK_Suppress"></a> Kod Analizi uyarılarını gizleme
 Kod Analizi uyarısının düzeltilmeyeceğine karar verirken zamanlar olabilir. Uyarı çözmenin, kodunuzun gerçek hayatta herhangi bir uygulamada ortaya çıkması olasılığa göre çok fazla kaynak gerektirir. Ya da uyarıda kullanılan çözümlemenin belirli bir bağlam için uygun olmadığından emin olabilirsiniz. Kod Analizi penceresinde artık görünmemek için tek tek uyarıları bastırın.

 Bir uyarıyı bastırmak için:

1. Ayrıntılı bilgiler görüntülenmiyorsa, genişletilecek uyarının başlığına tıklayın.

2. Uyarının altındaki **Eylemler** bağlantısını seçin.

3. **Iletiyi bastır** ' ın üzerine gelin ve **kaynak** ya da **gizleme dosyası**' nı seçin.

   - **Kaynak** `SuppressMessage` dosyasında, uyarıyı oluşturan metodun üzerine kaynak dosyasına bir öznitelik ekler. Bu, gizleme daha keşfedilmesini sağlar.

   - **Gizleme dosyası içinde** `SuppressMessage` , projenin **GlobalSuppressions.cs** dosyasına bir öznitelik ekler. Bu, gizlemelerin yönetimini kolaylaştırır. `SuppressMessage` **GlobalSuppression.cs** öğesine eklenen özniteliğin da uyarıyı oluşturan yöntemi hedeflediğini unutmayın. Bu, uyarıyı küresel olarak göstermez.

     Kaynak dosyadaki uyarının engellenip engellenmeyeceğini kararınız veya gizleme dosyasında kodlama stilinize ve gereksinimlerinize göre değişiklik yapılıp yapılmayacağını belirtir.

## <a name="searching-and-filtering-code-analysis-results"></a><a name="BKMK_Search"></a> Kod analizi sonuçlarını arama ve filtreleme
 Uyarı iletilerinin uzun listelerinde arama yapabilir ve çok projeli çözümlerde uyarıları filtreleyebilirsiniz.

 ![Kod Analizi penceresinde arama ve filtreleme](../test/media/ca-searchfilter.png "CA_SearchFilter")

 [!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]' De, tüm kod analizi uyarıları, uyarı önem düzeyine sahiptir.

## <a name="visual-basic-and-c-code-analysis-warnings"></a><a name="BKMK_Warnings"></a> Visual Basic ve C# kod analizi uyarıları
 Kod Analizi aşağıdaki uyarıları oluşturur:

 [CA1001: Atılabilen alanlara sahip türler atılabilir olmalıdır](https://msdn.microsoft.com/library/ms182172.aspx)

 [CA1821: Boş sonlandırıcıları kaldırın](https://msdn.microsoft.com/library/bb264476.aspx)

 [CA2213: Atılabilen alanlar atılmalıdır](https://msdn.microsoft.com/library/ms182328.aspx)

 [CA2229: Serileştirme oluşturucularını uygulayın](https://msdn.microsoft.com/library/ms182343.aspx)

 [CA2231: Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin](https://msdn.microsoft.com/library/ms182359.aspx)
