---
title: 'Örnek Excel uzantısı: TechnologyManager sınıfı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac9a4517fcf13dbb0e1d7a6f994092168723e660
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672160"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Örnek Excel Uzantısı: TechnologyManager Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sınıf, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> sınıfını genişletir ve [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] uzantısı için çekirdek hizmetler sağlamaktan sorumludur. Temel sınıfın birçok yöntemi olsa da, bu örnekte yalnızca bir alt kümesi kullanılır.

 Bazı yöntemler yalnızca bir özellik değeri döndürür. Yöntemlerin birçoğu, geliştiricinin kodlanmış UI test altyapısına varsayılan algoritma derlemesini geçersiz kılmasını sağlamak için tasarlanmıştır. Bu yöntemler, çerçeveye varsayılan algoritmayı kullanmasını söyleyen bir <xref:System.NotSupportedException> veya dönüş `null` oluşturur.

 Temel teknolojinin karmaşıklığına bağlı olarak, teknoloji yöneticisi kodunun geliştirilmesi birkaç haftadan birkaç aya kadar sürebilir. Excel potansiyel olarak çok kapsamlı teknoloji Yöneticisi oluşturma fırsatı sağlar. Bu örnek, özellikle Excel çalışma sayfaları ve hücreleri ile sınırlı biçimlendirme kullanır.

 Mümkün olduğunda, teknoloji Yöneticisi kodu, Excel işleminde çalışan eklentiden bilgi ayıklamak için `Communicator` sınıfı tarafından açılan .NET Remoting kanalını kullanır.

## <a name="com-visibility"></a>COM görünürlüğü
 Bu sınıfın ve <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> sınıfını genişleten her bir öğe sınıfının, sınıfların COM 'a görünür olduğundan emin olmak için `true` değeri olan <xref:System.Runtime.InteropServices.ComVisibleAttribute> sahip olduğuna dikkat edin.

## <a name="technologyname-property"></a>TechnologyName özelliği
 @No__t_0 özelliğinin bu geçersiz kılması, uzantının diğer her bileşeni için temeldeki teknolojiyi tanımlayan benzersiz ve anlamlı bir ad sağlamalıdır. Bu uzantı için, değer "Excel" dir.

## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel yöntemi
 @No__t_0 yönteminin bu geçersiz kılması, teknoloji yöneticisinin belirtilen tanıtıcı tarafından temsil edilen denetim için sunabileceği desteğin düzeyini gösteren bir sayı döndürür. Döndürülen değer arttıkça, teknoloji Yöneticisi denetimi destekleyebilirler. Bu durumda, yöntemi denetimi içeren pencereyi denetler ve bir Excel çalışma sayfası ise, yöntem en yüksek değeri döndürür; Aksi halde, hiçbir desteğin sağlanmadığını belirten sıfır döndürür.

## <a name="methods-to-get-an-element"></a>Öğe almak için Yöntemler
 Kodlanmış UI test çerçevesi tarafından bir tanıtıcı, ekranda bir nokta veya farklı bir teknolojiden bir öğe sağlayarak teknolojiye özgü bir öğe almak için kullanılan çeşitli önemli yöntemler vardır. Bu yöntemlerin kodu kendi kendine açıklayıcıdır. Temel yöntemler aşağıdaki gibidir:

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>

## <a name="parsequeryid-method"></a>ParseQueryId yöntemi
 Kodlanmış bir UI testi oluşturulduğunda, Kullanıcı testteki bazı veya tüm denetimlerin özellik değerlerini belirtebilir. Bu özellik değerleri test çerçevesi tarafından, test sırasında belirli kullanıcı arabirimi denetimlerini bulmak için kullanılan arama özellikleri adlı ad-değer çiftleri oluşturmak için kullanılır. Tüm arama özellikleri, her denetimi içeren teknolojideki her öğenin <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> özelliğinin değerini temsil eder. Bir denetimin bir test sırasında birkaç kez bulunması gerektiğinden, bu yöntem teknoloji yöneticisine verilen denetimin arama özelliklerini ayrıştırmayı iyileştirmek için bir yol sağlar. Bu yöntem ayrıca Framework 'ün bu denetimin sonraki aramalarında kullanabileceği bir tanımlama bilgisi döndürür. Bu yöntemin uygulanması, arama özelliklerini ayrıştırmak için <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> yöntemini kullanır.

## <a name="matchelement-method"></a>MatchElement yöntemi
 Teknoloji Yöneticisi tarafından bir denetim araması gerçekleştirmek için, olası eşleşmelerin dizisini döndürmek üzere <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> metodunu uygulayabilir veya <xref:System.NotSupportedException> oluşturarak çerçeveye kendi arama algoritmasını kullanmasını söyler. Her iki durumda da, bu uygulamanın yeniden <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> yöntemini kullandığı <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> yöntemini uygulamanız gerekir.

## <a name="navigation-methods"></a>Gezinti yöntemleri
 Bu yöntemler, UI hiyerarşisinden belirtilen öğenin üst, alt veya Eşdüzey öğelerini alır. Kod basittir ve açıkça açıklama eklenir.

## <a name="getexcelelement-internal-method"></a>Getexcele, Iç yöntemi
 Bu iç yöntem bir pencere tutamacı ve bir Excel öğesi hakkında bilgi alır ve istenen Excel öğesini döndürür.

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager><xref:System.NotSupportedException>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
